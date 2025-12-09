# 5 Finanzplanung

Dieses Kapitel schätzt die zu erwartenden Kosten, beschreibt Mechanismen zur Kostenkontrolle und skizziert die geplante
Monetarisierung
für die BlitzerApp. Es beizieht sich dabei auf die Annahmen und Planungen aus den vorherigen Abschnitten.

Die Finanzplanung ist eng mit dem agilen Vorgehen nach Scrum verknüpft. Anstatt die Gesamtkosten einmalig und starr
vorab festzulegen, erfolgt die Freigabe von Mitteln inkrementell entlang der definierten Phasen und Releases. Ergebnisse
aus
abgeschlossenen Sprints und Meilensteinen dienen als Grundlage für fundierte Entscheidungen über die weitere Mittel-
verwendung.

## 5.1 Kostenplanung

Die Kostenplanung der BlitzerApp orientiert sich am hybriden Vorgehensmodell und leitet aus Sprints, FTE-Kapazitäten und
Rollenprofilen klassische Kos-ten­größen wie Personentage und Euro ab. Dabei wird bewusst agil vorgegan-gen: Statt früh
Detailaufwände exakt zu schätzen, dienen die stabilen Sprintka-pazitäten des Kernteams als verlässlicher
Orientierungsrahmen und werden mit der erwarteten Sprintanzahl pro Phase kombiniert. Nach jedem Meilenstein kann anhand
der real erzielten Ergebnisse und des tatsächlichen Ressourcen-verbrauchs geprüft werden, ob Budget und Umfang angepasst
werden müssen.
Ausgangspunkt ist die Ableitung der Sprintkosten aus den FTE-Annahmen und Tagessätzen des Kernteams; darauf baut die
weitere Kostensumme bis zum ersten Release auf.
Dabei werden diese Schätzwerte für die PT-Kosten je Rolle angenommen:

•    (interner) Produkt Owner: 750 € / PT
•    (interner) Entwicklung: 700 € / PT
•    (interner) UX/Design: 650 € / PT
•    (interner) QA/Testing: 600 € / PT
•    (extern) Beratung (Privacy/Compliance): 800 € / PT (punktuell)
•    (intern) Community Management: 500 € / PT (ab Release-Phase)

Die genannten Tagessätze sind als Vollkostenansätze für in Deutschland beschäftigte Fachkräfte zu verstehen. Sie
umfassen neben dem Gehalt auch übliche Arbeitgebernebenkosten (z. B. Sozialabgaben, Versicherungen) sowie ei-nen
pauschalen Anteil für interne Overheads wie Infrastruktur und Verwaltung. Die Werte orientieren sich an branchenüblichen
Tagessätzen für vergleichbare Rollen im Mobile-Umfeld (vgl. Quellenverzeichnis). Für punktuell eingesetzte ex-terne
Beratungen wird ein marktüblicher, erfahrungsgemäß höherer Tagessatz angesetzt, der die spezifische Expertise
widerspiegelt.

Für die Berechnung der Personentage (PT) wird folgende FTE-Logik verwendet:
• 1,0 FTE entspricht ca. 5 PT pro Woche
• 0,5 FTE entspricht ca. 2,5 PT pro Woche

Bei einem zweiwöchigen Sprint ergibt sich daraus eine Kapazität von ca. 10 PT pro Sprint je 1,0 FTE. Auf diesen Annahmen
baut die folgende Kostenplanung auf.

### 5.1.1 Sprintkosten

Aus der FTE-Definition und den Tagessätzen ergeben sich Orientierungsgrößen für die Kosten pro Sprint bei voller
bzw. teilweiser Belegung:

- 1,0 FTE Produkt Owner pro Sprint → ca. 10 PT × 750 €/PT = 7.500 €
- 1,0 FTE Entwicklung pro Sprint → ca. 10 PT × 700 €/PT = 7.000 €
- 1,0 FTE Entwicklung pro Sprint → ca. 10 PT × 700 €/PT = 7.000 €
- 1,0 FTE UX/Design pro Sprint → ca. 10 PT × 650 €/PT = 6.500 €
- 1,0 FTE QA/Testing pro Sprint → ca. 10 PT × 600 €/PT = 6.000 €
  Gesamtkosten pro Sprint: ≈ 34.000 € bei voller Belegung

Ab der Release-Phase (ab M4) wird zusätzlich Community Management eingeplant:

- 0,5 FTE Community Management pro Sprint → ca. 5 PT × 500 €/PT = 2.500 €
  Gesamtkosten pro Sprint ab Release-Phase: ≈ 36.500 € bei voller Belegung

Externe Beratung (Privacy/Compliance) wird nicht als fester Bestandteil der allgemeinen Sprintkosten modelliert,
sondern bewusst als punktueller Posten betrachtet. Für die initiale Entwicklung bis zur Version 1.0 wird ein Bedarf
von insgesamt ca. 4 Personentagen Beratung angenommen. Bei einem Tagessatz von 800 €/PT ergibt dies zusätzliche
Beratungskosten von rund 3.200 € über den gesamten betrachteten Zeitraum.

### 5.1.2 Personenkosten nach Phasen

Die folgende Übersicht fasst die geschätzten Kosten bis zum 1.0 Release je Phase zusammen und leitet diese aus der
Anzahl der Sprints und
der vorher beschriebenen Kosten pro Sprint ab. Sie bildet den größten Block der Gesamtkosten und ist direkt an die in
Kapitel 4 beschriebenen Phasen, Releases und Kapazitäten gekoppelt (vgl. Ressourcenplanung 4.4 und Zeitplan 4.3.1).

Detaillierte PT-Werte pro Rolle werden hier nicht ausgewiesen, sondern sind implizit in den sprintbasierten
Kostenschätzungen enthalten. Die folgende Tabelle zeigt daher pro Phase nur noch die Sprintanzahl und die daraus
abgeleiteten geschätzten Personalkosten.

| Phase                                  | Geschätzte Anzahl Sprints | Kostenansatz (Personalkosten, auf Basis typischer Sprintbelegung) |
|----------------------------------------|---------------------------|-------------------------------------------------------------------|
| Preparation (Grundlagen & Architektur) | 2 Sprint                  | ≈ 2 · 34.000 € + (Berater) 4 · 800 € = 71.200 €                   |
| MVP-Kern (AP-B1–B7)                    | 4–5 Sprints               | ≈ 5 · 34.000 € = 170.000 €                                        |
| AppStore-Release & Qualität            | 2 Sprints                 | ≈ 2 · 36.500 € = 73.000 €                                         |
| Gesamtsumme                            | ≈ 8–9 Sprints             | ≈ 314.200 €                                                       |

Hinweis: Die Preparation-Phase umfasst neben den reinen Entwicklungssprints auch den punktuellen Einsatz externer
Beratung (Privacy/Compliance) mit geschätzten 4 Personentagen.

Für die Erweiterungszyklen nach dem ersten Release (ab M5) werden vorerst mit 2 Sprints kalkuliert und damit würde eine
Erweiterung (Inkrement) ca. 2 · 36.500 € = 73.000 € kosten. Diese Phasen werden inkrementell und auf Basis der
verfügbaren
Mittel geplant. Dabei muss davon ausgegangen werden, dass das Kernteam in diesen Phasen nur noch eingeschränkt
Kapazitäten
für die Weiterentwicklung bereitstellen kann, da es auch für Wartung und Support zuständig ist (DevOps-Aspekte).

### 5.1.3 Sachkosten / Dienste

Ergänzend zum Personenaufwand fallen Sachkosten für Infrastruktur, Geräte und Werkzeuge an. Aufgrund des gewählten
Client-only-Ansatzes und des Einsatzes von Open-Source-Komponenten bleiben diese Kosten im Vergleich zu den
Personalkosten moderat. Die folgende Tabelle basiert auf den in Kapitel 4.4.3 beschriebenen externen Ressourcen und
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

- Unerwartete Verzögerungen (Performance, Geofencing, Store-Review): +10–15 % der Personalkosten ≈ 30.000–45.000 €.
- Wechsel Tile-Provider (falls Limits erreicht oder Konditionen ungünstig): zusätzliche 300–500 €.
- Rechtliche Beratung bei Länderrestriktionen oder geänderten Rahmenbedingungen: +1.500 € (Kontingent).

Die Höhe der Puffer orientiert sich an den in der Risikoanalyse beschriebenen technischen und organisatorischen Risiken
(z. B. Komplexität von Geofencing und Performance-Optimierung, mögliche Store-Review-Verzögerungen). Bei Eintritt
solcher Risiken werden zunächst Umfang und Priorität der Backlog-Items angepasst, bevor zusätzliche Mittel in Anspruch
genommen werden.

Geschätzte Gesamtkosten bis zum Release 1.0 inkl. Puffer: ≈ mind. 350.000 €, max. 370.000 €.

### 5.1.5 Kostentreiber & Einsparpotenziale

Auf Basis der sprintbasierten Kostenlogik (vgl. 5.1.2) und der phasenorientierten Planung (vgl. 4.3.1) lassen sich
klar benennen, welche Faktoren die Gesamtkosten der BlitzerApp besonders stark beeinflussen – und an welchen Stellen
gezielt Einsparungen möglich sind, ohne die Kernziele zu gefährden.

**Kostentreiber:**

- **Anzahl Sprints bei voller Teambelegung:**
    - Jeder zusätzlich geplante Sprint mit nahe voller Belegung der Kernrollen (PO, Dev, UX, QA) verursacht – je nach
      tatsächlicher FTE – einen vierstelligen Mehrbetrag. Bei einem idealtypischen Vollteam (1,0 FTE je Rolle) liegen
      die
      reinen Personalkosten pro Sprint im Bereich von deutlich über 20.000 €.
    - Eine Verlängerung der MVP-Phase um einen weiteren Sprint kann sinnvoll sein, erhöht die Kosten aber unmittelbar.
- **Qualitätssicherung und Release-Vorbereitung:**
    - In der Phase „AppStore-Release & Qualität“ steigen QA-Anteil und Build-/Test-Aktivitäten an; jeder Sprint in
      dieser
      Phase ist kostenintensiv, trägt aber direkt zur Stabilität und Review-Fähigkeit der App bei.
    - Zusätzliche Testrunden oder wiederholte Review-Schleifen in den Stores können weitere Sprints nach sich ziehen.
- **Architektur- und Performance-Themen:**
    - Aufwendige Optimierungen (z. B. Geofencing, Energieprofiling, Caching) binden über mehrere Sprints hinweg
      Entwicklung und QA. Werden sie spät adressiert, steigt das Risiko für Rework und zusätzliche Sprints.
- **Erweiterungszyklen nach Release:**
    - Jeder Erweiterungszyklus (typisch 2 Sprints) mit signifikanter Beteiligung des Kernteams führt zu einem klar
      kalkulierbaren Aufwuchs der Gesamtkosten. Ohne klare Priorisierung können sich diese Zyklen schnell aufsummieren.

**Einsparpotenziale:**

- **Strikter Fokus auf den MVP-Umfang:**
    - Durch eine enge Definition des MVP-Kerns (Kapitel 4.2) und konsequente Priorisierung im Product Backlog lässt sich
      die Anzahl der Sprints bis M3 (MVP funktionsfähig) begrenzen. Optionale Features (z. B. Komfortfunktionen,
      weitergehende Einstellungen) werden bewusst in spätere Erweiterungszyklen verschoben.
- **Bewusster Zuschnitt der Teambelegung pro Sprint:**
    - Rollen wie UX und QA müssen nicht in jeder Phase und in jedem Sprint mit 1,0 FTE eingeplant werden. Insbesondere
      in frühen Architektur- und Setup-Phasen kann eine reduzierte Belegung (z. B. 0,5 FTE) ausreichend sein und die
      Sprintkosten spürbar senken.
    - Ab der Wartungs- und Erweiterungsphase kann die Entwicklungskapazität in einzelnen Sprints bewusst reduziert
      werden, um Budget zu schonen und sich stärker auf Bugfixing und kleine Inkremente zu konzentrieren.
- **Gezielter und begrenzter Einsatz externer Beratung:**
    - Die geplanten 3–4 Personentage für Privacy/Compliance-Beratung (vgl. 5.1.2) werden möglichst gebündelt an
      neuralgischen Punkten eingesetzt (z. B. vor Beta-Release, vor AppStore-Submission), um Mehrfacheinsätze zu
      vermeiden.
    - Weitere rechtliche Klärungen werden – soweit verantwortbar – in spätere Erweiterungszyklen oder in die laufende
      Wartungsphase verschoben.
- **Architekturentscheidungen zugunsten Einfachheit:**
    - Der Verzicht auf ein eigenes Backend und die Konzentration auf einen Client-only-Ansatz mit Overpass/OSM reduziert
      dauerhaft Infrastruktur- und Betriebsaufwände.
    - Eine bewusst einfache erste Ausprägung mancher Features (z. B. Basis-Einstellungen statt komplexer Profile,
      minimalistische Offline-Funktion) senkt die benötigte Anzahl Sprints in den Erweiterungszyklen.
- **Nutzung von Open-Source-Tools und bestehenden Ressourcen:**
    - Der starke Einsatz von Open-Source-Komponenten, vorhandenen Build-Pipelines und günstigen Developer-Plänen
      (z. B. für Tile-Provider, CI/CD) hält die Sachkosten niedrig und vermeidet zusätzliche Sprint-Aufwände für
      Evaluierung und Integration proprietärer Lösungen.

Aus Sicht der Finanzplanung bedeutet dies: Die maßgebliche Stellgröße sind nicht einzelne Tage pro Person, sondern die
Anzahl und Auslastung der Sprints pro Phase. Durch einen klaren MVP-Fokus, eine phasenbewusste Teambelegung und den
gezielten Einsatz von Beratung und Erweiterungszyklen kann der Kostenrahmen (vgl. 5.1.3 und 5.1.5) aktiv gesteuert
werden, ohne die zentralen Qualitäts- und Datenschutzanforderungen der BlitzerApp zu kompromittieren.
