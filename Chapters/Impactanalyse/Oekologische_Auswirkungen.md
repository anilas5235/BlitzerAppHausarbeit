# 7 Impactanalyse

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

## 7.1 Ökologische Auswirkungen

### Ausgangslage & Relevanz
* Fahrverhalten (insbesondere gefahrene Geschwindigkeit & Beschleunigungs-/Bremsverhalten) hängen mit Kraftstoffverbrauch & damit mit Emissionen zusammen
* Bekanntheit der Standorte von Blitzer beeinflussen das Fahrverhalten (z.B. allgemein schnelleres Fahren)
* Digitale Dienste wie Apps und Serverinfrastruktur verursachen ebenfalls Energieverbrauch (eher geringere Auswirkungen)

### Positive Auswirkungen
<img width="1377" height="243" alt="image" src="https://github.com/user-attachments/assets/2f68fb28-72a2-44fc-b0da-0fa036414d12" />


### Negative Auswirkungen / Risiken
<img width="1373" height="390" alt="image" src="https://github.com/user-attachments/assets/3b622b78-cc00-401f-af1c-c637d7ccf843" />


### Betroffene Stakeholder
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
