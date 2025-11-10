## 5.3 Finanzierungsquellen

Zweck: Deckung initialer Entwicklungskosten, nachhaltige Pflege ohne Aufgabe des Datenschutz-Versprechens.

### 5.3.1 Primäre Quellen

- Eigenmittel / internes Budget: Volle Kontrolle, schnell; limitiert Skalierung.
- Förderprogramme (Digitalisierung, Open Data, Verkehrssicherheit): Antrag mit Fokus Datenschutz & Gemeinwohl.
- Kooperation mit Verkehrssicherheitsorganisationen (Verbände, Initiativen): Sachmittel (Geräte) oder Zuschuss.

### 5.3.2 Sekundäre Monetarisierungsoptionen (datenschutzfreundlich)

- Freemium: Basisfunktionen frei, optionale Komfortfeatures (z. B. erweiterte Offline-Regionpacks, zusätzliche
  Warnsounds) gegen geringe Einmalzahlung. Keine Standortdatenweitergabe.
- Spendenmodell / „Pay what you want“: Transparente Kostenaufstellung, freiwillige Unterstützung.
- Privacy-Abo (klein): Fokus auf nachhaltige Pflege & Updates, ohne Tracking; klare Leistungsbeschreibung.
- Partnerschaften mit Fahrassistenz-/Smart-Mobility Projekten: Austausch von anonymisierten Aggregaten (nur wenn mit
  Privacy vereinbar; optional, streng geprüft).

### 5.3.3 Open-Source Ansatz

- Veröffentlichung Kernlogik (z. B. Parser, Distanzberechnung) unter permissiver Lizenz → Community-Contributions, PRs
  für Datenqualität.
- Vorteil: Reduziert langfristige Wartungskosten, erhöht Vertrauen.
- Nachteil: Ggf. Wettbewerbsklone; Gegenstrategie: Marke/Qualität, schnelle Updates.

### 5.3.4 Nachhaltigkeit & Kosten-Nutzen

- Break-Even Analyse (vereinfachte Sicht): Bei Gesamtbudget 100k € und Freemium-Konversion 2% von 50k Downloads * 5 € =
  5.000 zahlende Nutzer → 25.000 € Erlös (Deckung Teilkosten). Ergänzt durch Spenden/Förderung zur Volldeckung.
- Ziel: Kombination aus Fördermitteln (z. B. 40%), Eigenmittel (20%), Nutzereinnahmen (30%), Spenden (10%).

### 5.3.5 Bewertung Monetarisierungs-Risiken

| Option                    | Risiko                   | Mitigation                                    |
|---------------------------|--------------------------|-----------------------------------------------|
| Classic Ads               | Datenschutz-Imageverlust | Nicht einsetzen                               |
| Verkauf Standortdaten     | Widerspricht Kernwerten  | Ausschließen                                  |
| Zu hohe Abo-Preise        | Geringe Adoption         | Moderate Preisstrategie, Mehrwert klar zeigen |
| Reine Spendenabhängigkeit | Unsichere Planung        | Mischmodell, transparente Roadmap             |

## Zusammenfassung

Die Finanzplanung zeigt ein moderates Gesamtbudget durch Wegfall serverseitiger Infrastruktur. Kostenkontrolle stützt
sich auf schlanke Metriken (EV/CPI, Nutzung, Performance) und frühzeitige Risiko-Spikes. Monetarisierung priorisiert
Datenschutzkonformität und Transparenz (Freemium/Spenden statt Tracking). Damit wird langfristige Wartbarkeit und
Erweiterbarkeit unterstützt, ohne Kernprinzipien zu kompromittieren.
