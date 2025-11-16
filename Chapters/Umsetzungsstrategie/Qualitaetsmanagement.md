## 9.3 Qualitätsmanagement

### Ziele (Abgleich mit Kap. 3)

- Startzeit < 2 s (Cold Start)
- Warn-Latenz ≤ 2 s (95. Perzentil)
- Energieverbrauch Hintergrund < 3%/h
- Crashrate < 0.5% in Beta
- Testabdeckung kritischer Logik ≥ 70% Branch Coverage

Das Qualitätsmanagement ist in den Scrum-Zyklus eingebettet: Tests, Reviews und Retrospektiven finden sprintweise statt
und die Definition of Done (vgl. Kapitel 4.1) stellt sicher, dass jedes Inkrement tatsächlich release-fähig ist.

### Teststrategie

| Testart             | Fokus                     | Beispiele                                            |
|---------------------|---------------------------|------------------------------------------------------|
| Unit-Tests          | Berechnungslogik & Parser | Distanzberechnung, Warn-Debounce, JSON → POI Mapping |
| Widget-Tests        | UI-Zustände               | Warn-Overlay Anzeige, Settings Interaktion           |
| Integrations-Tests  | API + DataFlow            | Overpass Mock Antwort → Cache → UI Aktualisierung    |
| Performance-Tests   | Startzeit, Latenz         | Automatisiertes Profiling Skript / Benchmark Harness |
| Feldtests           | Realgeräte Verhalten      | Energieprofil, GPS-Genauigkeit, Geofence-Auslösung   |
| Accessibility-Tests | Nutzbarkeit               | Screenreader Fokus, Kontrastprüfung                  |

Automatisierte Tests sind Teil der Definition of Done und werden in der CI/CD-Pipeline bei jedem Merge ausgeführt.

### Metriken & Monitoring (Privacy-freundlich)

- Lokal aggregierte Performance (Startzeit, Query-Latenz, Warn-Latenz) – Anzeige im Diagnose-Bereich (Opt-in).
- Fehlercodes (HTTP Timeout, Rate-Limit) zählen; keine Speicherung von Koordinaten.
- Timestamp des letzten Datenupdates für Transparenz.

### Release-Gates / Abnahmecheck

Vor jedem Meilenstein-Release (vgl. Projektstrukturplan):

1. Build Stabilität: Keine kritischen Fehler/Warnungen.
2. CI/CD-Pipeline: Build, Lint und Tests (Unit/Widget/Integration) grün.
3. Tests: Kern-Suite grün; Coverage-Bericht erfüllt Mindestschwelle.
4. Performance: Benchmark Skript bestätigt Startzeit/Warn-Latenz.
5. Energie: Feldmessung Hintergrundbetrieb im Zielkorridor.
6. Datenschutz: Code-Scan bestätigt keine Standortübermittlung; Privacy-Text aktuell.
7. Accessibility: Checkliste (Kontrast, Labels) ohne kritische Mängel.
8. DoD erfüllt: Definition of Done gemäß Kapitel 4.1 eingehalten (inkl. Dokumentationsupdate und Review durch PO).

### Fehler- & Incident-Handling

- Klassifizierung: P1 (Crash/Sicherheitsrelevant), P2 (Funktionsbeeinträchtigung), P3 (Kosmetisch).
- Reaktionszeiten: P1 Hotfix (≤72h), P2 nächste Minor-Version, P3 Backlog.
- Logging minimal: Fehlerklasse, Zeit, Modul; keine exakten GPS-Daten.

### Technische Schulden & Wartung

- Regelmäßiges Dependency Audit (monatlich) → Aktualisierung minor/patch, Major-Versionen mit Migrationsplan.
- Review von Performance-Hotspots nach jeder größeren Feature-Erweiterung.
- Dokumentation: Architektur-Übersicht, Datenflüsse, Sicherheits-/Privacy-Konzept im Repo (README + /docs).

### Kontinuierliche Verbesserung

- Beta-Feedback Kanban → Priorisierung nach Impact (Performance/Privacy > Komfortfeatures).
- KPI-Drift (Startzeit, Energie) → automatisierter Hinweis im Diagnosepanel (Opt-in) → Task-Erstellung.
- Sprint Reviews liefern strukturiertes Stakeholder-Feedback; Aktionen daraus und aus der Sprint Retrospektive werden als
  Backlog-Items erfasst, priorisiert und in kommenden Sprints umgesetzt.

### Risiken im Qualitätsmanagement (Auszug) & Mitigation

| Risiko                               | Auswirkung              | Mitigation                                               |
|--------------------------------------|-------------------------|----------------------------------------------------------|
| Unzureichende Testabdeckung          | Regressionen            | Tests für neue Use Cases verpflichtend vor Merge         |
| Parser-Änderungen OSM                | Datenfehler             | Versionierte Parser, Fallback auf letzte stabile Version |
| Geofence Inkonsistenzen              | Fehlwarnungen / Energie | Vergleich Foreground vs. Geofence Events in Feldtests    |
| Später Performance-Fokus             | Teure Refaktoren        | Früh Benchmark-Harness im MVP                            |
| Fehlende Transparenz Datenaktualität | Fehlinterpretation      | UI Timestamp + „Datenstand“ Hinweis                      |

### Zusammenfassung Qualitätsmanagement

Ein schlanker, testbarer Architekturansatz mit klaren Metriken und Release-Gates reduziert technische Risiken und wahrt
Datenschutz-/Leistungsziele. Lokales, optionales Monitoring ersetzt zentrales Tracking. So bleiben Wartbarkeit und
Vertrauenswürdigkeit langfristig hoch.

---

Kurzfazit: Die Umsetzungsstrategie verbindet eine modulare Client-Architektur mit einem klaren Qualitätsrahmen. Sie
nutzt offene Standards, priorisiert Datenschutz und Energieeffizienz und erlaubt kontrollierte Erweiterungen (z. B. OSM
Notes, Offline-Regionen), ohne ein komplexes Backend einzuführen.
