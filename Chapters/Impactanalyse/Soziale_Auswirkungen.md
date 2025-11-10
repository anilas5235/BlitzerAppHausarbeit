## 7.2 Soziale Auswirkungen

### Positive Effekte

- Erhöhte Einhaltung von Geschwindigkeitsbegrenzungen → potenziell weniger Unfälle und gesteigerte Verkehrssicherheit (
  indirekt, keine Garantie).
- Bewusstsein für lokale Regeln (maxspeed) fördert verantwortungsvolles Fahrverhalten.
- Offene Daten (OSM) stärken Community-Beteiligung: Nutzer verbessern Datenqualität durch Notes.
- Datenschutzfreundliche Umsetzung (kein Tracking) unterstützt gesellschaftliches Vertrauen in digitale Assistenz.
- Barrierefreiheit (Kontraste, Screenreader) ermöglicht inklusiven Zugang für mehr Nutzergruppen.

### Negative / Kritische Aspekte

- Ablenkungsrisiko durch zusätzliche App (Bedienung während Fahrt, falls nicht optimal gestaltet).
- Fehlende oder unvollständige Daten könnten falsches Sicherheitsgefühl vermitteln (User glaubt alle Blitzer seien
  abgedeckt).
- Community-Missbrauch (Spam-Meldungen) kann Moderationsaufwand in OSM erhöhen.
- Rechtliche Grauzonen in Ländern mit restriktiver Gesetzgebung können zu sozialer Kontroverse führen.

### Kennzahlen / Indikatoren

| KPI                                                      | Ziel / Interpretation   | Messansatz                                     |
|----------------------------------------------------------|-------------------------|------------------------------------------------|
| Nutzerfeedback zur Warnklarheit (% positiv)              | >80% Zufriedenheit      | Beta-Umfrage                                   |
| Anzahl fehlerhafter Meldungen (Spam/ungenau)             | Niedrig                 | Manuelle Stichprobe OSM Notes (Opt-in Nutzer)  |
| Accessibility-Abdeckungsgrad (Checklistenpunkte erfüllt) | ≥90%                    | A11y-Review                                    |
| Opt-in Rate für Community Notes                          | Moderat (zeigt Nutzung) | App-intern (lokal gezählt, ohne Profilbildung) |

### Maßnahmen zur Förderung positiver sozialer Effekte

- Einfache, nicht-intrusive Warn-UI (Audio + kurzes visuelles Signal) statt komplexer Interaktionen.
- Klarer Hinweis: „Nicht alle Blitzer garantiert erfasst“ → fördert realistische Erwartung.
- Community-Guidelines für Notes direkt in der Meldemaske.
- Frühe Accessibility-Tests mit Screenreader.

### Maßnahmen zur Reduktion negativer Effekte

- Sperre komplexer Einstellungen während Fahrt (Detection: Geschwindigkeit > X km/h → UI „Lesemodus“).
- Validierung von Meldetexten (Mindestlänge, keine Copy-Spam) + Rate-Limit pro Zeitfenster.
- Dynamische Einblendung von Disclaimer in Regionen mit bekannter Rechtsrestriktion.
