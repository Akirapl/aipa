# AI Interaction Pattern Assessment (AIPA) — wariant „Złożoność pytań"
## v0.4 — Prompt A: SĘDZIA ZŁOŻONOŚCI (tryb rozdzielony)

---

## Rola i kontekst tego promptu

Ten prompt jest częścią czteroczęściowej procedury rozdzielonej (split):

- **Prompt A (ten prompt):** SĘDZIA ZŁOŻONOŚCI klasyfikuje złożoność pytań (K1–K5) — **na ślepo**, bez znajomości wcześniejszych raportów.
- **Prompt B (osobny czat, równolegle i niezależnie):** SĘDZIA KOREKT klasyfikuje zdarzenia korekcyjne (E1–E5). A i B NIE mogą znać wzajemnie swoich raportów.
- **Prompt C (osobny czat):** KOMPARATOR porównuje raporty sędziów podłużnie (w czasie) i między instrumentami. Ignoruje bloki REFLECT.
- **Prompt D (osobny czat):** MAINTAINER (opiekun instrumentu) ocenia wyłącznie bloki REFLECT z wielu przebiegów i proponuje ulepszenia instrumentu. Nigdy nie widzi wyników.

**Uruchamiaj ten prompt wyłącznie w świeżym czacie, bez żadnych załączonych plików.**

---

## Cel

Analizuj wyłącznie historię czatów dostępną na tym koncie. Celem nie jest ocena osobowości, inteligencji ani wiedzy fachowej. Przedmiotem analizy jest strukturalna złożoność pytań i próśb, które stanowią dowód dla danego wymiaru. Nie ocenia się jakości odpowiedzi ani intensywności zachowania, lecz złożoność zadawanych pytań. Analiza służy wyłącznie opisowi zachowań użytkowych.

---

## Przegląd procesu (ściśle sekwencyjny)

| Faza | Treść | Punkt kontrolny zakończenia |
|---|---|---|
| 0 | Deklaracja czystości | „Faza 0 zakończona" |
| 1 | Zbieranie dowodów | „Faza 1 zakończona, odrzucono N trafień" |
| 2 | Klasyfikacja + blokada | „Faza 2 zakończona, klasyfikacje ZABLOKOWANE" |
| 3 | Walidacja + samokrytyka | „Faza 3 zakończona" |
| 4 | REFLECT — retrospekcja przebiegu | „Faza 4 zakończona" |

Kolejną fazę wolno rozpocząć dopiero po wyraźnym podaniu punktu kontrolnego fazy poprzedniej. Zabrania się zmieniania w późniejszej fazie wyników fazy wcześniejszej.

---

## FAZA 0 — Deklaracja czystości

1. **Warstwa pamięci (memory):** Czy dostępna pamięć użytkownika zawiera wnioski, wyniki lub oceny z wcześniejszych przebiegów tego instrumentu (lub bardzo podobnej pod względem treści oceny)?
   - Jeśli tak: odnotuj w nagłówku raportu „Kontaminacja wejściowa: TAK (warstwa pamięci)". NIE przerywaj.
   - Jeśli nie: odnotuj „Kontaminacja wejściowa: NIE".
2. **Zakaz używania pamięci jako dowodu:** Warstwa pamięci NIE może być używana jako źródło dowodów w Fazie 1 i 2. Dopuszczalnym dowodem są wyłącznie wyniki wyszukiwania w historii czatów (preferowane fragmenty surowe, podsumowania traktowane jako pomocnicze i wyraźnie oznaczone).
3. **Deklaracja możliwości:** Potwierdź dostęp do wyszukiwania w historii czatów. **Jeśli dostępu brak: przerwij i zgłoś to.** Przebieg zastępczy na fragmentach przypadkowo obecnych w bieżącym kontekście jest niedopuszczalny — instrument nie może działać bez dostępu do wyszukiwania.

**Punkt kontrolny:** Podaj: „Faza 0 zakończona. Kontaminacja wejściowa: [TAK/NIE]."

---

## FAZA 1 — Zbieranie dowodów

### Zasady wyszukiwania

1. Przeprowadź wyszukiwania w **co najmniej 6 różnych domenach tematycznych** (np. diagnostyka techniczna, praca projektowa, tematy koncepcyjne, sprawy formalne/urzędowe, codzienne zapytania, zadania redakcyjne). Dodatkowo: próbka czasowa najnowszych rozmów, aby ograniczyć błąd selekcji.
2. **Zapytania wyszukiwania zawierające nazwę tego instrumentu, oznaczenia wersji lub terminy taksonomii są zabronione.**
3. **Reguła odrzucania:** Trafienia, które są rozpoznawalnie wcześniejszymi raportami tego instrumentu lub dyskusjami o samym instrumencie, są **odrzucane bez czytania** i liczone.
4. Preferuj surowe fragmenty rzeczywistej wymiany zdań nad podsumowaniami. Jeśli klasyfikacja opiera się głównie na podsumowaniach, należy to zaznaczyć przy ocenie pewności.
5. Udokumentuj obserwowany okres danych (najwcześniejsza i najpóźniejsza data).

### Podstawowe zasady wykorzystania dowodów

- Korzystaj wyłącznie z informacji zawartych w dostępnych historiach czatów.
- Nie snuj domysłów.
- Oceniaj złożoność wyłącznie na podstawie obserwowalnej struktury pytań, nie na podstawie domniemanych intencji.
- Jeśli brak pytań potwierdzających dany wymiar, napisz wyraźnie „Niewystarczające dowody".
- Nie cytuj rozmów. Nie podawaj danych osobowych, prywatnych tematów, nazwisk osób ani nazw firm. Opisuj wyłącznie zabstrahowane wzorce pytań.
- **Reguła atrybucji:** Klasyfikowana jest wyłącznie struktura pytań UŻYTKOWNIKA. Złożoność pochodząca z odpowiedzi modelu nie jest dowodem. Przy podsumowaniach, w których pytanie i odpowiedź się zlewają: w razie wątpliwości klasyfikuj niżej lub oznacz jako niepewne.
- **Protokół przypadków granicznych:** Każdy przypadek, w którym przypisanie między dwoma sąsiednimi poziomami (zwłaszcza K3/K4) wydaje się nierozstrzygalne, jest liczony, a zastosowana heurystyka decyzyjna — odnotowana. To liczenie zasila Fazę 4.

**Punkt kontrolny:** Podaj: „Faza 1 zakończona. Domeny: [liczba]. Odrzucone trafienia: [liczba]. Okres danych: [od–do]."

---

## FAZA 2 — Klasyfikacja i blokada

### Taksonomia złożoności

**K1 — Faktograficzny / Punktowy** Pojedyncze pytanie merytoryczne z dokładnie jedną poprawną odpowiedzią. Pobranie definicji lub pojedynczych faktów, brak warunków brzegowych.

**K2 — Proceduralny / Wieloetapowy** Pytanie o wieloetapowy sposób postępowania lub z kontekstem. Sekwencyjne, bez konkurujących warunków brzegowych.

**K3 — Analityczny / Warunkowy** Pytanie z wieloma warunkami brzegowymi, porównaniami, kompromisami lub rozgałęzieniami typu jeśli-to. Wymaga ważenia opcji.

**K4 — Syntetyczny / Systemowy** Pytanie integruje wiele koncepcji lub dziedzin, celuje w projektowanie bądź architekturę lub antycypuje skutki drugiego rzędu.

**K5 — Generatywny / Meta** Pytanie kwestionuje samo postawienie problemu, sprawdza własne założenia, tworzy nowe struktury koncepcyjne lub jest rekurencyjne/autorefleksyjne.

### Wymiary analizy

Scharakteryzuj każdy wymiar na podstawie: dominującego poziomu złożoności (K1–K5), najwyższego zaobserwowanego poziomu, stabilności (stała / sporadyczna / rosnąca / malejąca — odnoszona wyłącznie do bieżącego okna danych), pewności (Niska / Średnia / Wysoka), uzasadnienia, charakterystyki obserwowanych pytań (zabstrahowana, bez cytatów), możliwej alternatywnej interpretacji. Bez pytań potwierdzających: „Niewystarczające dowody".

**1. Curiosity** — Tendencja do aktywnego odkrywania nowych tematów, pytania o mechanizmy działania i budowania wiedzy wykraczającej poza bezpośrednie rozwiązanie problemu. Wskaźnik: pytania dotyczą mechanizmu działania, nie tylko zastosowania.

**2. Depth of Inquiry** — Systematyczne pogłębianie poprzez pytania uzupełniające, ograniczenia, kontrprzykłady, szczegółowe analizy. Wskaźnik: warstwowe pytania uzupełniające, które wprowadzają warunki brzegowe lub kontrprzykłady do wcześniejszej odpowiedzi.

**3. Iterative Learning** — Powracanie do wcześniejszych tematów i ich rozwijanie w wielu rozmowach. Wskaźnik: powracające pytania budują na wcześniejszych wynikach zamiast je powtarzać.

**4. Cross-domain Integration** — Przenoszenie koncepcji między dziedzinami. Wskaźnik: pytania łączą wiele — najlepiej odległych — domen w jednym zapytaniu.

**5. Problem-solving Behaviour** — Rozwijanie trwałych procesów rozwiązywania problemów zamiast punktowych odpowiedzi. Wskaźnik: pytania celują w wielokrotnie użyteczne procedury lub analizy przyczyn źródłowych.

**6. Information Seeking** — Aktywne poszukiwanie źródeł, alternatyw, literatury, porównań, dowodów. Wskaźnik: pytania ważą ze sobą wiele źródeł lub opcji.

**7. Reflective Thinking** — Krytyczna ocena własnych założeń, strategii i decyzji. Wskaźnik: pytania czynią przedmiotem badania własne założenia użytkownika. **Doprecyzowanie v0.4:** Rozróżnij i wykaż osobno dwie podformy: (a) ZAPROJEKTOWANA refleksja — użytkownik buduje struktury/narzędzia, których celem jest sprawdzanie własnych założeń; (b) SPONTANICZNA refleksja — użytkownik kwestionuje własne założenia w trakcie procesu merytorycznego, bez strukturalnego przymusu. Dominujący poziom wymiaru należy wyznaczyć z OBU podform; wysoką ocenę opartą wyłącznie na podformie (a) należy oznaczyć. (Kontekst: ten wymiar wykazywał w dotychczasowych seriach najniższą zgodność między sędziami.)

**8. Experimentation** — Systematyczne testowanie sposobów postępowania, promptów, metod pracy. Wskaźnik: pytania celowo testują warianty względem siebie.

### Profil ogólny

- **Overall Interaction Profile** — typowy poziom złożoności we wszystkich wymiarach.
- **Profil złożoności:** rozkład wymiarów na K1–K5, dominujący poziom ogólny, najwyższy zaobserwowany poziom.
- **Trzy zaobserwowane mocne strony** i **trzy możliwości rozwoju.**

**Punkt kontrolny:** Podaj: „Faza 2 zakończona. Wszystkie klasyfikacje są niniejszym ZABLOKOWANE i nie zostaną zmienione w żadnej kolejnej fazie."

---

## FAZA 3 — Walidacja i samokrytyka

Wszystkie sprawdzenia dotyczą ZABLOKOWANYCH klasyfikacji. Wątpliwości należy dokumentować, a nie korygować w locie.

### Walidacja

1. Czy wszystkie klasyfikacje opierały się wyłącznie na obserwowalnej strukturze pytań?
2. Czy jakaś klasyfikacja zawiera spekulatywne wnioski?
3. Czy dla każdej klasyfikacji było wystarczająco dużo pytań potwierdzających?
4. Czy ujawniono dane osobowe lub poufne informacje?
5. Która klasyfikacja ma najniższą pewność i dlaczego?
6. Czy zachowano regułę atrybucji (tylko pytania użytkownika)?
7. Czy zachowano regułę odrzucania (wcześniejsze raporty odrzucone bez czytania)?
8. Czy przy Reflective Thinking wykazano podział na refleksję zaprojektowaną/spontaniczną?

### Sprawdzenie samokrytyczne

Świadomie spróbuj obalić własne klasyfikacje: mylenie długiego sformułowania z głębią strukturalną; wysoka ocena na podstawie pytania wyjątkowego zamiast wzorca; zniekształcenie przez dobór domen wyszukiwania lub okna czasowego. Wyraźnie udokumentuj wiarygodne interpretacje alternatywne.

### Ocena ogólna

Wiarygodność raportu: **Niska / Średnia / Wysoka** — z krótkim uzasadnieniem.

**Punkt kontrolny:** Podaj: „Faza 3 zakończona."

---

## FAZA 4 — REFLECT: retrospekcja przebiegu

**Cel:** Po każdej analizie retrospekcja jakości raportu i procesu oceny — jako dane serwisowe dla instrumentu, NIE jako część wyniku.

**Żelazne zasady:**
- Faza 4 działa na ZABLOKOWANYCH wynikach. Żaden wynik, żadna pewność, żadne sformułowanie wyniku nie ulega zmianie.
- Przedmiotem jest INSTRUMENT i PROCES, nigdy oceniana osoba. Kandydaci do zapamiętania mogą dotyczyć wyłącznie mechaniki procesu (np. „zapytania wyszukiwania z terminem X zwracają stare raporty"), nigdy treści profilu ani wyników.
- Rozdzielaj ściśle: błędy narzędzia (słabości promptu/taksonomii) vs. ograniczenia danych (właściwości dostępnego korpusu).

**Kryteria sukcesu:**
- Każdy zidentyfikowany problem ma: obserwację, skutek, propozycję usprawnienia.
- Lista usprawnień: maksymalnie 10 punktów, po jednym zdaniu, w trybie rozkazującym, uszeregowanych według wpływu, bez ogólników; każdy punkt wskazuje fazę i sekcję promptu, której dotyczy.

**Proces:**

1. **Session Review** — sprawdź raport i proces jego powstawania pod kątem: błędów (fałszywe założenia, zbyt daleko idące wnioski, brak dowodu), tarć (miejsca, w których prompt wymuszał nieuregulowaną decyzję i improwizację), pustych wysiłków (sekcje bez wartości poznawczej), zysków (elementy, które poprawiły mierzalność lub interpretowalność).
2. **Measurement Audit** — czy każda klasyfikacja ma dowód; czy każda pewność jest uzasadniona; czy wystąpił dryf definicji (czy poziom był interpretowany inaczej w trakcie przebiegu niż na początku)?
3. **Prompt Audit** — czy prompt ma: kryteria sukcesu, self-check, jasny format wejścia/wyjścia; czy zakazy mają pozytywne alternatywy; czy zawiera puste instrukcje ozdobne?
4. **Lista usprawnień** — maksymalnie 10, zasady jak w kryteriach sukcesu.
5. **Kandydaci do zapamiętania** — tylko wpisy, które przechodzą filtr: „Czy to zapobiega błędowi PROCESU w przyszłej analizie?" Wpisy odnoszące się do wyników są zabronione.
6. **Self-Check** — czy oceniana jest osoba zamiast wzorca? Czy ujawniono dane prywatne? Czy każda rekomendacja wynika z obserwacji? Czy jest ≤10 usprawnień?

**Format wyjściowy:** Na KOŃCU raportu, po wszystkich innych sekcjach, blok czytelny maszynowo w dokładnie takim schemacie. Blok jest w nagłówku wyraźnie oznaczony jako NIE-wynik. Prompt C go ignoruje; ocenia go wyłącznie Prompt D.

```yaml
# AIPA-REFLECT — Dane serwisowe. NIE są częścią wyniku. Wyłącznie dla Promptu D (Maintainer).
reflect:
  instrument: AIPA-K
  wersja_procedury: v0.4
  data: ""
  sedzia: ""
  metryki_danych:
    udzial_fragmentow_surowych: ""   # przewazajaco / mieszane / przewazajaco podsumowania
    trafienia_odrzucone: 0
    domeny_wymagane: 6
    domeny_osiagniete: 0
    okres_danych: ""
  slabe_punkty:
    przypadki_graniczne_lacznie: 0    # liczba nierozstrzygalnych przypadkow sasiednich poziomow
    przypadki_graniczne_k3_k4: 0
    heurystyka_przypadkow_granicznych: ""
    wymiar_najnizszej_pewnosci: ""
  bledy: []                           # {obserwacja, skutek, propozycja}
  tarcia: []                          # {instrukcja, zaimprowizowana_decyzja}
  puste_wysilki: []
  zyski: []
  usprawnienia: []                    # max 10: {priorytet, faza, sekcja, instrukcja}
  kandydaci_pamieciowi: []            # WYLACZNIE mechanika procesu
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
Instrument: AIPA-K (złożoność pytań)
Wersja procedury: v0.4 (tryb rozdzielony, Prompt A)
Data wykonania: [data]
Sędzia: [nazwa/generacja modelu]
Ślepota: [NA ŚLEPO / kontaminacja wejściowa przez warstwę pamięci]
Odrzucone trafienia (Faza 1): [liczba]
Liczba domen: [liczba]
Okres danych: [od – do]
Podstawa dowodowa: [przeważająco surowe fragmenty / mieszana / przeważająco podsumowania]
```

Bez pełnego bloku metadanych raport jest nieważny dla Promptu C.

**Instrukcja dla użytkownika (powtórzyć w raporcie):** Zapisz ten raport jako plik. Porównuj wyłącznie w OSOBNYM czacie z Promptem C. Ten raport NIGDY nie może zostać załączony do czatu z Promptem A ani Promptem B. Blok REFLECT można dodatkowo przekazać do Promptu D (razem z blokami REFLECT z innych przebiegów, BEZ wyników).
