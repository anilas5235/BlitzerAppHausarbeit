# Produktplan & Zeitplan

Dieses Kapitel beschreibt die strukturierte Zerlegung (Work Breakdown Structure), den Zeitplan mit Meilensteinen sowie
die Ressourcenplanung für die BlitzerApp. Fokus: rein clientseitige Entwicklung ohne eigenes Backend, Nutzung offener
Schnittstellen (Overpass/OSM), Privacy-by-Design. Die nachfolgenden Strukturen bilden die Grundlage für die weitere
Kapazitäts- und Kostenplanung.

Im Sinne eines agilen Vorgehens nach Scrum werden die Arbeitspakete nicht als starre, vollständig vorab geplante
Einheiten verstanden, sondern als Grundlage für ein Product Backlog. Die Umsetzung erfolgt iterativ in Sprints, in
denen jeweils ein potenziell auslieferbares Inkrement entsteht.

Hinweis: Vorgehen gemäß Scrum-Grundlagen; vgl. Scrum Guide (2020) und Agile Manifest (siehe Quellenverzeichnis).

## 4.1 Arbeitspakete (WBS)

Die Arbeitspakete beschreiben die fachlichen und technischen Bausteine, die als Epics im Product Backlog geführt und
über mehrere Sprints hinweg umgesetzt werden. Sie sind nach Phasen gruppiert, die jeweils einen sinnvollen
Release- bzw. Ergebniszuschnitt darstellen.

### 4.1.1 Grundlagen & MVP

#### Phase A – Grundlagen & Planung

1. AP-A1: Feinspezifikation Anforderungen
    - Ziel: Detaillierte Verfeinerung aus Kapitel 3; MUSS/SOLL finalisieren.
    - Deliverables: Abgenommene Anforderungsliste, Priorisierung.
    - User Value: Als Product Owner möchte ich eine klare, priorisierte Anforderungsliste haben, damit das Team Sprints zielgerichtet planen kann.
    - Abhängigkeiten: Kapitel 3 fertig.
    - Aufwand: M
2. AP-A2: Architektur-Validierung (Client-only)
    - Ziel: Bestätigung Layer-Modell, Auswahl Flutter vs. Alternative.
    - Deliverables: Architektur-Diagramm, Technologieentscheidung, Risiko-Check.
    - Abhängigkeiten: AP-A1.
    - Aufwand: M
3. AP-A3: Setup Entwicklungsumgebung & Projektgerüst
    - Ziel: Repo-Struktur, CI-Basis, Linter, erste Build-Konfiguration.
    - Deliverables: Grundgerüst, README, CI-Status „grün“.
    - Abhängigkeiten: AP-A2.
    - Aufwand: S

#### Phase B – MVP Kern

Hinweis: Phase B stellt den MVP-Scope dar, der in einem ersten Release ausgeliefert werden kann. Die Elemente AP-B1 bis
AP-B6 sind Must-have für den MVP; AP-B7 ist Nice-to-have (kann bei Bedarf nach hinten priorisiert werden).

1. AP-B1: Kartenintegration & Tile-Provider
    - Ziel: Anzeige Grundkarte + Attribution.
    - Deliverables: MapView, Attribution-Leiste.
    - User Value: Als Fahrer:in möchte ich eine übersichtliche Karte sehen, damit ich meine aktuelle Umgebung und relevante Blitzer besser einordnen kann.
    - Abhängigkeiten: AP-A3.
    - Aufwand: M
2. AP-B2: Standortbestimmung (Foreground)
    - Ziel: Live-Position mit Update-Stream.
    - Deliverables: LocationService Modul, Permission-Dialog.
    - Abhängigkeiten: AP-B1.
    - Aufwand: S
3. AP-B3: Overpass-Abfrage + Parser
    - Ziel: Abfrage stationärer Blitzer und maxspeed (optional) für Bounding Box.
    - Deliverables: OverpassClient, QueryBuilder, Parser-Tests.
    - User Value: Als Fahrer:in möchte ich, dass Blitzerstandorte zuverlässig geladen werden, damit ich mich auf die Warnungen der App verlassen kann.
    - Abhängigkeiten: AP-B2.
    - Aufwand: M
4. AP-B4: POI-Overlay & Cache
    - Ziel: Darstellung gefundener POIs, lokaler Cache (Hive/SQLite).
    - Deliverables: CacheRepository, POI-Modelle, Overlay-Komponenten.
    - Abhängigkeiten: AP-B3.
    - Aufwand: M
5. AP-B5: Warnlogik (Distanzberechnung + HUD + Audio)
    - Ziel: Erste visuelle/akustische Warnung beim Eintritt in konfigurierten Radius.
    - Deliverables: WarningEngine, HUD-Komponente, Basis-Sound.
    - User Value: Als Fahrer:in möchte ich frühzeitig und klar erkennbar vor Blitzern gewarnt werden, damit ich mein Fahrverhalten rechtzeitig anpassen kann.
    - Abhängigkeiten: AP-B4.
    - Aufwand: M
6. AP-B6: Geofencing (Hintergrundwarnungen)
   - Ziel: Energieeffiziente Hintergrundwarnungen.
   - Deliverables: GeofencingService, Testfälle.
   - Besonderheit: Enthält initial einen Spike zur Evaluierung der Plattform-Geofencing-Möglichkeiten, um technische Risiken frühzeitig zu reduzieren.
   - User Value: Als Fahrer:in möchte ich auch bei gesperrtem Bildschirm rechtzeitig und energieeffizient gewarnt werden, damit ich mich auf die Fahrt konzentrieren kann.
   - Abhängigkeiten: AP-B5.
   - Aufwand: L

### 4.1.2 Erweiterungen

#### Phase C – Erweiterung I

1. AP-C1: Einstellungen (Radius, Ton, Datenschutzhinweis)
   - Ziel: Persistente Konfiguration.
   - Deliverables: SettingsView, SettingsStore, Datenschutzhinweis.
   - Abhängigkeiten: AP-B5.
   - Aufwand: S
2. AP-C2: Offline-Grundfunktion (Letzte Region)
   - Ziel: Anzeige letzter POIs ohne Netz.
   - Deliverables: Cache-Ladepfad, Offline-Hinweis.
   - Abhängigkeiten: AP-B4.
   - Aufwand: S
3. AP-C3: Mehrsprachigkeit (DE/EN)
    - Ziel: i18n Grundlagen.
    - Deliverables: Lokalisierte Strings, Umschaltlogik.
    - Abhängigkeiten: AP-B6.
    - Aufwand: S
4. AP-C4: Accessibility Basis
    - Ziel: Kontraste, Labels, Screenreader-Test.
    - Deliverables: A11y-Checkliste, UI-Anpassungen.
    - User Value: Als Nutzer:in mit Assistive-Technologien möchte ich die App barrierearm bedienen können, damit Warnungen zuverlässig zugänglich sind.
    - Abhängigkeiten: AP-B1–B6.
    - Aufwand: M

#### Phase D – Erweiterung II

1. AP-D1: OSM Notes Integration (Meldungen)
    - Ziel: Nutzer kann Note erstellen (anonym/OAuth).
    - Deliverables: NotesClient, Meldedialog, Validierung.
    - User Value: Als Nutzer:in möchte ich Probleme und fehlende Blitzer anonym melden können, damit die Datenqualität gemeinsam verbessert wird.
    - Abhängigkeiten: AP-B3, optional AP-C2.
    - Aufwand: M
2. AP-D2: Performance & Energieoptimierung
    - Ziel: Einhaltung Startzeit, Latenz, Akku-Verbrauch.
    - Deliverables: Profiling-Bericht, Optimierungspatches.
    - Besonderheit: Enthält gezieltes Performance-Profiling als Spike, um potenziell teure Nacharbeiten spät im Projekt zu vermeiden.
    - Abhängigkeiten: AP-C1.
    - Aufwand: M
3. AP-D3: Erweiterte Offline-Cache/Regionen
    - Ziel: Vorkonfiguration zusätzlicher Regionen.
    - Deliverables: Regionpack-Logik, Speichergrößeninfo.
    - Abhängigkeiten: AP-B7.
    - Aufwand: M

### 4.1.3 Release & Betrieb

#### Phase E – Release & Qualität

1. AP-E1: Testautomatisierung Ausbau
    - Ziel: ≥70% Branch Coverage kritische Logik.
    - Deliverables: Test-Suite, Coverage-Bericht.
    - Abhängigkeiten: Kernmodule fertig.
    - Aufwand: M
2. AP-E2: Beta-Test & Feedback-Auswertung
    - Ziel: Stabilitäts-/Usability-Prüfung.
    - Deliverables: Testprotokolle, Anpassungsliste.
    - Abhängigkeiten: MVP + Erweiterungen stabil.
    - Aufwand: M
3. AP-E3: App-Store Vorbereitung (Listing, Compliance)
    - Ziel: Einreichungsbereitschaft.
    - Deliverables: Beschreibung, Screenshots, Datenschutz-Formulare.
    - Abhängigkeiten: AP-E2.
    - Aufwand: S
4. AP-E4: Release-Kandidaten & Final Review
    - Ziel: Freigabe.
    - Deliverables: RC-Builds, Abschlusscheckliste.
    - Abhängigkeiten: AP-E3.
    - Aufwand: S

#### Phase F – Nachrelease / Wartung (laufend)

1. AP-F1: Fehlerbehebungen / Patch-Zyklus
    - Ziel: Stabilität, Crashrate < 0.5%.
    - Aufwand: laufend.
2. AP-F2: Monitoring lokale Metriken (Opt-in)
    - Ziel: Verbesserungsdaten ohne Tracking.
    - Aufwand: S (Initial) + laufend.
3. AP-F3: Community-Feedback OSM Notes
    - Ziel: Prüfung Note-Qualität, ggf. Guideline-Anpassungen.
    - Aufwand: laufend.