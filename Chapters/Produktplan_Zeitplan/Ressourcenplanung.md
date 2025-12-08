## 4.4 Ressourcenplanung

Die Ressourcenplanung verknüpft die in Kapitel 4.2 definierten Arbeitspakete mit dem zeitlichen Rahmen aus Kapitel 4.3
und ordnet ihnen die benötigten Rollen, Kapazitäten und Skills zu. Im Fokus steht ein kleines, cross-funktionales
Kernteam, das über die Phasen hinweg möglichst stabil bleibt. Zusätzliche Rollen werden punktuell, vor allem in
Qualitäts- und Erweiterungsphasen, eingebunden. Für die Dauer des Projekts wird das Kernteam idealerweise mit 100 %
seiner verfügbaren Arbeitszeit für das Projekt eingeplant, um Kontextwechsel und Koordinationsaufwand zu minimieren.

### 4.4.1 Rollen und Kapazitäten

Rollen & grobe Kapazitäten (Annahme kleines Kernteam, 1 Sprint = 2 Wochen, ca. 18–20 Wochen Projektlaufzeit für den
initialen Zyklus):

| Rolle                       | FTE / Umfang              | Hauptaufgaben                                                                                                                                               | Zuordnung / Schwerpunkte                                                                                                                                                             |
|-----------------------------|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Product Owner               | 1,0 FTE                   | Verantwortlich für Produktvision, Priorisierung des Product Backlogs und Abnahme der Inkremente im Sprint Review.                                           | Kapazitätsschwerpunkt: durchgängig; erhöhte Auslastung in Preparation (Anforderungs-Refinement), AppStore-Release (Store-Vorbereitung) und beim Management von Erweiterungswünschen. |
| Mobile Entwickler – Dev1    | 1,0 FTE (Flutter Lead)    | Technische Gesamtverantwortung (Architektur, Build, CI), Implementierung der Kernfunktionen.                                                                | AP-A2, AP-B1–B4, AP-B6, AP-R1–R4, zentrale Erweiterungen.                                                                                                                            |
| Mobile Entwickler – Dev2    | 1,0 FTE (Flutter/Testing) | Unterstützung bei Implementierung, Tests und speziell bei Overpass-Integration, Performance-Optimierung und OSM Notes.                                      | AP-B2, AP-E2, AP-E4.                                                                                                                                                                 |
| UX/Design                   | 1,0 FTE                   | Gestaltung der UI, Onboarding, Konzeption des Warn-HUDs, Unterstützung bei Accessibility.                                                                   | AP-B3, AP-B4, AP-E3, AP-E7.                                                                                                                                                          |
| QA/Tester                   | ca. 1,0 FTE               | Testplanung, manuelle Tests, Unterstützung bei Testautomatisierung, Performance-/Energieprofiling.                                                          | AP-R1, AP-R2, Performance-/Energieprofiling in AP-E4.                                                                                                                                |
| Privacy/Compliance Beratung | ca. 0,1 FTE (ad hoc)      | Prüfung der Datenschutztexte, rechtlicher Hinweise und Disclaimer.                                                                                          | AP-B5, AP-R3, AP-E3.                                                                                                                                                                 |
| Community Liaison           | ca. 0,5 FTE               | Zuständig für Guidelines und Prozesse rund um Community-Funktionen (z. B. OSM Notes) sowie strukturierte Auswertung von Nutzerfeedback und Monitoringdaten. | AP-E2, AP-W3.                                                                                                                                                                        |

Die hier skizzierten FTE-Kapazitäten werden über die in Abschnitt 4.3 beschriebenen Phasen und Sprints mit den in 4.2
beschriebenen Arbeitspaketen verknüpft. Sie bilden damit die Grundlage für die weitere Kapazitäts- und
Kostenplanung (vgl. Kapitel 5). Da das Kernteam für den Projektzeitraum voll auf die BlitzerApp allokiert ist, steht
nicht die Verteilung von Auslastungsgraden zwischen Projekten im Fokus, sondern vielmehr die inhaltliche Nutzung der
verfügbaren Kapazität für die wichtigsten Backlog-Einträge pro Phase.

Die Ressourcenplanung folgt dem Scrum-Prinzip eines stabilen, cross-funktionalen Teams. Der Product Owner verantwortet
Vision und Priorisierung des Product Backlogs sowie die Abnahme der Inkremente im Sprint Review. Das Entwicklungsteam
(Entwickler:innen, UX/Design, QA) liefert gemeinsam die Sprintziele und organisiert sich in der Umsetzung eigenständig.
Privacy/Compliance sowie Community Liaison werden bedarfsgerecht in Sprints eingebunden, insbesondere bei
Datenschutzthemen und Community-Funktionen.

### 4.4.2 Skills und Spezialisierungen

Die folgende Skill-Übersicht zeigt, welche Kernthemen im Team abgedeckt sind und welche Arbeitspaket-Gruppen davon
besonders profitieren. Sie wird bei der Zuordnung komplexerer Arbeitspakete (z. B. Geofencing, Performance-Optimierung
oder OSM Notes) zu Phasen genutzt und dient als Grundlage für die Einschätzung technischer Risiken und möglicher
Engpässe. Neben domänenspezifischen Fähigkeiten (z. B. Geodaten, OSM) werden auch allgemeine agile und
qualitätsorientierte Kompetenzen betrachtet.

#### 4.4.2.1 Technische und domänenspezifische Skills

| Skillbereich                                | Hauptrollen       | Beschreibung / Kernkompetenzen                                                                                                                                                                                  | Relevante Arbeitspakete                                                                                                                                     |
|---------------------------------------------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Geodaten / Overpass / OSM-Basis             | Dev1 (Lead), Dev2 | Umgang mit Geodaten, Overpass-API und OSM-Basisfunktionen (Abfragen, Filtern, Caching von POIs).                                                                                                                | AP-B2 (Overpass-Abfrage), AP-B6 (POI-Overlay & Cache), AP-E2 (OSM Notes), AP-E5 (erweiterte Offline-Caches)                                                 |
| Performance / Energieprofiling              | Dev2, QA          | Analyse und Optimierung von Performance und Energieverbrauch der App, inkl. Messung, Profiling und Ableitung von Optimierungsmaßnahmen.                                                                         | AP-B7 (Geofencing), AP-E4 (Performance & Energieoptimierung)                                                                                                |
| Karten- und UI-Design                       | UX, Dev1          | Gestaltung und Implementierung von Karten-UI, Warn-HUD und weiteren visuellen Elementen unter Berücksichtigung von Usability und Klarheit.                                                                      | AP-B3 (Kartenintegration & UI), AP-B4 (Warn-HUD), AP-E3 (Einstellungen), AP-E7 (Accessibility Basis)                                                        |
| OAuth / OSM Notes                           | Dev2              | Integration von OAuth-Workflows und OSM-Notizen, inkl. Authentifizierung, Rechteverwaltung und Umgang mit Community-Beiträgen.                                                                                  | AP-E2 (OSM Notes Integration), ggf. weitere Community-Funktionen                                                                                            |
| Architektur / Build / CI / DevOps           | Dev1              | Definition und Pflege der Systemarchitektur, Build-Konfiguration, CI-Pipelines und DevOps-Prozesse für einen stabilen und wiederholbaren Entwicklungs- und Release-Prozess.                                     | AP-A2 (Architektur-Validierung), AP-A3 (Projektgerüst & CI), AP-R1 (Testautomatisierung), laufende Wartung                                                  |
| iOS‑Plattformkompetenz (Swift/SwiftUI)      | Dev1              | Plattformkenntnisse für iOS: CoreLocation (inkl. Region Monitoring), Hintergrundmodi, lokale Benachrichtigungen, Audio-Ausgabe, App‑Store‑Richtlinien und TestFlight-Distribution.                              | AP-B1 (Standortbestimmung), AP-B4 (Warnlogik/Benachrichtigungen), AP-B7 (Geofencing), AP-R3/AP-R4 (Store‑Vorbereitung/Release)                              |
| Android‑Plattformkompetenz (Kotlin/Jetpack) | Dev2              | Plattformkenntnisse für Android: FusedLocationProviderClient, GeofencingClient, Foreground Services, Hintergrund-Jobs, Runtime-Permissions, Energie- und Doze-Richtlinien, Play‑Console- und Review-Guidelines. | AP-B1 (Standortbestimmung), AP-B4 (Warnlogik/Benachrichtigungen), AP-B7 (Geofencing), AP-E4 (Performance/Energie), AP-R3/AP-R4 (Store‑Vorbereitung/Release) |

#### 4.4.2.2 Agile und qualitätsorientierte Skills

| Skillbereich                          | Hauptrollen                  | Beschreibung                                                                                                                                                                                     | Relevante Arbeitspakete / Phasen                                                        |
|---------------------------------------|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| Agile Produktentwicklung / Scrum      | Product Owner, gesamtes Team | Fähigkeit, Anforderungen inkrementell zu verfeinern, ein priorisiertes Product Backlog zu pflegen und in kurzen Zyklen nutzbare Inkremente zu liefern.                                           | Vorbereitung/Preparation (AP-A1), Umgang mit Feedback (AP-R2, AP-W3)                    |
| Testdesign und Testautomatisierung    | QA, Dev1, Dev2               | Entwurf systematischer Testfälle und Umsetzung in automatisierten Tests (Unit-, Widget- und ggf. Integrationstests), um kritische Logik im MVP-Kern und in Erweiterungen nachhaltig abzusichern. | AP-R1 (Testautomatisierung Ausbau), generelle Absicherung im MVP und Erweiterungen      |
| DevOps / CI/CD-Pipelines              | Dev1, QA                     | Aufbau und Betrieb automatisierter Builds, Tests und Deployment-Pipelines (z. B. GitHub Actions, mobile CI-Dienste) zur schnellen Rückmeldung zu Codeänderungen und Reduktion manueller Fehler.  | AP-A3 (Projektgerüst & CI), AP-R1 (Testautomatisierung), Wartung/Release-Phasen         |
| UX-Research und Usability-Testing     | UX, PO, QA                   | Qualitative Auswertung von Nutzerfeedback (z. B. aus Beta-Tests, Interviews) und Ableitung konkreter Verbesserungen für UI, Interaktionskonzepte und Onboarding-Flows.                           | Gestaltung von Warn-HUD, Einstellungen und Onboarding (insb. MVP- und Beta-Phase)       |
| Datenschutz- und Compliance-Kompetenz | Privacy/Compliance, PO       | Verständnis rechtlicher Rahmenbedingungen (insb. Datenschutz, rechtliche Situation von Blitzer-Apps) und deren Übersetzung in klare Hinweise, UI-Elemente und Dokumentation.                     | AP-B5 (Disclaimer & Datenschutzinfo), AP-R3 (Store-Vorbereitung), AP-E3 (Einstellungen) |

#### 4.4.2.3 Teamübergreifende Aspekte

| Aspekt                            | Beschreibung                                                                                                                                                                                                                              |
|-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Klare "Owner" für zentrale Themen | Bestimmte Themen (z. B. Overpass/OSM, Performanceoptimierung, Datenschutz) sind klaren Ownern im Team zugeordnet, um Verantwortung und Ansprechpartner:innen eindeutig zu machen.                                                         |
| Wissensaustausch & Bus-Faktor     | Rollen sind bewusst breit aufgestellt, sodass Pairing und Wissensaustausch möglich sind und Bus-Faktoren reduziert werden. Dies ist insbesondere bei Querschnittsthemen wie Architektur, Testautomatisierung und Datenschutz essenziell.  |
| Steuerung kritischer Phasen       | In kritischen Phasen (z. B. kurz vor AppStore-Release oder beim Einführen neuer Community-Funktionen) dient die Skill-Matrix als Grundlage, um Prioritäten zu setzen und ggf. Arbeitspakete in spätere Erweiterungszyklen zu verschieben. |
| Risikoorientierte Planung         | Die Skills bestimmen nicht nur, wer welche Aufgaben übernehmen kann, sondern auch, welche Themen aus Risikosicht frühzeitig adressiert werden sollten, um technische, organisatorische und regulatorische Risiken zu minimieren.          |


### 4.4.3 Externe Ressourcen und Tools

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
