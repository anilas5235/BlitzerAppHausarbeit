# Produktplan & Zeitplan

Dieses Kapitel beschreibt die strukturierte Zerlegung (Work Breakdown Structure), den Zeitplan mit Meilensteinen sowie
die Ressourcenplanung für die BlitzerApp. Fokus: rein clientseitige Entwicklung ohne eigenes Backend, Nutzung offener
Schnittstellen (Overpass/OSM), Privacy-by-Design.

Im Sinne eines agilen Vorgehens nach Scrum werden die Arbeitspakete nicht als starre, vollständig vorab geplante
Einheiten verstanden, sondern als Grundlage für ein Product Backlog. Die Umsetzung erfolgt iterativ in Sprints, in
denen jeweils ein potenziell auslieferbares Inkrement entsteht.

Hinweis: Vorgehen gemäß Scrum-Grundlagen; vgl. Scrum Guide (2020) und Agile Manifest (siehe Quellenverzeichnis).

## 4.2 Arbeitspakete (WBS)

Die Arbeitspakete beschreiben die fachlichen und technischen Bausteine, die zur Umsetzung der BlitzerApp erforderlich
sind. Jedes Arbeitspaket enthält eine kurze Beschreibung, die Ziele, erwarteten Ergebnisse (Deliverables), User Value,
geschätzten
Aufwand sowie gegebenenfalls Abhängigkeiten zu anderen Paketen. Die Arbeitspakete sind in Phasen gegliedert, die jeweils
einen logischen Abschnitt des Entwicklungsprozesses darstellen. Die Arbeitspakete sind als Epics/Storys zu verstehen,
die im Rahmen der Plannings/ Refinements weiter in Tasks zerlegt und geschätzt werden müssen. Auch die Priorisierung
erfolgt dynamisch im Product Backlog. Wichtig ist, dass die Arbeitspakete als lebendige Artefakte betrachtet werden, die
im Projektverlauf angepasst und erweitert werden können, nach Absprache mit den Stakeholdern, dem Product Owner und dem
Entwicklungsteam (z. B. bei neuen Erkenntnissen, geänderten Anforderungen oder technischen Herausforderungen).

### 4.2.1 Grundlagen & MVP

#### Phase: Preparation – Grundlagen & Refinement

| ID    | Titel                                      | Ziel                                                                               | Deliverables                                                 | User Value                                                                                                                                                               | Abhängigkeiten   | Aufwand |
|-------|--------------------------------------------|------------------------------------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|---------|
| AP-A1 | Refinement der MVP Anforderungen           | Detaillierte Verfeinerung aus Kapitel 3; MUSS/SOLL finalisieren für den MVP-Scope. | Abgenommene Anforderungsliste, Priorisierung.                | Als Product Owner möchte ich eine klare, priorisierte Anforderungsliste für den MVP haben, damit das Team Sprints zielgerichtet planen kann.                             | Kapitel 3 fertig | M       |
| AP-A2 | Architektur-Validierung (Client-only)      | Bestätigung Layer-Modell, Auswahl Flutter vs. Alternative.                         | Architektur-Diagramm, Technologieentscheidung, Risiko-Check. | Als Entwickler:in möchte ich eine validierte Architektur und einen Technologie-Stack haben, damit ich mit der Implementierung des MVP beginnen kann.                     | AP-A1            | L       |
| AP-A3 | Setup Entwicklungsumgebung & Projektgerüst | Repo-Struktur, CI-Basis, Linter, erste Build-Konfiguration.                        | Grundgerüst, README, CI-Status „grün“.                       | Als Entwickler:in möchte ich eine funktionierende Entwicklungsumgebung und ein initiales Projektgerüst haben, damit ich effizient mit der Implementierung beginnen kann. | AP-A2            | S       |

#### Phase: MVP – MVP Kern

Phase MVP stellt den MVP-Scope dar, der in einem ersten Release ausgeliefert werden kann (Sideloading).
Die Elemente AP-B1 bis AP-B6 sind Must-have für den MVP; Erweiterungen (Phase EI und EII) bauen darauf auf.
Es wird empfohlen, die Arbeitspakete in der angegebenen Reihenfolge umzusetzen, da spätere Pakete auf den
Ergebnissen früherer Pakete aufbauen. Jedoch wird nicht ausgeschlossen, dass einzelne Pakete parallelisiert oder in
abweichender Reihenfolge bearbeitet werden, sofern die Abhängigkeiten beachtet werden. Ab AP-B3 sollten Testnutzer bei
den Entwicklungen einbezogen werden (z.B. im Review), um frühes Feedback zu Funktionalität und Usability zu erhalten.

| ID    | Titel                                       | Ziel                                                                      | Deliverables                                       | User Value                                                                                                                                                                       | Abhängigkeiten | Aufwand | Besonderheiten                                                                                                                      |
|-------|---------------------------------------------|---------------------------------------------------------------------------|----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|---------|-------------------------------------------------------------------------------------------------------------------------------------|
| AP-B1 | Standortbestimmung (Foreground)             | Live-Position mit Update-Stream.                                          | LocationService Modul, Permission-Dialog.          | —                                                                                                                                                                                | —              | S       | —                                                                                                                                   |
| AP-B2 | Overpass-Abfrage + Parser                   | Abfrage stationärer Blitzer und maxspeed (optional) für Bounding Box.     | OverpassClient, QueryBuilder, Parser-Tests.        | Als Fahrer:in möchte ich, dass Blitzerstandorte zuverlässig geladen werden, damit ich mich auf die Warnungen der App verlassen kann.                                             | AP-B1          | M       | —                                                                                                                                   |
| AP-B3 | Kartenintegration & Tile-Provider           | Anzeige Grundkarte + Attribution.                                         | MapView, Attribution-Leiste.                       | Als Fahrer:in möchte ich eine übersichtliche Karte sehen, damit ich meine aktuelle Umgebung und relevante Blitzer besser einordnen kann.                                         | AP-B1          | M       | —                                                                                                                                   |
| AP-B4 | Warnlogik (Distanzberechnung + HUD + Audio) | Erste visuelle/akustische Warnung beim Eintritt in konfigurierten Radius. | WarningEngine, HUD-Komponente, Basis-Sound.        | Als Fahrer:in möchte ich frühzeitig und klar erkennbar vor Blitzern gewarnt werden, damit ich mein Fahrverhalten rechtzeitig anpassen kann.                                      | AP-B2          | M       | —                                                                                                                                   |
| AP-B5 | local Disclaimer & Datenschutzinfo          | Anzeige rechtlicher und datenschutzrelevanter Hinweise beim ersten Start. | Disclaimer-View, Persistenz-Logik.                 | Als Nutzer:in möchte ich transparent über die Datenquellen und deren Nutzung sowie die rechtlichen Risiken informiert werden, damit ich eine bewusste Entscheidung treffen kann. | AP-B4          | S       | Muss länderspezifische Hinweise unterstützen (z. B. DE, AT, CH). Initial nur ENG/DE.                                                |
| AP-B6 | POI-Overlay & Cache                         | Darstellung gefundener POIs, lokaler Cache (Hive/SQLite).                 | CacheRepository, POI-Modelle, Overlay-Komponenten. | Als Fahrer:in möchte ich, dass Blitzer-Standorte auch bei kurzzeitigen Netzwerkproblemen verfügbar sind, damit ich kontinuierlich gewarnt werde.                                 | AP-B2          | M       | —                                                                                                                                   |
| AP-B7 | Geofencing (Hintergrundwarnungen)           | Energieeffiziente Hintergrundwarnungen.                                   | GeofencingService, Testfälle.                      | Als Fahrer:in möchte ich auch bei gesperrtem Bildschirm rechtzeitig und energieeffizient gewarnt werden, damit ich mich auf die Fahrt konzentrieren kann.                        | AP-B4          | L       | Enthält initial einen Spike zur Evaluierung der Plattform-Geofencing-Möglichkeiten, um technische Risiken frühzeitig zu reduzieren. |

### 4.2.2 AppStore-Release & Betrieb

Nach Fertigstellung des MVP-Kerns (Phase MVP) und Validierung der Grundfunktionalität folgt die Phase R, die auf
Qualitätssicherung, Release-Vorbereitung und den eigentlichen Launch abzielt. Diese Phase stellt sicher, dass die App
den Anforderungen an Stabilität, Usability und Store-Compliance entspricht.

#### Phase: R – AppStore-Release & Qualität

| ID    | Titel                                        | Ziel                                  | Deliverables                                      | User Value                                                                                                                                                                                               | Abhängigkeiten      | Aufwand |
|-------|----------------------------------------------|---------------------------------------|---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|---------|
| AP-R1 | Testautomatisierung Ausbau                   | ≥90% Branch Coverage kritische Logik. | Test-Suite, Coverage-Bericht.                     | Als Entwickler:in möchte ich eine umfassende Testabdeckung der kritischen Geschäftslogik sicherstellen, damit ich Änderungen mit Vertrauen vornehmen kann und die Stabilität der App gewährleistet ist.  | Abschluss Phase MVP | M       |
| AP-R2 | Beta-Test & Feedback-Auswertung              | Stabilitäts-/Usability-Prüfung.       | Testprotokolle, Anpassungsliste.                  | Als Product Owner möchte ich durch einen Beta-Test wertvolles Feedback von echten Nutzer:innen erhalten, damit wir die App vor dem offiziellen Release verbessern und an die Zielgruppe anpassen können. | Abschluss Phase MVP | M       |
| AP-R3 | App-Store Vorbereitung (Listing, Compliance) | Einreichungsbereitschaft.             | Beschreibung, Screenshots, Datenschutz-Formulare. | Als Product Owner möchte ich sicherstellen, dass die App den Anforderungen der App-Stores entspricht, damit der Veröffentlichungsprozess reibungslos verläuft und die App zugänglich ist.                | AP-R2               | S       |
| AP-R4 | Release-Kandidaten & Final Review            | Freigabe.                             | RC-Builds, Abschlusscheckliste.                   | Als Entwickler:in möchte ich sicherstellen, dass der Release-Kandidat den Qualitätsstandards entspricht, damit die App stabil und zuverlässig bereitgestellt werden kann.                                | AP-R3               | S       |

Die Phase W folgt dem Release und konzentriert sich auf die Wartung, Fehlerbehebung und das Monitoring der App im
laufenden Betrieb. Ziel ist es, die Stabilität zu gewährleisten und auf Nutzerfeedback zu reagieren. Diese Phase ist
laufend und wird über die gesamte Lebensdauer der App fortgesetzt.

#### Phase: W – Betrieb/Wartung (laufend)

| ID    | Titel                               | Ziel                                   | Deliverables                           | User Value                                                                                                                                     | Aufwand               |
|-------|-------------------------------------|----------------------------------------|----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|
| AP-W1 | Fehlerbehebungen / Patch-Zyklus     | Stabilität, Crashrate < 0.5%.          | Bugfix-Releases, Changelog.            | Als Nutzer:in möchte ich, dass die App regelmäßig aktualisiert wird, um Fehler zu beheben und die Stabilität zu gewährleisten.                 | laufend               |
| AP-W2 | Monitoring lokale Metriken (Opt-in) | Verbesserungsdaten ohne Tracking.      | Monitoring-Modul, Dashboard.           | Als Entwickler:in möchte ich anonymisierte, lokal aggregierte Metriken sammeln können, um die App kontinuierlich zu verbessern, ohne Tracking. | S (Initial) + laufend |
| AP-W3 | Community-Feedback Auswertung       | Priorisierung Bugfixes/Verbesserungen. | Feedback-Log, priorisierte ToDo-Liste. | Als Entwickler:in möchte ich das Feedback der Nutzer:innen systematisch auswerten können, um gezielt auf deren Bedürfnisse einzugehen.         | laufend               |

### 4.2.3 Erweiterungs-Backlog

Das Erweiterungs-Backlog (Phase E) enthält optionale Features und Verbesserungen, die über den MVP-Kern hinausgehen.
Diese Features sind nicht zwingend erforderlich, bieten jedoch zusätzlichen Nutzen für dieNutzer:innen und sollten in
späteren Releases implementiert werden. Es wird empfohlen, diese Arbeitspakete nach Abschluss derPhase MVP zu
priorisieren, neu zu bewerten und in das Product Backlog aufzunehmen.

| ID    | Titel                                           | Ziel                                          | Deliverables                                     | User Value                                                                                                                                                                        | Abhängigkeiten | Aufwand | Besonderheiten                                                                                                                                   |
|-------|-------------------------------------------------|-----------------------------------------------|--------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| AP-E1 | Offline-Grundfunktion (Letzte Region)           | Anzeige letzter POIs ohne Netz.               | Cache-Ladepfad, Offline-Hinweis.                 | Als Nutzer:in möchte ich auch ohne aktive Internetverbindung vor Blitzern gewarnt werden, damit ich mich in Gebieten mit schlechter Netzabdeckung sicher fühle.                   | AP-B4          | S       | —                                                                                                                                                |
| AP-E2 | OSM Notes Integration (Meldungen)               | Nutzer kann Note erstellen (anonym/OAuth).    | NotesClient, Meldedialog, Validierung.           | Als Nutzer:in möchte ich fehlende Blitzer anonym melden können, damit die Datenqualität gemeinsam verbessert wird.                                                                | AP-B3          | M       | —                                                                                                                                                |
| AP-E3 | Einstellungen (Radius, Ton, Datenschutzhinweis) | Persistente Konfiguration.                    | SettingsView, SettingsStore, Datenschutzhinweis. | Als Nutzer:in möchte ich die Warnradius- und Toneinstellungen an meine Bedürfnisse anpassen können, damit die App meinen Präferenzen entspricht.                                  | AP-B5          | S       | —                                                                                                                                                |
| AP-E4 | Performance & Energieoptimierung                | Einhaltung Startzeit, Latenz, Akku-Verbrauch. | Profiling-Bericht, Optimierungspatches.          | Als Nutzer:in möchte ich, dass die App schnell startet, Warnungen ohne Verzögerung anzeigt und den Akkuverbrauch minimiert, damit meine Fahrerfahrung nicht beeinträchtigt wird.  | AP-W2          | M       | Fokus auf kritische Performance-Pfade (App-Start, Warn-Latenz) und Energieverbrauch im Hintergrundbetrieb, inkl. Nutzung der Metriken aus AP-W2. |
| AP-E5 | Erweiterte Offline-Cache/Regionen               | Vorkonfiguration zusätzlicher Regionen.       | Regionpack-Logik, Speichergrößeninfo.            | Als Nutzer:in möchte ich zusätzliche Regionen für die Offline-Nutzung herunterladen können, damit ich auch in Gebieten ohne Netzabdeckung zuverlässig vor Blitzern gewarnt werde. | AP-E1, AP-B6   | M       | —                                                                                                                                                |
| AP-E6 | Mehrsprachigkeit (DE/ES/FR/...)                 | i18n Grundlagen.                              | Lokalisierte Strings, Umschaltlogik.             | Als nicht-englischsprachige:r Nutzer:in möchte ich die App in meiner bevorzugten Sprache nutzen können, damit ich alle Funktionen und Warnungen problemlos verstehe.              | AP-E3          | M       | —                                                                                                                                                |
| AP-E7 | Accessibility Basis                             | Kontraste, Labels, Screenreader-Test.         | A11y-Checkliste, UI-Anpassungen.                 | Als Nutzer:in mit Assistive-Technologien möchte ich die App barrierearm bedienen können, damit Warnungen zuverlässig zugänglich sind.                                             | AP-B4          | M       | —                                                                                                                                                |

