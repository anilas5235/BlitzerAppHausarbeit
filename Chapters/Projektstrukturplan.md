# 5 Projektstrukturplan

Dieses Kapitel beschreibt die strukturierte Zerlegung (Work Breakdown Structure), den Zeitplan mit Meilensteinen sowie
die Ressourcenplanung für die BlitzerApp. Fokus: rein clientseitige Entwicklung ohne eigenes Backend, Nutzung offener
Schnittstellen (Overpass/OSM), Datenschutz by Design.

## 5.1 Arbeitspakete (WBS)

Die Arbeitspakete sind nach Phasen gruppiert. Jede Einheit enthält Ziel, Haupt-Deliverables, Abhängigkeiten und grobe
Aufwandsschätzung (S = ≤2 PT, M = 3–5 PT, L = >5 PT).

### Phase A – Grundlagen & Planung

1. AP-A1: Feinspezifikation Anforderungen
    - Ziel: Detaillierte Verfeinerung aus Kapitel 3; MUSS/SOLL finalisieren.
    - Deliverables: Abgenommene Anforderungsliste, Priorisierung.
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

### Phase B – MVP Kern

4. AP-B1: Kartenintegration & Tile-Provider
    - Ziel: Anzeige Grundkarte + Attribution.
    - Deliverables: MapView, Attribution-Leiste.
    - Abhängigkeiten: AP-A3.
    - Aufwand: M
5. AP-B2: Standortbestimmung (Foreground)
    - Ziel: Live-Position mit Update-Stream.
    - Deliverables: LocationService Modul, Permission-Dialog.
    - Abhängigkeiten: AP-B1.
    - Aufwand: S
6. AP-B3: Overpass-Abfrage + Parser
    - Ziel: Abfrage stationärer Blitzer und maxspeed (optional) für Bounding Box.
    - Deliverables: OverpassClient, QueryBuilder, Parser-Tests.
    - Abhängigkeiten: AP-B2.
    - Aufwand: M
7. AP-B4: POI-Overlay & Cache
    - Ziel: Darstellung gefundener POIs, lokaler Cache (Hive/SQLite).
    - Deliverables: CacheRepository, POI-Modelle, Overlay-Komponenten.
    - Abhängigkeiten: AP-B3.
    - Aufwand: M
8. AP-B5: Warnlogik (Distanzberechnung + HUD + Audio)
    - Ziel: Erste visuelle/akustische Warnung beim Eintritt in konfigurierten Radius.
    - Deliverables: WarningEngine, HUD-Komponente, Basis-Sound.
    - Abhängigkeiten: AP-B4.
    - Aufwand: M
9. AP-B6: Einstellungen (Radius, Ton, Datenschutzhinweis)
    - Ziel: Persistente Konfiguration.
    - Deliverables: SettingsView, SettingsStore, Datenschutzhinweis.
    - Abhängigkeiten: AP-B5.
    - Aufwand: S
10. AP-B7: Offline-Grundfunktion (Letzte Region)
    - Ziel: Anzeige letzter POIs ohne Netz.
    - Deliverables: Cache-Ladepfad, Offline-Hinweis.
    - Abhängigkeiten: AP-B4.
    - Aufwand: S

### Phase C – Erweiterung I

11. AP-C1: Geofencing (Hintergrundwarnungen)
    - Ziel: Energieeffiziente Hintergrundwarnungen.
    - Deliverables: GeofencingService, Testfälle.
    - Abhängigkeiten: AP-B5.
    - Aufwand: L
12. AP-C2: Mehrsprachigkeit (DE/EN)
    - Ziel: i18n Grundlagen.
    - Deliverables: Lokalisierte Strings, Umschaltlogik.
    - Abhängigkeiten: AP-B6.
    - Aufwand: S
13. AP-C3: Accessibility Basis
    - Ziel: Kontraste, Labels, Screenreader-Test.
    - Deliverables: A11y-Checkliste, UI-Anpassungen.
    - Abhängigkeiten: AP-B1–B6.
    - Aufwand: M

### Phase D – Erweiterung II

14. AP-D1: OSM Notes Integration (Meldungen)
    - Ziel: Nutzer kann Note erstellen (anonym/OAuth).
    - Deliverables: NotesClient, Meldedialog, Validierung.
    - Abhängigkeiten: AP-B3, optional AP-C2.
    - Aufwand: M
15. AP-D2: Performance & Energieoptimierung
    - Ziel: Einhaltung Startzeit, Latenz, Akku-Verbrauch.
    - Deliverables: Profiling-Bericht, Optimierungspatches.
    - Abhängigkeiten: AP-C1.
    - Aufwand: M
16. AP-D3: Erweiterte Offline-Cache/Regionen
    - Ziel: Vorkonfiguration zusätzlicher Regionen.
    - Deliverables: Regionpack-Logik, Speichergrößeninfo.
    - Abhängigkeiten: AP-B7.
    - Aufwand: M

### Phase E – Release & Qualität

17. AP-E1: Testautomatisierung Ausbau
    - Ziel: ≥70% Branch Coverage kritische Logik.
    - Deliverables: Test-Suite, Coverage-Bericht.
    - Abhängigkeiten: Kernmodule fertig.
    - Aufwand: M
18. AP-E2: Beta-Test & Feedback-Auswertung
    - Ziel: Stabilitäts-/Usability-Prüfung.
    - Deliverables: Testprotokolle, Anpassungsliste.
    - Abhängigkeiten: MVP + Erweiterungen stabil.
    - Aufwand: M
19. AP-E3: App-Store Vorbereitung (Listing, Compliance)
    - Ziel: Einreichungsbereitschaft.
    - Deliverables: Beschreibung, Screenshots, Datenschutz-Formulare.
    - Abhängigkeiten: AP-E2.
    - Aufwand: S
20. AP-E4: Release-Kandidaten & Final Review
    - Ziel: Freigabe.
    - Deliverables: RC-Builds, Abschlusscheckliste.
    - Abhängigkeiten: AP-E3.
    - Aufwand: S

### Phase F – Nachrelease / Wartung (laufend)

21. AP-F1: Fehlerbehebungen / Patch-Zyklus
    - Ziel: Stabilität, Crashrate < 0.5%.
    - Aufwand: laufend.
22. AP-F2: Monitoring lokale Metriken (Opt-in)
    - Ziel: Verbesserungsdaten ohne Tracking.
    - Aufwand: S (Initial) + laufend.
23. AP-F3: Community-Feedback OSM Notes
    - Ziel: Prüfung Note-Qualität, ggf. Guideline-Anpassungen.
    - Aufwand: laufend.

## 5.2 Zeitplan und Meilensteine

Grober Zeitrahmen (Beispielhaft für ~24 Wochen Gesamtentwicklung). Wochenzahlen können an Ressourcen angepasst werden.

| Zeitraum (KW) | Phase | Kernaktivitäten                          | Meilensteine                            |
|---------------|-------|------------------------------------------|-----------------------------------------|
| 1–2           | A     | Anforderungen, Architektur               | M1: Abgenommene Anforderungen           |
| 3–6           | B     | MVP Kern AP-B1–B6 + Offline              | M2: MVP Feature-Complete                |
| 7–9           | C     | Geofencing, i18n, Accessibility          | M3: Hintergrundwarnungen funktionsfähig |
| 10–13         | D     | OSM Notes, Performance, Offline-Regionen | M4: Erweiterung I abgeschlossen         |
| 14–18         | E     | Tests, Beta, Store-Vorbereitung          | M5: Beta erfolgreich, Store ready       |
| 19–20         | E     | Release-Kandidaten & Launch              | M6: Version 1.0 veröffentlicht          |
| 21–24         | F     | Wartung, Optimierungen                   | M7: Stabilitätsziele erfüllt            |

Puffer: 2–3 Wochen gesamt für unvorhergesehene Verzögerungen (Rate-Limit-Probleme, Geräte-Spezifika).

ASCII-Gantt (vereinfacht):

```
KW:  1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
A:   █████
B:         ██████████
C:                   ███
D:                      █████
E:                             ██████████
Rel:                                       ██
F:                                             ██████████
```

Legende: Blöcke repräsentieren ungefähre Bearbeitungsdauer; Rel = Release-Fenster.

Meilensteine (Detail):

- M1 (Ende Phase A): Abgenommene Anforderungen + Architekturentscheid.
- M2 (Ende KW6): MVP zeigt Karte, Standort, Blitzer-POIs, Warnung, Cache.
- M3 (Ende KW9): Hintergrundwarnungen validiert (mind. 1 Plattform), Accessibility-Basis erfüllt.
- M4 (Ende KW13): OSM Notes Meldung möglich, Performance-Ziele (Startzeit, Latenz) erreicht.
- M5 (Ende KW18): Testabdeckung ≥70%, Beta-Feedback eingearbeitet, Store-Assets fertig.
- M6 (KW20): Release 1.0 im Store.
- M7 (Ende KW24): Crashrate <0.5%, Energieziel <3%/h bestätigt.

## 5.3 Ressourcenplanung

Rollen & grobe Kapazitäten (Annahme kleines Kernteam):

- Product Owner (0.4 FTE): Priorisierung, Store-Vorbereitung, Kommunikation.
- Mobile Entwickler:
    - Dev1 (Flutter Lead) (1.0 FTE)
    - Dev2 (Flutter/Testing) (0.8 FTE ab Phase B)
- UX/Design (0.3 FTE): UI, Accessibility, Onboarding.
- QA/Tester (0.5 FTE ab Phase C): Testplanung, Beta-Begleitung.
- Privacy/Compliance Beratung (0.1 FTE ad hoc): Prüfung Datenschutztexte, rechtliche Hinweise.
- Community Liaison (evtl. Product kombiniert) (0.1 FTE): OSM Notes Guidelines, Feedbackkanäle.

Skill-Matrix (Kernthemen):

- Geodaten/Overpass: Dev1
- Performance/Energieprofiling: Dev2 + QA
- Accessibility: UX + QA
- OAuth/OSM Notes: Dev2
- Architektur/Build/CI: Dev1

Auslastungsüberblick vs. Phasen (qualitativ):

- Phase A: PO, Dev1, UX (gering), Privacy.
- Phase B: Dev1 hoch, Dev2 mittel, UX startet UI-Feinschliff.
- Phase C/D: Dev1+Dev2 hoch, QA steigt ein, UX für Accessibility/i18n.
- Phase E: QA hoch (Tests/Beta), PO für Store, Devs Performance & Stabilität.
- Phase F: Devs Wartung, QA Monitoring leicht, PO Feedback.

Externe Ressourcen / Tools:

- Tile-Provider API-Key (Kostenmodell prüfen; Low-Usage Plan).
- Geräte/Testumgebung: Mind. 2 Android Varianten (Mid/Low), 2 iOS Generationen.
- Profiling Tools: Android Profiler, Xcode Instruments.

Risikofaktoren Ressourcen:

- Engpass Geofencing-Spezialwissen → frühzeitige Spike in Phase B.
- Verzögerung durch Performance-Probleme → gezieltes Profiling in AP-D2 statt zu spät.
- i18n/A11y unterschätzt → separate kleine Meilensteine (C2/C3) statt „am Ende“.

Strategie für Skalierung (falls mehr Nutzer/Feature-Wünsche):

- Add-On weiterer Dev für Feature-Phase D/E.
- Separater Support/Community-Manager bei steigendem Meldungsvolumen.

## Zusammenfassung

Der Projektstrukturplan zerlegt das Vorhaben in klar priorisierte Arbeitspakete und bringt einen realistischen Zeitplan
mit definierten Meilensteinen und Ressourcenzuordnung. Schlüsselelemente (Warnlogik, Datenschutz, Geofencing,
Performance) erhalten eigene Pakete und frühzeitige Validierung, um technische und regulatorische Risiken zu minimieren.
