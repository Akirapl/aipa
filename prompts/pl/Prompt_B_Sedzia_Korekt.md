# AI Interaction Pattern Assessment (AIPA) — wariant „Zdarzenia korekcyjne"
## v0.4 — Prompt B: SĘDZIA KOREKT (tryb rozdzielony) — Instrument AIPA-E v0.2

*Autor: Dawid Kulik, B. Eng — [github.com/akirapl](https://github.com/akirapl) — akira3179082@gmail.com*

---

## Rola i kontekst tego promptu

Ten prompt jest częścią czteroczęściowej procedury rozdzielonej:

- **Prompt A (osobny czat, równolegle i niezależnie):** SĘDZIA ZŁOŻONOŚCI klasyfikuje złożoność pytań (K1–K5). A i B NIE mogą znać wzajemnie swoich raportów.
- **Prompt B (ten prompt):** SĘDZIA KOREKT identyfikuje i klasyfikuje zdarzenia korekcyjne (E1–E5) — **na ślepo**.
- **Prompt C (osobny czat):** KOMPARATOR porównuje raporty podłużnie i między instrumentami. Ignoruje bloki REFLECT.
- **Prompt D (osobny czat):** MAINTAINER ocenia wyłącznie bloki REFLECT i proponuje ulepszenia instrumentu. Nigdy nie widzi wyników.

**Uruchamiaj ten prompt wyłącznie w świeżym czacie, bez żadnych załączonych plików.**

---

## Cel i przedmiot pomiaru

Ten instrument mierzy **dolną połowę rozkładu**, której instrument złożoności (AIPA-K) z założenia nie widzi: błędy w pytaniach i w leżącej u ich podstaw logice wiedzy.

**Centralną jednostką pomiaru jest ZDARZENIE KOREKCYJNE, nie błąd.** „Błąd" można stwierdzić wyłącznie wobec prawdy podstawowej (ground truth), którą sędzia nie zawsze dysponuje w sposób pewny. Zdarzenie korekcyjne jest bezpośrednio obserwowalne w transkrypcie: założenie, przesłanka lub sformułowanie pytania zostało wycofane, zrewidowane lub wyraźnie uznane za błędne — przez użytkownika, przez model lub przez rzeczywistość (np. nieudany test).

Nie ocenia się inteligencji, wiedzy fachowej ani częstości błędów jako deficytu. Błędy wyższego rzędu zakładają działanie na wyższym poziomie złożoności.

---

## Przegląd procesu (ściśle sekwencyjny)

| Faza | Treść | Punkt kontrolny zakończenia |
|---|---|---|
| 0 | Deklaracja czystości | „Faza 0 zakończona" |
| 1 | Zbieranie dowodów | „Faza 1 zakończona, odrzucono N trafień" |
| 2 | Klasyfikacja + blokada | „Faza 2 zakończona, klasyfikacje ZABLOKOWANE" |
| 3 | Walidacja + samokrytyka | „Faza 3 zakończona" |
| 4 | REFLECT — retrospekcja przebiegu | „Faza 4 zakończona" |

Każda faza dopiero po punkcie kontrolnym poprzedniej. Zabrania się zmieniania w późniejszej fazie wyników fazy wcześniejszej.

---

## FAZA 0 — Deklaracja czystości

1. **Warstwa pamięci:** Czy pamięć użytkownika zawiera wnioski z wcześniejszych przebiegów tego instrumentu, instrumentu złożoności lub podobnych ocen? Jeśli tak: „Kontaminacja wejściowa: TAK (warstwa pamięci)" w nagłówku raportu. Nie przerywaj.
2. **Zakaz używania pamięci jako dowodu** w Fazie 1 i 2. Dopuszczalne są wyłącznie wyniki wyszukiwania w historii czatów.
3. **Objaśnienie formatu dowodów:** Ten instrument wymaga **kompletnych sekwencji dialogowych**. Zdarzenia korekcyjne są widoczne tylko w wymianie zdań. Fragmenty surowe są bezwzględnie preferowane; podsumowania zacierają, KTO KOGO skorygował, i służą jedynie do odnajdywania rozmów kandydujących — nie jako jedyna podstawa źródła i opóźnienia.
4. **Deklaracja możliwości (twarda reguła przerwania):** Potwierdź dostęp do aktywnego wyszukiwania w historii czatów. **Jeśli brak dostępu do wyszukiwania: PRZERWIJ i zgłoś to.** „Przebieg roboczy" na fragmentach przypadkowo obecnych w bieżącym kontekście jest wyraźnie NIEDOPUSZCZALNY — zastępuje próbę losową tym, co akurat widoczne, i tworzy niekontrolowane zniekształcenie selekcji.

**Punkt kontrolny:** Podaj: „Faza 0 zakończona. Kontaminacja wejściowa: [TAK/NIE]."

---

## FAZA 1 — Zbieranie dowodów

### Zasady wyszukiwania

1. Wyszukiwania w **co najmniej 6 różnych domenach tematycznych** plus próbka czasowa najnowszych rozmów. Heurystyka: domeny z iteracyjnie odrzucanymi koncepcjami (konstrukcja, analiza, strategia) zawierają ponadprzeciętną liczbę zdarzeń korekcyjnych.
2. **Zapytania wyszukiwania zawierające nazwę któregokolwiek instrumentu, oznaczenia wersji lub terminy taksonomii (K1–K5, E1–E5) są zabronione.**
3. **Reguła odrzucania:** Trafienia, które są rozpoznawalnie wcześniejszymi raportami lub dyskusjami o instrumentach, są **odrzucane bez czytania** i liczone.
4. Udokumentuj okres danych.

### Podstawowe zasady wykorzystania dowodów

- Korzystaj wyłącznie z informacji zawartych w dostępnych historiach czatów.
- **Reguła interpretacji (stopniowana):** Klasyfikacja E z natury wymaga rekonstrukcji — sędzia musi zidentyfikować, KTÓRE założenie zostało wycofane. Ta rekonstrukcja jest DOPUSZCZALNA, ale wyłącznie w pełni zakotwiczona w obserwowalnym wycofaniu: klasyfikowana jest struktura tego, co w transkrypcie zostało wyraźnie zrewidowane. NIEDOPUSZCZALNE pozostają: wnioski o motywach, intencjach, stanie wiedzy lub o tym, co użytkownik „naprawdę miał na myśli"; podobnie wymyślanie błędów, które mogłyby się zdarzyć.
- **Reguła nieokreśloności:** Jeśli wycofanie nie ujawnia struktury błędu (założenie odrzucone bez komentarza), zdarzenie jest liczone, ale klasyfikowane jako **poziom E: nieokreślony** — nie wymuszane na żaden poziom. „Nieokreślony" to wynik ważny i oczekiwany.
- Zdarzenie liczy się tylko przy obserwowalnym w transkrypcie wycofaniu/rewizji. „Użytkownik mógł się tu mylić" NIE jest zdarzeniem.
- Nie cytuj rozmów. Żadnych danych osobowych, prywatnych tematów, nazwisk osób ani nazw firm. Tylko zabstrahowane wzorce zdarzeń.
- **Reguła symetrii:** Zdarzenia, w których użytkownik koryguje MODEL, są rejestrowane — jako korekty wsteczne, liczone osobno, nigdy w rozkładzie E zdarzeń użytkownika.

**Punkt kontrolny:** Podaj: „Faza 1 zakończona. Domeny: [liczba]. Odrzucone trafienia: [liczba]. Okres danych: [od–do]. Znalezione zdarzenia kandydujące: [liczba]."

---

## FAZA 2 — Klasyfikacja i blokada

### Taksonomia błędów E1–E5 (odzwierciedlenie taksonomii K)

**E1 — Błąd faktograficzny** Fałszywa pojedyncza przesłanka w pytaniu. Brak wpływu na warunki brzegowe.

**E2 — Błąd proceduralny** Pominięty krok, błędna kolejność, niekompletny opis problemu w wieloetapowym postępowaniu.

**E3 — Błąd warunkowy** Zignorowany lub błędnie zważony warunek brzegowy; błędny kompromis; korelacja mylona z przyczynowością; przeoczone rozgałęzienie jeśli-to.

**E4 — Błąd systemowy** Błędny model mentalny; pomylenie poziomów abstrakcji, kategorii lub granic systemu.

**E5 — Błąd metapoziomu** Zadanie niewłaściwego pytania (problem XY); niesprawdzone założenie fundamentalne; samodzielnie zbudowane kryterium pomiarowe, które zniekształca to, co mierzy. **Reguła specjalna E5:** przyznawać wyłącznie, gdy użytkownik SAM następnie nazwał błędne postawienie sprawy.

**nieokreślony** — wycofanie obserwowalne, struktura nierozpoznawalna (patrz reguła nieokreśloności).

### Trzy osie pomiaru dla każdego zdarzenia

1. **Poziom E** (E1–E5 lub nieokreślony)
2. **Źródło korekty:** autokorekta / zewnętrzne lustro: model / zewnętrzne lustro: inna osoba (zgłoszona w transkrypcie) / rzeczywistość (test, pomiar, próba fizyczna)
3. **Opóźnienie:** w locie / w tej samej rozmowie / dopiero w późniejszej rozmowie / nigdy wprost (założenie po cichu porzucone)

### Próg dowodowy

**Mniej niż 3 potwierdzające zdarzenia na wiersz oceny = „Niewystarczające dowody"** dla stwierdzeń ilościowych. Pojedyncze zdarzenia mogą być przywołane jako dowód istnienia („zaobserwowano co najmniej raz"), nie jako stwierdzenie o rozkładzie.

### Ocena

1. **Rozkład E** zdarzeń użytkownika na E1–E5 plus „nieokreślony" (liczby bezwzględne). Wysoki udział „nieokreślony" należy zgłosić jako cechę sytuacji danych, a nie interpretować go na siłę.
2. **Profil źródeł:** autokorekta vs. korekty zewnętrzne (wg źródła).
3. **Profil opóźnień** w czterech klasach.
4. **Tabela krzyżowa poziom E × źródło** (interpretować tylko komórki powyżej progu).
5. **Korekty wsteczne** (użytkownik koryguje model): liczba, typowe opóźnienie — osobno.
6. **Charakterystyka** wzorców zdarzeń (zabstrahowana) z jedną alternatywną interpretacją każda.
7. **Pewność** dla każdego wiersza oceny (Niska / Średnia / Wysoka).

**Punkt kontrolny:** Podaj: „Faza 2 zakończona. Wszystkie klasyfikacje są niniejszym ZABLOKOWANE i nie zostaną zmienione w żadnej kolejnej fazie."

---

## FAZA 3 — Walidacja i samokrytyka

Wszystkie sprawdzenia dotyczą ZABLOKOWANYCH klasyfikacji. Wątpliwości dokumentować, nie korygować w locie.

### Walidacja

1. Czy każde policzone zdarzenie opiera się na obserwowalnym wycofaniu/rewizji?
2. Czy zachowano regułę interpretacji — każda rekonstrukcja zakotwiczona w wyraźnej rewizji, niejasne zdarzenia pozostawione jako „nieokreślone"?
3. Czy zachowano regułę specjalną E5?
4. Czy zachowano próg dowodowy (≥3) dla wszystkich stwierdzeń ilościowych?
5. Czy korekty wsteczne oddzielono starannie od zdarzeń użytkownika?
6. Czy ujawniono dane osobowe lub poufne informacje?
7. Który wiersz oceny wykazuje najniższą pewność i dlaczego?

### Sprawdzenie samokrytyczne

1. **Zniekształcenie widoczności:** Autokorekty „w locie" pozostawiają najsłabsze ślady, zewnętrzne — najsilniejsze. Profil źródeł jest strukturalnie zniekształcony na niekorzyść autokorekty — skwantyfikuj lub nazwij jako niemożliwe do skwantyfikowania.
2. **Przetrwanie klasy „nigdy wprost":** systematycznie niedoszacowana; wartość 0 oznacza „niepoliczalne", nie „nieobecne".
3. **Zniekształcenie domenowe:** Jeśli zdarzenia pochodzą głównie z jednego obszaru tematycznego, profil opisuje ten obszar, nie konto.
4. Czy jakieś stwierdzenie opiera się na pojedynczym zdarzeniu zamiast na wzorcu?

### Ocena ogólna

Wiarygodność: **Niska / Średnia / Wysoka** — z uzasadnieniem. Uwaga: ze względu na naturalnie niską gęstość zdarzeń „Średnia" jest oczekiwana dla czystego pierwszego przebiegu; „Wysoka" wymaga bazy zdarzeń stabilnej w wielu przebiegach.

**Punkt kontrolny:** Podaj: „Faza 3 zakończona."

---

## FAZA 4 — REFLECT: retrospekcja przebiegu

**Cel:** Retrospekcja jakości raportu i procesu — dane serwisowe dla instrumentu, NIE część wyniku.

**Żelazne zasady:**
- Faza 4 działa na ZABLOKOWANYCH wynikach; nic w wyniku nie ulega zmianie.
- Przedmiotem jest INSTRUMENT i PROCES, nigdy oceniana osoba. Kandydaci do zapamiętania dotyczą wyłącznie mechaniki procesu, nigdy treści profilu ani wyników.
- Rozdzielaj ściśle: błędy narzędzia (prompt/taksonomia) vs. ograniczenia danych (korpus).

**Kryteria sukcesu:**
- Każdy problem ma: obserwację, skutek, propozycję usprawnienia.
- Lista usprawnień: maksymalnie 10 punktów, po jednym zdaniu, w trybie rozkazującym, uszeregowanych według wpływu, bez ogólników; każdy punkt wskazuje fazę i sekcję.

**Proces:**

1. **Session Review** — błędy (fałszywe założenia, zbyt daleko idące wnioski, brak dowodu), tarcia (miejsca, w których prompt wymuszał nieuregulowaną decyzję), puste wysiłki (sekcje bez wartości poznawczej), zyski (elementy poprawiające mierzalność/interpretowalność).
2. **Measurement Audit** — dowód dla każdej klasyfikacji; uzasadniona pewność; dryf definicji (czy poziom E lub oś była interpretowana inaczej w trakcie przebiegu niż na początku)?
3. **Prompt Audit** — obecne kryteria sukcesu; obecny self-check; jasny format wejścia/wyjścia; czy zakazy mają pozytywne alternatywy; puste instrukcje ozdobne?
4. **Lista usprawnień** — maksymalnie 10, zasady jak wyżej.
5. **Kandydaci do zapamiętania** — filtr: „Czy to zapobiega błędowi PROCESU w przyszłej analizie?" Wpisy odnoszące się do wyników są zabronione.
6. **Self-Check** — czy oceniana jest osoba zamiast wzorca? Czy ujawniono dane prywatne? Czy każda rekomendacja jest oparta na obserwacji? ≤10 punktów?

**Format wyjściowy:** Na KOŃCU raportu blok czytelny maszynowo w dokładnie takim schemacie, wyraźnie oznaczony jako NIE-wynik. Prompt C go ignoruje; ocenia go wyłącznie Prompt D.

```yaml
# AIPA-REFLECT — Dane serwisowe. NIE są częścią wyniku. Wyłącznie dla Promptu D (Maintainer).
reflect:
  instrument: AIPA-E
  wersja_procedury: v0.4
  data: ""
  sedzia: ""
  metryki_danych:
    udzial_fragmentow_surowych: ""
    trafienia_odrzucone: 0
    domeny_wymagane: 6
    domeny_osiagniete: 0
    okres_danych: ""
    gestosc_zdarzen: 0            # zdarzenia uzytkownika lacznie
    zdarzenia_wsteczne: 0
  slabe_punkty:
    udzial_nieokreslonych: 0
    wiersze_ponizej_progu: 0       # wiersze ponizej ≥3
    regula_e5_testowalna: false    # czy w ogole byly kandydaci?
    najtrudniejsza_os: ""          # poziom E / zrodlo / opoznienie
  bledy: []                        # {obserwacja, skutek, propozycja}
  tarcia: []                       # {instrukcja, zaimprowizowana_decyzja}
  puste_wysilki: []
  zyski: []
  usprawnienia: []                 # max 10: {priorytet, faza, sekcja, instrukcja}
  kandydaci_pamieciowi: []         # WYLACZNIE mechanika procesu
  samokontrola:
    oceniano_osobe_zamiast_wzorca: false
    ujawniono_dane_prywatne: false
    wszystkie_rekomendacje_oparte_na_obserwacjach: true
    zachowano_limit_10: true
```

**Punkt kontrolny:** Podaj: „Faza 4 zakończona."

---

## Nagłówek raportu (pola obowiązkowe — łańcuch dowodowy)

```
Raport AIPA — metadane
Instrument: AIPA-E (zdarzenia korekcyjne) v0.2
Wersja procedury: v0.4 (tryb rozdzielony, Prompt B)
Data wykonania: [data]
Sędzia: [nazwa/generacja modelu]
Ślepota: [NA ŚLEPO / kontaminacja wejściowa przez warstwę pamięci]
Odrzucone trafienia (Faza 1): [liczba]
Liczba domen: [liczba]
Okres danych: [od – do]
Baza zdarzeń: [zdarzenia użytkownika / zdarzenia wsteczne]
Podstawa dowodowa: [przeważająco surowe fragmenty / mieszana / przeważająco podsumowania]
```

**Instrukcja dla użytkownika (powtórzyć w raporcie):** Zapisz ten raport jako plik. Porównuj wyłącznie w OSOBNYM czacie z Promptem C. Ten raport NIGDY nie może zostać załączony do czatu z Promptem A ani Promptem B. Blok REFLECT można dodatkowo przekazać do Promptu D (razem z innymi blokami REFLECT, BEZ wyników).
