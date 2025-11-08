# 1 Einleitung

## 1.1 Hintergrund
Der Straßenverkehr steht in vielen Regionen vor der Herausforderung, Sicherheit, Verkehrsfluss und Gesetzeskonformität miteinander zu vereinen. Geschwindigkeitsbegrenzungen dienen der Unfallprävention sowie dem Lärmschutz und Umweltaspekten. Dennoch kommt es häufig zu Überschreitungen – teils unbeabsichtigt durch mangelnde Aufmerksamkeit, teils durch fehlende Transparenz über wechselnde Limits. Stationäre Geschwindigkeitsüberwachungsanlagen (umgangssprachlich „Blitzer“) sind ein etabliertes Mittel zur Durchsetzung lokaler Grenzwerte. Parallel hat sich mit offenen Geodaten (OpenStreetMap) und standardisierten Abfragediensten (Overpass API) ein Ökosystem entwickelt, das eine frei zugängliche, gemeinschaftlich gepflegte Datengrundlage bereitstellt. 

Gleichzeitig gewinnt der Datenschutz an Bedeutung: Viele bestehende Lösungen greifen auf zentrale Server, Tracking oder Profilbildung zurück. Dieses Projekt setzt bewusst auf einen Ansatz ohne eigenes Server-Backend und mit lokaler, transparenter Verarbeitung – um Nutzenden mehr Kontrolle und Vertrauen zu geben und rechtliche/ethische Anforderungen besser zu erfüllen.

## 1.2 Zielsetzung
Die BlitzerApp soll Verkehrsteilnehmende dabei unterstützen, Geschwindigkeitsbegrenzungen einzuhalten und frühzeitig auf bekannte stationäre Blitzerstandorte sowie relevante kontextuelle Hinweise (z. B. Limitwechsel) aufmerksam werden zu lassen. Sie verfolgt drei Kernziele:
1. Bereitstellung einer plattformübergreifenden, datenschutzfreundlichen mobilen Anwendung für iOS und Android ohne eigenes zentrales Backend.
2. Nutzung ausschließlich offener, bestehender Schnittstellen (insbesondere Overpass für OSM-Daten) zur Anzeige stationärer Blitzer und optional zugehöriger Verkehrsattribute (maxspeed, POIs, relevante Hinweise).
3. Einbindung von Community-Mechanismen über bestehende offene Systeme (z. B. OSM Notes) zur Verbesserung der Datenqualität – ohne Aufbau eines separaten Melde- oder Moderationsservers.

Ergänzend verfolgt das Projekt qualitative Ziele wie Verständlichkeit der Warnungen, energieeffiziente Hintergrundverarbeitung (Geofencing statt Dauer-GPS), hohe Transparenz über Datenquellen und Einhaltung rechtlicher Rahmenbedingungen in zulässigen Ländern.

## 1.3 Methodik
Die Herangehensweise folgt einem iterativen, evidenzbasierten Vorgehen:
- Analysephase: Markt- und Situationsanalyse existierender Lösungen (Funktionsumfang, Schwächen beim Datenschutz, Nutzerbedürfnisse). Stakeholder- und Risikoanalyse zur Identifikation kritischer Erfolgsfaktoren.
- Anforderungsdefinition: Detaillierte funktionale und nicht-funktionale Anforderungen (Performance, Datenschutz, Rechtliches, Usability) werden strukturiert abgeleitet und priorisiert (MUSS/SOLL/KANN). 
- Architektur & Technologieauswahl: Bewertung von Cross-Plattform-Ansätzen (z. B. Flutter, React Native, native Entwicklung) hinsichtlich Performance, Plattformintegration (CarPlay/Android Auto Perspektive), Energieeffizienz und Community-Support. Entscheidung für einen Stack mit starker Offline- und Geodaten-Unterstützung.
- Prototyping (MVP): Implementierung eines minimalen Kernumfangs (Karte, Standort, Overpass-Abfrage, Warnlogik, lokales Caching) zur Validierung grundlegender Funktionalität und Performanceziele.
- Iterative Erweiterung: Sukzessive Integration von Hintergrundwarnungen, Mehrsprachigkeit, Nutzer-Meldefunktion via OSM Notes, Barrierefreiheit. Kontinuierliche Tests (Unit, Integration, Feldtests) und Feedback-Schleifen.
- Qualitätssicherung: Automatisierte Tests für Distanzberechnung, Geofencing, Caching und API-Ausfälle; manuelle Feldtests zur Messung von Latenz, Genauigkeit und Energieverbrauch. Dokumentation von Datenquellen und Nutzungseinschränkungen.
- Evaluierung & Monitoring (späteres Kapitel): Definition von Kennzahlen (Warn-Latenz, Crashrate, Energieverbrauch), regelmäßige Überprüfung und Ableitung von Optimierungen, ohne invasive Nutzungsanalyse.

Die Methodik legt ihren Schwerpunkt auf Minimalismus in der Infrastruktur, Nutzung offener Standards und transparente Kommunikation der Grenzen (z. B. Unvollständigkeit mobiler Blitzer). Rechtliche und ethische Aspekte fließen durch einen früh eingebauten Compliance-Check und klare Nutzerhinweise beim ersten Start mit ein.

> Weiterführende Details zu Anforderungen, Architektur, Risiken und Evaluierung sind in den jeweiligen Kapiteln (2–11) der Arbeit vertieft und bauen auf dieser Einleitung auf.
