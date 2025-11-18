# 5 Finanzplanung

Dieses Kapitel schätzt die zu erwartenden Kosten, beschreibt Mechanismen zur Kostenkontrolle und skizziert mögliche
Finanzierungsquellen für die BlitzerApp. Es baut auf dem in Kapitel 4 beschriebenen Produktplan (Arbeitspakete,
Zeitplan, Ressourcen) auf und überführt dessen Annahmen in Budgetgrößen. Fokus: Client-only Architektur (kein eigenes
Backend), Nutzung offener Schnittstellen (Overpass/OSM), Datenschutz als Wertversprechen.

Die Finanzplanung ist eng mit dem agilen Vorgehen nach Scrum verknüpft. Anstatt das Gesamtbudget einmalig und starr
vorab festzulegen, erfolgt die Budgetfreigabe inkrementell entlang der definierten Phasen und Releases. Ergebnisse aus
abgeschlossenen Sprints und Meilensteinen dienen als Grundlage für fundierte Entscheidungen über die weitere Mittel-
verwendung.

Hinweis: Agile Budgetsteuerung orientiert an Scrum-Grundlagen (Scrum Guide 2020) und den Prinzipien des Agile Manifests
(siehe Quellenverzeichnis).

## 5.1 Budgetierung

Die Budgetierung erfolgt auf Basis von Personenaufwand (Personentage, PT), Sachkosten (Tools, Geräte, Dienste) und einem
Risiko-/Reserveposten. Beispielhafte Annahmen (können angepasst werden):

- interner Tagessatz Entwicklung: 600 € / PT
- UX/Design: 550 € / PT
- QA/Testing: 500 € / PT
- Beratung (Privacy/Compliance): 800 € / PT (punktuell)

### 5.1.1 Einordnung und agile Herleitung

Die geschätzten Personentage leiten sich aus dem in Kapitel 4.2 beschriebenen Zeitplan, den in Kapitel 4.3 dargestellten
Kapazitäten (FTE je Rolle), dem Umfang der im Produktplan (Kapitel 4.1) beschriebenen Arbeitspakete (Epics) sowie
der Anzahl geplanter Sprints pro Phase ab. Die Arbeitspakete werden hierfür im Product Backlog grob geschätzt (z. B. in
Story Points) und über die Sprints verteilt; zur Finanzplanung werden diese agilen Schätzwerte anschließend in
Personentage pro Rolle verdichtet. Damit bleibt die Budgetierung eng an die tatsächliche Teamverfügbarkeit gekoppelt, ist
aber dennoch in klassischen Budgetgrößen ausdrückbar.

Nach jedem wesentlichen Meilenstein (z. B. M1–M5) kann auf Basis der gelieferten Inkremente, der Kostenentwicklung und
der Projektziele entschieden werden, ob und in welchem Umfang die nächste Phase finanziert wird. Zu Projektstart wird
verbindlich nur das Budget für die Grundlagen- und MVP-Phase (A und B) reserviert. Nach Abschluss des MVP-Meilensteins
(M2) erfolgt auf Basis der Sprint-Reviews, der erreichten Qualität und der Rückmeldungen der Stakeholder eine Stop/Go-
Entscheidung für die Erweiterungsphasen C und D. Ein weiterer wesentlicher Entscheidungspunkt ist der Beta-Meilenstein
(M5): Hier wird anhand der Testabdeckung, der Stabilität und des Nutzerfeedbacks geprüft, ob zusätzliche Mittel in die
Nachrelease-Phase F (Wartung, Optimierungen) fließen oder ob der Fokus auf Stabilisierung innerhalb des bestehenden
Rahmens bleibt. Dadurch wird das finanzielle Risiko reduziert, und weitere Investitionen erfolgen nur, wenn der
bisherige Projektverlauf und der sichtbare Produktnutzen dies rechtfertigen.

### 5.1.2 Personenaufwand

Die folgende Übersicht fasst die geschätzten Personentage je Rolle und Phase zusammen und leitet daraus die erwarteten
Personalkosten ab. Sie bildet den größten Block des Gesamtbudgets und ist direkt an die in Kapitel 4 beschriebenen
Releases und Kapazitäten gekoppelt (vgl. Ressourcenplanung 4.3). Hierbei handelt es sich um eine grobe Schätzung; die tatsächlichen Aufwände werden 
im Rahmen der Sprint Plannings bzw. bei der Planung der nächsten Phase durch das Team selbst ermittelt und können im 
Projektverlauf angepasst werden.

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

### 5.1.3 Sachkosten / Dienste

Ergänzend zum Personenaufwand fallen Sachkosten für Infrastruktur, Geräte und Werkzeuge an. Aufgrund des gewählten
Client-only-Ansatzes und des Einsatzes von Open-Source-Komponenten bleiben diese Kosten im Vergleich zum
Personenbudget moderat.

| Kostenquelle                  | Annahme                         | Kostenschätzung (€/Jahr) | Kommentar                                |
|-------------------------------|---------------------------------|--------------------------|------------------------------------------|
| Tile-Provider API             | Low-Usage Developer Plan        | 300–600                  | Nach Verbrauch, Caching reduziert Abrufe |
| Testgeräte (Neuanschaffung)   | 2 Android (Mid/Low) + 1 iPhone  | 1.800–2.200 einmalig     | Nutzungsdauer >1 Jahr                    |
| Design-/Prototyping Tools     | Figma (Team), o. ä.             | 150–300                  | Kann entfallen bei Einzelaccount         |
| CI (Cloud Build)              | Open Source Rabatt / Basic Plan | 0–600                    | Abhängig von Provider & Minuten          |
| Monitoring lokal (Libs)       | Open Source                     | 0                        | Kein externes Tracking                   |
| OAuth App Registrierung (OSM) | Kostenlos                       | 0                        | Verwaltungsaufwand intern                |
| Sonstige Lizenzen             | Keine proprietären SDKs geplant | 0                        | Open Source Stack                        |

### 5.1.4 Reserve / Risikopuffer

Um auf Unsicherheiten im Projektverlauf reagieren zu können, wird zusätzlich ein Risikopuffer eingeplant. Dieser soll
insbesondere technische Risiken und externe Abhängigkeiten abfedern.

- Unerwartete Verzögerungen (Performance, Geofencing, Store-Review): +10% Personenbudget ≈ 8.700 €.
- Wechsel Tile-Provider (falls Limits erreicht): zusätzliche 300–500 €.
- Rechtliche Beratung bei Länderrestriktionen: +1.500 € (Kontingent).

Die Höhe der Puffer orientiert sich an den in der Risikoanalyse beschriebenen technischen und organisatorischen Risiken
(z. B. Komplexität von Geofencing und Performance-Optimierung, mögliche Store-Review-Verzögerungen). Bei Eintritt
solcher
Risiken werden zunächst Umfang und Priorität der Backlog-Items angepasst, bevor zusätzliche Mittel in Anspruch genommen
werden.

Geschätztes Gesamtbudget inkl. Puffer: ca. 100.000 € (Bandbreite 95k–105k) bis Release + erste Stabilisierung.

### 5.1.5 Kostentreiber & Einsparpotenziale

Die größten Kostentreiber und Einsparpotenziale ergeben sich aus Architekturentscheidungen und Qualitätsansprüchen:

- Kostentreiber: Geofencing-Optimierung, Performance-Tuning, QA für Stabilität & Energieverbrauch.
- Einsparung: Verzicht auf eigenes Backend → keine Server-/Ops-Kosten; konsequentes Caching → niedrigere Tile-Kosten;
  modulare Architektur → schnellere Iterationen.

Bei Budgetdruck wird der Projektumfang gezielt über das Product Backlog gesteuert. Zuerst werden optionale
Erweiterungsfeatures mit geringerem unmittelbarem Nutzen für den MVP reduziert oder in spätere Phasen verschoben (z. B.
Nice-to-have-Funktionen in Phase D sowie ausgewählte Komfortfunktionen in Phase F). Demgegenüber gelten
Kernfunktionalität, Stabilität, Datenschutz-Compliance und grundlegende Barrierefreiheit als nicht verhandelbar und
werden auch bei Kostendruck nicht gekürzt. Die Priorisierung im Backlog stellt sicher, dass das verfügbare Budget
konsequent in die wertvollsten Inkremente fließt.
