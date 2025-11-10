## 5.2 Kostenkontrolle

Ziel: Frühzeitiges Erkennen von Abweichungen, ohne Overhead.

### 5.2.1 Steuerungsinstrumente

- Kostenbaseline: Summe geplanter PT pro Phase vs. Ist-Aufwand (wöchentlich aktualisiert).
- Burn-Down Diagramm (Aufgaben / verbleibende PT) je Sprint/Iterationsblock.
- Earned Value Light:
    - PV (Planned Value): Geplante PT bis Stichtag.
    - EV (Earned Value): Abgeschlossene AP-PT (Abnahme-Kriterium erfüllt).
    - AC (Actual Cost): Tatsächlich angefallene PT * Tagessätze.
    - Indikatoren: CPI = EV/AC (<1 = Kostenüberzug), SPI = EV/PV (<1 = Verzug).

### 5.2.2 Überwachung externer Nutzung

- Overpass-Abfragen: Logging Anzahl/Tag, mittlere Antwortzeit, Fehlerquote; Warnschwelle >20% Fehlversuche.
- Tile-Abrufe: Statistiken (sofern Provider-Dashboard) → monatlicher Check; Ziel: stabile Nutzung, kein exponentielles
  Wachstum.
- Geräte-Profiling: Quartalsweise Energieverbrauchs-Review (bei wesentlicher Feature-Erweiterung.

### 5.2.3 Entscheidungs-Trigger

- Abweichung >15% in CPI/SPI über 2 aufeinanderfolgende Wochen → Review & Re-Priorisierung (Feature-Scope kürzen oder
  Ressourcen erhöhen).
- Performanceziel (Startzeit, Warn-Latenz) nicht erfüllt vor Phase D → zusätzliche Optimierungs-Sprint einplanen (Budget
  aus Reserve).
- Store-Review Blockade → sofortige Taskforce (Dev + Compliance) ≤ 3 PT Zusatz.

### 5.2.4 Reporting & Transparenz

- Wöchentlich: Kurzbericht (Progress, EV/CPI, größte Risiken) an Projektteam.
- Meilenstein-Ende: Zusammenfassung Ist vs. Plan, verbleibende Restkosten, Nachjustierungen.
- Keine personenbezogenen Daten im Reporting; rein technische & Aufwandmetriken.

### 5.2.5 Kostenrisiken & Gegenmaßnahmen

| Risiko                             | Auswirkung                       | Gegenmaßnahme                                 |
|------------------------------------|----------------------------------|-----------------------------------------------|
| Geofencing komplexer als erwartet  | Mehr Entwicklungs-PT             | Früher Spike (Prototyp) in Phase B            |
| Übernutzung Overpass → Rate-Limits | Verzögerung, Re-Engineering      | Caching, kleinere BBox, Backoff, Mirrors      |
| Energieverbrauch zu hoch           | Ablehnung durch Nutzer/App Store | Profiling früh, iterative Optimierung (AP-D2) |
| Verzögerte Store-Freigabe          | Release verschoben               | Frühe Prüfung Richtlinien, Beta Testlauf      |
| Zugänglichkeit (A11y) unterschätzt | Nacharbeit, Image-Risiko         | Früh AP-C3, Checklisten etablieren            |
| Datenqualität unzureichend lokal   | Geringer Nutzen                  | OSM Notes Integration zur Verbesserung        |
