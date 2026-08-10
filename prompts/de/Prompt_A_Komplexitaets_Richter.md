# AI Interaction Pattern Assessment (AIPA) — Variante „Fragekomplexität"
## v0.4 — Prompt A: KOMPLEXITÄTS-RICHTER (Split-Modus)

---

## Rolle und Kontext dieses Prompts

Dieser Prompt ist Teil eines vierteiligen Split-Verfahrens:

- **Prompt A (dieser Prompt):** Der KOMPLEXITÄTS-RICHTER klassifiziert Fragekomplexität (K1–K5) — **blind**, ohne Kenntnis früherer Berichte.
- **Prompt B (separater Chat, parallel und unabhängig):** Der KORREKTUR-RICHTER klassifiziert Korrektur-Ereignisse (E1–E5). A und B dürfen die Berichte des jeweils anderen NICHT kennen.
- **Prompt C (separater Chat):** Der KOMPARATOR vergleicht Richter-Berichte longitudinal und instrumentübergreifend. Er ignoriert REFLECT-Blöcke.
- **Prompt D (separater Chat):** Der MAINTAINER wertet ausschließlich die REFLECT-Blöcke mehrerer Durchläufe aus und schlägt Verbesserungen des Instruments vor. Er sieht niemals Befunde.

**Führe diesen Prompt ausschließlich in einem frischen Chat ohne angehängte Dateien aus.**

---

## Zweck

Analysiere ausschließlich die auf diesem Konto verfügbaren Chatverläufe. Ziel ist nicht die Bewertung von Persönlichkeit, Intelligenz oder Fachwissen. Gegenstand der Analyse ist die strukturelle Komplexität der Fragen und Anfragen, die als Evidenz für die jeweilige Dimension dienen. Bewertet wird nicht die Qualität einer Antwort und nicht die Intensität eines Verhaltens, sondern die Komplexität der gestellten Fragen. Die Analyse dient ausschließlich der Beschreibung des Nutzungsverhaltens.

---

## Ablaufübersicht (strikt sequentiell)

| Phase | Inhalt | Abschluss-Checkpoint |
|---|---|---|
| 0 | Reinheitserklärung | „Phase 0 abgeschlossen" |
| 1 | Evidenzerhebung | „Phase 1 abgeschlossen, N Treffer verworfen" |
| 2 | Klassifikation + Sperrung | „Phase 2 abgeschlossen, Einstufungen GESPERRT" |
| 3 | Validierung + Selbstkritik | „Phase 3 abgeschlossen" |
| 4 | REFLECT — Retrospektive des Durchlaufs | „Phase 4 abgeschlossen" |

Jede Phase darf erst begonnen werden, wenn der Checkpoint der vorherigen Phase ausdrücklich ausgegeben wurde. Es ist verboten, in einer späteren Phase Ergebnisse einer früheren Phase zu verändern.

---

## PHASE 0 — Reinheitserklärung

1. **Gedächtnisschicht (Memory):** Enthält das verfügbare Nutzergedächtnis Schlussfolgerungen, Ergebnisse oder Bewertungen aus früheren Durchläufen dieses Instruments (oder eines inhaltlich sehr ähnlichen Assessments)?
   - Falls ja: notiere im Berichtskopf „Eingangskontamination: JA (Gedächtnisschicht)". Brich NICHT ab.
   - Falls nein: notiere „Eingangskontamination: NEIN".
2. **Verbot der Gedächtnisnutzung als Evidenz:** Die Gedächtnisschicht darf in Phase 1 und 2 NICHT als Evidenzquelle verwendet werden. Zulässige Evidenz sind ausschließlich Ergebnisse der Chatverlauf-Suche (Rohfragmente bevorzugt, Zusammenfassungen nachrangig und als solche gekennzeichnet).
3. **Fähigkeitserklärung:** Bestätige, dass Zugriff auf die Chatverlauf-Suche besteht. **Falls kein Zugriff besteht: brich ab und melde dies.** Ein Ersatzdurchlauf auf zufällig im Kontext vorhandenen Fragmenten ist unzulässig — das Instrument ist ohne Suchzugriff nicht ausführbar.

**Checkpoint:** Gib aus: „Phase 0 abgeschlossen. Eingangskontamination: [JA/NEIN]."

---

## PHASE 1 — Evidenzerhebung

### Suchregeln

1. Führe Suchen über **mindestens 6 unterschiedliche Themendomänen** durch (z. B. technische Diagnostik, Projektarbeit, konzeptionelle Themen, formale Vorgänge, alltägliche Anfragen, redaktionelle Aufgaben). Zusätzlich: eine zeitbasierte Stichprobe der jüngsten Konversationen, um Selektionsverzerrung zu reduzieren.
2. **Verboten sind Suchanfragen, die den Namen dieses Instruments, seine Versionsbezeichnungen oder seine Taxonomiebegriffe enthalten.**
3. **Verwerfungsregel:** Treffer, die erkennbar frühere Berichte dieses Instruments oder Diskussionen über das Instrument selbst sind, werden **ungelesen verworfen** und gezählt.
4. Bevorzuge Rohfragmente echter Wortwechsel gegenüber Zusammenfassungen. Stützt sich eine Einstufung überwiegend auf Zusammenfassungen, muss dies bei der Konfidenz benannt werden.
5. Dokumentiere den beobachteten Datenzeitraum (frühestes und spätestes Datum).

### Grundregeln der Evidenzverwendung

- Verwende ausschließlich Informationen aus den verfügbaren Chatverläufen.
- Triff keine Vermutungen.
- Bewerte Komplexität ausschließlich anhand der beobachtbaren Struktur der Fragen, nicht anhand vermuteter Absichten.
- Wenn keine Fragen vorliegen, die eine Dimension belegen, schreibe ausdrücklich „Unzureichende Evidenz".
- Zitiere keine Gespräche. Gib keine personenbezogenen Daten, privaten Themen, Namen von Personen oder Unternehmen wieder. Beschreibe ausschließlich abstrahierte Fragemuster.
- **Attributionsregel:** Klassifiziert wird ausschließlich die Struktur der NUTZERfragen. Komplexität aus Modellantworten ist keine Evidenz. Bei Zusammenfassungen, in denen Frage und Antwort verschmolzen sind: im Zweifel niedriger einstufen oder als unsicher kennzeichnen.
- **Grenzfall-Protokoll:** Jeder Fall, in dem die Zuordnung zwischen zwei benachbarten Stufen (insbesondere K3/K4) unentscheidbar erscheint, wird gezählt und die verwendete Entscheidungsheuristik notiert. Diese Zählung fließt in Phase 4 ein.

**Checkpoint:** Gib aus: „Phase 1 abgeschlossen. Domänen: [Anzahl]. Verworfene Treffer: [Anzahl]. Datenzeitraum: [von–bis]."

---

## PHASE 2 — Klassifikation und Sperrung

### Komplexitätstaxonomie

**K1 — Faktisch / Punktuell** Einzelne Sachfrage mit genau einer korrekten Antwort. Abruf von Definitionen oder Einzelfakten, keine Randbedingungen.

**K2 — Prozedural / Mehrschrittig** Frage nach einem mehrschrittigen Vorgehen oder mit Kontext. Sequentiell, ohne konkurrierende Randbedingungen.

**K3 — Analytisch / Bedingt** Frage mit mehreren Randbedingungen, Vergleichen, Abwägungen oder Wenn-Dann-Verzweigungen. Verlangt das Gewichten von Optionen.

**K4 — Synthetisch / Systemisch** Frage integriert mehrere Konzepte oder Fachgebiete, zielt auf Entwurf bzw. Architektur oder antizipiert Folgewirkungen zweiter Ordnung.

**K5 — Generativ / Meta** Frage hinterfragt die Problemstellung selbst, prüft eigene Annahmen, erzeugt neue konzeptionelle Strukturen oder ist rekursiv/selbstreflexiv.

### Analysedimensionen

Charakterisiere jede Dimension anhand: dominante Komplexitätsstufe (K1–K5), höchste beobachtete Stufe, Stabilität (durchgängig / sporadisch / steigend / fallend — bezogen ausschließlich auf das aktuelle Datenfenster), Konfidenz (Niedrig / Mittel / Hoch), Begründung, Charakteristik der beobachteten Fragen (abstrahiert, ohne Zitate), mögliche alternative Interpretation. Ohne belegende Fragen: „Unzureichende Evidenz".

**1. Curiosity** — Tendenz, neue Themen aktiv zu erkunden, nach Mechanismen zu fragen und über die unmittelbare Problemlösung hinaus Wissen aufzubauen. Marker: Fragen adressieren den Wirkmechanismus statt nur die Anwendung.

**2. Depth of Inquiry** — Systematische Vertiefung durch Folgefragen, Einschränkungen, Gegenbeispiele, Detailanalysen. Marker: geschichtete Folgefragen, die Randbedingungen oder Gegenbeispiele in eine vorherige Antwort einführen.

**3. Iterative Learning** — Wiederaufgreifen und Weiterentwickeln früherer Themen über mehrere Gespräche. Marker: wiederaufgegriffene Fragen bauen auf früheren Ergebnissen auf statt sie zu wiederholen.

**4. Cross-domain Integration** — Übertragung von Konzepten zwischen Fachgebieten. Marker: Fragen verbinden mehrere — möglichst weit entfernte — Domänen in einer Fragestellung.

**5. Problem-solving Behaviour** — Entwicklung nachhaltiger Lösungsprozesse statt punktueller Antworten. Marker: Fragen zielen auf wiederverwendbare Verfahren oder Ursachenanalysen.

**6. Information Seeking** — Aktive Suche nach Quellen, Alternativen, Literatur, Vergleichen, Evidenz. Marker: Fragen wägen mehrere Quellen oder Optionen gegeneinander ab.

**7. Reflective Thinking** — Kritische Bewertung eigener Annahmen, Strategien und Entscheidungen. Marker: Fragen machen die eigenen Annahmen des Nutzers zum Gegenstand. **Präzisierung v0.4:** Unterscheide zwei Unterformen und weise sie getrennt aus: (a) DESIGNTE Reflexion — der Nutzer baut Strukturen/Werkzeuge, deren Zweck die Prüfung eigener Annahmen ist; (b) SPONTANE Reflexion — der Nutzer stellt eigene Annahmen mitten in einem inhaltlichen Prozess in Frage, ohne dass die Struktur ihn dazu zwingt. Die dominante Stufe der Dimension ist aus BEIDEN Unterformen zu bilden; eine hohe Einstufung allein aus Unterform (a) ist zu kennzeichnen. (Hintergrund: Diese Dimension zeigte in bisherigen Serien die geringste Inter-Judge-Übereinstimmung.)

**8. Experimentation** — Systematisches Testen von Vorgehensweisen, Prompts, Arbeitsmethoden. Marker: Fragen testen Varianten gezielt gegeneinander.

### Gesamtprofil

- **Overall Interaction Profile** — typisches Komplexitätsniveau über alle Dimensionen.
- **Komplexitätsprofil:** Verteilung der Dimensionen über K1–K5, dominante Gesamtstufe, höchste beobachtete Stufe.
- **Drei beobachtete Stärken** und **drei Entwicklungsmöglichkeiten.**

**Checkpoint:** Gib aus: „Phase 2 abgeschlossen. Alle Einstufungen sind hiermit GESPERRT und werden in keiner folgenden Phase verändert."

---

## PHASE 3 — Validierung und Selbstkritik

Alle Prüfungen erfolgen auf den GESPERRTEN Einstufungen. Zweifel werden dokumentiert, nicht einkorrigiert.

### Validierung

1. Wurden alle Einstufungen ausschließlich auf beobachtbare Fragestrukturen gestützt?
2. Enthält eine Einstufung spekulative Schlussfolgerungen?
3. Lagen für jede Einstufung ausreichend viele belegende Fragen vor?
4. Wurden personenbezogene oder vertrauliche Informationen offengelegt?
5. Welche Einstufung weist die geringste Sicherheit auf und warum?
6. Wurde die Attributionsregel eingehalten (nur Nutzerfragen)?
7. Wurde die Verwerfungsregel eingehalten (frühere Berichte ungelesen verworfen)?
8. Wurde bei Reflective Thinking die Trennung designte/spontane Reflexion ausgewiesen?

### Selbstkritische Prüfung

Versuche bewusst, die eigenen Einstufungen zu widerlegen: Verwechslung von langer Formulierung mit struktureller Tiefe; hohe Einstufung auf Basis einer Ausnahmefrage statt eines Musters; Verzerrung durch Auswahl der Suchdomänen oder des Zeitfensters. Plausible Alternativinterpretationen ausdrücklich dokumentieren.

### Gesamteinschätzung

Zuverlässigkeit des Berichts: **Niedrig / Mittel / Hoch** — mit kurzer Begründung.

**Checkpoint:** Gib aus: „Phase 3 abgeschlossen."

---

## PHASE 4 — REFLECT: Retrospektive des Durchlaufs

**Zweck:** Nach jeder Analyse eine Retrospektive der Berichtsqualität und des Bewertungsprozesses — als Wartungsdaten für das Instrument, NICHT als Teil des Befunds.

**Eiserne Regeln:**
- Phase 4 arbeitet auf den GESPERRTEN Ergebnissen. Kein Ergebnis, keine Konfidenz, keine Formulierung des Befunds wird verändert.
- Gegenstand ist das INSTRUMENT und der PROZESS, niemals die bewertete Person. Merkkandidaten dürfen ausschließlich Prozessmechanik betreffen (z. B. „Suchanfragen mit Begriff X liefern alte Berichte"), niemals Profilinhalte oder Ergebnisse.
- Trenne strikt: Werkzeugfehler (Schwächen des Prompts/der Taxonomie) vs. Datenlimitierungen (Eigenschaften des verfügbaren Korpus).

**Erfolgskriterien:**
- Jedes erkannte Problem hat: Beobachtung, Auswirkung, Verbesserungsvorschlag.
- Verbesserungsliste: maximal 10 Punkte, je ein Satz, Befehlsform, nach Wirkung sortiert, ohne Allgemeinplätze; jeder Punkt benennt Phase und Abschnitt des Prompts, den er betrifft.

**Prozess:**

1. **Session Review** — prüfe Bericht und Entstehungsprozess nach: Fehler (falsche Annahmen, zu starke Schlüsse, fehlender Beleg), Reibung (Stellen, an denen der Prompt eine nicht geregelte Entscheidung erzwang und improvisiert wurde), Leeraufwand (Abschnitte ohne Erkenntniswert), Gewinne (Elemente, die Messbarkeit oder Interpretierbarkeit verbessert haben).
2. **Measurement Audit** — hat jede Einstufung einen Beleg; ist jede Konfidenz begründet; gab es Definitionsdrift (wurde eine Stufe im Verlauf anders ausgelegt als am Anfang)?
3. **Prompt Audit** — hat der Prompt: Erfolgskriterien, Self-Check, klares Eingabe-/Ausgabeformat; haben Verbote positive Alternativen; enthält er leere Zierinstruktionen?
4. **Verbesserungsliste** — maximal 10, Regeln siehe Erfolgskriterien.
5. **Merkkandidaten** — nur Einträge, die den Filter bestehen: „Verhindert dies einen PROZESSfehler in einer künftigen Analyse?" Ergebnisbezogene Einträge sind verboten.
6. **Self-Check** — wird die Person statt der Muster bewertet? Werden private Daten offengelegt? Folgt jede Empfehlung aus einer Beobachtung? Sind es ≤10 Verbesserungen?

**Ausgabeformat:** Am ENDE des Berichts, nach allen anderen Abschnitten, ein maschinenlesbarer Block in genau diesem Schema. Der Block ist mit der Kopfzeile deutlich als NICHT-Befund markiert. Prompt C ignoriert ihn; nur Prompt D wertet ihn aus.

```yaml
# AIPA-REFLECT — Wartungsdaten. KEIN Teil des Befunds. Nur für Prompt D (Maintainer).
reflect:
  instrument: AIPA-K
  verfahrensversion: v0.4
  datum: ""
  richter: ""
  datenmetriken:
    rohfragment_anteil: ""        # überwiegend / gemischt / überwiegend Zusammenfassungen
    verworfene_treffer: 0
    domaenen_gefordert: 6
    domaenen_erreicht: 0
    datenzeitraum: ""
  weichstellen:
    grenzfaelle_gesamt: 0          # Anzahl unentscheidbarer Nachbarstufen-Fälle
    grenzfaelle_k3_k4: 0
    heuristik_bei_grenzfaellen: ""
    dimension_geringste_konfidenz: ""
  fehler: []                       # {beobachtung, auswirkung, vorschlag}
  reibung: []                      # {instruktion, improvisierte_entscheidung}
  leeraufwand: []
  gewinne: []
  verbesserungen: []               # max 10: {prio, phase, abschnitt, anweisung}
  merkkandidaten: []               # NUR Prozessmechanik
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
Instrument: AIPA-K (Fragekomplexität) 
Verfahrensversion: v0.4 (Split-Modus, Prompt A)
Ausführungsdatum: [Datum]
Richter: [Modellname/-generation]
Blindheit: [BLIND / Eingangskontamination über Gedächtnisschicht]
Verworfene Treffer (Phase 1): [Anzahl]
Anzahl Domänen: [Anzahl]
Datenzeitraum: [von – bis]
Evidenzbasis: [überwiegend Rohfragmente / gemischt / überwiegend Zusammenfassungen]
```

Ohne vollständigen Metadaten-Block ist der Bericht für Prompt C ungültig.

**Anweisung an den Nutzer (im Bericht wiederholen):** Speichere diesen Bericht als Datei. Vergleich nur in einem SEPARATEN Chat mit Prompt C. Dieser Bericht darf NIEMALS einem Chat mit Prompt A oder Prompt B angehängt werden. Der REFLECT-Block darf zusätzlich (gemeinsam mit REFLECT-Blöcken anderer Durchläufe, OHNE die Befunde) an Prompt D übergeben werden.
