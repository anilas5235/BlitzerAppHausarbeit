# 7 Impactanalyse

Die folgende Impactanalyse untersucht die positiven und negativen Auswirkungen der App im Vergleich zu einem Szenario ohne Veröffentlichung. Es wird dabei davon ausgegangen, dass bereits andere Blitzer- und Navigations-Apps existieren. Daher beziehen sich die genannten Auswirkungen auf den zusätzlichen Effekt der geplanten App. Der Fokus der Untersuchung liegt insbesondere auf der Rolle als datenschutzfreundliche Alternative zu anderen Applikationen und nicht auf eine völlige Einführung des Prinzips "Blitzer-App".
Die Impactanalyse betrachtet die Auswirkungen der App aus ökologischer, sozialer und wirtschaftlicher Perspektive, wobei jede Perspektive getrennt nach dem gleichen Schema untersucht wird. Nach einer kurzen Darstellung der Ausgangslage und Relevanz, in der erläutert wird, weshalb die App in der jeweiligen Perspektive Auswirkungen entfaltet, folgen die positiven Effekte sowie mögliche negative Effekte bzw. Risiken. Dabei werden die Effekte nicht nur benannt, sondern zusätzlich nach Art des Effekts (direkt bedeutet sofort wirksam, indirekt wirkt über Umwege), Zeithorizont sowie Stärke des Effekts eingeordnet. Anschließend werden die betroffenen Stakeholder betrachtet, bevor zum Schluss konkrete Maßnahmen und Empfehlungen abgeleitet werden, um negative Effekte präventiv zu vermeiden und positive Effekte zu verstärken [[1]](https://commission.europa.eu/system/files/2023-09/BRT-2023-Chapter%202-How%20to%20carry%20out%20an%20impact%20assessment_0.pdf?).

---------------------------------------------------------------------------------------

* Es wird davon ausgegangen, dass bereits andere Blitzer- und Navigations-Apps existieren
* Die folgenden Auswirkungen beziehen sich daher auf den zusätzlichen Effekt der geplanten App
* Fokus liegt insbesondere auf der Rolle als datenschutzfreundliche Alternative & nicht auf eine völlige Einführung des Prinzips "Blitzer-App"
* 3 Perspektiven:
  * Ökologische Auswirkungen (Verbrauch, Emissionen, IT-Infrastruktur)
  * Soziale Auswirkungen (Sicherheitsempfinden, Stress, Fairness, Datenschutz)
  * Wirtschaftliche Auswirkungen (Kosten/Nutzen für Nutzer, Betreiber, Staat, Versicherer, andere Anbieter)
* Vorgehen je Dimension:
  * Kurze Ausgangslage & Relevanz
  * Positive Effekte gegenüber dem Status quo
  * Negative Effekte / Risiken
  * Betroffene Stakeholder
  * Maßnahmen & Empfehlungen
* Bewertung:
  * Qualitative Einschätzung, keine exakten Zahlen
  * Stärke der Effekte grob: "gering"/"mittel"/"hoch"
  * Einordnung immer als zusätzlicher Effekt zu existierenden Lösungen, nicht als komplette Neudefinition des Verkehrssystems
  * Quelle: https://commission.europa.eu/system/files/2023-09/BRT-2023-Chapter%202-How%20to%20carry%20out%20an%20impact%20assessment_0.pdf?

## 7.1 Ökologische Auswirkungen

### Ausgangslage & Relevanz

Das Fahrverhalten eines Kraftfahrzeugs steht in engem Zusammenhang mit dem Kraftstoffverbrauch und den daraus resultierenden Emissionen [[2]](https://www.sciencedirect.com/science/article/pii/S2095756424000709). Dabei spielen insbesondere die gefahrene Geschwindigkeit sowie Beschleunigungs- und Bremsvorgänge eine zentrale Rolle. Die Bekanntheit von Blitzerstandorten, die durch die App entstehen kann, kann das Fahrverhalten beeinflussen, etwa durch allgemein schnelleres Fahren außerhalb bekannter Kontrollbereiche. Zudem verursachen digitale Dienste wie Apps und die zugrunde liegende Serverinfrastruktur ebenfalls Energieverbrauch, der im Vergleich zu fahrbedingten Effekten jedoch als geringer einzustufen ist. Aus diesen Gründen ist ein Blick auf ökologische Auswirkungen der App begründet und notwendig.

---------------------------------------------------------------------------------------

* Fahrverhalten (insbesondere gefahrene Geschwindigkeit & Beschleunigungs-/Bremsverhalten) hängen mit Kraftstoffverbrauch & damit mit Emissionen zusammen
* Bekanntheit der Standorte von Blitzer beeinflussen das Fahrverhalten (z.B. allgemein schnelleres Fahren)
* Digitale Dienste wie Apps und Serverinfrastruktur verursachen ebenfalls Energieverbrauch (eher geringere Auswirkungen)

### Positive Auswirkungen

Durch frühzeitige Hinweise auf Blitzer und Limitwechsel kann das Fahrverhalten gleichmäßiger werden, da abruptes Beschleunigen und Abbremsen reduziert wird. Dies kann indirekt zu einem geringeren Kraftstoffverbrauch führen und entfaltet seine Wirkung mittel- bis langfristig. Die Stärke des Effekts ist jedoch insgesamt als gering einzustufen, da die App keinen direkten Eingriff in das Fahrverhalten vornimmt und die Wirkung situationsabhängig sowie nutzerabhängig ist.
Zudem können bekannte Blitzerstandorte dazu beitragen, dass Fahrer im jeweiligen Umfeld vorsichtiger fahren und niedrigere Durchschnittsgeschwindigkeiten einhalten. Auch dieser Effekt wirkt indirekt auf die Emissionen und tritt eher kurzfristig und wiederkehrend auf. In seiner Stärke ist er ebenfalls als gering zu bewerten, da sich das angepasste Fahrverhalten meist nur auf das unmittelbare Blitzerumfeld beschränkt und mit rund 4800 installierten Blitzern [[3]](https://www.blitzer.de/land/blitzer-in-Deutschland) nur ein begrenzter Teil des Straßennetzes abgedeckt wird.
Darüber hinaus verzichtet die App auf eine eigene Server-Backend-Infrastruktur und nutzt bestehende offene Schnittstellen. Dadurch fällt der zusätzliche Energiebedarf geringer aus als bei vergleichbaren Anwendungen mit eigener Backend-Infrastruktur [[4]](https://interactdc.com/static/images/documents/JRC135926_01.pdf). Dieser indirekte Effekt wirkt langfristig, ist jedoch von geringer Stärke, da der absolute Energieverbrauch der App sehr niedrig ist und lediglich aus einzelnen API-Abfragen sowie geringem Datenverkehr besteht, was keinen relevanten zusätzlichen Stromverbrauch verursacht.
Insgesamt sind aus ökologischer Sicht vor allem das Fahrverhalten und die gefahrenen Kilometer relevant, während der IT-bedingte Energieverbrauch eine nachgeordnete Rolle spielt.

---------------------------------------------------------------------------------------

<img width="1377" height="243" alt="image" src="https://github.com/user-attachments/assets/2f68fb28-72a2-44fc-b0da-0fa036414d12" />
Quelle für "Rechenzentren & Netze brauchen viel Strom": https://interactdc.com/static/images/documents/JRC135926_01.pdf
Quelle für "Höheres Tempo = Mehr Emissionen": https://www.sciencedirect.com/science/article/pii/S2095756424000709

### Negative Auswirkungen / Risiken

Ein möglicher negativer Effekt der App besteht darin, dass sich Nutzer durch die Nutzung der Anwendung subjektiv "abgesichert" fühlen und außerhalb bekannter Blitzerzonen tendenziell schneller fahren. Dieses Verhalten kann dazu führen, dass die genannten positiven Effekte innerhalb von Blitzerumfeldern teilweise ausgeglichen oder sogar überkompensiert werden, wodurch sich der durchschnittliche Kraftstoffverbrauch erhöhren kann. Dieser Effekt wirkt indirekt, entwickelt sich mittel- bis langfristig durch Fahrgewohnheiten und ist in seiner Stärke als gering einzustufen, da er nur einen Teil der Nutzer betrifft, nur in bestimmten Bereichen auftritt und stark vom individuellen Fahrverhalten abhängt.
Darüber hinaus kann die dauerhafte Standortbestimmung der App, kombiniert mit Hintergrundprozessen und wiederkehrenden Abfragen, zu einem erhöhten Energiebedarf der Smartphones führen, auf denen die App läuft. Infolgedessen müssen Geräte häufiger geladen werden, was den Stromverbrauch geringfügig erhöht. Dieser Effekt ist direkter Natur, wirkt kurzfristig während der Nutzung, kann sich jedoch bei regelmäßiger Verwendung langfristig kumulieren, bleibt insgesamt aber von geringer Stärke, da der zusätzliche Energiebedarf einzelner Ladevorgänge gering ist und im Verhältnis zum normalen Geräteverbrauch kaum ins Gewicht fällt.
Zusätzlich erzeugen regelmäßige Abfragen externer Schnittstellen einen erhöhten Datenverkehr sowie zusätzlichen Rechenaufwand in Mobilfunknetzen und Rechenzentren. Dadurch steigt der Energiebedarf der IT-Infrastruktur geringfügig an. Dieser Effekt wirkt indirekt, entfaltet seine Wirkung langfristig und ist jedoch ebenfalls als gering einzustufen.
Schließlich kann es vereinzelt zu zusätzlichen Fahrkilometern kommen, etwa wenn Nutzer aus Neugier oder zu Testzwecken gezielt Strecken mit bekannten Blitzern abfahren. Diese Test- oder "Spielfahrten" verursachen unmittelbar zusätzliche Emissionen, obwohl sie keinen verkehrlichen Zweck erfüllen. Der Effekt wirkt indirekt, ist punktuell und situationsabhängig und wird in seiner Stärke als sehr gering bewertet.

---------------------------------------------------------------------------------------

<img width="1373" height="390" alt="image" src="https://github.com/user-attachments/assets/3b622b78-cc00-401f-af1c-c637d7ccf843" />
Quelle für "Höheres Tempo = Mehr Emissionen": https://www.sciencedirect.com/science/article/pii/S2095756424000709

### Betroffene Stakeholder

Von den ökologischen Auswirkungen der App sind mehrere Stakeholder betroffen. Dazu zählen in erster Linie die Nutzer der App, deren Fahrverhalten den Kraftstoffverbrauch sowie die damit verbundenen Emissionen beeinflusst. Darüber hinaus ist die Umwelt bzw. die Allgemeinheit betroffen, etwa durch Veränderungen der Luftqualität, der CO₂-Emissionen und der Lärmbelastung. Auf technischer Ebene sind außerdem Betreiber von IT-Infrastruktur betroffen, da zusätzlicher Datenverkehr in Rechenzentren und Mobilfunknetzen Energie erfordert. Schließlich betreffen die Auswirkungen auch Community-basierte Datenplattformen wie OpenStreetMap, deren Betrieb und Pflege mit einem zusätzlichen Ressourcen- und Energieaufwand verbunden sind.

---------------------------------------------------------------------------------------

* Nutzer der App
  * Fahrverhalten (Geschwindigkeit, Bremsen/Beschleunigen) beeinflusst Verbrauch & Emissionen
  * Ladeverhalten der Geräte (häufigeres Laden durch App-Nutzung)
* Umwelt / Allgemeinheit
  * Luftqualität, CO₂-Emissionen und Lärmbelastung durch Fahrverhalten
  * Ressourcenverbrauch durch zusätzliche oder eingesparte Fahrkilometer
* Betreiber von IT-Infrastruktur
  * Rechenzentren & Netzbetreiber, die den zusätzlichen Datenverkehr (API-Abfragen, Mobilfunkdaten) verarbeiten müssen & dafür Energie einsetzen
* Community & Datenplattformen (z. B. OSM)
  * Aufwand für Pflege & Betrieb der offenen Dienste mit Energie- und Ressourcenverbrauch der dahinterliegenden Server

### Maßnahmen & Empfehlungen

Zur Reduktion negativer ökologischer Effekte und zur gezielten Verstärkung positiver Wirkungen gibt es sowohl technische als auch verhaltensbezogene Maßnahmen. Auf technischer Ebene liegt der Fokus auf einer energieeffizienten Umsetzung der App, insbesondere durch eine ressourcenschonende Standortnutzung, einen sparsamen Umgang mit externen Schnittstellen sowie eine energiearme Gestaltung der Benutzeroberfläche. Ergänzend dazu können verhaltensbezogene Empfehlungen für Nutzer sinnvoll sein, um Fehlanreize wie unnötige "Testfahrten" zu vermeiden und ein sicheres effizientes Fahrverhalten zu fördern. Darüber hinaus ist ein bewusster Umgang mit möglichen Rebound- und Fehlanreizen erforderlich, was durch eine klare und transparente Kommunikation der Funktionsgrenzen der App erreicht werden kann.

---------------------------------------------------------------------------------------

* Technische Maßnahmen in der App
  * Energiesparende Standortnutzung
    * Verwendung von Geofencing und sinnvollen Update-Intervallen statt dauerndem Live-GPS
    * Optionaler „Energiespar-Modus“ in den Einstellungen (z. B. seltener aktualisieren, nur bei Bewegung)
  * Schonender Umgang mit externen Schnittstellen
    * Caching von Daten, damit Abfragen an Overpass & Co. nicht unnötig oft ausgeführt werden.
    * Aktualisierungsintervalle so wählen, dass sie praxisnah sind, aber keine Dauerlast erzeugen
  * Ressourcenschonende UI
    * Keine dauerhaft extrem hellen Vollflächen oder unnötige Animationen
* Verhaltensbezogene Empfehlungen für Nutzer
  * Hinweise gegen „Testfahrten“
    * In Onboarding oder Hilfe klarstellen, dass die App den Alltag unterstützen & nicht zu Extra-Fahrten anregen soll
  * Kommunikation von Zielbild "effizient & sicher"
    * In Texten & Hinweisen betonen, dass gleichmäßiges & vorausschauendes Fahren das ist Ziel und nicht das schnellere Fahren in blitzerfreien Bereichen
* Umgang mit Rebound- & Fehlanreizen
  * Formulierung der Warnungen
    * Warntexte so gestalten, dass sie an Einhaltung der Geschwindigkeit erinnern
  * Transparent machen, dass nicht alle Kontrollen erfasst sind → kein „Sicherheitsgefühl“, das zu noch riskanterem Verhalten führen könnte
