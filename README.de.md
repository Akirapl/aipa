[English](README.md) | **Deutsch** | [Polski](README.pl.md)

# AIPA — AI Interaction Pattern Assessment

Ein Framework, das die *Form* eines Mensch-KI-Gesprächs bewertet — nicht was das Modell ausgibt, sondern wie die Person fragt und wie gut Fehler erkannt werden — mithilfe isolierter LLM-Richter statt Selbstauskunft.

## Das Problem

Antworten sind billig geworden. Ein Prompt rein, eine fertig aussehende Antwort raus, Sekunden später — und die Reibung, die früher echtes Verständnis erzwang, ist verschwunden. Jede existierende KI-Evaluierung misst die Qualität der Modellausgabe. Keine stellt die andere Frage: Baut *dieser Austausch* tatsächlich Verständnis auf und fängt seine eigenen Fehler ab — oder produziert er nur schnell etwas Plausibles?

AIPA begann als Versuch, das für meine eigenen Gespräche zu beantworten — das Transkript als Daten zu behandeln, statt einem Bauchgefühl zu vertrauen, ob ein Austausch „gut gelaufen" ist.

## Wie es aufgebaut ist

Zwei unabhängige Instrumente teilen sich eine Methodik:

- **AIPA-K** klassifiziert die strukturelle *Komplexität* der gestellten Fragen (K1–K5) entlang acht Verhaltensdimensionen: Curiosity, Depth of Inquiry, Iterative Learning, Cross-domain Integration, Problem-solving Behaviour, Information Seeking, Reflective Thinking, Experimentation.
- **AIPA-E** klassifiziert *Korrektur-Ereignisse* (E1–E5). Nicht „Fehler" — ein Fehler braucht eine Grundwahrheit, über die der Richter nicht zuverlässig verfügt. Ein Korrektur-Ereignis ist im Transkript direkt beobachtbar: Eine Prämisse, Annahme oder Behauptung wird revidiert, zurückgenommen oder als falsch erwiesen — durch den Nutzer, das Modell oder die Realität (z. B. einen fehlgeschlagenen Test). Bewertet auf drei unabhängigen Achsen: Schweregrad, Quelle, Latenz.

Beide laufen durch vier isolierte Richter-Prompts, jeder in einer eigenen frischen Sitzung ausgeführt, sodass kein Richter je den Bericht eines anderen sieht:

| Prompt | Rolle | Sieht |
|---|---|---|
| A — Komplexitäts-Richter | Klassifiziert K1–K5 | Nur das Transkript, blind |
| B — Korrektur-Richter | Klassifiziert E1–E5 | Nur das Transkript, blind, unabhängig von A |
| C — Komparator | Vergleicht Berichte über Durchläufe und Instrumente hinweg | Nur gesperrte Richter-Berichte — nie Reflect-Daten |
| D — Maintainer | Schlägt die nächste Version vor | Nur angesammelte Reflect-Blöcke — nie die eigentlichen Befunde |

Innerhalb jedes Richters laufen die Phasen strikt sequentiell und sperren, bevor die nächste beginnt: eine Kontaminationserklärung, Evidenzerhebung (eine Mindestabdeckung an Domänen ist erzwungen, nicht optional), Klassifikation (danach eingefroren), Validierung und Selbstkritik, sowie ein maschinenlesbarer Reflect-Block, der den Maintainer speist.

Zwei Regeln halten das Instrument ehrlich: eine **Verwerfungsregel**, die jede Evidenz verwirft, die *über AIPA selbst* handelt — damit es sich nicht seine eigenen Hausaufgaben bewerten kann — und eine **Attributionsregel**, die ausschließlich die Fragestruktur des Menschen bewertet, nie die Antwortkomplexität des Modells.

Dass die vier Richter als separate Prompts laufen, ist Design, kein Zufall. Eine API-orchestrierte Version wurde früh skizziert und wieder verworfen — manuelle Isolation machte Kontaminationsfreiheit leichter garantierbar und, wichtiger noch, leichter auditierbar.

## Was der Einsatz ergeben hat

- Plattformübergreifende Tests deckten einen echten methodischen Fehler auf, nicht nur eine Claude-Eigenheit: Ein Durchlauf auf GPT zeigte, dass ein Richter, der aus bereits zusammengefasstem Kontext statt aus einer frischen Suche arbeitet, eine unkontrollierte Selektionsverzerrung einführt. Prompt B bricht jetzt hart ab, statt auf Fragmenten fortzufahren.
- *Reflective Thinking* hat sich über wiederholte, unabhängige Durchläufe hinweg als die Dimension mit der geringsten Übereinstimmung erwiesen — ein stabiles Muster über Versionen hinweg, kein Rauschen, und jetzt ein benanntes Ziel für v0.5.
- Der letzte vollständige Durchlauf zog Evidenz aus 12 unabhängigen Gesprächsdomänen — doppelt so viel wie das im Protokoll erzwungene Minimum —, die technisches, administratives und alltägliches Material abdeckten; das Instrument hielt auch außerhalb eines engen Testfelds stand.
- Das Instrument ist darauf ausgelegt, sich selbst zu revidieren: Prompt D sieht niemals einen einzelnen Befund, nur Reflect-Logs vergangener Durchläufe — diese Schleife treibt die bereits für v0.5 vorgemerkten offenen Punkte an.

## Bekannte Grenzen

- Wenn nur Gesprächszusammenfassungen (keine Rohtranskripte) als Evidenz verfügbar sind, stuft AIPA-E die Konfidenz auf den betroffenen Achsen ausdrücklich herab, statt eine Klassifikation zu erzwingen.
- Daten zur Inter-Judge-Reliabilität sind noch dünn. Mehr unabhängige Durchläufe — idealerweise von anderen Nutzern, an anderen Gesprächen — würden sie schneller stärken als weitere Durchläufe einer einzelnen Person.

## Status

Aktiv, aktuell **v0.4**. AIPA-K und AIPA-E versionieren unabhängig voneinander. Mehrere v0.5-Änderungen stehen bereits aus Maintainer-Ausgaben an.

## Repository-Struktur

```
/prompts/en/   Prompts A–D, Englisch (kanonisch)
/prompts/de/   Prompts A–D, Deutsch (Original)
/prompts/pl/   Prompts A–D, Polnisch
/examples/     Anonymisierte Beispiel-Richterberichte und ein vollständiger Durchlauf
README.md      Englische Fassung
README.de.md   Diese Datei (Deutsch)
README.pl.md   Polnisch
LICENSE
```

## Verwendung

Die Richter sind Prompts, kein Code. Führe sie nacheinander aus, jeweils in einer sauberen Sitzung ohne angehängten Vorkontext:

1. Prompt A auf ein Transkript anwenden → gesperrten Bericht speichern.
2. Prompt B auf *dasselbe* Transkript anwenden, separat → gesperrten Bericht speichern.
3. Beide gesperrten Berichte — niemals das Rohtranskript — in Prompt C für den instrumentübergreifenden Vergleich einspeisen.
4. Sobald sich Reflect-Blöcke über mehrere Durchläufe angesammelt haben, ausschließlich diese in Prompt D für die Änderungsliste der nächsten Version einspeisen.

Führe alle vier Prompts einer Bewertungsserie in derselben Sprachspur aus (alle aus `/prompts/de/`, alle aus `/prompts/en/` oder alle aus `/prompts/pl/`). Die drei Spuren sind originalgetreue Übersetzungen derselben Methodik, aber der maschinenlesbare Reflect-Block verwendet je Sprache unterschiedliche Feldnamen, und Prompt D erwartet die Feldnamen seiner eigenen Spur.

## Lizenz

MIT.
