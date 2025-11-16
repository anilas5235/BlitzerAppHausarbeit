## 5.2 Kostenkontrolle

Ziel: Frühzeitiges Erkennen von Abweichungen, ohne Overhead, und Unterstützung der in Abschnitt 5.1 beschriebenen
agilen Budgetsteuerung.

### 5.2.1 Steuerungsinstrumente

- Kostenbaseline: Summe geplanter PT pro Phase vs. Ist-Aufwand (wöchentlich aktualisiert).
- Burn-Down Diagramm (Aufgaben / verbleibende PT) je Sprint/Iterationsblock.
- Earned Value Light:
    - PV (Planned Value): Geplante PT bis Stichtag.
    - EV (Earned Value): Abgeschlossene AP-PT (Abnahme-Kriterium erfüllt).
    - AC (Actual Cost): Tatsächlich angefallene PT * Tagessätze.
    - Indikatoren: CPI = EV/AC (<1 = Kostenüberzug), SPI = EV/PV (<1 = Verzug).

Diese Kennzahlen werden sprintweise erhoben und im Rahmen der Sprint Reviews betrachtet. Abweichungen fließen in die
Sprint Retrospektiven ein und führen zu Anpassungen bei Planung, Schätzung und Arbeitsweise. Sie beziehen sich auf die
in Abschnitt 5.1 geplanten Personentage und Phasen und dienen damit als Frühwarnsystem, ob die nächste Budgettranche
(z. B. für die Erweiterungsphasen C und D oder die Nachrelease-Phase F) wie vorgesehen freigegeben werden sollte oder ob
Umfang und Prioritäten im Backlog angepasst werden müssen.

Hinweis: Sprint-basierte Steuerung in Anlehnung an den Scrum Guide (2020); Werte/Prinzipien vgl. Agile Manifest (siehe
Quellenverzeichnis).

Zusätzlich zu Aufwand- und Kostenmetriken werden Outcome-orientierte Kennzahlen beobachtet, z. B. Crashrate,
App-Startzeit, Warn-Latenz sowie Feedback aus Beta-Tests. So bleibt der Fokus auf Nutzen und Qualität, nicht nur auf
verbrauchten Ressourcen.

### 5.2.2 Überwachung externer Nutzung

- Overpass-Abfragen: Logging Anzahl/Tag, mittlere Antwortzeit, Fehlerquote; Warnschwelle >20% Fehlversuche.
- Tile-Abrufe: Statistiken (sofern Provider-Dashboard) → monatlicher Check; Ziel: stabile Nutzung, kein exponentielles
  Wachstum.
- Geräte-Profiling: Quartalsweise Energieverbrauchs-Review (bei wesentlicher Feature-Erweiterung).

### 5.2.3 Entscheidungs-Trigger

- Abweichung >15% in CPI/SPI über 2 aufeinanderfolgende Wochen → Review & Re-Priorisierung (Feature-Scope kürzen oder
  Ressourcen erhöhen).
- Performanceziel (Startzeit, Warn-Latenz) nicht erfüllt vor Phase D → zusätzlichen Optimierungs-Sprint einplanen (Budget
  aus Reserve).
- Store-Review Blockade → sofortige Taskforce (Dev + Compliance) ≤ 3 PT Zusatz.

Insbesondere an den Meilensteinen M2 (MVP) und M5 (Beta/Store-Ready) werden die aggregierten Kennzahlen (EV, CPI/SPI,
Outcome-Metriken) herangezogen, um über die Freigabe der nächsten Budgettranche gemäß Abschnitt 5.1 zu entscheiden.
So werden Scope- und Budgetentscheidungen nicht nur einmalig zu Projektbeginn getroffen, sondern regelmäßig auf Basis
der tatsächlich gelieferten Ergebnisse und Kosten überprüft.

### 5.2.4 Reporting & Transparenz

- Wöchentlich: Kurzbericht (Progress, EV/CPI, größte Risiken) an Projektteam.
- Meilenstein-Ende: Zusammenfassung Ist vs. Plan, verbleibende Restkosten, Nachjustierungen.
- Keine personenbezogenen Daten im Reporting; rein technische & Aufwandmetriken.

Sprint Reviews dienen als natürliche Reporting-Termine mit Stakeholdern, Sprint Retrospektiven als Forum zur internen
Verbesserung. Größere Releases werden zusätzlich mit aggregierten Kosten- und Nutzenberichten hinterlegt, um
mehrphasige Budgetentscheidungen zu unterstützen. Diese Berichte bilden zugleich eine Entscheidungsgrundlage für die in
Abschnitt 5.1 beschriebene phasenweise Budgetfreigabe und mögliche Anpassungen des Projektumfangs.

### 5.2.5 Kostenrisiken & Gegenmaßnahmen

| Risiko                             | Auswirkung                       | Gegenmaßnahme                                 |
|------------------------------------|----------------------------------|-----------------------------------------------|
| Geofencing komplexer als erwartet  | Mehr Entwicklungs-PT             | Früher Spike (Prototyp) in Phase B            |
| Übernutzung Overpass → Rate-Limits | Verzögerung, Re-Engineering      | Caching, kleinere BBox, Backoff, Mirrors      |
| Energieverbrauch zu hoch           | Ablehnung durch Nutzer/App Store | Profiling früh, iterative Optimierung (AP-D2) |
| Verzögerte Store-Freigabe          | Release verschoben               | Frühe Prüfung Richtlinien, Beta Testlauf      |
| Zugänglichkeit (A11y) unterschätzt | Nacharbeit, Image-Risiko         | Früh AP-C3, Checklisten etablieren            |
| Datenqualität unzureichend lokal   | Geringer Nutzen                  | OSM Notes Integration zur Verbesserung        |

Die hier beschriebenen Kostenrisiken stehen in engem Zusammenhang mit der Risikoanalyse in Kapitel 6. Relevante
Maßnahmen werden im Backlog abgebildet und in Sprints eingeplant, sodass Risiken und Kosteneffekte frühzeitig adressiert
werden können.
