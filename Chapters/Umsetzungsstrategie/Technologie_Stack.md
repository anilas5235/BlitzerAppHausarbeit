## 9.2 Technologie-Stack

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
