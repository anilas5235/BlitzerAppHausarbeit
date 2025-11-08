# 8 Impactanalyse

Dieses Kapitel bewertet die Auswirkungen der BlitzerApp auf ökologische, soziale und wirtschaftliche Dimensionen.
Grundlage sind die Architektur (rein clientseitig, keine eigene Server-Infrastruktur), Privacy-by-Design und die
Zielsetzung, Geschwindigkeitsbegrenzungen einzuhalten, ohne neue Risiken (Ablenkung, Datenschutzverletzungen) zu
schaffen.

## 8.1 Ökologische Auswirkungen

### Positive Effekte

- Reduzierte Geschwindigkeitsüberschreitungen können den Kraftstoffverbrauch senken (effizientere Fahrweise → geringerer
  CO₂-Ausstoß).
- Konstantere Geschwindigkeit (frühzeitige Warnung statt abruptes Abbremsen) verringert unnötige
  Beschleunigungs-/Bremsvorgänge.
- Keine eigene Server-Infrastruktur → niedriger zusätzlicher Energiebedarf; Auslagerung auf bereits existierende offene
  Dienste (Overpass/OSM) minimiert ökologischen Fußabdruck.
- Lokales Caching reduziert wiederholte Netzaufrufe → weniger Datentransfer, indirekt geringere Rechenzentrumsbelastung.

### Negative / Neutrale Effekte

- Zusätzliche App-Nutzung erhöht marginal den Energieverbrauch des Endgeräts (GPS, Geofencing, Rendering).
- Falls Nutzer häufiger auf das Display schauen → potenziell leichte Ablenkung, indirekt ineffiziente Fahrmanöver.
- Nutzung externer Tile- und Overpass-Server verursacht dennoch Netzwerktraffic (wenn auch begrenzt durch Caching).

### Kennzahlen / Indikatoren

| KPI                                             | Ziel / Interpretation          | Messansatz                                      |
|-------------------------------------------------|--------------------------------|-------------------------------------------------|
| Durchschnittliche Geschwindigkeit vs. Limit     | Höhere Limit-Einhaltungsquote  | Optionale lokal aggregierte Statistik (Opt-in)  |
| Anzahl abrupten Geschwindigkeitswechsel (Proxy) | Reduktion gegenüber Basislinie | Lokale Heuristik (Differenz >X km/h in <Y s)    |
| Energieverbrauch der App (% Akku/h)             | <3%/h Hintergrundwarnung       | Geräteprofiling in Feldtests                    |
| Netzwerkvolumen pro aktive Stunde               | Niedrig durch Cache            | Log der übertragenen Bytes (ohne Standortdaten) |

### Maßnahmen zur Maximierung positiver Effekte

- Effiziente Distanzberechnung (Throttling) zur Minimierung Akkuverbrauch.
- UI-Design: klare Warnungen, reduzierter Interaktionsbedarf während Fahrt (Audio bevorzugt vor ständigen Blicken).
- Deutliche Einstellung zur Aktivierung energiesparender Modi (z. B. „Hintergrund sparsam“).
- Transparenz über Datenaktualität → verhindert unnötige wiederholte Updates.

### Maßnahmen zur Minimierung negativer Effekte

- Energiemonitoring lokal (Opt-in) mit Hinweis bei überdurchschnittlichem Verbrauch.
- Sanfte Warnfrequenz (kein „Spam“ bei Nähe mehrerer POIs) → weniger Displayaktivierungen.
- Bounding Box dynamisch begrenzen (nur relevante Umgebung) → weniger Netztraffic.

## 8.2 Soziale Auswirkungen

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

## 8.3 Wirtschaftliche Auswirkungen

### Positive Effekte

- Potenzielle Kosteneinsparungen für Nutzer*innen durch Vermeidung von Bußgeldern (Geschwindigkeitsüberschreitungen).
- Geringe Betriebskosten (kein eigenes Backend) → niedrigere Eintrittsbarriere für langfristige Wartung.
- Nutzung offener Daten reduziert Lizenzkosten und erhöht Flexibilität.
- Verbesserte Datenqualität (Community Feedback) steigert langfristig Nutzen → kann Nutzerbindung fördern.
- Möglichkeit freier / günstiger Basisversion steigert Adoption (Skalierung über positive Mundpropaganda).

### Negative / Kritische Aspekte

- Geringe Monetarisierung kann nachhaltige Pflege gefährden (Feature-Stagnation, Qualitätsabfall).
- Abhängigkeit von externen Open-Source-Komponenten (Risiko für zukünftige Migrationskosten bei Obsoleszenz).
- Potenzieller Konflikt mit Einnahmeinteressen lokaler Behörden (Bußgelder sinken) → indirekter politischer Widerstand (
  gering bis moderat).
- Unkalkulierbare langfristige Pflegekosten bei starkem Nutzerwachstum (Support, Gerätevielfalt).

### Kennzahlen / Indikatoren

| KPI                                                    | Ziel / Interpretation   | Messansatz                                             |
|--------------------------------------------------------|-------------------------|--------------------------------------------------------|
| Durchschnittliche Kosten pro aktiver Nutzer (jährlich) | Niedrig                 | Aufteilung geplante Kosten / aktive Nutzer (Schätzung) |
| Freemium → Paid/Spenden Conversion (%)                 | Stabiler Anteil (≥2%)   | Interne Auswertung Einnahmen (anonym aggregiert)       |
| Pflegeaufwand (PT/Quartal)                             | Prognose ±15%           | Zeittracking intern                                    |
| Abhängigkeit kritischer Libraries (# kritische Libs)   | ≤ definiertem Grenzwert | Audit Paketliste                                       |

### Maßnahmen zur Maximierung positiver wirtschaftlicher Effekte

- Früh transparente Kostenkommunikation → fördert Spenden/Abo-Bereitschaft.
- Modularer Code reduziert Migrationskosten bei Library-Wechsel.
- Automatisierte Tests minimieren Aufwand für Regressionen.
- Fokus auf stabile Kernfeatures statt kostenintensiver Nischenfunktionen.

### Maßnahmen zur Minimierung negativer Effekte

- Regelmäßige Dependency-Audits und Versions-Strategie (SemVer Monitoring).
- Diversifikation Einnahmequellen (Freemium + Spenden + Fördermittel) zur Risikoabsicherung.
- Lean-Backlog Pflege: Abbruch wenig genutzter Features, Priorisierung Wartbarkeit.
- Frühzeitiger Performance-/Energie-Optimierungszyklus, um spätere teure Refaktorierungen zu vermeiden.

## Zusammenfassung

Die Impactanalyse zeigt, dass der clientseitige, datenschutzorientierte Ansatz ökologische und soziale Vorteile bietet (
reduzierter Infrastruktur-Footprint, potenzielle Sicherheitssteigerung, hohe Transparenz). Ökonomisch wird durch geringe
Betriebskosten und offene Daten eine tragfähige Basis geschaffen, deren Nachhaltigkeit von angemessener Monetarisierung
und Qualitätsstrategie abhängt. Negativpotenziale (Ablenkung, Datenlücken, Energieverbrauch) lassen sich durch
UI/UX-Maßnahmen, technische Optimierungen und klare Kommunikation mitigieren. Kontinuierliches Monitoring der
definierten KPIs ermöglicht iterative Verbesserungen ohne Aufgabe der Privacy-Prinzipien.
