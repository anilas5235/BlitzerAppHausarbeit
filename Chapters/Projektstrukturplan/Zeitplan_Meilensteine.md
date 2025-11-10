## 4.2 Zeitplan und Meilensteine

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