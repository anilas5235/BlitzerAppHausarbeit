# 9 Umsetzungsstrategie

Dieses Kapitel konkretisiert den Weg von Anforderungen (Kapitel 3) zu einer lauffähigen, nachhaltigen Lösung. Der Fokus
liegt auf einer rein clientseitigen Architektur (kein eigenes Backend), der Nutzung offener Schnittstellen (
OSM/Overpass, optional OSM Notes/Nominatim) sowie Privacy-by-Design. Die drei Kernbereiche: Entwicklungsansatz,
Technologie-Stack, Qualitätsmanagement.

## 9.1 Entwicklungsansatz

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

Zusätzlich stützt sich der Entwicklungsansatz auf ein Scrum-inspiriertes Vorgehen mit kurzen Iterationen und einem
stabilen, cross-funktionalen Team:

- Das zentrale Planungsartefakt ist ein priorisiertes Product Backlog, das fachliche Anforderungen, technische
  Verbesserungen und Wartungsaufgaben bündelt (vgl. Projektstrukturplan in Kapitel 4).
- In festen Sprints (zwei Wochen) plant das Scrum-Team im Sprint Planning, welche Backlog-Einträge zum nächsten
  Inkrement verarbeitet werden. Die detaillierte Zerlegung in Tasks und die Aufwandsschätzung (z. B. Planning Poker)
  erfolgen dabei durch das Team selbst und werden im Rahmen dieser Arbeit bewusst nicht im Detail vorweggenommen.
- Am Ende jedes Sprints steht ein potenziell auslieferbares Inkrement, das im Sprint Review demonstriert wird. Feedback
  von Stakeholdern fließt direkt in die Priorisierung des Backlogs ein.
- In der anschließenden Sprint Retrospektive reflektiert das Team die Zusammenarbeit und die Prozessqualität und leitet
  konkrete Verbesserungen für den nächsten Sprint ab.

Hinweis: Das Vorgehen orientiert sich am offiziellen Scrum Guide (Version 2020) sowie den Werten und Prinzipien des
Agile Manifests (siehe Quellenverzeichnis).

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
