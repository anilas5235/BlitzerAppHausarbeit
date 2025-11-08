# 6 Finanzplanung

Dieses Kapitel schätzt die zu erwartenden Kosten, beschreibt Mechanismen zur Kostenkontrolle und skizziert mögliche Finanzierungsquellen für die BlitzerApp. Fokus: Client-only Architektur (kein eigenes Backend), Nutzung offener Schnittstellen (Overpass/OSM), Datenschutz als Wertversprechen.

## 6.1 Budgetierung
Die Budgetierung erfolgt auf Basis von Personenaufwand (Personentage, PT), Sachkosten (Tools, Geräte, Dienste) und einem Risiko-/Reserveposten. Beispielhafte Annahmen (können angepasst werden):
- interner Tagessatz Entwicklung: 600 € / PT
- UX/Design: 550 € / PT
- QA/Testing: 500 € / PT
- Beratung (Privacy/Compliance): 800 € / PT (punktuell)

### 6.1.1 Personenaufwand (Phasen kumuliert, aus Kapitel 5 abgeleitet)
| Phase | Geschätzte PT Dev | PT UX | PT QA | PT Beratung | Summe PT | Kosten (€) |
|-------|-------------------|-------|------|-------------|----------|-----------|
| A (Anforderungen/Architektur) | 8 | 2 | 0 | 2 | 12 | 8*600 + 2*550 + 2*800 = 4.800 + 1.100 + 1.600 = 7.500 |
| B (MVP Kern) | 30 | 6 | 4 | 0 | 40 | 30*600 + 6*550 + 4*500 = 18.000 + 3.300 + 2.000 = 23.300 |
| C (Erweiterung I) | 18 | 4 | 6 | 1 | 29 | 18*600 + 4*550 + 6*500 + 1*800 = 10.800 + 2.200 + 3.000 + 800 = 16.800 |
| D (Erweiterung II) | 20 | 3 | 6 | 1 | 30 | 12.000 + 1.650 + 3.000 + 800 = 17.450 |
| E (Release & Qualität) | 14 | 2 | 12 | 1 | 29 | 8.400 + 1.100 + 6.000 + 800 = 16.300 |
| F (Nachrelease erste 4 Wochen) | 8 | 1 | 4 | 0 | 13 | 4.800 + 550 + 2.000 = 7.350 |
| Gesamtsumme | 98 | 18 | 32 | 5 | 153 | ≈ 87.700 € |

Hinweis: Rundungsdifferenzen möglich; Reserven siehe unten.

### 6.1.2 Sachkosten / Dienste
| Kostenquelle | Annahme | Kostenschätzung (€/Jahr) | Kommentar |
|--------------|---------|--------------------------|-----------|
| Tile-Provider API | Low-Usage Developer Plan | 300–600 | Nach Verbrauch, Caching reduziert Abrufe |
| Testgeräte (Neuanschaffung) | 2 Android (Mid/Low) + 1 iPhone | 1.800–2.200 einmalig | Nutzungsdauer >1 Jahr |
| Design-/Prototyping Tools | Figma (Team), o. ä. | 150–300 | Kann entfallen bei Einzelaccount |
| CI (Cloud Build) | Open Source Rabatt / Basic Plan | 0–600 | Abhängig von Provider & Minuten |
| Monitoring lokal (Libs) | Open Source | 0 | Kein externes Tracking |
| OAuth App Registrierung (OSM) | Kostenlos | 0 | Verwaltungsaufwand intern |
| Sonstige Lizenzen | Keine proprietären SDKs geplant | 0 | Open Source Stack |

### 6.1.3 Reserve / Risikopuffer
- Unerwartete Verzögerungen (Performance, Geofencing, Store-Review): +10% Personenbudget ≈ 8.700 €.
- Wechsel Tile-Provider (falls Limits erreicht): zusätzliche 300–500 €.
- Rechtliche Beratung bei Länderrestriktionen: +1.500 € (Kontingent).

Geschätztes Gesamtbudget inkl. Puffer: ca. 100.000 € (Bandbreite 95k–105k) bis Release + erste Stabilisierung.

### 6.1.4 Kostentreiber & Einsparpotenziale
- Kostentreiber: Geofencing-Optimierung, Performance-Tuning, QA für Stabilität & Energieverbrauch.
- Einsparung: Verzicht auf eigenes Backend → keine Server-/Ops-Kosten; konsequentes Caching → niedrigere Tile-Kosten; modulare Architektur → schnellere Iterationen.

## 6.2 Kostenkontrolle
Ziel: Frühzeitiges Erkennen von Abweichungen, ohne Overhead.

### 6.2.1 Steuerungsinstrumente
- Kostenbaseline: Summe geplanter PT pro Phase vs. Ist-Aufwand (wöchentlich aktualisiert).
- Burn-Down Diagramm (Aufgaben / verbleibende PT) je Sprint/Iterationsblock.
- Earned Value Light:
  - PV (Planned Value): Geplante PT bis Stichtag.
  - EV (Earned Value): Abgeschlossene AP-PT (Abnahme-Kriterium erfüllt).
  - AC (Actual Cost): Tatsächlich angefallene PT * Tagessätze.
  - Indikatoren: CPI = EV/AC (<1 = Kostenüberzug), SPI = EV/PV (<1 = Verzug).

### 6.2.2 Überwachung externer Nutzung
- Overpass-Abfragen: Logging Anzahl/Tag, mittlere Antwortzeit, Fehlerquote; Warnschwelle >20% Fehlversuche.
- Tile-Abrufe: Statistiken (sofern Provider-Dashboard) → monatlicher Check; Ziel: stabile Nutzung, kein exponentielles Wachstum.
- Geräte-Profiling: Quartalsweise Energieverbrauchs-Review (bei wesentlicher Feature-Erweiterung.

### 6.2.3 Entscheidungs-Trigger
- Abweichung >15% in CPI/SPI über 2 aufeinanderfolgende Wochen → Review & Re-Priorisierung (Feature-Scope kürzen oder Ressourcen erhöhen).
- Performanceziel (Startzeit, Warn-Latenz) nicht erfüllt vor Phase D → zusätzliche Optimierungs-Sprint einplanen (Budget aus Reserve).
- Store-Review Blockade → sofortige Taskforce (Dev + Compliance) ≤ 3 PT Zusatz.

### 6.2.4 Reporting & Transparenz
- Wöchentlich: Kurzbericht (Progress, EV/CPI, größte Risiken) an Projektteam.
- Meilenstein-Ende: Zusammenfassung Ist vs. Plan, verbleibende Restkosten, Nachjustierungen.
- Keine personenbezogenen Daten im Reporting; rein technische & Aufwandmetriken.

### 6.2.5 Kostenrisiken & Gegenmaßnahmen
| Risiko | Auswirkung | Gegenmaßnahme |
|--------|------------|---------------|
| Geofencing komplexer als erwartet | Mehr Entwicklungs-PT | Früher Spike (Prototyp) in Phase B |
| Übernutzung Overpass → Rate-Limits | Verzögerung, Re-Engineering | Caching, kleinere BBox, Backoff, Mirrors |
| Energieverbrauch zu hoch | Ablehnung durch Nutzer/App Store | Profiling früh, iterative Optimierung (AP-D2) |
| Verzögerte Store-Freigabe | Release verschoben | Frühe Prüfung Richtlinien, Beta Testlauf |
| Zugänglichkeit (A11y) unterschätzt | Nacharbeit, Image-Risiko | Früh AP-C3, Checklisten etablieren |
| Datenqualität unzureichend lokal | Geringer Nutzen | OSM Notes Integration zur Verbesserung |

## 6.3 Finanzierungsquellen
Zweck: Deckung initialer Entwicklungskosten, nachhaltige Pflege ohne Aufgabe des Datenschutz-Versprechens.

### 6.3.1 Primäre Quellen
- Eigenmittel / internes Budget: Volle Kontrolle, schnell; limitiert Skalierung.
- Förderprogramme (Digitalisierung, Open Data, Verkehrssicherheit): Antrag mit Fokus Datenschutz & Gemeinwohl.
- Kooperation mit Verkehrssicherheitsorganisationen (Verbände, Initiativen): Sachmittel (Geräte) oder Zuschuss.

### 6.3.2 Sekundäre Monetarisierungsoptionen (datenschutzfreundlich)
- Freemium: Basisfunktionen frei, optionale Komfortfeatures (z. B. erweiterte Offline-Regionpacks, zusätzliche Warnsounds) gegen geringe Einmalzahlung. Keine Standortdatenweitergabe.
- Spendenmodell / „Pay what you want“: Transparente Kostenaufstellung, freiwillige Unterstützung.
- Privacy-Abo (klein): Fokus auf nachhaltige Pflege & Updates, ohne Tracking; klare Leistungsbeschreibung.
- Partnerschaften mit Fahrassistenz-/Smart-Mobility Projekten: Austausch von anonymisierten Aggregaten (nur wenn mit Privacy vereinbar; optional, streng geprüft).

### 6.3.3 Open-Source Ansatz
- Veröffentlichung Kernlogik (z. B. Parser, Distanzberechnung) unter permissiver Lizenz → Community-Contributions, PRs für Datenqualität.
- Vorteil: Reduziert langfristige Wartungskosten, erhöht Vertrauen.
- Nachteil: Ggf. Wettbewerbsklone; Gegenstrategie: Marke/Qualität, schnelle Updates.

### 6.3.4 Nachhaltigkeit & Kosten-Nutzen
- Break-Even Analyse (vereinfachte Sicht): Bei Gesamtbudget 100k € und Freemium-Konversion 2% von 50k Downloads * 5 € = 5.000 zahlende Nutzer → 25.000 € Erlös (Deckung Teilkosten). Ergänzt durch Spenden/Förderung zur Volldeckung.
- Ziel: Kombination aus Fördermitteln (z. B. 40%), Eigenmittel (20%), Nutzereinnahmen (30%), Spenden (10%).

### 6.3.5 Bewertung Monetarisierungs-Risiken
| Option | Risiko | Mitigation |
|--------|-------|------------|
| Classic Ads | Datenschutz-Imageverlust | Nicht einsetzen |
| Verkauf Standortdaten | Widerspricht Kernwerten | Ausschließen |
| Zu hohe Abo-Preise | Geringe Adoption | Moderate Preisstrategie, Mehrwert klar zeigen |
| Reine Spendenabhängigkeit | Unsichere Planung | Mischmodell, transparente Roadmap |

## Zusammenfassung
Die Finanzplanung zeigt ein moderates Gesamtbudget durch Wegfall serverseitiger Infrastruktur. Kostenkontrolle stützt sich auf schlanke Metriken (EV/CPI, Nutzung, Performance) und frühzeitige Risiko-Spikes. Monetarisierung priorisiert Datenschutzkonformität und Transparenz (Freemium/Spenden statt Tracking). Damit wird langfristige Wartbarkeit und Erweiterbarkeit unterstützt, ohne Kernprinzipien zu kompromittieren.
