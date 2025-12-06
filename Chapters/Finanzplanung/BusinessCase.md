# 5.3 Business Case

Der Business Case begründet die Notwendigkeit und Wirtschaftlichkeit des Projekts „Blitzer-App“. Er analysiert Kosten,
Nutzen und Risiken, um eine fundierte Entscheidungsgrundlage für die Durchführung zu schaffen.

### 5.3.1 Management Summary

Das Projekt zielt auf die Entwicklung einer mobilen App, die Autofahrer in Echtzeit vor Geschwindigkeitskontrollen
warnt. Trotz eines etablierten Marktes besteht eine Lücke für eine datenschutzfreundliche, zuverlässige und
nutzerzentrierte Anwendung, wie in der Marktanalyse festgestellt wurde. Die App wird als Einmalkauf für 4,99 €
angeboten. Die geschätzten Entwicklungskosten bis zum Release belaufen sich auf ca. 310.000 €. Basierend auf
konservativen Absatzprognosen, die davon ausgehen, dass die App zunächst nur einen sehr kleinen Teil des bestehenden
Blitzer-App-Markts erreicht, wird ein positiver Return on Investment (ROI) im dritten Jahr erwartet. Das Projekt steht
im Einklang mit dem Ziel des Teams, praktische Erfahrung in der App-Entwicklung zu sammeln und ein marktfähiges Produkt
zu schaffen. Die Durchführung des Projekts wird empfohlen.

### 5.3.2 Problemstellung und strategische Ausrichtung

**Problemstellung:** Autofahrer sehen sich mit steigenden Bußgeldern und einer hohen Dichte an
Geschwindigkeitskontrollen konfrontiert. Bestehende Blitzer-Apps sind oft unzuverlässig, datenschutzrechtlich bedenklich
oder bieten eine unzureichende User Experience (vgl. Marktanalyse). Es fehlt eine transparente, auf die Privatsphäre der
Nutzer bedachte Alternative.

**Strategische Ausrichtung:** Das Projekt dient dem strategischen Ziel des Teams, Kompetenzen in der gesamten
Wertschöpfungskette der Softwareentwicklung aufzubauen – von der Konzeption über die agile Entwicklung (Planungsvorgehen)
bis hin zur Vermarktung und Wartung. Es positioniert das Team als fähig, komplexe, nutzerorientierte Produkte zu liefern.

### 5.3.3 Machbarkeitsstudie (Feasibility Study)

Die Machbarkeit des Projekts wurde anhand technischer, wirtschaftlicher und organisatorischer Kriterien geprüft.

* **Technische Machbarkeit:** Die App basiert auf einer reinen Client-Architektur und nutzt etablierte Technologien wie
  Flutter sowie offene Datenquellen (OpenStreetMap). Der technische Ansatz ist im Produktplan detailliert und validiert.
  Technische Risiken wie die Komplexität des Geofencing werden durch frühe Prototypen adressiert (vgl. Risikoanalyse).
* **Wirtschaftliche Machbarkeit:** Die Finanzierung der initialen Entwicklungskosten stellt die größte Hürde dar und
  erfordert externe Investoren oder Eigenkapital. Die Umsatzprognose zeigt jedoch eine klare Perspektive zur Erreichung
  der Gewinnschwelle.
* **Organisatorische Machbarkeit:** Das Kernteam verfügt über die notwendigen Skills in der App-Entwicklung und im
  Projektmanagement, wie in der Ressourcenplanung dargelegt.

### 5.3.4 Kosten-Nutzen-Analyse

**Finanzierungsbedarf (Kosten):**
Die Gesamtkosten für die Entwicklung bis zum Release (Version 1.0) werden auf Basis der Kostenplanung geschätzt. Sie
umfassen 9 Sprints (2 Prep + 5 MVP + 2 Release) à ca. 34.000 € sowie ca. 4.000 € für externe Beratung.

* **Gesamtkosten (bis Release 1.0):** 9 * 34.000 € + 4.000 € = **310.000 €**

**Nutzen (Umsatzprognose):**
Der Umsatz wird durch einen Einmalkaufpreis von 4,99 € generiert. Die Absatzprognose basiert auf den Daten der
Marktanalyse, berücksichtigt aber eine konservative Markteintrittsphase für ein neues Produkt.

* **Annahmen:**
    * Preis pro Einheit: 4,99 €
    * Plattformgebühr (Apple/Google): ca. 30%
    * Nettoerlös pro Einheit: ca. 3,50 €
* **Absatzprognose:**
    * Jahr 1: 10.000 Verkäufe -> **35.000 €** Umsatz
    * Jahr 2: 25.000 Verkäufe -> **87.500 €** Umsatz
    * Jahr 3: 50.000 Verkäufe -> **175.000 €** Umsatz

Über die ersten drei Jahre summieren sich die Gesamtumsätze damit auf rund 297.500 € und liegen knapp unter den
initialen Entwicklungskosten. Ab dem vierten Jahr wird bei vergleichbarer Absatzentwicklung die Gewinnschwelle
voraussichtlich überschritten.

**Finanzkennzahlen:**

* **Return on Investment (ROI):** Der ROI wird positiv im Laufe des dritten Jahres, nachdem die kumulierten Umsätze die
  initialen Entwicklungskosten übersteigen.
* **Net Present Value (NPV):** Bei einem angenommenen Diskontierungszinssatz von 10% wird der NPV über einen
  3-Jahres-Zeitraum voraussichtlich negativ sein, was die hohe Anfangsinvestition widerspiegelt. Er nähert sich jedoch
  der Gewinnschwelle.
* **Payback Period (Amortisationszeit):** Die Investition wird sich voraussichtlich innerhalb von **3 bis 4 Jahren**
  amortisieren, abhängig von der tatsächlichen Marktakzeptanz und dem Marketingerfolg.

### 5.3.5 Risikobewertung

Die Risikoanalyse hat mehrere hoch bewertete Risiken identifiziert. Die wichtigsten sind:

1. **Regulatorische Risiken:** Verbote in bestimmten Ländern. (Maßnahme: rechtliche Disclaimer).
2. **Technische Abhängigkeiten:** Ausfall der Overpass-API. (Maßnahme: Caching, Fallback-Systeme).
3. **Marktrisiko:** Fehlende Akzeptanz und unzureichende Verkaufszahlen. (Maßnahme: Gezieltes Marketing, hohe
   Produktqualität, Beta-Tests).

Eine detaillierte Maßnahmenplanung (vgl. Kapitel 6 Risikoanalyse) ist vorhanden, um diese Risiken zu mitigieren.

### 5.3.6 Key Performance Indicators (KPIs) zur Erfolgsmessung

* **Finanziell:**
    * `Verkaufseinheiten pro Monat`
    * `Umsatz pro Monat`
* **Produkt & Qualität:**
    * `App-Store-Bewertung` (Ziel: > 4,5 Sterne)
    * `Nutzer-Retentionsrate` (30-Tage)
    * `Absturzrate` (Ziel: < 0,1%)
* **Marketing:**
    * `Conversion Rate` (App-Store-Seitenaufrufe zu Downloads)

### 5.3.7 Fazit und Empfehlung

Der Business Case zeigt, dass das Projekt trotz hoher Anfangsinvestition und signifikanter Risiken eine klare
wirtschaftliche Perspektive bietet. Die strategischen Vorteile durch den Kompetenzaufbau im Team sind ebenfalls hoch zu
bewerten. Die konservative Planung und die identifizierten Gegenmaßnahmen für Risiken schaffen eine solide Grundlage für
den Projekterfolg.

Dieses Fazit bezieht sich speziell auf die wirtschaftliche und strategische Bewertung des Projekts im Rahmen der
Finanzplanung. Eine übergreifende Bewertung des Projekts erfolgt in Kapitel 10 (Fazit und Ausblick).

**Empfehlung:** Die Durchführung des Projekts wird empfohlen, vorausgesetzt, die Finanzierung der initialen
Entwicklungskosten in Höhe von ca. 310.000 € kann sichergestellt werden.
