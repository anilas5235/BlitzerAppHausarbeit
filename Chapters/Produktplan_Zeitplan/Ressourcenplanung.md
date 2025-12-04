## 4.3 Ressourcenplanung

Die Ressourcenplanung verknüpft die in Kapitel 4.1 definierten Arbeitspakete mit dem zeitlichen Rahmen aus Kapitel 4.2
und ordnet ihnen die benötigten Rollen, Kapazitäten und Skills zu. Im Fokus steht ein kleines, cross-funktionales
Kernteam, das über die Phasen hinweg möglichst stabil bleibt. Zusätzliche Rollen werden punktuell, vor allem in
Qualitäts- und Erweiterungsphasen, eingebunden. Für die Dauer des Projekts wird das Kernteam idealerweise mit 100 %
seiner verfügbaren Arbeitszeit für das Projekt eingeplant, um Kontextwechsel und Koordinationsaufwand zu minimieren.

### 4.3.1 Rollen und Kapazitäten

Rollen & grobe Kapazitäten (Annahme kleines Kernteam, 1 Sprint = 2 Wochen, ca. 18–20 Wochen Projektlaufzeit für den
initialen Zyklus):

- Product Owner (ca. 0,4 FTE):
    - Verantwortlich für Produktvision, Priorisierung des Product Backlogs und Abnahme der Inkremente im Sprint Review.
    - Kapazitätsschwerpunkt: durchgängig, mit erhöhter Auslastung in Preparation (Anforderungs-Refinement),
      AppStore-Release (Store-Vorbereitung) und beim Management von Erweiterungswünschen.
- Mobile Entwickler:
    - Dev1 (Flutter Lead, ca. 1,0 FTE):
        - Technische Gesamtverantwortung (Architektur, Build, CI), Implementierung Kernfunktionen (AP-A2, AP-B1–B4,
          AP-B6, AP-R1–R4, zentrale Erweiterungen).
    - Dev2 (Flutter/Testing, ca. 0,8 FTE ab Phase MVP):
        - Unterstützung bei Implementierung, Tests und speziell bei Overpass-Integration, Performance-Optimierung und
          OSM Notes (AP-B2, AP-E2, AP-E4).
- UX/Design (ca. 0,3 FTE):
    - Gestaltung der UI, Onboarding, Konzeption des Warn-HUDs, Unterstützung bei Accessibility (AP-B3, AP-B4,
      AP-E3, AP-E7).
- QA/Tester (ca. 0,5 FTE ab Release-/Qualitätsphase):
    - Testplanung, manuelle Tests, Begleitung der Beta-Phase, Unterstützung bei Testautomatisierung (AP-R1, AP-R2,
      Performance-/Energieprofiling in AP-E4).
- Privacy/Compliance Beratung (ca. 0,1 FTE ad hoc):
    - Prüfung der Datenschutztexte, rechtlicher Hinweise und Disclaimer (AP-B5, AP-R3, AP-E3).
- Community Liaison (ggf. mit Product Owner kombiniert, ca. 0,1 FTE):
    - Zuständig für Guidelines und Prozesse rund um Community-Funktionen (z. B. OSM Notes), sowie strukturierte
      Auswertung von Nutzerfeedback und Monitoringdaten (AP-E2, AP-W3).

Die hier skizzierten FTE-Kapazitäten werden über die in Abschnitt 4.2 beschriebenen Phasen und Sprints mit den in 4.1
beschriebenen Arbeitspaketen verknüpft. Sie bilden damit die Grundlage für die weitere Kapazitäts- und
Kostenplanung (vgl. Kapitel 5). Da das Kernteam für den Projektzeitraum voll auf die BlitzerApp allokiert ist, steht
nicht die Verteilung von Auslastungsgraden zwischen Projekten im Fokus, sondern vielmehr die inhaltliche Nutzung der
verfügbaren Kapazität für die wichtigsten Backlog-Einträge pro Phase.

Die Ressourcenplanung folgt dem Scrum-Prinzip eines stabilen, cross-funktionalen Teams. Der Product Owner verantwortet
Vision und Priorisierung des Product Backlogs sowie die Abnahme der Inkremente im Sprint Review. Das Entwicklungsteam
(Entwickler:innen, UX/Design, QA) liefert gemeinsam die Sprintziele und organisiert sich in der Umsetzung eigenständig.
Privacy/Compliance sowie Community Liaison werden bedarfsgerecht in Sprints eingebunden, insbesondere bei
Datenschutzthemen und Community-Funktionen.

### 4.3.2 Skills und Spezialisierungen

Die folgende Skill-Übersicht zeigt, welche Kernthemen im Team abgedeckt sind und welche Arbeitspaket-Gruppen davon
besonders profitieren. Sie wird bei der Zuordnung komplexerer Arbeitspakete (z. B. Geofencing, Performance-Optimierung
oder OSM Notes) zu Phasen genutzt und dient als Grundlage für die Einschätzung technischer Risiken und möglicher
Engpässe. Neben domänenspezifischen Fähigkeiten (z. B. Geodaten, OSM) werden auch allgemeine agile und
qualitätsorientierte Kompetenzen betrachtet.

#### 4.3.2.1 Technische und domänenspezifische Skills

- Geodaten / Overpass / OSM-Basis (Dev1 Lead, Dev2)
    - Relevanz insbesondere für: AP-B2 (Overpass-Abfrage), AP-B6 (POI-Overlay & Cache), AP-E2 (OSM Notes), AP-E5
      (erweiterte Offline-Caches).
- Performance / Energieprofiling (Dev2, QA)
    - Relevanz insbesondere für: AP-B7 (Geofencing), AP-E4 (Performance & Energieoptimierung).
- Karten- und UI-Design (UX, Dev1)
    - Relevanz insbesondere für: AP-B3 (Kartenintegration & UI), AP-B4 (Warn-HUD), AP-E3 (Einstellungen), AP-E7
      (Accessibility Basis).
- OAuth / OSM Notes (Dev2)
    - Relevanz insbesondere für: AP-E2 (OSM Notes Integration), ggf. weitere Community-Funktionen.
- Architektur / Build / CI / DevOps (Dev1)
    - Relevanz insbesondere für: AP-A2 (Architektur-Validierung), AP-A3 (Projektgerüst & CI), AP-R1
      (Testautomatisierung), laufende Wartung.
- iOS‑Plattformkompetenz (Swift/SwiftUI, Dev1)
    - Kernkompetenzen: CoreLocation (inkl. Region Monitoring), Hintergrundmodi (Location Updates, Background Fetch),
      lokale Benachrichtigungen (UNUserNotificationCenter), Audio-Ausgabe (AVAudioSession), App‑Store‑Richtlinien,
      TestFlight‑Distribution.
    - Relevanz insbesondere für: AP-B1 (Standortbestimmung), AP-B4 (Warnlogik/Benachrichtigungen), AP-B7 (Geofencing),
      AP-R3/AP-R4 (Store‑Vorbereitung/Release).
- Android‑Plattformkompetenz (Kotlin/Jetpack, Dev2)
    - Kernkompetenzen: FusedLocationProviderClient, GeofencingClient, Foreground Service mit Notification,
      WorkManager/AlarmManager, Runtime‑Permissions (inkl. Hintergrundstandort), Doze/App‑Standby‑Richtlinien,
      Play‑Console & Review‑Guidelines.
    - Relevanz insbesondere für: AP-B1 (Standortbestimmung), AP-B4 (Warnlogik/Benachrichtigungen), AP-B7 (Geofencing),
      AP-E4 (Performance/Energie), AP-R3/AP-R4 (Store‑Vorbereitung/Release).

#### 4.3.2.2 Agile und qualitätsorientierte Skills

- Agile Produktentwicklung / Scrum (Product Owner, gesamtes Team)
    - Fähigkeit, Anforderungen inkrementell zu verfeinern, ein priorisiertes Product Backlog zu pflegen und in kurzen
      Zyklen nutzbare Inkremente zu liefern. Relevanz über alle Phasen, insbesondere in Preparation (AP-A1) und beim
      Umgang mit Feedback aus Beta-Phase und Betrieb (AP-R2, AP-W3).
- Testdesign und Testautomatisierung (QA, Dev1, Dev2)
    - Fähigkeit, systematische Testfälle zu entwerfen und automatisiert umzusetzen (Unit-, Widget- und ggf.
      Integrationstests). Relevanz insbesondere für AP-R1 (Testautomatisierung Ausbau), sowie generell für die
      Absicherung kritischer Logik im MVP-Kern und in Erweiterungen.
- DevOps / CI/CD-Pipelines (Dev1, QA)
    - Erfahrung mit automatisierten Builds, Tests und Deployment-Pipelines (z. B. GitHub Actions, mobile CI-Dienste).
      Unterstützt eine schnelle Rückmeldung zu Codeänderungen und reduziert manuelle Fehler im Release-Prozess.
- UX-Research und Usability-Testing (UX, PO, QA)
    - Fähigkeit, Nutzerfeedback qualitativ auszuwerten (z. B. aus Beta-Tests, Interviews) und in Designentscheidungen
      einfließen zu lassen. Relevanz für die Gestaltung des Warn-HUD, der Einstellungen und der Onboarding-Flows.
- Datenschutz- und Compliance-Kompetenz (Privacy/Compliance, PO)
    - Verständnis für rechtliche Rahmenbedingungen (insb. Datenschutz und rechtliche Situation von Blitzer-Apps) und
      deren Übersetzung in klare Hinweise und UI-Elemente (AP-B5, AP-R3, AP-E3).

#### 4.3.2.3 Teamübergreifende Aspekte

Aus dieser Skill-Matrix lässt sich ableiten, dass bestimmte Themen (z. B. Overpass/OSM, Performanceoptimierung,
Datenschutz) klaren "Ownern" im Team zugeordnet sind. Gleichzeitig wird darauf geachtet, dass Rollen breit genug
aufgestellt sind, um Pairing und Wissensaustausch zu ermöglichen und sogenannte Bus-Faktoren zu reduzieren. Dies ist
insbesondere bei kritischen Querschnittsthemen wie Architektur, Testautomatisierung und Datenschutz wichtig.

In kritischen Phasen (z. B. kurz vor AppStore-Release oder beim Einführen neuer Community-Funktionen) kann auf Basis
dieser Skill-Matrix entschieden werden, welche Arbeitspakete priorisiert und welche gegebenenfalls in spätere
Erweiterungszyklen verschoben werden. Die Skills bestimmen damit nicht nur, _wer_ welche Aufgaben übernehmen kann,
sondern auch, welche Themen aus Risikosicht frühzeitig adressiert werden sollten.

Zur besseren Übersicht fasst Tabelle 4‑x die zentralen Skillbereiche, die primär verantwortlichen Rollen sowie die
zugehörigen Arbeitspaket-Gruppen und unterstützenden Tools zusammen:

| Skillbereich              | Hauptrollen            | Zentrale Arbeitspakete / Phasen                          | Relevante Tools / Ressourcen               |
|---------------------------|------------------------|----------------------------------------------------------|--------------------------------------------|
| OSM / Overpass / Geodaten | Dev1 (Lead), Dev2      | AP-B2, AP-B6, AP-E2, AP-E5 (MVP, Erweiterungen)          | Overpass API, OSM-Dokumentation            |
| Karten & UI / UX          | UX, Dev1               | AP-B3, AP-B4, AP-E3, AP-E7 (MVP, Erweiterungen)          | Design-Tools, Map-Framework, Tile-Provider |
| Performance & Geofencing  | Dev2, QA               | AP-B7, AP-E4 (MVP, Erweiterungen)                        | Profiling-Tools, Gerätefarm/Testgeräte     |
| iOS-Plattform             | Dev1                   | B1, B4, B7, R3, R4 (MVP, Release)                        | Xcode, TestFlight, Apple Developer Console |
| Android-Plattform         | Dev2                   | B1, B4, B7, E4, R3, R4 (MVP, Erweiterungen, Release)     | Android Studio, Play Console, Gerätefarm   |
| Testautomatisierung & QA  | QA, Dev1, Dev2         | R1, R2, W1–W3 (Release, Wartung)                         | Testframeworks, CI/CD-Plattform            |
| Datenschutz & Compliance  | Privacy/Compliance, PO | B5, R3, E3 (MVP, Release, Erweiterungen)                 | Rechtsquellen, interne Guidelines          |
| DevOps / CI/CD            | Dev1, QA               | A3, R1, laufende Wartung (Preparation, Release, Betrieb) | CI/CD-Plattform, Repo-Hosting, Monitoring  |

### 4.3.3 Externe Ressourcen und Tools

Zusätzlich zu den personellen Kapazitäten werden einige externe Ressourcen und Werkzeuge benötigt, die vor allem die
Qualitätssicherung, Performance-Optimierung und den Release-Prozess unterstützen und in die Sachkostenplanung
(Kapitel 5) einfließen. Sie ergänzen die im Team vorhandenen Skills und ermöglichen deren effektiven Einsatz.

Externe Ressourcen / Tools (Auszug):

- Tile-Provider API-Key (Kostenmodell prüfen; Low-Usage Plan):
    - Nutzung vor allem für Kartenanzeige und POI-Overlays (AP-B3, AP-B6, Erweiterungen). Relevante Kostenposition in
      der Finanzplanung (z. B. nutzungsabhängige Gebühren oder Pauschaltarife).
- Geräte/Testumgebung: Mindestens zwei Android-Geräte (Mid-/Low-End), zwei iOS-Generationen zur Abdeckung typischer
  Leistungsprofile:
    - Einsatzschwerpunkte in MVP-Phase (erste Gerätetests), Release-Phase (Beta-Tests, Performance) und Wartung
      (Regressionstests für Bugfixes).
- Profiling-Tools: Android Profiler, Xcode Instruments für Performance- und Energieanalysen:
    - Unterstützen gezielt die Arbeit an AP-B7 (Geofencing) und AP-E4 (Performance & Energieoptimierung) sowie
      allgemeine
      Optimierungen in Erweiterungsphasen.
- CI/CD-Plattform: GitHub Actions, Bitrise o. ä. (Open-Source-freundliche Pläne bevorzugt), um automatisierte Builds,
  Tests und ggf. Beta-Deployments zu ermöglichen:
    - Zentrale Grundlage für AP-A3 (Projektgerüst & CI), AP-R1 (Testautomatisierung) und für einen effizienten
      Patch-/Release-Prozess in der Wartungsphase.

Diese Ressourcen werden über die Phasen hinweg unterschiedlich stark genutzt: Während Profiling-Tools vor allem in
MVP- und Erweiterungsphasen (Performance-Optimierung) zum Einsatz kommen, gewinnt die CI/CD-Plattform in allen Phasen
an Bedeutung, insbesondere jedoch in der Releasephase und im laufenden Betrieb (stabile Build-Pipelines, schnelle
Fehlerbehebung). Dies ermöglicht eine effiziente und qualitativ hochwertige Umsetzung der BlitzerApp im Rahmen des
verfügbaren Kostenrahmens und schafft gleichzeitig Transparenz für die in Kapitel 5 betrachteten Sachkosten.
