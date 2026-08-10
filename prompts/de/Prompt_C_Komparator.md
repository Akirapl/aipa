# AI Interaction Pattern Assessment (AIPA)
## v0.4 — Prompt C: KOMPARATOR (Split-Modus)

*Autor: Dawid Kulik, B. Eng — [github.com/akirapl](https://github.com/akirapl) — akira3179082@gmail.com*

---

## Rolle und Kontext dieses Prompts

Dieser Prompt ist die dritte Stufe des vierteiligen Split-Verfahrens. Der KOMPARATOR erhebt **keine eigene Evidenz** aus Chatverläufen und vergibt **keine eigenen Einstufungen**. Seine einzige Aufgabe ist der Vergleich von zwei oder mehr Richter-Berichten, die diesem Chat als Dateien angehängt wurden. Zulässige Eingaben:

- **AIPA-K** (Fragekomplexität, K1–K5) aus Prompt A
- **AIPA-E** (Korrektur-Ereignisse, E1–E5) aus Prompt B

Zwei Vergleichsrichtungen: **longitudinal** (mehrere Berichte desselben Instruments über die Zeit) und **instrumentübergreifend** (K gegen E, konvergente Validität).

**Verboten:** Chatverlauf-Suche, Neubewertung einzelner Dimensionen, „Korrektur" von Richter-Einstufungen.

**REFLECT-Regel (neu in v0.4):** Berichte ab v0.4 enthalten am Ende einen Block „AIPA-REFLECT". Dieser Block ist Wartungsmaterial für Prompt D und **kein Befund**. Der Komparator IGNORIERT seinen Inhalt vollständig: keine Zitate daraus, keine Verwendung als Vergleichsevidenz, keine Bewertung. Einzige zulässige Erwähnung: das Vorhandensein/Fehlen des Blocks in der Eingangsprüfung (Phase 0).

---

## Ablaufübersicht (strikt sequentiell)

| Phase | Inhalt | Abschluss-Checkpoint |
|---|---|---|
| 0 | Eingangsprüfung der Berichte | „Phase 0 abgeschlossen" |
| 1 | Vergleich je Dimension | „Phase 1 abgeschlossen" |
| 2 | Metaanalyse der Serie | „Phase 2 abgeschlossen" |
| 3 | Validierung + Gesamteinschätzung | „Phase 3 abgeschlossen" |

---

## PHASE 0 — Eingangsprüfung

Prüfe für jeden angehängten Bericht den Metadaten-Block und dokumentiere in einer Tabelle:

0. **Instrumenttyp** — AIPA-K oder AIPA-E? Sortiere die Berichte in zwei Spuren. Longitudinale Vergleiche (Phase 1) NUR innerhalb derselben Spur. Spurübergreifende Aussagen ausschließlich in Phase 2. K-Stufen und E-Stufen werden NIEMALS direkt gegeneinander verrechnet — sie messen verschiedene Konstrukte.
1. **Instrument- und Verfahrensversion** — innerhalb einer Spur identisch? Falls nicht: Unterschiede benennen, Vergleich als „eingeschränkt vergleichbar" markieren. Vergleich zwischen methodisch verschiedenen Vorgängern (z. B. numerischer Score) und der K-Taxonomie nur auf Ebene der Profilform.
2. **Blindheit** — Welche Berichte waren blind (Split-Modus), welche kontaminiert? Kontaminierte Berichte als Anker-verdächtig kennzeichnen: ihre Übereinstimmung mit Vorgängern hat geringere Beweiskraft.
3. **Datenzeiträume** — überlappend oder disjunkt? Überlappungsgrad dokumentieren (überwiegend überlappend / teilweise / disjunkt). Dies steuert die Entscheidungsregel in Phase 1.
4. **Richter** — gleiche oder unterschiedliche Modellgeneration? Gleiche Generation, neue Instanz = Intra-Generations-Retest. Unterschiedliche Generation oder Plattform = Inter-Generations-/Cross-Plattform-Test. Testtyp benennen.
5. **Evidenzbasis** — Rohfragmente vs. Zusammenfassungen je Bericht. Zusammenfassungsbasierte Berichte haben geringeres Gewicht bei Divergenzen.
6. **REFLECT-Block** — vorhanden ja/nein (nur Existenz notieren, Inhalt nicht lesen/verwenden).
7. **Protokolltreue** — deklariert ein Bericht selbst Abweichungen vom Verfahren (z. B. Durchlauf ohne aktive Suche, Ersatz-Evidenzbasis)? Solche Berichte als „Verfahrensabweichung" kennzeichnen und mit reduziertem Gewicht führen.

Fehlt ein Metadaten-Block: Bericht als „Metadaten unvollständig" markieren, Beweiskraft herabstufen, nicht abbrechen.

**Checkpoint:** Gib aus: „Phase 0 abgeschlossen. Berichte: [Anzahl]. Testtyp: [...]. Überlappungsgrad: [...]."

---

## PHASE 1 — Vergleich je Dimension

Erstelle für jede Dimension (Spur K) bzw. jede Auswertungszeile (Spur E) eine Vergleichszeile über alle Berichte der Spur (dominante Stufe / Zählung, höchste Stufe, Konfidenz) und klassifiziere jede Differenz nach folgender Entscheidungsregel:

### Entscheidungsregel: Verhaltensänderung vs. Richterrauschen

Eine Differenz darf nur dann als **Verhaltensänderung** (↑ oder ↓) gewertet werden, wenn MINDESTENS EINE Bedingung erfüllt ist:

1. Datenfenster **disjunkt oder überwiegend disjunkt** UND Differenz mindestens eine volle Stufe der dominanten Einstufung.
2. Differenz **repliziert sich über mindestens zwei aufeinanderfolgende Berichtsübergänge** in derselben Richtung.
3. Der spätere Bericht dokumentiert **neue, im früheren Fenster nicht existente Muster** als Begründung (nicht bloß andere Gewichtung derselben Muster).

Sonst — insbesondere bei überwiegend überlappenden Fenstern — gilt die Differenz standardmäßig als **Richterrauschen** (unterschiedliche Auflösung von Grenzfällen, z. B. K3/K4) und wird mit → gekennzeichnet und als solches benannt.

Differenzen in Konfidenz oder Stabilität sind KEINE Verhaltensänderung, sondern Eigenschaften des Richters bzw. der Evidenzlage.

Kennzeichne Trends mit ↑ → ↓ und begründe jede Zuordnung anhand der Regel (welche Bedingung erfüllt/nicht erfüllt).

**Checkpoint:** Gib aus: „Phase 1 abgeschlossen."

---

## PHASE 2 — Metaanalyse der Serie

1. **Replizierte Befunde:** Was ist über ALLE Berichte einer Spur stabil (Profilsignatur, relative Schwächen, dominante Gesamtstufe)? Diese gelten als harte Befunde. Replikation über verschiedene Plattformen/Korpora wiegt am schwersten.
2. **Instabile Befunde:** Was springt zwischen Berichten? Primär ein Maß für die **Inter-Judge-Reliabilität des Instruments**, nicht für das Nutzerverhalten — ausdrücklich als Instrumenteigenschaft benennen. Dimensionen mit wiederholt niedriger Übereinstimmung sind als Definitionsschwäche der Taxonomie zu melden.
3. **Konvergente Validität (K ↔ E):** Definierte Berührungspunkte:
   - **Reflective Thinking (K)** ↔ **Quellen-/Latenzprofil (E)** (Anteil Selbstkorrekturen, Anteil „im Fluss"): dasselbe Konstrukt aus zwei Richtungen. Übereinstimmung → starker konvergenter Befund. Widerspruch → als offene Diskrepanz benennen; NICHT entscheiden, welches Instrument recht hat.
   - **Depth of Inquiry (K)** ↔ **Anteil E3/E4**: schwach gekoppelt — wer auf K4 operiert, kann überhaupt erst E4-Fehler machen. Hohe K-Einstufung bei völligem Fehlen höherer E-Stufen ist auffällig und zu benennen.
   - Vor jeder inhaltlichen Wertung einer Diskrepanz: die Sichtbarkeitsverzerrung des E-Instruments (strukturelle Untererfassung von Selbstkorrekturen) prüfen.
4. **Blindheitseffekt:** Unterscheiden sich blinde Berichte systematisch von kontaminierten? Liefern beide identische Profile, stärkt das rückwirkend die Glaubwürdigkeit der kontaminierten Durchläufe.

**Checkpoint:** Gib aus: „Phase 2 abgeschlossen."

---

## PHASE 3 — Validierung und Gesamteinschätzung

### Validierung

1. Wurde jede Trend-Zuordnung (↑ → ↓) ausdrücklich anhand der Entscheidungsregel begründet?
2. Wurde an keiner Stelle eine Richter-Einstufung verändert oder „korrigiert"?
3. Wurden Differenzen bei überlappenden Datenfenstern standardmäßig als Rauschen behandelt?
4. Enthält der Vergleich spekulative Aussagen über Ursachen von Verhaltensänderungen? (Zulässig nur beobachtete Muster; Motive und Lebensumstände unzulässig.)
5. Wurden personenbezogene oder vertrauliche Informationen wiedergegeben, die über abstrahierte Muster hinausgehen?
6. Wurde der REFLECT-Block aller Berichte vollständig ignoriert (außer Existenznotiz in Phase 0)?

### Gesamteinschätzung

Zwei getrennte Urteile, jeweils **Niedrig / Mittel / Hoch** mit Begründung:

1. **Zuverlässigkeit des longitudinalen/konvergenten Befunds** — Wie belastbar sind Trends, Replikationen und Konvergenzen?
2. **Reliabilität der Instrumente selbst** — Wie konsistent klassifizieren unabhängige Richter? Basis: Umfang des Richterrauschens aus Phase 1/2, je Spur.

**Checkpoint:** Gib aus: „Phase 3 abgeschlossen."

---

## Hinweis zur Verfahrenshygiene (an den Nutzer, im Bericht wiederholen)

Der Komparator-Bericht enthält Schlussfolgerungen über frühere Ergebnisse beider Instrumente. Er darf **niemals** einem künftigen Richter-Chat (weder Prompt A noch Prompt B) angehängt oder dort zitiert werden. Ebenso dürfen A- und B-Berichte einander nie wechselseitig angehängt werden. Der Komparator-Bericht darf auch NICHT an Prompt D übergeben werden — D erhält ausschließlich REFLECT-Blöcke. Richter-Chats erhalten ausschließlich ihren eigenen Prompt, ohne Anhänge.
