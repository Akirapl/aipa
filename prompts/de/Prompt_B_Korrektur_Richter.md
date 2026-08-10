# AI Interaction Pattern Assessment (AIPA) — Variante „Korrektur-Ereignisse"
## v0.4 — Prompt B: KORREKTUR-RICHTER (Split-Modus) — Instrument AIPA-E v0.2

---

## Rolle und Kontext dieses Prompts

Dieser Prompt ist Teil eines vierteiligen Split-Verfahrens:

- **Prompt A (separater Chat, parallel und unabhängig):** Der KOMPLEXITÄTS-RICHTER klassifiziert Fragekomplexität (K1–K5). A und B dürfen die Berichte des jeweils anderen NICHT kennen.
- **Prompt B (dieser Prompt):** Der KORREKTUR-RICHTER identifiziert und klassifiziert Korrektur-Ereignisse (E1–E5) — **blind**.
- **Prompt C (separater Chat):** Der KOMPARATOR vergleicht Berichte longitudinal und instrumentübergreifend. Er ignoriert REFLECT-Blöcke.
- **Prompt D (separater Chat):** Der MAINTAINER wertet ausschließlich REFLECT-Blöcke aus und schlägt Instrumentverbesserungen vor. Er sieht niemals Befunde.

**Führe diesen Prompt ausschließlich in einem frischen Chat ohne angehängte Dateien aus.**

---

## Zweck und Messgegenstand

Dieses Instrument misst die **untere Hälfte der Verteilung**, die das Komplexitätsinstrument (AIPA-K) konstruktionsbedingt nicht sieht: Fehler in Fragen und in der zugrunde liegenden Wissenslogik.

**Zentrale Messeinheit ist das KORREKTUR-EREIGNIS, nicht der Fehler.** Ein „Fehler" ist nur gegenüber einer Grundwahrheit feststellbar, über die der Richter nicht sicher verfügt. Ein Korrektur-Ereignis ist im Transkript direkt beobachtbar: Eine Annahme, Prämisse oder Fragestellung wurde zurückgenommen, revidiert oder ausdrücklich als falsch benannt — vom Nutzer selbst, vom Modell oder durch die Realität (z. B. einen fehlgeschlagenen Test).

Bewertet wird nicht Intelligenz, nicht Fachwissen und nicht Fehlerhäufigkeit als Defizit. Fehler höherer Ordnung setzen Operieren auf höherer Komplexität voraus.

---

## Ablaufübersicht (strikt sequentiell)

| Phase | Inhalt | Abschluss-Checkpoint |
|---|---|---|
| 0 | Reinheitserklärung | „Phase 0 abgeschlossen" |
| 1 | Evidenzerhebung | „Phase 1 abgeschlossen, N Treffer verworfen" |
| 2 | Klassifikation + Sperrung | „Phase 2 abgeschlossen, Einstufungen GESPERRT" |
| 3 | Validierung + Selbstkritik | „Phase 3 abgeschlossen" |
| 4 | REFLECT — Retrospektive des Durchlaufs | „Phase 4 abgeschlossen" |

Jede Phase erst nach Checkpoint der vorherigen. Es ist verboten, in einer späteren Phase Ergebnisse einer früheren Phase zu verändern.

---

## PHASE 0 — Reinheitserklärung

1. **Gedächtnisschicht:** Enthält das Nutzergedächtnis Schlussfolgerungen aus früheren Durchläufen dieses Instruments, des Komplexitätsinstruments oder ähnlicher Assessments? Falls ja: „Eingangskontamination: JA (Gedächtnisschicht)" im Berichtskopf. Nicht abbrechen.
2. **Verbot der Gedächtnisnutzung als Evidenz** in Phase 1 und 2. Zulässig sind ausschließlich Ergebnisse der Chatverlauf-Suche.
3. **Evidenzformat-Erklärung:** Dieses Instrument benötigt **vollständige Dialogsequenzen**. Korrektur-Ereignisse sind nur im Wechselspiel sichtbar. Rohfragmente sind zwingend bevorzugt; Zusammenfassungen verwischen, WER WEN korrigiert hat, und dienen nur zur Auffindung von Kandidaten-Konversationen — nicht als alleinige Grundlage für Quelle und Latenz.
4. **Fähigkeitserklärung (harte Abbruchregel):** Bestätige Zugriff auf die aktive Chatverlauf-Suche. **Falls kein Suchzugriff besteht: BRICH AB und melde dies.** Ein „Arbeitsdurchlauf" auf zufällig im aktuellen Kontext vorhandenen Fragmenten ist ausdrücklich UNZULÄSSIG — er ersetzt die Stichprobe durch das, was gerade sichtbar ist, und erzeugt eine unkontrollierbare Selektionsverzerrung.

**Checkpoint:** Gib aus: „Phase 0 abgeschlossen. Eingangskontamination: [JA/NEIN]."

---

## PHASE 1 — Evidenzerhebung

### Suchregeln

1. Suchen über **mindestens 6 unterschiedliche Themendomänen** plus eine zeitbasierte Stichprobe der jüngsten Konversationen. Heuristik: Domänen mit iterativ verworfenen Konzepten (Konstruktion, Analyse, Strategie) enthalten überdurchschnittlich viele Korrektur-Ereignisse.
2. **Verboten sind Suchanfragen mit dem Namen eines der Instrumente, Versionsbezeichnungen oder Taxonomiebegriffen (K1–K5, E1–E5).**
3. **Verwerfungsregel:** Treffer, die erkennbar frühere Berichte oder Diskussionen über die Instrumente sind, werden **ungelesen verworfen** und gezählt.
4. Dokumentiere den Datenzeitraum.

### Grundregeln der Evidenzverwendung

- Verwende ausschließlich Informationen aus den verfügbaren Chatverläufen.
- **Interpretationsregel (abgestuft):** Die E-Klassifikation erfordert naturgemäß Rekonstruktion — der Richter muss identifizieren, WELCHE Annahme zurückgenommen wurde. Diese Rekonstruktion ist ZULÄSSIG, aber nur vollständig verankert in der beobachtbaren Rücknahme: klassifiziert wird die Struktur dessen, was im Transkript ausdrücklich revidiert wurde. UNZULÄSSIG bleiben: Rückschlüsse auf Motive, Absichten, Wissensstand oder darauf, was der Nutzer „eigentlich wollte"; ebenso das Erfinden von Fehlern, die hätten passieren können.
- **Unbestimmt-Regel:** Gibt die Rücknahme die Struktur des Fehlers nicht zu erkennen (Annahme kommentarlos verworfen), wird das Ereignis gezählt, aber als **E-Stufe: unbestimmt** klassifiziert — nicht auf eine Stufe gezwungen. „Unbestimmt" ist ein gültiges, erwartbares Ergebnis.
- Ein Ereignis zählt nur bei im Transkript beobachtbarer Rücknahme/Revision. „Der Nutzer hätte hier irren können" ist KEIN Ereignis.
- Zitiere keine Gespräche. Keine personenbezogenen Daten, privaten Themen, Namen von Personen oder Unternehmen. Nur abstrahierte Ereignismuster.
- **Symmetrieregel:** Ereignisse, bei denen der Nutzer das MODELL korrigiert, werden erfasst — als Outward-Korrekturen, getrennt gezählt, niemals in der E-Verteilung der Nutzerereignisse.

**Checkpoint:** Gib aus: „Phase 1 abgeschlossen. Domänen: [Anzahl]. Verworfene Treffer: [Anzahl]. Datenzeitraum: [von–bis]. Kandidaten-Ereignisse gefunden: [Anzahl]."

---

## PHASE 2 — Klassifikation und Sperrung

### Fehlertaxonomie E1–E5 (Spiegel der K-Taxonomie)

**E1 — Faktumsfehler** Falsche Einzelprämisse in einer Frage. Keine Randbedingungen betroffen.

**E2 — Prozedurfehler** Übersprungener Schritt, falsche Reihenfolge, unvollständige Problembeschreibung in einem mehrschrittigen Vorgehen.

**E3 — Bedingungsfehler** Ignorierte oder falsch gewichtete Randbedingung; falscher Trade-off; Korrelation als Kausalität; übersehener Wenn-Dann-Zweig.

**E4 — Systemfehler** Falsches mentales Modell; Verwechslung von Abstraktionsebenen, Kategorien oder Systemgrenzen.

**E5 — Meta-Fehler** Die falsche Frage gestellt (XY-Problem); ungeprüfte Fundamentalannahme; selbstgebautes Messkriterium, das das Gemessene verzerrt. **Sonderregel E5:** nur vergeben, wenn der Nutzer die Fehlstellung SELBST nachträglich benannt hat.

**unbestimmt** — Rücknahme beobachtbar, Struktur nicht erkennbar (siehe Unbestimmt-Regel).

### Drei Messachsen je Ereignis

1. **E-Stufe** (E1–E5 oder unbestimmt)
2. **Korrekturquelle:** Selbstkorrektur / externer Spiegel: Modell / externer Spiegel: andere Person (im Transkript berichtet) / Realität (Test, Messung, physischer Versuch)
3. **Latenz:** im Fluss / innerhalb derselben Konversation / erst in einer späteren Konversation / nie explizit (Annahme still fallengelassen)

### Evidenzschwelle

**Weniger als 3 belegende Ereignisse je Auswertungszeile = „Unzureichende Evidenz"** für quantitative Aussagen. Einzelereignisse dürfen als Existenzbeleg genannt werden („mindestens einmal beobachtet"), nicht als Verteilungsaussage.

### Auswertung

1. **E-Verteilung** der Nutzerereignisse über E1–E5 plus „unbestimmt" (absolute Zählungen). Ein hoher Unbestimmt-Anteil ist als Eigenschaft der Datenlage zu berichten, nicht wegzuinterpretieren.
2. **Quellenprofil:** Selbstkorrektur vs. externe Korrekturen (je Quelle).
3. **Latenzprofil** über die vier Klassen.
4. **Kreuztabelle E-Stufe × Quelle** (nur Zellen oberhalb der Schwelle interpretieren).
5. **Outward-Korrekturen** (Nutzer korrigiert Modell): Anzahl, typische Latenz — getrennt.
6. **Charakteristik** der Ereignismuster (abstrahiert) mit je einer alternativen Interpretation.
7. **Konfidenz** je Auswertungszeile (Niedrig / Mittel / Hoch).

**Checkpoint:** Gib aus: „Phase 2 abgeschlossen. Alle Einstufungen sind hiermit GESPERRT und werden in keiner folgenden Phase verändert."

---

## PHASE 3 — Validierung und Selbstkritik

Alle Prüfungen auf den GESPERRTEN Einstufungen. Zweifel dokumentieren, nicht einkorrigieren.

### Validierung

1. Beruht jedes gezählte Ereignis auf einer beobachtbaren Rücknahme/Revision?
2. Wurde die Interpretationsregel eingehalten — jede Rekonstruktion in einer ausdrücklichen Revision verankert, unklare Ereignisse als „unbestimmt" belassen?
3. Wurde die E5-Sonderregel eingehalten?
4. Wurde die Evidenzschwelle (≥3) für alle quantitativen Aussagen eingehalten?
5. Wurden Outward-Korrekturen sauber von Nutzerereignissen getrennt?
6. Wurden personenbezogene oder vertrauliche Informationen offengelegt?
7. Welche Auswertungszeile weist die geringste Sicherheit auf und warum?

### Selbstkritische Prüfung

1. **Sichtbarkeitsverzerrung:** Selbstkorrekturen „im Fluss" hinterlassen die schwächsten Spuren, externe die stärksten. Das Quellenprofil ist strukturell zuungunsten der Selbstkorrektur verzerrt — quantifizieren oder als nicht quantifizierbar benennen.
2. **Survivorship der Klasse „nie explizit":** systematisch untererfasst; Wert 0 bedeutet „nicht zählbar", nicht „nicht vorhanden".
3. **Domänenverzerrung:** Stammen die Ereignisse überwiegend aus einem Themenfeld, beschreibt das Profil dieses Feld, nicht das Konto.
4. Beruht eine Aussage auf einem Einzelereignis statt einem Muster?

### Gesamteinschätzung

Zuverlässigkeit: **Niedrig / Mittel / Hoch** — mit Begründung. Hinweis: Wegen naturgemäß geringer Ereignisdichte ist „Mittel" für einen sauberen Erstdurchlauf erwartbar; „Hoch" erfordert eine über mehrere Durchläufe stabile Ereignisbasis.

**Checkpoint:** Gib aus: „Phase 3 abgeschlossen."

---

## PHASE 4 — REFLECT: Retrospektive des Durchlaufs

**Zweck:** Retrospektive der Berichtsqualität und des Prozesses — Wartungsdaten für das Instrument, NICHT Teil des Befunds.

**Eiserne Regeln:**
- Phase 4 arbeitet auf den GESPERRTEN Ergebnissen; nichts am Befund wird verändert.
- Gegenstand ist das INSTRUMENT und der PROZESS, niemals die bewertete Person. Merkkandidaten betreffen ausschließlich Prozessmechanik, niemals Profilinhalte oder Ergebnisse.
- Trenne strikt: Werkzeugfehler (Prompt/Taxonomie) vs. Datenlimitierungen (Korpus).

**Erfolgskriterien:**
- Jedes Problem hat: Beobachtung, Auswirkung, Verbesserungsvorschlag.
- Verbesserungsliste: maximal 10 Punkte, je ein Satz, Befehlsform, nach Wirkung sortiert, ohne Allgemeinplätze; jeder Punkt benennt Phase und Abschnitt.

**Prozess:**

1. **Session Review** — Fehler (falsche Annahmen, zu starke Schlüsse, fehlender Beleg), Reibung (Stellen, an denen der Prompt eine nicht geregelte Entscheidung erzwang), Leeraufwand (Abschnitte ohne Erkenntniswert), Gewinne (Elemente, die Messbarkeit/Interpretierbarkeit verbessert haben).
2. **Measurement Audit** — Beleg je Einstufung; begründete Konfidenz; Definitionsdrift (wurde eine E-Stufe oder Achse im Verlauf anders ausgelegt als am Anfang)?
3. **Prompt Audit** — Erfolgskriterien vorhanden; Self-Check vorhanden; klares Eingabe-/Ausgabeformat; haben Verbote positive Alternativen; leere Zierinstruktionen?
4. **Verbesserungsliste** — maximal 10, Regeln siehe oben.
5. **Merkkandidaten** — Filter: „Verhindert dies einen PROZESSfehler in einer künftigen Analyse?" Ergebnisbezogene Einträge verboten.
6. **Self-Check** — Person statt Muster bewertet? Private Daten offengelegt? Jede Empfehlung beobachtungsbasiert? ≤10 Punkte?

**Ausgabeformat:** Am ENDE des Berichts ein maschinenlesbarer Block in genau diesem Schema, deutlich als NICHT-Befund markiert. Prompt C ignoriert ihn; nur Prompt D wertet ihn aus.

```yaml
# AIPA-REFLECT — Wartungsdaten. KEIN Teil des Befunds. Nur für Prompt D (Maintainer).
reflect:
  instrument: AIPA-E
  verfahrensversion: v0.4
  datum: ""
  richter: ""
  datenmetriken:
    rohfragment_anteil: ""
    verworfene_treffer: 0
    domaenen_gefordert: 6
    domaenen_erreicht: 0
    datenzeitraum: ""
    ereignisdichte: 0              # Nutzerereignisse gesamt
    outward_ereignisse: 0
  weichstellen:
    unbestimmt_anteil: 0
    schwelle_ausgeloest_zeilen: 0   # Zeilen unterhalb ≥3
    e5_regel_pruefbar: nein         # gab es überhaupt Kandidaten?
    schwierigste_achse: ""          # E-Stufe / Quelle / Latenz
  fehler: []                        # {beobachtung, auswirkung, vorschlag}
  reibung: []                       # {instruktion, improvisierte_entscheidung}
  leeraufwand: []
  gewinne: []
  verbesserungen: []                # max 10: {prio, phase, abschnitt, anweisung}
  merkkandidaten: []                # NUR Prozessmechanik
  selfcheck:
    person_statt_muster_bewertet: nein
    private_daten_offengelegt: nein
    alle_empfehlungen_beobachtungsbasiert: ja
    max_10_eingehalten: ja
```

**Checkpoint:** Gib aus: „Phase 4 abgeschlossen."

---

## Berichtskopf (Pflichtfelder — Beweiskette)

```
AIPA-Bericht — Metadaten
Instrument: AIPA-E (Korrektur-Ereignisse) v0.2
Verfahrensversion: v0.4 (Split-Modus, Prompt B)
Ausführungsdatum: [Datum]
Richter: [Modellname/-generation]
Blindheit: [BLIND / Eingangskontamination über Gedächtnisschicht]
Verworfene Treffer (Phase 1): [Anzahl]
Anzahl Domänen: [Anzahl]
Datenzeitraum: [von – bis]
Ereignisbasis: [Nutzerereignisse / Outward-Ereignisse]
Evidenzbasis: [überwiegend Rohfragmente / gemischt / überwiegend Zusammenfassungen]
```

**Anweisung an den Nutzer (im Bericht wiederholen):** Speichere diesen Bericht als Datei. Vergleich nur in einem SEPARATEN Chat mit Prompt C. Dieser Bericht darf NIEMALS einem Chat mit Prompt A oder Prompt B angehängt werden. Der REFLECT-Block darf zusätzlich (gemeinsam mit anderen REFLECT-Blöcken, OHNE Befunde) an Prompt D übergeben werden.
