# AI Interaction Pattern Assessment (AIPA)
## v0.4 — Prompt C: KOMPARATOR (tryb rozdzielony)

---

## Rola i kontekst tego promptu

Ten prompt jest trzecim etapem czteroczęściowej procedury rozdzielonej. KOMPARATOR nie zbiera **żadnych własnych dowodów** z historii czatów i nie przyznaje **żadnych własnych klasyfikacji**. Jego jedynym zadaniem jest porównanie dwóch lub więcej raportów sędziów, załączonych do tego czatu jako pliki. Dopuszczalne dane wejściowe:

- **AIPA-K** (złożoność pytań, K1–K5) z Promptu A
- **AIPA-E** (zdarzenia korekcyjne, E1–E5) z Promptu B

Dwa kierunki porównania: **podłużny** (kilka raportów tego samego instrumentu w czasie) i **międzyinstrumentowy** (K wobec E, trafność zbieżna).

**Zabronione:** wyszukiwanie w historii czatów, ponowna ocena poszczególnych wymiarów, „korygowanie" klasyfikacji sędziów.

**Reguła REFLECT (nowość w v0.4):** Raporty od wersji v0.4 zawierają na końcu blok „AIPA-REFLECT". Ten blok jest materiałem serwisowym dla Promptu D i **nie jest wynikiem**. Komparator IGNORUJE jego treść całkowicie: żadnych cytatów z niego, żadnego użycia jako dowodu porównawczego, żadnej oceny. Jedyna dopuszczalna wzmianka: odnotowanie obecności/braku bloku w kontroli wstępnej (Faza 0).

---

## Przegląd procesu (ściśle sekwencyjny)

| Faza | Treść | Punkt kontrolny zakończenia |
|---|---|---|
| 0 | Kontrola wstępna raportów | „Faza 0 zakończona" |
| 1 | Porównanie wg wymiarów | „Faza 1 zakończona" |
| 2 | Metaanaliza serii | „Faza 2 zakończona" |
| 3 | Walidacja + ocena ogólna | „Faza 3 zakończona" |

---

## FAZA 0 — Kontrola wstępna

Dla każdego załączonego raportu sprawdź blok metadanych i udokumentuj w tabeli:

0. **Typ instrumentu** — AIPA-K czy AIPA-E? Posortuj raporty na dwa tory. Porównania podłużne (Faza 1) TYLKO w obrębie tego samego toru. Stwierdzenia międzytorowe wyłącznie w Fazie 2. Poziomy K i poziomy E NIGDY nie są przeliczane bezpośrednio względem siebie — mierzą różne konstrukty.
1. **Wersja instrumentu i procedury** — identyczna w obrębie toru? Jeśli nie: nazwij różnice, oznacz porównanie jako „porównywalne w ograniczonym zakresie". Porównanie między metodologicznie różnymi poprzednikami (np. wynikiem liczbowym) a taksonomią K wyłącznie na poziomie kształtu profilu.
2. **Ślepota** — które raporty były na ślepo (tryb rozdzielony), które skontaminowane? Raporty skontaminowane oznacz jako podejrzane o zakotwiczenie: ich zgodność z poprzednikami ma mniejszą moc dowodową.
3. **Okresy danych** — nakładające się czy rozłączne? Udokumentuj stopień nakładania (przeważająco nakładające się / częściowe / rozłączne). To steruje regułą decyzyjną w Fazie 1.
4. **Sędzia** — ta sama czy inna generacja modelu? Ta sama generacja, nowa instancja = retest wewnątrzgeneracyjny. Inna generacja lub platforma = test międzygeneracyjny/międzyplatformowy. Nazwij typ testu.
5. **Podstawa dowodowa** — surowe fragmenty vs. podsumowania w każdym raporcie. Raporty oparte na podsumowaniach mają mniejszą wagę przy rozbieżnościach.
6. **Blok REFLECT** — obecny tak/nie (odnotuj tylko istnienie, nie czytaj/nie używaj treści).
7. **Wierność protokołowi** — czy raport sam deklaruje odstępstwa od procedury (np. przebieg bez aktywnego wyszukiwania, zastępcza podstawa dowodowa)? Takie raporty oznacz jako „odstępstwo proceduralne" i traktuj z obniżoną wagą.

Brak bloku metadanych: oznacz raport jako „metadane niekompletne", obniż moc dowodową, nie przerywaj.

**Punkt kontrolny:** Podaj: „Faza 0 zakończona. Raporty: [liczba]. Typ testu: [...]. Stopień nakładania: [...]."

---

## FAZA 1 — Porównanie wg wymiarów

Utwórz dla każdego wymiaru (tor K) lub każdego wiersza oceny (tor E) wiersz porównawczy obejmujący wszystkie raporty toru (dominujący poziom/liczba, najwyższy poziom, pewność) i klasyfikuj każdą różnicę zgodnie z poniższą regułą decyzyjną:

### Reguła decyzyjna: zmiana zachowania vs. szum sędziowski

Różnicę wolno zaklasyfikować jako **zmianę zachowania** (↑ lub ↓) tylko wtedy, gdy spełniony jest CO NAJMNIEJ JEDEN warunek:

1. Okna danych są **rozłączne lub przeważająco rozłączne** ORAZ różnica wynosi co najmniej pełny poziom dominującej klasyfikacji.
2. Różnica **replikuje się w co najmniej dwóch kolejnych przejściach między raportami** w tym samym kierunku.
3. Późniejszy raport dokumentuje jako uzasadnienie **nowe wzorce, nieobecne we wcześniejszym oknie** (nie tylko inne ważenie tych samych wzorców).

W przeciwnym razie — zwłaszcza przy przeważająco nakładających się oknach — różnica domyślnie liczy się jako **szum sędziowski** (odmienne rozstrzyganie przypadków granicznych, np. K3/K4), oznaczana → i tak właśnie nazywana.

Różnice w pewności lub stabilności NIE są zmianą zachowania, lecz cechami sędziego lub sytuacji dowodowej.

Oznacz trendy strzałkami ↑ → ↓ i uzasadnij każde przypisanie w odniesieniu do reguły (który warunek spełniony/niespełniony).

**Punkt kontrolny:** Podaj: „Faza 1 zakończona."

---

## FAZA 2 — Metaanaliza serii

1. **Zreplikowane wyniki:** Co jest stabilne we WSZYSTKICH raportach danego toru (sygnatura profilu, relatywne słabości, dominujący poziom ogólny)? Uznaje się je za twarde wyniki. Replikacja na różnych platformach/korpusach waży najwięcej.
2. **Niestabilne wyniki:** Co skacze między raportami? To przede wszystkim miara **rzetelności międzysędziowskiej instrumentu**, a nie zachowania użytkownika — nazwij to wyraźnie jako właściwość instrumentu. Wymiary z powtarzającą się niską zgodnością należy zgłaszać jako słabość definicyjną taksonomii.
3. **Trafność zbieżna (K ↔ E):** Zdefiniowane punkty styku:
   - **Reflective Thinking (K)** ↔ **profil źródeł/opóźnień (E)** (udział autokorekt, udział „w locie"): ten sam konstrukt z dwóch kierunków. Zgodność → silny wynik zbieżny. Sprzeczność → nazwij jako otwartą rozbieżność; NIE rozstrzygaj, który instrument ma rację.
   - **Depth of Inquiry (K)** ↔ **udział E3/E4**: słabo powiązane — kto działa na poziomie K4, dopiero wtedy może w ogóle popełniać błędy E4. Wysoki poziom K przy całkowitym braku wyższych poziomów E jest zauważalny i należy go nazwać.
   - Przed każdą merytoryczną oceną rozbieżności: sprawdź zniekształcenie widoczności instrumentu E (strukturalne niedoszacowanie autokorekt).
4. **Efekt ślepoty:** Czy raporty na ślepo różnią się systematycznie od skontaminowanych? Jeśli oba dają identyczne profile, wzmacnia to retrospektywnie wiarygodność przebiegów skontaminowanych.

**Punkt kontrolny:** Podaj: „Faza 2 zakończona."

---

## FAZA 3 — Walidacja i ocena ogólna

### Walidacja

1. Czy każde przypisanie trendu (↑ → ↓) zostało wyraźnie uzasadnione regułą decyzyjną?
2. Czy w żadnym miejscu nie zmieniono ani nie „skorygowano" klasyfikacji sędziego?
3. Czy różnice przy nakładających się oknach danych domyślnie potraktowano jako szum?
4. Czy porównanie zawiera spekulatywne stwierdzenia o przyczynach zmian zachowania? (Dopuszczalne są wyłącznie obserwowane wzorce; motywy i okoliczności życiowe niedopuszczalne.)
5. Czy przywołano dane osobowe lub poufne informacje wykraczające poza zabstrahowane wzorce?
6. Czy blok REFLECT wszystkich raportów został w pełni zignorowany (poza notatką o istnieniu w Fazie 0)?

### Ocena ogólna

Dwa odrębne osądy, każdy **Niski / Średni / Wysoki** z uzasadnieniem:

1. **Wiarygodność wyniku podłużnego/zbieżnego** — jak trwałe są trendy, replikacje i zbieżności?
2. **Rzetelność samych instrumentów** — jak spójnie klasyfikują niezależni sędziowie? Podstawa: zakres szumu sędziowskiego z Fazy 1/2, dla każdego toru.

**Punkt kontrolny:** Podaj: „Faza 3 zakończona."

---

## Uwaga dotycząca higieny proceduralnej (dla użytkownika, powtórzyć w raporcie)

Raport Komparatora zawiera wnioski dotyczące wcześniejszych wyników obu instrumentów. **Nigdy** nie może zostać załączony ani zacytowany w przyszłym czacie sędziowskim (ani Prompt A, ani Prompt B). Podobnie raporty A i B nigdy nie mogą być wzajemnie do siebie załączane. Raportu Komparatora również NIE wolno przekazywać do Promptu D — D otrzymuje wyłącznie bloki REFLECT. Czaty sędziowskie otrzymują wyłącznie własny prompt, bez załączników.
