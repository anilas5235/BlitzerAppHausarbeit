## 5.3 Finanzierungsquellen

Zweck: Deckung initialer Entwicklungskosten, nachhaltige Pflege ohne Aufgabe des Datenschutz-Versprechens.

### 5.3.1 Primäre Quellen

- Eigenmittel / internes Budget: Volle Kontrolle, schnell; limitiert Skalierung.
- Förderprogramme (Digitalisierung, Open Data, Verkehrssicherheit): Antrag mit Fokus Datenschutz & Gemeinwohl.
- Kooperation mit Verkehrssicherheitsorganisationen (Verbände, Initiativen): Sachmittel (Geräte) oder Zuschuss.

Die Bereitstellung von Mitteln kann entlang der definierten Releases (vgl. Kapitel 4) erfolgen. Nach Abschluss eines
Releases liegen jeweils sichtbare, testbare Ergebnisse aus mehreren Sprints vor, die als Grundlage für Entscheidungen
über weitere Finanzierungsrunden dienen.

### 5.3.2 Sekundäre Monetarisierungsoptionen (datenschutzfreundlich)

- Freemium: Basisfunktionen frei, optionale Komfortfeatures (z. B. erweiterte Offline-Regionpacks, zusätzliche
  Warnsounds) gegen geringe Einmalzahlung. Keine Standortdatenweitergabe.
- Spendenmodell / „Pay what you want“: Transparente Kostenaufstellung, freiwillige Unterstützung.
- Privacy-Abo (klein): Fokus auf nachhaltige Pflege & Updates, ohne Tracking; klare Leistungsbeschreibung.
- Partnerschaften mit Fahrassistenz-/Smart-Mobility Projekten: Austausch von anonymisierten Aggregaten (nur wenn mit
  Privacy vereinbar; optional, streng geprüft).

Iterative Validierung: Monetarisierungsvarianten werden schrittweise getestet (z. B. A/B-Varianten von Freemium-
Angeboten ohne nutzerbezogenes Tracking, Auswertung ausschließlich aggregierter Opt-in-Daten). Anpassungen erfolgen
transparent und vorsichtig, um Nutzervertrauen nicht zu beeinträchtigen.

Die Monetarisierungsmodelle werden iterativ erprobt. In frühen Releases liegt der Schwerpunkt auf Nutzenvalidierung und
Nutzerakzeptanz; Monetarisierungsfunktionen werden behutsam und transparent eingeführt und bei Bedarf angepasst, ohne
Tracking oder den Verkauf von Standortdaten.

### 5.3.3 Open-Source Ansatz

- Veröffentlichung Kernlogik (z. B. Parser, Distanzberechnung) unter permissiver Lizenz → Community-Contributions, PRs
  für Datenqualität.
- Vorteil: Reduziert langfristige Wartungskosten, erhöht Vertrauen.
- Nachteil: Ggf. Wettbewerbsklone; Gegenstrategie: Marke/Qualität, schnelle Updates.

### 5.3.4 Nachhaltigkeit & Kosten-Nutzen

- Break-Even Analyse (vereinfachte Sicht): Bei Gesamtbudget 100k € und Freemium-Konversion 2% von 50k Downloads * 5 € =
  5.000 zahlende Nutzer → 25.000 € Erlös (Deckung Teilkosten). Ergänzt durch Spenden/Förderung zur Volldeckung.
- Ziel: Kombination aus Fördermitteln (z. B. 40%), Eigenmitteln (20%), Nutzereinnahmen (30%), Spenden (10%).
- Finanz-Meilensteine (Beispiele):
  - FM1: Entscheidung über Fördermittel/Eigenmittel vor Start der MVP-Phase (B).
  - FM2: Evaluierung des gewählten Monetarisierungsmodells nach 6 Monaten Live-Betrieb (Anpassung oder Pivot bei Bedarf).

Aus agiler Sicht wird die Finanzierungsstrategie regelmäßig im Rahmen von Release-Reviews überprüft. Erzielte Erlöse
fließen bevorzugt in Backlog-Items mit hohem Nutzermehrwert (z. B. zusätzliche Sicherheits- oder
Barrierefreiheits-Funktionen). So bleibt die Weiterentwicklung des Produkts eng an Wirkung und Nutzerfeedback gekoppelt.

Hinweis: Agiles Vorgehen und Release-Reviews vgl. Scrum Guide (2020) und Agile Manifest (siehe Quellenverzeichnis).

## Zusammenfassung

Die Finanzplanung zeigt ein moderates Gesamtbudget durch Wegfall serverseitiger Infrastruktur. Kostenkontrolle stützt
sich auf schlanke Metriken (EV/CPI, Nutzung, Performance) und frühzeitige Risiko-Spikes. Monetarisierung priorisiert
Datenschutzkonformität und Transparenz (Freemium/Spenden statt Tracking). Durch die Verknüpfung von Finanzierung,
inkrementellen Releases und einem Scrum-basierten Vorgehen kann das Projekt schrittweise weiterentwickelt werden, ohne
Kernprinzipien zu kompromittieren.
