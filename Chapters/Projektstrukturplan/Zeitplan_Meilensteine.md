## 4.2 Zeitplan und Meilensteine

Der Projektablauf wird in Sprints mit einer festen Dauer von zwei Wochen strukturiert. Mehrere Sprints bilden gemeinsam
jeweils eine Phase bzw. ein Release (z. B. MVP, Erweiterung, Qualitäts-/Release-Phase). Der Zeitplan dient als
Orientierung für die Umsetzung der in Abschnitt 4.1 beschriebenen Arbeitspakete und bildet die zeitliche Grundlage für
die Kapazitäts- und Budgetplanung.

### 4.2.1 Übersicht Sprints und Phasen

| Sprint | Phase | Zeitraum (ca.) | Kernaktivitäten                                 | Meilensteine                            |
|--------|-------|----------------|-------------------------------------------------|-----------------------------------------|
| S1     | A     | Woche 1–2      | Anforderungen, Architektur                      | M1: Abgenommene Anforderungen           |
| S2     | B     | Woche 3–4      | MVP Kern (Karte, Standort, Overpass)            |                                         |
| S3     | B     | Woche 5–6      | MVP Kern (Warnlogik, Cache, Settings)           | M2: MVP Feature-Complete                |
| S4     | C     | Woche 7–8      | Geofencing, i18n                                |                                         |
| S5     | C     | Woche 9–10     | Accessibility Basis, Feinschliff                | M3: Hintergrundwarnungen funktionsfähig |
| S6     | D     | Woche 11–12    | OSM Notes Integration                           |                                         |
| S7     | D     | Woche 13–14    | Performance, Offline-Regionen                   | M4: Erweiterung I abgeschlossen         |
| S8     | E     | Woche 15–16    | Tests, Testautomatisierung                      |                                         |
| S9     | E     | Woche 17–18    | Beta, Feedback-Auswertung                       | M5: Beta erfolgreich, Store ready       |
| S10    | E     | Woche 19–20    | Release-Kandidaten & Launch                     | M6: Version 1.0 veröffentlicht          |
| S11    | F     | Woche 21–22    | Wartung, Fehlerbehebungen, Optimierungen        |                                         |
| S12    | F     | Woche 23–24    | Stabilisierung, Optimierungen, Abschluss-Review | M7: Stabilitätsziele erfüllt            |

Die Phasendarstellung dient der Übersicht und ist kein starres Wasserfallmodell; Umfang und Reihenfolge der Inhalte
werden über das Product Backlog fortlaufend priorisiert und bei Bedarf angepasst.

Hinweis: Sprint-Zyklus gemäß Scrum Guide (2020); Werte/Prinzipien vgl. Agile Manifest (siehe Quellenverzeichnis).

### 4.2.2 Sprintverlauf (Gantt, vereinfacht)

```
Sprint: S1 S2 S3 S4 S5 S6 S7 S8 S9 S10 S11 S12
Phase:  A  B  B  C  C  D  D  E  E  E   F   F
A:      ██
B:         ████
C:             ███
D:                  ███
E:                      ███
Rel:                           ██
F:                                ██
```

Legende: Blöcke repräsentieren ungefähre Bearbeitungsdauer pro Phase; Rel = Release-Fenster (S10).

Sprint Reviews und Sprint Retrospektiven stellen wiederkehrende Mikro-Meilensteine dar. Im Review werden die Ergebnisse
jedes Sprints demonstriert und mit Stakeholdern abgeglichen; in der Retrospektive verbessert das Team kontinuierlich
seine Zusammenarbeit und Vorgehensweise.

### 4.2.3 Puffer und Gesamtdauer

Zusätzlich zu den 12 geplanten Sprints (24 Wochen) werden 1–2 weitere Sprints als Puffer eingeplant, um
unvorhergesehene Verzögerungen (Rate-Limit-Probleme, Geräte-Spezifika, Store-Review-Verzögerungen) abzufedern.

Damit ergibt sich eine geschätzte Gesamtdauer von ca. 26–28 Wochen für Entwicklung, Release und erste
Stabilisierungsphase. Umfang und Inhalte einzelner Sprints können bei Bedarf angepasst werden, während der
übergeordnete Endtermin im Blick bleibt.

In Kombination aus Zeitpuffer (zusätzliche Sprints), realistisch angesetzter Auslastung pro Sprint und der Möglichkeit,
den Scope über das Product Backlog anzupassen, ergibt sich ein effektiver Sicherheitspuffer von grob 20 %, ohne die
Qualität zu reduzieren.

### 4.2.4 Meilensteine (Detail)

- M1 (Ende S1): Abgenommene Anforderungen + Architekturentscheid.
- M2 (Ende S3): MVP zeigt Karte, Standort, Blitzer-POIs, Warnung, Cache. Stakeholder-Review (Fahrende/PO),
  Backlog-Update.
- M3 (Ende S5): Hintergrundwarnungen validiert (mind. 1 Plattform), Accessibility-Basis erfüllt. Stakeholder-Review,
  Priorisierung Anpassungen.
- M4 (Ende S7): OSM Notes Meldung möglich, Performance-Ziele (Startzeit, Latenz) erreicht. Review mit Community-Fokus (
  OSM), ggf. Leitlinien verfeinern.
- M5 (Ende S9): Testabdeckung ≥70%, Beta-Feedback eingearbeitet, Store-Assets fertig. Beta-Review,
  Stop/Go/Nachjustierung für Launch.
- M6 (Ende S10): Release 1.0 im Store.
- M7 (Ende S12): Crashrate <0.5%, Energieziel <3%/h bestätigt.
