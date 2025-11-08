# 10 Umsetzungsstrategie

Dieses Kapitel konkretisiert den Weg von Anforderungen (Kapitel 3) zu einer lauffähigen, nachhaltigen Lösung. Der Fokus
liegt auf einer rein clientseitigen Architektur (kein eigenes Backend), der Nutzung offener Schnittstellen (
OSM/Overpass, optional OSM Notes/Nominatim) sowie Privacy-by-Design. Die drei Kernbereiche: Entwicklungsansatz,
Technologie-Stack, Qualitätsmanagement.

## 10.1 Entwicklungsansatz

### Grundprinzipien

- Client-only: Alle Kernfunktionen (Standort, Warnlogik, Caching, Meldungen) laufen lokal; keine zentrale Speicherung
  von Standortverläufen.
- Privacy-by-Design: Minimierung personenbezogener Daten, keine Tracking-SDKs standardmäßig, transparente Datenquellen.
- Iterativ & Inkrementell: MVP (Karte, Standort, Warnung, Cache) zuerst, dann Geofencing, i18n, Notes,
  Performance-/Energieoptimierung.
- Risiko-getrieben: Frühzeitige Validierung der Top-Risiken (Kapitel 7: Overpass-Stabilität, Performance,
  Energieverbrauch, rechtliche Konformität).
- Clean Architecture / Layered:
    - UI Layer (Views/Widgets)
    - Domain Layer (Use Cases: QueryCameras, ComputeWarnings, ManageGeofences, SubmitNote, Load/SaveCache)
    - Data Layer (Clients + Repositories: OverpassClient, NotesClient, CacheRepo, TileProvider)
    - Platform Services (Location, Geofencing, Permissions, Audio)
- Testbarkeit: Business-Logik (Distanz, Geofence-Registrierung, Parser) isoliert ohne UI-Abhängigkeit.

### Ablauf Phasen (Kurz)

1. Architektur-Feinschnitt & Projekt-Setup (CI, Linter, Basis-Ordnerstruktur)
2. MVP Implementierung (Karte → Standort → Overpass-Abfrage → POI-Overlay → Warnlogik → Cache → Einstellungen)
3. Erweiterung: Geofencing, Mehrsprachigkeit, Accessibility-Basis
4. Community-Funktionen: OSM Notes, Performance-/Energie-Tuning, Offline-Regionen
5. Qualität & Release: Testabdeckung, Beta-Feedback, Store-Compliance
6. Wartung: Fehlerbehebungen, Monitoring (lokal, ohne Tracking), leichte Feature-Erweiterungen

### Entscheidungsrichtlinien

- Einfachheit vor Komplexität: Erst lineares Distanzmodell, später Optimierung (z. B. Richtung, Fahrtrichtungserkennung
  optional).
- Energieeffizienz: Geofencing bevorzugen; Fallback Polling nur foreground und gedrosselt.
- Datenabfragen: Kleine Bounding Boxes um aktuelle Position; inkrementelle Aktualisierung statt full reload.
- Offline-Pragmatismus: Cache für zuletzt genutzte Region; erweiterte Regionpacks erst nach MVP.

### Umgang mit Änderungen

- Anforderungen-Änderung → Impact-Check (Performance, Energie, Datenschutz) → Priorisierung im Backlog.
- Neue externe API-Nutzung → Compliance-/Fair-Use-Prüfung (Ratelimits, Attribution) vor Integration.

## 10.2 Technologie-Stack

(Annahme: Flutter – kann bei Bedarf durch einen alternativen Cross-Plattform-Stack ersetzt werden; Prinzipien bleiben.)

### Kernkomponenten

- Framework: Flutter (Dart) – schnelle UI-Iteration, gute Performance, breite Geräteabdeckung.
- Karte: MapLibre oder flutter_map + konformer Tile-Provider (API-Key, Fair-Use). Attribution eingeblendet.
- Standort & Geofencing: geolocator + plattformspezifische Geofencing-Plugins (Android FusedLocationProvider, iOS Region
  Monitoring).
- Netzwerk: dio oder http mit Timeout, Retry/Backoff (Exponential), eigener User-Agent zur Fair-Use Kennzeichnung.
- Persistenz: Hive (Key-Value für Settings/Cache-Metadaten) + SQLite (drift) für strukturierte POI-Daten und ggf.
  Offline-Regionpacks.
- Auth (optional für OSM Notes): OAuth Flow (nur bei Opt-in; sichere Token-Speicherung Keychain/Keystore).
- Logging: Lokal rotierend (Performance, Fehlercodes) ohne Speicherung von Standortverläufen; Opt-in für Diagnosedaten.
- Internationalisierung: ARB/JSON-String-Dateien (DE/EN); Erweiterbar.
- Accessibility: Nutzung semantischer Widgets, Kontrast-Check im UI-Design.

### Datenflüsse (High-Level)

1. Standort-Update → Berechnung Bounding Box → Overpass Query → Parser → Cache speichern → Kartenoverlay aktualisieren
2. Distanzberechnung (Event-basiert) → Eintritt in Warnradius → HUD/Audio auslösen (Debounce) → Log (nur Ereignistyp,
   keine Koordinaten)
3. OSM Note (optional) → Validierung Eingabe → POST Notes API → Anzeige Bestätigung → Speicherung minimaler Metadaten (
   Note-ID lokal)

### Beispiel Overpass Query (vereinfachte Form)

```
[out:json][timeout:25];
(
  node["highway"="speed_camera"]({{bbox}});
  node["man_made"="speed_camera"]({{bbox}});
  node["enforcement"="maxspeed"]({{bbox}});
);
out tags center;
```

### Sicherheits- & Datenschutzaspekte im Stack

- HTTPS erzwungen (keine Plain HTTP Requests).
- Keine Third-Party Tracking-Libraries; Analytics nur mit ausdrücklichem Opt-in.
- Minimale Speicherung: Warnradius, Audio-Flag, Locale, Caches; keine dauerhafte Liste angefahrener POIs.
- Clear Separation: UI darf keine direkten Netzwerkaufrufe; Data-Layer kontrolliert alle externen Abfragen.

### Skalierbarkeit & Zukunftsfähigkeit

- Erhöhte POI-Dichte → Clustering / selektive Sichtbarkeit.
- Performance-Tuning: Isolierte Isolates (Dart) für Parser bei großen Antwortmengen.
- Austauschbarkeit: Tile-Provider oder Overpass Mirror via Konfig (Konstanten/Env abstrakt).

## 10.3 Qualitätsmanagement

### Ziele (Abgleich mit Kap. 3)

- Startzeit < 2 s (Cold Start)
- Warn-Latenz ≤ 2 s (95. Perzentil)
- Energieverbrauch Hintergrund < 3%/h
- Crashrate < 0.5% in Beta
- Testabdeckung kritischer Logik ≥ 70% Branch Coverage

### Teststrategie

| Testart             | Fokus                     | Beispiele                                            |
|---------------------|---------------------------|------------------------------------------------------|
| Unit-Tests          | Berechnungslogik & Parser | Distanzberechnung, Warn-Debounce, JSON → POI Mapping |
| Widget-Tests        | UI-Zustände               | Warn-Overlay Anzeige, Settings Interaktion           |
| Integrations-Tests  | API + DataFlow            | Overpass Mock Antwort → Cache → UI Aktualisierung    |
| Performance-Tests   | Startzeit, Latenz         | Automatisiertes Profiling Skript / Benchmark Harness |
| Feldtests           | Realgeräte Verhalten      | Energieprofil, GPS-Genauigkeit, Geofence-Auslösung   |
| Accessibility-Tests | Nutzbarkeit               | Screenreader Fokus, Kontrastprüfung                  |

### Metriken & Monitoring (Privacy-freundlich)

- Lokal aggregierte Performance (Startzeit, Query-Latenz, Warn-Latenz) – Anzeige im Diagnose-Bereich (Opt-in).
- Fehlercodes (HTTP Timeout, Rate-Limit) zählen; keine Speicherung von Koordinaten.
- Timestamp des letzten Datenupdates für Transparenz.

### Release-Gates / Abnahmecheck

Vor jedem Meilenstein-Release (vgl. Projektstrukturplan):

1. Build Stabilität: Keine kritischen Fehler/Warnungen.
2. Tests: Kern-Suite grün; Coverage-Bericht erfüllt Mindestschwelle.
3. Performance: Benchmark Skript bestätigt Startzeit/Warn-Latenz.
4. Energie: Feldmessung Hintergrundbetrieb im Zielkorridor.
5. Datenschutz: Code-Scan bestätigt keine Standortübermittlung; Privacy-Text aktuell.
6. Accessibility: Checkliste (Kontrast, Labels) ohne kritische Mängel.

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
