# 4.2 Zeitplan und Meilensteine

Dieses Kapitel beschreibt den zeitlichen Ablauf der Umsetzung der BlitzerApp auf Basis der in Kapitel 4.1
beschriebenen Arbeitspakete. Der Fokus liegt auf einem agilen Vorgehen mit festen Timeboxen (Sprints) und einer
phasenorientierten Planung. Der Zeitplan ist bewusst grob gehalten und versteht sich als Orientierung, die im Rahmen
von Backlog Refinements und Sprint-Planungen iterativ geschärft und angepasst wird.

Im Gegensatz zu einem klassischen Projektplan werden keine einzelnen Arbeitspakete fest bestimmten Sprints
zugeordnet. Stattdessen wird für jede Phase eine realistische Anzahl von Sprints geplant. Innerhalb einer Phase
werden die priorisierten Arbeitspakete inkrementell aus dem Product Backlog gezogen.

Zur Strukturierung werden folgende Phasen angesetzt (vgl. Kapitel 4.1):

- Preparation
- MVP-Kern
- AppStore-Release & Qualität
- Betrieb / Wartung (laufend)
- Erweiterungen

## 4.2.1 Phasen und geplante Sprintanzahl

Für das Projekt wird von einem zweiwöchigen Sprint-Rhythmus ausgegangen. Insgesamt wird ein Zeitraum von rund
18–20 Wochen angenommen. Die folgende Übersicht ordnet den Phasen eine typische Anzahl von Sprints zu und zeigt den
jeweiligen inhaltlichen Schwerpunkt. Konkrete Arbeitspakete werden im agilen Sinne erst in den Sprint-Planungen
festgelegt und können sich abhängig von Priorisierung und Kapazität verschieben.

| Phase                            | Geplante Dauer           | Geschätzte Anzahl Sprints | Inhaltlicher Schwerpunkt                                                 |
|----------------------------------|--------------------------|---------------------------|--------------------------------------------------------------------------|
| Preparation                      | ca. 2–4 Wochen           | 1–2 Sprints               | Verfeinerung Anforderungen, Architekturklärung, Projekt-Setup            |
| MVP-Kern                         | ca. 6–10 Wochen          | 4–5 Sprints               | Umsetzung der Must-have-Funktionalität (MVP)                             |
| AppStore-Release & Qualität      | ca. 4 Wochen             | 2 Sprints                 | Testautomatisierung, Beta-Phase, Store-Vorbereitung, Release-Kandidat    |
| Erweiterungszyklen (fortlaufend) | je ca. 4 Wochen          | je 2 Sprints (iterativ)   | Priorisierte Erweiterungen in Zyklen auf Basis von Feedback & Monitoring |
| Betrieb / Wartung (laufend)      | fortlaufend nach Release | nicht fest begrenzt       | Fehlerbehebung, Monitoring, kontinuierliche Verbesserungen               |

Die Phase „Betrieb / Wartung“ wird nicht in eine feste Sprintanzahl überführt, da sie im Sinne eines lebenden
Produkts als kontinuierlicher Prozess verstanden wird. In der Praxis findet auch Wartung in Sprints statt, im Rahmen
kongruenter Team-Sprints; für die hier betrachtete Planung wird sie jedoch nur grob als laufender Post-Release-Prozess
markiert. Die Erweiterungszyklen können je nach Bedarf und Ressourcenplanung mehrfach wiederholt werden, um den
Funktionsumfang der App schrittweise zu erhöhen. Jede Erweiterungsphase sollte mindestens ein neues Release (z. B. 1.1,
1.2) ermöglichen. Die Anzahl der Erweiterungszyklen hängt von den verfügbaren Ressourcen und dem Nutzerfeedback ab.

## 4.2.2 Meilensteine

Die Meilensteine werden im Folgenden nicht einzelnen Sprints, sondern den Phasen und groben Kalenderwochen
zugeordnet. Sie markieren jeweils einen klar definierten Produktzustand, der für Stakeholder nachvollziehbar ist.

**M1: Grundlagen & Architektur abgeschlossen**

- Voraussichtlicher Zeitraum: Ende Preparation (Woche 2–4)
- Zuordnung zu Arbeitspaketen:
    - AP-A1 (Refinement der MVP-Anforderungen)
    - AP-A2 (Architektur-Validierung)
    - AP-A3 (Setup Entwicklungsumgebung & Projektgerüst)
- Ergebnis: Abgenommene, priorisierte Anforderungsliste, validierte Architektur und funktionsfähiges Projektgerüst.
  Das Team kann mit der Umsetzung des MVP-Kerns beginnen.

**M2: Technischer MVP-Kern steht**

- Voraussichtlicher Zeitraum: 1/3 der MVP-Phase (Woche 5–6)
- Schwerpunkt-Arbeitspakete:
    - AP-B1 (Standortbestimmung)
    - AP-B2 (Overpass-Abfrage + Parser)
    - AP-B3 (Kartenintegration)
- Ergebnis: Die technische Grundlage für die Kernfunktionen (Positionsermittlung, Abruf und Darstellung von Blitzern
  auf der Karte) ist vorhanden. Erste interne Tests und Feedbackschleifen sind möglich.

**M3: MVP funktionsfähig (intern nutzbar)**

- Voraussichtlicher Zeitraum: Ende MVP-Phase (Woche 9–10)
- Schwerpunkt-Arbeitspakete:
    - AP-B4 (Warnlogik)
    - AP-B5 (Disclaimer & Datenschutzinfo)
    - AP-B6 (POI-Overlay & Cache)
    - AP-B7 (Geofencing)
- Ergebnis: Alle für den MVP definierten Must-have-Funktionen sind umgesetzt. Die App ist intern nutzbar und kann von
  einem begrenzten Nutzerkreis (z. B. Projektteam, ausgewählte Tester:innen) erprobt werden.

**M4: Beta-Release & Qualitätssicherung**

- Voraussichtlicher Zeitraum: Mitte der Phase AppStore-Release & Qualität (Woche 11–12)
- Schwerpunkt-Arbeitspakete:
    - AP-R1 (Testautomatisierung Ausbau)
    - AP-R2 (Beta-Test & Feedback-Auswertung)
- Ergebnis: Eine stabile Beta-Version der App liegt vor. Die wichtigsten Testfälle sind automatisiert abgedeckt, und
  strukturiertes Nutzerfeedback zur Stabilität und Usability liegt vor. Dieses Feedback fließt in das Product Backlog
  ein.

**M5: AppStore-Release 1.0**

- Voraussichtlicher Zeitraum: Ende der Phase AppStore-Release & Qualität (Woche 13–14)
- Schwerpunkt-Arbeitspakete:
    - AP-R3 (App-Store Vorbereitung)
    - AP-R4 (Release-Kandidaten & Final Review)
    - Start AP-W1 (Fehlerbehebungen / Patch-Zyklus)
- Ergebnis: Die Version 1.0 der App ist in den relevanten Stores veröffentlicht. Der reguläre Wartungsprozess ist
  etabliert; erste reale Nutzungsdaten und Fehlerberichte können in die weitere Planung einfließen.

**M6: Stabilisierung & erste Erweiterungen**

- Voraussichtlicher Zeitraum: Ende des ersten Erweiterungszyklus (Woche 17–18)
- Schwerpunkt-Arbeitspakete (je nach Priorisierung):
    - AP-W1–W3 (Wartung, Monitoring, Feedback-Auswertung)
    - AP-E1 (Offline-Grundfunktion)
    - AP-E3 (Einstellungen)
    - optional: weitere Erweiterungen (z. B. AP-E2 OSM Notes, AP-E4 Performance & Energieoptimierung)
- Ergebnis: Die App ist im laufenden Betrieb stabilisiert, und erste Erweiterungen erhöhen den praktischen Nutzen für
  die Nutzer:innen (Release 1.1). Auf Basis von Monitoring- und Feedback-Daten werden nächste Ausbaustufen vorbereitet.

Durch die Verortung der Meilensteine auf Phasen- und Zeitachsen-Ebene wird ein klarer Rahmen geschaffen, ohne die
agile Flexibilität der Sprintplanung einzuschränken. Die Verbindung zu den in Kapitel 4.1 definierten Arbeitspaketen
bleibt dabei transparent und nachvollziehbar.

## 4.2.3 Puffer und Gesamtdauer

Die geplante Gesamtdauer des initialen Umsetzungszyklus (Preparation bis erster Erweiterungszyklus) beträgt
ungefähr 18 Wochen. Dabei werden Puffer explizit auf Phasenebene und nicht auf Ebene einzelner Arbeitspakete
modelliert.

**Pufferannahmen:**

- Innerhalb der Phase MVP-Kern wird ein Sprint als impliziter Puffer verstanden (z. B. 3–4 statt exakt 3 Sprints), um
  mit Schätzunsicherheiten umgehen zu können.
- Die Phase AppStore-Release & Qualität enthält zeitlichen Spielraum für unvorhergesehene Verzögerungen im
  App-Store-Prozess oder bei der Behebung kritischer Befunde aus dem Beta-Test.
- Der erste Erweiterungszyklus ist bewusst zeitlich etwas einen Sprint nach dem initialen Release angesetzt, um auf
  Nutzerfeedback und Monitoring-Daten reagieren zu können. Dies dient als Puffer für unvorhergesehene
  Nacharbeiten oder Anpassungen.

**Gesamtbetrachtung:**

- Preparation: ca. 2–4 Wochen (1–2 Sprints)
- MVP-Kern: ca. 6–10 Wochen (4–5 Sprints)
- AppStore-Release & Qualität: ca. 4 Wochen (2 Sprints)
- Erweiterungen (1. Zyklus): ca. 4 Wochen (2 Sprints)

Damit ergibt sich ein realistischer, aber bewusst nicht überdeterminierter Zeitplan. Er bildet einen klaren Rahmen
für die Hausarbeit, lässt aber genügend Flexibilität für eine agile Umsetzung mit sich verändernder Backlog-Priorität.

## 4.2.4 Zeitliche Roadmap

Anstelle eines detaillierten Gantt-Diagramms mit Sprint- und Paketzuordnung wird eine vereinfachte zeitliche Roadmap
verwendet. Diese stellt dar, zu welchem ungefähren Zeitpunkt die einzelnen Phasen und Meilensteine liegen. Grundlage
ist ein Projektstart in Woche 1 und ein zweiwöchiger Sprint-Rhythmus.

```text
Kalenderwochen (relativ):   1-2        3-4        5-6       7-8      9-10       11-12      13-14      15-16      17-18       19+ 
Phasen:
Preparation                 [======]
MVP-Kern                              [============|=========================]
AppStore-Release & Qualität                                                             [========]
Erweiterungen (1. Zyklus)                                                                                           [========]
Betrieb / Wartung                                                                                         [----------------------->

Meilensteine:
M1: Grundlagen & Architektur        ^
M2: Technischer MVP-Kern                           ^
M3: MVP funktionsfähig                                                       ^
M4: Beta-Release                                                                            ^
M5: AppStore-Release 1.0                                                                                  ^
M6: Stabilisierung & erste Erweiterungen                                                                                     ^
```

Erläuterung:

- **Preparation (Woche 1–4, 1–2 Sprints):** Abschluss des Anforderungs-Refinements, Architektur-Entscheidungen und
  Setup (AP-A1–AP-A3). Abschließend liegt eine tragfähige Grundlage für die Umsetzung vor (Meilenstein M1).
- **MVP-Kern (Woche 3–10, 4–5 Sprints):** Überlappend mit dem Ende der Preparation beginnt die Umsetzung des
  MVP-Kerns (AP-B1–AP-B7). Ziel ist ein intern nutzbarer MVP, der schrittweise entsteht. In der ersten Hälfte werden
  vor allem technische Kernfunktionen realisiert (M2), in der zweiten Hälfte wird der MVP vervollständigt (M3).
- **AppStore-Release & Qualität (Woche 11–14, 2 Sprints):** Aufbauend auf dem MVP erfolgt der Ausbau der
  Testautomatisierung, eine Beta-Phase und die Vorbereitung des Store-Listings (AP-R1–AP-R4). Am Ende dieser Phase
  steht der AppStore-Release 1.0 (M5), häufig nach einem vorgelagerten Beta-Meilenstein (M4).
- **Erweiterungen (erster Zyklus, Woche 15–18, 2 Sprints):** Nach dem ersten Release werden ausgewählte
  Erweiterungen (z. B. Offline-Grundfunktion, Einstellungen, erste OSM-Integration) umgesetzt. Am Ende steht ein
  erster Erweiterungs-Meilenstein (M6), der den Funktionsumfang gegenüber Version 1.0 erhöht.
- **Betrieb / Wartung (ab Woche 15, laufend):** Wartung, Monitoring und Fehlerbehebungen werden als kontinuierliche
  Aktivität betrachtet. Sie wird parallel zur Erweiterungsphase stattfinden und setzen sich auch nach dem hier
  betrachteten Zeitraum fort.

Bei der Darstellung steht die agile Idee im Vordergrund, dass pro Phase jeweils die aktuell wichtigsten, priorisierten
Backlog-Einträge gezogen werden, solange die übergeordneten Zeitboxen und Meilensteine eingehalten werden.