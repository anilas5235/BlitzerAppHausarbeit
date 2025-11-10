# 5 Finanzplanung

Dieses Kapitel schätzt die zu erwartenden Kosten, beschreibt Mechanismen zur Kostenkontrolle und skizziert mögliche
Finanzierungsquellen für die BlitzerApp. Fokus: Client-only Architektur (kein eigenes Backend), Nutzung offener
Schnittstellen (Overpass/OSM), Datenschutz als Wertversprechen.

## 5.1 Budgetierung

Die Budgetierung erfolgt auf Basis von Personenaufwand (Personentage, PT), Sachkosten (Tools, Geräte, Dienste) und einem
Risiko-/Reserveposten. Beispielhafte Annahmen (können angepasst werden):

- interner Tagessatz Entwicklung: 600 € / PT
- UX/Design: 550 € / PT
- QA/Testing: 500 € / PT
- Beratung (Privacy/Compliance): 800 € / PT (punktuell)

### 5.1.1 Personenaufwand (Phasen kumuliert, aus Kapitel 5 abgeleitet)

| Phase                          | Geschätzte PT Dev | PT UX | PT QA | PT Beratung | Summe PT | Kosten (€)                                                             |
|--------------------------------|-------------------|-------|-------|-------------|----------|------------------------------------------------------------------------|
| A (Anforderungen/Architektur)  | 8                 | 2     | 0     | 2           | 12       | 8*600 + 2*550 + 2*800 = 4.800 + 1.100 + 1.600 = 7.500                  |
| B (MVP Kern)                   | 30                | 6     | 4     | 0           | 40       | 30*600 + 6*550 + 4*500 = 18.000 + 3.300 + 2.000 = 23.300               |
| C (Erweiterung I)              | 18                | 4     | 6     | 1           | 29       | 18*600 + 4*550 + 6*500 + 1*800 = 10.800 + 2.200 + 3.000 + 800 = 16.800 |
| D (Erweiterung II)             | 20                | 3     | 6     | 1           | 30       | 12.000 + 1.650 + 3.000 + 800 = 17.450                                  |
| E (Release & Qualität)         | 14                | 2     | 12    | 1           | 29       | 8.400 + 1.100 + 6.000 + 800 = 16.300                                   |
| F (Nachrelease erste 4 Wochen) | 8                 | 1     | 4     | 0           | 13       | 4.800 + 550 + 2.000 = 7.350                                            |
| Gesamtsumme                    | 98                | 18    | 32    | 5           | 153      | ≈ 87.700 €                                                             |

Hinweis: Rundungsdifferenzen möglich; Reserven siehe unten.

### 5.1.2 Sachkosten / Dienste

| Kostenquelle                  | Annahme                         | Kostenschätzung (€/Jahr) | Kommentar                                |
|-------------------------------|---------------------------------|--------------------------|------------------------------------------|
| Tile-Provider API             | Low-Usage Developer Plan        | 300–600                  | Nach Verbrauch, Caching reduziert Abrufe |
| Testgeräte (Neuanschaffung)   | 2 Android (Mid/Low) + 1 iPhone  | 1.800–2.200 einmalig     | Nutzungsdauer >1 Jahr                    |
| Design-/Prototyping Tools     | Figma (Team), o. ä.             | 150–300                  | Kann entfallen bei Einzelaccount         |
| CI (Cloud Build)              | Open Source Rabatt / Basic Plan | 0–600                    | Abhängig von Provider & Minuten          |
| Monitoring lokal (Libs)       | Open Source                     | 0                        | Kein externes Tracking                   |
| OAuth App Registrierung (OSM) | Kostenlos                       | 0                        | Verwaltungsaufwand intern                |
| Sonstige Lizenzen             | Keine proprietären SDKs geplant | 0                        | Open Source Stack                        |

### 5.1.3 Reserve / Risikopuffer

- Unerwartete Verzögerungen (Performance, Geofencing, Store-Review): +10% Personenbudget ≈ 8.700 €.
- Wechsel Tile-Provider (falls Limits erreicht): zusätzliche 300–500 €.
- Rechtliche Beratung bei Länderrestriktionen: +1.500 € (Kontingent).

Geschätztes Gesamtbudget inkl. Puffer: ca. 100.000 € (Bandbreite 95k–105k) bis Release + erste Stabilisierung.

### 5.1.4 Kostentreiber & Einsparpotenziale

- Kostentreiber: Geofencing-Optimierung, Performance-Tuning, QA für Stabilität & Energieverbrauch.
- Einsparung: Verzicht auf eigenes Backend → keine Server-/Ops-Kosten; konsequentes Caching → niedrigere Tile-Kosten;
  modulare Architektur → schnellere Iterationen.