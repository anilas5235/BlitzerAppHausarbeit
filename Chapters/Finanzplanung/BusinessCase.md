# 5.3 Business Case

Der Business Case begründet die Notwendigkeit und Wirtschaftlichkeit des Projekts „Blitzer-App“. Er analysiert Kosten,
Nutzen und Risiken, um eine fundierte Entscheidungsgrundlage für die Durchführung zu schaffen.

### 5.3.1 Management Summary

Das Projekt zielt auf die Entwicklung einer mobilen App, die Autofahrer in Echtzeit vor Geschwindigkeitskontrollen
warnt. Trotz eines etablierten Marktes besteht eine Lücke für eine datenschutzfreundliche, zuverlässige und
nutzerzentrierte Anwendung, wie in der Marktanalyse festgestellt wurde. Die App wird als Einmalkauf für 4,99 €
angeboten. Die geschätzten Entwicklungskosten bis zum Release belaufen sich auf ca. 350.000 €. Auf Basis einer
Szenario-Betrachtung (Worst-, Realistic- und Best-Case) zeigt die Umsatzprognose, dass im Worst-Case die
Entwicklungskosten in den ersten drei Jahren nicht vollständig gedeckt werden, im realistischen Szenario die
Gewinnschwelle innerhalb dieses Zeitraums nur unter günstigen Annahmen erreichbar ist und im Best-Case ein deutlicher
Überschuss erzielt werden kann.

Gleichzeitig weist der Business Case auf ein unausgewogenes Chancen-Risiko-Profil hin: Die hohe Anfangsinvestition, die
späte und unsichere Amortisation, erhebliche rechtliche Unsicherheiten (bis hin zu möglichen Verboten und
App-Store-Restriktionen) sowie kritische Abhängigkeiten von externen Plattformen und Datenquellen (OpenStreetMap,
Overpass-API, Apple/Google App Stores) stellen wesentliche Risiken dar. Zusätzlich steht mit Blick auf die
organisatorische Ebene kein reales, eingespieltes Umsetzungsteam zur Verfügung, das ein solches Produkt langfristig
entwickeln, betreiben und rechtlich absichern könnte – die Ressourcenplanung bleibt damit hypothetisch.

Aus Sicht eines risikoaversen Unternehmens bzw. Investors wird die Umsetzung des Projekts in der dargestellten Form
nicht empfohlen.

### 5.3.2 Problemstellung und strategische Ausrichtung

**Problemstellung:** Autofahrer sehen sich mit steigenden Bußgeldern und einer hohen Dichte an
Geschwindigkeitskontrollen konfrontiert. Bestehende Blitzer-Apps sind oft unzuverlässig, datenschutzrechtlich bedenklich
oder bieten eine unzureichende User Experience (vgl. Marktanalyse). Es fehlt eine transparente, auf die Privatsphäre der
Nutzer bedachte Alternative.

**Strategische Ausrichtung:** Aus strategischer Sicht soll die App einen Beitrag zu sichererem und regelkonformem Fahren
leisten, indem sie Fahrende frühzeitig auf bekannte stationäre Blitzer und relevante Geschwindigkeitswechsel hinweist.
Gleichzeitig verfolgt das Konzept das Ziel, eine plattformübergreifende, schlanke Lösung ohne eigenes zentrales Backend
zu realisieren, die datenschutzfreundlich arbeitet, offene Geodaten (z. B. OpenStreetMap/Overpass) nutzt und bewusst auf
eine eigene Live-Meldeinfrastruktur verzichtet (vgl. Zielsetzung 1.2).

Diese strategische Ausrichtung steht jedoch in einem Spannungsfeld zu den wirtschaftlichen und rechtlichen Rahmen-
bedingungen: Das Produkt bewegt sich in einem rechtlich sensiblen Umfeld, ist stark von externen Datenquellen und
Plattformrichtlinien abhängig und erfordert trotz schlanker Architektur einen erheblichen Kapitalbedarf für Entwicklung,
Betrieb und Vermarktung. Hinzu kommt, dass in der aktuellen Konstellation kein reales, eingespieltes Umsetzungsteam zur
Verfügung steht, das diese Strategie organisatorisch tragfähig umsetzen und langfristig verantworten könnte. In der
Gesamtschau relativiert dies die strategische Attraktivität des Projekts deutlich; ähnliche Ziele (z. B. Datenschutz,
Nutzung offener Daten, alltagstaugliche UX) könnten mit weniger kapitalintensiven und rechtlich weniger riskanten
Softwareprojekten verfolgt werden.

### 5.3.3 Machbarkeitsstudie (Feasibility Study)

Die Machbarkeit des Projekts wurde anhand technischer, wirtschaftlicher und organisatorischer Kriterien geprüft.

* **Technische Machbarkeit:** Die App basiert auf einer reinen Client-Architektur und nutzt etablierte Technologien wie
  Flutter sowie offene Datenquellen (OpenStreetMap). Der technische Ansatz ist im Produktplan detailliert und validiert.
  Technische Risiken wie die Komplexität des Geofencing werden durch frühe Prototypen adressiert (vgl. Risikoanalyse).
  Gleichzeitig besteht eine starke Abhängigkeit von externen Diensten wie der Overpass-API, den OpenStreetMap-Daten
  sowie den Richtlinien der App-Stores. Änderungen an Nutzungsbedingungen, technischen Schnittstellen oder
  Geschäftsmodellen dieser Anbieter können das Produkt in seiner Kernfunktionalität erheblich einschränken.
* **Wirtschaftliche Machbarkeit:** Die Finanzierung der initialen Entwicklungskosten stellt die größte Hürde dar und
  erfordert externe Investoren oder Eigenkapital. Die Umsatzprognose zeigt zwar in einem Realistic- und Best-Case-Szenario
  eine Perspektive zur Erreichung der Gewinnschwelle, diese ist jedoch stark von ambitionierten Annahmen abhängig
  (z. B. Sichtbarkeit im App-Store, hohe Nutzerbewertungen, stabile Rechtslage). Der Kapitalwert (NPV) ist über einen
  3-Jahres-Zeitraum bei einem Diskontierungszinssatz von 10 % voraussichtlich negativ und spiegelt die hohe
  Anfangsinvestition sowie die späte Amortisation wider.
* **Organisatorische Machbarkeit:** In der Theorie wird ein Kernteam mit den notwendigen Skills in der App-Entwicklung
  und im Projektmanagement beschrieben. Faktisch steht jedoch kein eingespieltes, dauerhaft verfügbares Team zur
  Verfügung, das die Entwicklung, rechtliche Absicherung, Vermarktung und den langfristigen Betrieb verantworten kann.
  Dies reduziert die organisatorische Machbarkeit erheblich.

Insgesamt ist das Projekt aus technischer Sicht grundsätzlich umsetzbar. Unter Berücksichtigung der wirtschaftlichen,
rechtlichen und organisatorischen Unsicherheiten ist die Machbarkeit jedoch nur eingeschränkt empfehlenswert.

### 5.3.4 Kosten-Nutzen-Analyse

**Finanzierungsbedarf (Kosten):**
Die Gesamtkosten für die Entwicklung bis zum Release (Version 1.0) werden auf Basis der Kostenplanung geschätzt. Sie
umfassen 9 Sprints (2 Prep + 5 MVP + 2 Release) à ca. 34.000 € sowie ca. 4.000 € für externe Beratung und einen
Risikopuffer.

* **Gesamtkosten (bis Release 1.0):** 9 * 34.000 € + 4.000 € + 40.000 € (Puffer) = **350.000 €** (siehe Kostenplanung 5.1)

Dieser Betrag muss vollständig vorfinanziert werden, bevor gesicherte Umsätze existieren. Laufende Kosten für Wartung,
Weiterentwicklung, Infrastruktur, Marketing und die Anpassung an rechtliche Rahmenbedingungen sind darin nur teilweise
berücksichtigt und erhöhen die tatsächliche Kapitalbindung zusätzlich.

**Nutzen (Umsatzprognose):**
Der Umsatz wird durch einen Einmalkaufpreis von 4,99 € generiert. Die Absatzprognose basiert auf den Daten der
Marktanalyse, berücksichtigt aber eine konservative Markteintrittsphase für ein neues Produkt.

* **Annahmen:**
    * Preis pro Einheit: 4,99 €
    * Plattformgebühr (Apple/Google): ca. 30%
    * Nettoerlös pro Einheit: ca. 3,50 €

Zur besseren Einordnung werden drei Szenarien betrachtet:

1. **Worst-Case-Szenario (sehr zurückhaltende Adoption):**
    * Jahr 1: 10.000 Verkäufe → **35.000 €** Umsatz
    * Jahr 2: 25.000 Verkäufe → **87.500 €** Umsatz
    * Jahr 3: 50.000 Verkäufe → **175.000 €** Umsatz
    * **Summe 3 Jahre:** 297.500 €

2. **Realistic-Case-Szenario (moderate, aber erfolgreiche Etablierung):**
    * Jahr 1: 20.000 Verkäufe → **70.000 €** Umsatz
    * Jahr 2: 40.000 Verkäufe → **140.000 €** Umsatz
    * Jahr 3: 60.000 Verkäufe → **210.000 €** Umsatz
    * **Summe 3 Jahre:** 420.000 €

3. **Best-Case-Szenario (sehr erfolgreiche Marktetablierung):**
    * Jahr 1: 30.000 Verkäufe → **105.000 €** Umsatz
    * Jahr 2: 60.000 Verkäufe → **210.000 €** Umsatz
    * Jahr 3: 100.000 Verkäufe → **350.000 €** Umsatz
    * **Summe 3 Jahre:** 665.000 €

Im Worst-Case-Szenario summieren sich die Gesamtumsätze über die ersten drei Jahre damit auf rund 297.500 € und liegen
unter den initialen Entwicklungskosten von 350.000 €. Im realistischen Szenario wird die Gewinnschwelle innerhalb der
ersten drei Jahre nur unter günstigen Rahmenbedingungen überschritten, während im Best-Case-Szenario ein deutlicher
Überschuss möglich ist.

Die Szenariobetrachtung verdeutlicht, dass bereits moderate Abweichungen von den Annahmen (z. B. geringere Sichtbarkeit
im App-Store, restriktivere Rechtslage, stärkere Konkurrenz) schnell dazu führen können, dass das Projekt im Bereich des
Worst-Case-Szenarios landet. Dieses Szenario ist angesichts der identifizierten Markt- und Rechtsrisiken nicht rein
theoretisch, sondern als realistische Downside-Variante zu betrachten. Der Realistic-Case setzt eine Reihe ambitionierter
Voraussetzungen voraus (stabile Rechtslage, wirksames Marketing, überwiegend sehr gute Bewertungen), während der
Best-Case nur unter kumulativ günstigen Bedingungen erreichbar ist.

**Finanzkennzahlen:**

* **Return on Investment (ROI):** Der ROI wird im günstigen Fall im Laufe des dritten Jahres positiv, nachdem die
  kumulierten Umsätze die initialen Entwicklungskosten übersteigen. Der erwartete ROI bleibt jedoch aufgrund des hohen
  Kapitaleinsatzes und der Risiken in den ersten Jahren gering.
* **Net Present Value (NPV):** Bei einem angenommenen Diskontierungszinssatz von 10% wird der NPV über einen
  3-Jahres-Zeitraum voraussichtlich negativ sein, was die hohe Anfangsinvestition und die unsichere Amortisation
  widerspiegelt.
* **Payback Period (Amortisationszeit):** Die Investition wird sich unter optimistischen Annahmen voraussichtlich
  innerhalb von **3 bis 4 Jahren** amortisieren. Angesichts der erheblichen rechtlichen und technologischen
  Unsicherheiten erscheint diese Amortisationsdauer aus Sicht risikoaverser Investoren als zu lang.

Aus Sicht risikoaverser Kapitalgeber ist der Business Case aufgrund des hohen Vorab-Investments, der späten und
unsicheren Amortisation sowie des negativen Kapitalwerts wenig überzeugend.

### 5.3.5 Risikobewertung

Die Risikoanalyse hat mehrere hoch bewertete Risiken identifiziert. Die wichtigsten sind:

1. **Regulatorische Risiken:** Verbote in bestimmten Ländern sowie eine heterogene Rechtslage in den Zielmärkten.
   Zusätzlich besteht das Risiko, dass die App aufgrund von Policy-Änderungen in den App-Stores von Apple oder Google
   abgelehnt oder nachträglich entfernt wird. Haftungs- und Bußgeldrisiken können Betreiber und Nutzer betreffen. Die in
   Kapitel „Rechtliches & Compliance“ beschriebenen Maßnahmen (z. B. Disclaimer) reduzieren diese Risiken nur begrenzt;
   eine vollständige Rechtssicherheit ist nicht erreichbar und kann das Geschäftsmodell im Extremfall vollständig
   in Frage stellen.
2. **Technische Abhängigkeiten:** Ausfall oder Einschränkungen der Overpass-API sowie Änderungen an den
   OpenStreetMap-Daten oder den App-Store-Richtlinien. Caching und Fallback-Systeme können die Auswirkungen zwar
   abmildern, die strukturelle Abhängigkeit von externen Anbietern bleibt jedoch bestehen.
3. **Marktrisiko:** Fehlende Akzeptanz und unzureichende Verkaufszahlen in einem kompetitiven Umfeld. Dazu kommen
   potenzielle rechtliche Einschränkungen, die die potenzielle Nutzerbasis zusätzlich verkleinern.

Eine detaillierte Maßnahmenplanung (vgl. Kapitel 6 Risikoanalyse) ist vorhanden, um diese Risiken zu mitigieren. Trotz
geplanter Gegenmaßnahmen verbleiben wesentliche, teils nicht kontrollierbare Restrisiken, die den Business Case aus
Investorensicht deutlich schwächen.

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

Die genannten Kennzahlen dienen nicht nur der Erfolgsmessung, sondern auch als kritische Frühwarnindikatoren. Bereits
moderate Unterschreitungen – etwa geringere Downloadzahlen, schlechtere App-Store-Bewertungen oder niedrigere Conversion
Rates – würden die Umsatzprognosen deutlich verfehlen und den ohnehin knappen Wirtschaftlichkeitsrahmen weiter unter
Druck setzen. Angesichts der beschriebenen Markt- und Rechtsrisiken ist eine solche Abweichung keineswegs
unwahrscheinlich.

### 5.3.7 Fazit und Empfehlung

Der Business Case zeigt, dass das Projekt „Blitzer-App“ zwar auf einen realen Bedarf im Markt trifft und grundsätzlich
technisch umsetzbar ist, die wirtschaftliche, rechtliche und organisatorische Bewertung jedoch kritisch ausfällt. Die
hohe Anfangsinvestition von rund 350.000 €, der voraussichtlich negative Kapitalwert über den betrachteten Zeitraum, die
späte und unsichere Amortisation sowie die starke Abhängigkeit von externen Plattformen, Datenquellen und einer
heterogenen Rechtslage führen zu einem unausgewogenen Chancen-Risiko-Profil. Hinzu kommt, dass aktuell kein reales
Umsetzungsteam existiert, das die Entwicklung, Vermarktung, rechtliche Absicherung und den langfristigen Betrieb
verlässlich übernehmen könnte.

Regulatorische Eingriffe (z. B. Verbote oder Einschränkungen in wichtigen Märkten, Änderungen der App-Store-Policies)
und technische Abhängigkeiten (Overpass-API, OpenStreetMap, App-Stores) können das Geschäftsmodell auch nach
erfolgreichem Marktstart erheblich beeinträchtigen oder vollständig verhindern. Die mit dem Projekt verbundenen Lern- und
Kompetenzgewinne sind zwar strategisch wertvoll, rechtfertigen jedoch aus betriebswirtschaftlicher Sicht nicht das
finanzielle und rechtliche Risiko in dieser Konfiguration.

**Empfehlung:** Unter Abwägung von Kapitalbedarf, rechtlichen Unsicherheiten, kritischen externen Abhängigkeiten,
organisatorischen Einschränkungen (fehlendes reales Umsetzungsteam) und der unsicheren Amortisation wird die Umsetzung
des Projekts in der dargestellten Form aus Sicht eines risikoaversen Investors bzw. Unternehmens nicht empfohlen.

Dieses Fazit bezieht sich speziell auf die wirtschaftliche, rechtliche und organisatorische Bewertung des Projekts im
Rahmen der Finanzplanung. Eine übergreifende Bewertung des Projekts sowie mögliche alternative Nutzungsformen der
gewonnenen Erkenntnisse (z. B. Anpassung des Geschäftsmodells oder Fokussierung auf weniger risikobehaftete
Softwareprodukte) erfolgt in Kapitel 10 (Fazit und Ausblick).
