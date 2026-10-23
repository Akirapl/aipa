[English](README.md) | [Deutsch](README.de.md) | **Polski**

# AIPA — AI Interaction Pattern Assessment

Framework do oceny *kształtu* rozmowy człowieka z AI — nie tego, co wygenerował model, lecz tego, jak pyta osoba i jak dobrze wychwytywane są błędy — z wykorzystaniem izolowanych sędziów LLM zamiast samooceny.

## Problem

Odpowiedzi stały się tanie. Prompt wchodzi, gotowo wyglądająca odpowiedź wychodzi, kilka sekund później — a tarcie, które kiedyś wymuszało prawdziwe zrozumienie, zniknęło. Każda istniejąca ewaluacja AI mierzy jakość wyniku modelu. Żadna nie zadaje innego pytania: czy *ta konkretna wymiana* rzeczywiście buduje zrozumienie i wyłapuje własne błędy, czy po prostu szybko produkuje coś wiarygodnie brzmiącego?

AIPA zaczęło się jako próba odpowiedzi na to pytanie w odniesieniu do moich własnych rozmów — potraktowania transkryptu jako danych zamiast polegania na przeczuciu, czy wymiana zdań „poszła dobrze".

## Jak to jest zbudowane

Dwa niezależne instrumenty dzielą jedną metodykę:

- **AIPA-K** klasyfikuje strukturalną *złożoność* zadawanych pytań (K1–K5) w ośmiu wymiarach behawioralnych: curiosity, depth of inquiry, iterative learning, cross-domain integration, problem-solving behaviour, information seeking, reflective thinking, experimentation.
- **AIPA-E** klasyfikuje *zdarzenia korekcyjne* (E1–E5). Nie „błędy" — błąd wymaga prawdy podstawowej (ground truth), którą sędzia nie zawsze dysponuje w sposób pewny. Zdarzenie korekcyjne jest bezpośrednio obserwowalne w transkrypcie: przesłanka, założenie lub twierdzenie zostaje zrewidowane, wycofane lub wykazane jako błędne — przez użytkownika, przez model lub przez rzeczywistość (np. nieudany test). Oceniane na trzech niezależnych osiach: dotkliwość, źródło, opóźnienie.

Oba działają poprzez cztery izolowane prompty sędziowskie, każdy uruchamiany w osobnej, świeżej sesji, tak by żaden sędzia nigdy nie widział raportu innego:

| Prompt | Rola | Widzi |
|---|---|---|
| A — Sędzia Złożoności | Klasyfikuje K1–K5 | Historia czatów konta, przez wyszukiwanie - bez załączników, na ślepo |
| B — Sędzia Korekt | Klasyfikuje E1–E5 | Historia czatów konta, przez wyszukiwanie - bez załączników, na ślepo, niezależnie od A |
| C — Komparator | Porównuje raporty między przebiegami i instrumentami | Wyłącznie zablokowane raporty sędziów - ich bloki Reflect są ignorowane |
| D — Maintainer | Proponuje kolejną wersję | Wyłącznie zgromadzone bloki Reflect (opcjonalnie aktualne treści promptów) - nigdy faktyczne wyniki |

Wewnątrz każdego sędziego fazy przebiegają ściśle po kolei i blokują się, zanim rozpocznie się kolejna: deklaracja kontaminacji, zbieranie dowodów (minimalne pokrycie domen jest wymuszone, nie opcjonalne), klasyfikacja (następnie zamrożona), walidacja i samokrytyka oraz czytelny maszynowo blok Reflect, który zasila Maintainera.

Dwie zasady utrzymują uczciwość instrumentu: **reguła odrzucania**, która odrzuca każdy dowód dotyczący *samego AIPA* — aby instrument nie mógł oceniać własnej pracy domowej — oraz **reguła atrybucji**, która ocenia wyłącznie strukturę pytań człowieka, nigdy złożoność odpowiedzi modelu.

To, że czterej sędziowie działają jako osobne prompty, jest zamierzonym projektem, nie przypadkiem. Wersja zorkiestrowana przez API została wstępnie zaplanowana i odłożona — ręczna izolacja ułatwiała gwarantowanie braku kontaminacji, a co ważniejsze, ułatwiała audyt.

## Co wynikło z jego stosowania

- Testy międzyplatformowe ujawniły prawdziwy błąd metodologiczny, nie tylko dziwactwo Claude'a: przebieg na GPT pokazał, że pozwolenie sędziemu na pracę z już podsumowanym kontekstem zamiast ze świeżego wyszukiwania wprowadza niekontrolowane zniekształcenie selekcji. Prompt B teraz twardo przerywa działanie zamiast kontynuować na fragmentach.
- *Reflective thinking* okazało się wymiarem o najniższej zgodności w powtarzanych, niezależnych przebiegach — stabilny wzorzec między wersjami, nie szum, i teraz nazwany cel dla v0.5.
- Ostatni pełny przebieg zebrał dowody z 12 niezależnych domen konwersacyjnych — dwukrotność wymuszonego przez protokół minimum — obejmujących materiał techniczny, administracyjny i codzienny, a instrument sprawdził się również poza wąskim polem testowym.
- Instrument jest zaprojektowany, by się sam rewidować: Prompt D nigdy nie widzi pojedynczego wyniku, tylko logi Reflect z przeszłych przebiegów — ta pętla napędza otwarte punkty już zaplanowane na v0.5.

## Znane ograniczenia

- Gdy jako dowód dostępne są wyłącznie podsumowania rozmów (nie surowe transkrypty), AIPA-E wyraźnie obniża pewność na dotkniętych osiach zamiast wymuszać klasyfikację.
- Dane o rzetelności międzysędziowskiej są wciąż skąpe. Więcej niezależnych przebiegów — najlepiej od innych użytkowników, na innych rozmowach — wzmocniłoby je szybciej niż kolejne przebiegi jednej osoby.

## Status

Aktywny, obecnie **v0.4**. AIPA-K i AIPA-E wersjonują się niezależnie. Kilka zmian dla v0.5 jest już zaplanowanych na podstawie wyników Maintainera.

## Struktura repozytorium

```
/prompts/en/   Prompty A–D, angielski (kanoniczny)
/prompts/de/   Prompty A–D, niemiecki (oryginał)
/prompts/pl/   Prompty A–D, polski
/examples/     Zarezerwowane na zanonimizowane przykładowe przebiegi (jeszcze brak)
README.md      Wersja angielska
README.de.md   Wersja niemiecka
README.pl.md   Ten plik (polski)
LICENSE
```

## Jak z tego korzystać

Sędziowie to prompty, nie kod. Uruchamiaj je pojedynczo, każdy w świeżym czacie bez załączonych plików:

1. Uruchom Prompt A w świeżym czacie na platformie, której rozmowy chcesz ocenić. Sędzia sam przeszukuje historię czatów tego konta; jeśli wyszukiwanie w historii nie jest tam dostępne, celowo przerywa pracę - wklejony transkrypt go nie zastąpi. Zapisz zablokowany raport.
2. Uruchom Prompt B w ten sam sposób, w osobnym świeżym czacie → zapisz zablokowany raport.
3. Podaj oba zablokowane raporty - nigdy surowe rozmowy - do Promptu C w celu porównania międzyinstrumentowego.
4. Gdy bloki Reflect zgromadzą się z kilku przebiegów, podaj wyłącznie je do Promptu D, aby uzyskać listę zmian dla kolejnej wersji.

Uruchamiaj wszystkie cztery prompty jednej serii oceny w **tym samym torze językowym** (wszystkie z `/prompts/pl/`, wszystkie z `/prompts/en/` lub wszystkie z `/prompts/de/`). Trzy tory to wierne tłumaczenia tej samej metodyki, ale czytelny maszynowo blok Reflect używa innych nazw pól w każdym języku, a Prompt D oczekuje nazw pól właściwych dla swojego toru.

## Autor

**Dawid Kulik, B. Eng** — niezależny twórca z wykształceniem inżynierskim, który zbudował AIPA, by zamienić pytanie „czy ta rozmowa faktycznie poszła dobrze?" w coś mierzalnego zamiast przeczucia.

- GitHub: [@akirapl](https://github.com/akirapl)
- Kontakt: akira3179082@gmail.com

## Licencja

MIT.
