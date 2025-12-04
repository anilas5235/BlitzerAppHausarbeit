# 5 Finanzplanung

Dieses Kapitel schätzt die zu erwartenden Kosten, beschreibt Mechanismen zur Kostenkontrolle und skizziert mögliche
Finanzierungsquellen für die BlitzerApp. Es baut auf dem in Kapitel 4 beschriebenen Produktplan (Arbeitspakete,
Zeitplan, Ressourcen) auf und überführt dessen Annahmen in Kostenschätzungen. Fokus: Client-only Architektur (kein eigenes
Backend), Nutzung offener Schnittstellen (Overpass/OSM), Datenschutz als Wertversprechen.

Die Finanzplanung ist eng mit dem agilen Vorgehen nach Scrum verknüpft. Anstatt die Gesamtkosten einmalig und starr
vorab festzulegen, erfolgt die Freigabe von Mitteln inkrementell entlang der definierten Phasen und Releases. Ergebnisse aus
abgeschlossenen Sprints und Meilensteinen dienen als Grundlage für fundierte Entscheidungen über die weitere Mittel-
verwendung.

Hinweis: Agile Kostensteuerung orientiert an Scrum-Grundlagen (Scrum Guide 2020) und den Prinzipien des Agile Manifests
(siehe Quellenverzeichnis).

## 5.1 Kostenplanung

Die Kostenplanung erfolgt auf Basis von Personenaufwand (Personentage, PT), Sachkosten (Tools, Geräte, Dienste) und einem
Risiko-/Reserveposten. Beispielhafte Annahmen (können angepasst werden):

- interner Tagessatz Entwicklung: 600 € / PT
- UX/Design: 550 € / PT
- QA/Testing: 500 € / PT
- Beratung (Privacy/Compliance): 800 € / PT (punktuell)

Die genannten Tagessätze sind als Vollkostenansätze für die Entwicklung in Deutschland zu verstehen. Sie beinhalten neben
dem Bruttolohn auch typische Arbeitgebernebenkosten (Sozialabgaben, Versicherungen) sowie einen pauschalen Anteil für
interne Overheads (z. B. Infrastruktur, Verwaltung). Etwaige Umsatzsteuer auf extern bezogene Leistungen wird in dieser
internen Kostenbetrachtung nicht gesondert ausgewiesen.

Die folgenden Berechnungen sind als grobe, plausible Planwerte zu verstehen und können projektspezifisch justiert
werden.

### 5.1.1 Einordnung und agile Herleitung

Die geschätzten Personentage leiten sich aus dem in Kapitel 4.3 beschriebenen Zeitplan, den in Kapitel 4.4 dargestellten
Kapazitäten (FTE je Rolle), dem Umfang der im Produktplan (Kapitel 4.2) beschriebenen Arbeitspakete (Epics) sowie
der Anzahl geplanter Sprints pro Phase ab. Die Arbeitspakete werden hierfür im Product Backlog grob geschätzt (z. B. in
Story Points) und über die Sprints verteilt; zur Finanzplanung werden diese agilen Schätzwerte anschließend in
Personentage pro Rolle verdichtet. Damit bleibt die Budgetierung eng an die tatsächliche Teamverfügbarkeit gekoppelt,
ist aber dennoch in klassischen Budgetgrößen ausdrückbar.

Nach jedem wesentlichen Meilenstein (M1–M6, vgl. Kapitel 4.2.4) kann auf Basis der gelieferten Inkremente, der
Kostenentwicklung und der Projektziele entschieden werden, ob und in welchem Umfang die nächste Phase finanziert wird.
Zu Projektstart werden verbindlich nur Mittel für die Grundlagen- und MVP-Phase (Preparation und MVP-Kern) reserviert.
Nach Abschluss des MVP-Meilensteins (M3) erfolgt auf Basis der Sprint-Reviews, der erreichten Qualität und der
Rückmeldungen der Stakeholder eine Stop/Go-Entscheidung für die Release- und Erweiterungsphasen. Ein weiterer
wesentlicher Entscheidungspunkt ist der Beta-Meilenstein (M4): Hier wird anhand der Testabdeckung, der Stabilität und
des Nutzerfeedbacks geprüft, ob zusätzliche Mittel in Erweiterungszyklen und Nachrelease-Aktivitäten fließen oder ob der
Fokus auf Stabilisierung innerhalb des bestehenden Rahmens bleibt. Dadurch wird das finanzielle Risiko reduziert, und
weitere Investitionen erfolgen nur, wenn der bisherige Projektverlauf und der sichtbare Produktnutzen dies
rechtfertigen.

### 5.1.2 Personenaufwand

Die folgende Übersicht fasst die geschätzten Personentage je Rolle und Phase zusammen und leitet daraus die erwarteten
Personalkosten ab. Sie bildet den größten Block der Gesamtkosten und ist direkt an die in Kapitel 4 beschriebenen
Phasen, Releases und Kapazitäten gekoppelt (vgl. Ressourcenplanung 4.3). Hierbei handelt es sich um eine grobe
Schätzung; die tatsächlichen Aufwände werden im Rahmen der Sprint Plannings bzw. bei der Planung der nächsten Phase
im Team ermittelt und können im Projektverlauf angepasst werden.

| Phase                                    | Geschätzte PT Dev | PT UX | PT QA | PT Beratung | Summe PT | Kosten (€)                                                             |
|------------------------------------------|-------------------|-------|-------|-------------|----------|------------------------------------------------------------------------|
| Preparation (Grundlagen & Architektur)   | 8                 | 2     | 0     | 2           | 12       | 8*600 + 2*550 + 2*800 = 4.800 + 1.100 + 1.600 = 7.500                  |
| MVP-Kern (AP-B1–B7)                      | 32                | 6     | 4     | 0           | 42       | 32*600 + 6*550 + 4*500 = 19.200 + 3.300 + 2.000 = 24.500               |
| AppStore-Release & Qualität              | 16                | 2     | 12    | 1           | 31       | 16*600 + 2*550 + 12*500 + 1*800 = 9.600 + 1.100 + 6.000 + 800 = 17.500 |
| Erweiterungszyklen (erster Zyklus)       | 20                | 4     | 6     | 1           | 31       | 20*600 + 4*550 + 6*500 + 1*800 = 12.000 + 2.200 + 3.000 + 800 = 18.000 |
| Nachrelease / Wartung (erste 4–6 Wochen) | 10                | 1     | 4     | 0           | 15       | 10*600 + 1*550 + 4*500 = 6.000 + 550 + 2.000 = 8.550                   |
| Gesamtsumme                              | 86                | 15    | 26    | 4           | 131      | ≈ 76.000 €                                                             |

Hinweis: Rundungsdifferenzen sind möglich; Reserven siehe Abschnitt 5.1.4.

### 5.1.3 Sachkosten / Dienste

Ergänzend zum Personenaufwand fallen Sachkosten für Infrastruktur, Geräte und Werkzeuge an. Aufgrund des gewählten
Client-only-Ansatzes und des Einsatzes von Open-Source-Komponenten bleiben diese Kosten im Vergleich zu den
Personalkosten moderat. Die folgende Tabelle basiert auf den in Kapitel 4.3.3 beschriebenen externen Ressourcen und
ordnet ihnen beispielhafte Kosten zu.

| Kostenquelle                  | Annahme                         | Kostenschätzung (€/Jahr) | Kommentar                                            |
|-------------------------------|---------------------------------|--------------------------|------------------------------------------------------|
| Tile-Provider API             | Low-Usage Developer Plan        | 300–600                  | Nach Verbrauch; Caching reduziert Abrufe             |
| Testgeräte (Neuanschaffung)   | 2 Android (Mid/Low) + 1 iPhone  | 1.800–2.200 einmalig     | Nutzungsdauer > 1 Jahr                               |
| Design-/Prototyping-Tools     | Figma (Team), o. ä.             | 150–300                  | Je nach Lizenzmodell; ggf. über Hochschule abgedeckt |
| CI/CD (Cloud Build)           | Open-Source-Rabatt / Basic Plan | 0–600                    | Abhängig von Provider & Build-Minuten                |
| Monitoring / Logging lokal    | Open Source                     | 0                        | Kein externes Tracking, Bibliotheken kostenlos       |
| OAuth-App-Registrierung (OSM) | Kostenlos                       | 0                        | Verwaltungsaufwand intern                            |
| Sonstige Lizenzen / SDKs      | Keine proprietären SDKs geplant | 0                        | Reiner Open-Source-Stack                             |

### 5.1.4 Reserve / Risikopuffer

Um auf Unsicherheiten im Projektverlauf reagieren zu können, wird zusätzlich ein Risikopuffer eingeplant. Dieser soll
insbesondere technische Risiken und externe Abhängigkeiten abfedern.

- Unerwartete Verzögerungen (Performance, Geofencing, Store-Review): +10–15 % der Personalkosten ≈ 8.000–11.500 €.
- Wechsel Tile-Provider (falls Limits erreicht oder Konditionen ungünstig): zusätzliche 300–500 €.
- Rechtliche Beratung bei Länderrestriktionen oder geänderten Rahmenbedingungen: +1.500 € (Kontingent).

Die Höhe der Puffer orientiert sich an den in der Risikoanalyse beschriebenen technischen und organisatorischen Risiken
(z. B. Komplexität von Geofencing und Performance-Optimierung, mögliche Store-Review-Verzögerungen). Bei Eintritt
solcher Risiken werden zunächst Umfang und Priorität der Backlog-Items angepasst, bevor zusätzliche Mittel in Anspruch
genommen werden.

Geschätzte Gesamtkosten inkl. Puffer: ca. 90.000–95.000 € bis zum ersten Release (Version 1.0) und der ersten
Stabilisierungsphase.

### 5.1.5 Kostentreiber & Einsparpotenziale

Die größten Kostentreiber und Einsparpotenziale ergeben sich aus Architekturentscheidungen und Qualitätsansprüchen:

- Kostentreiber:
    - Geofencing-Optimierung und Performance-Tuning, insbesondere unter Energieaspekten.
    - QA für Stabilität & Energieverbrauch (intensive Tests auf realen Geräten, Beta-Phase).
    - AppStore-Review-Runden und Anpassungen aufgrund von Richtlinien (Zeit- und damit Kostenfaktor).
- Einsparpotenziale:
    - Verzicht auf eigenes Backend → keine Server-/Ops-Kosten; konsequentes Caching → niedrigere Tile-Kosten.
    - Nutzung eines Open-Source-Stack und Community-Ressourcen → keine Lizenzgebühren für Karten-/Analyse-SDKs.
    - Modulare Architektur → schnellere Iterationen, weniger Rework bei Erweiterungen.

Bei Kostendruck wird der Projektumfang gezielt über das Product Backlog gesteuert. Zuerst werden optionale
Erweiterungsfeatures mit geringerem unmittelbarem Nutzen für den MVP reduziert oder in spätere Phasen verschoben (z. B.
Teile der Erweiterungszyklen oder ausgewählte Komfortfunktionen in der Wartungsphase). Demgegenüber gelten
Kernfunktionalität, Stabilität, Datenschutz-Compliance und grundlegende Barrierefreiheit als nicht verhandelbar und
werden auch bei Kostendruck nicht gekürzt. Die Priorisierung im Backlog stellt sicher, dass die verfügbaren Mittel
konsequent in die wertvollsten Inkremente fließen.
