## 7.3 Wirtschaftliche Auswirkungen

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
