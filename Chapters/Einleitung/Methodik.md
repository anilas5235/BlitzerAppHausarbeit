## 1.3 Methodik

* Vorgehen iterativ (agil) in Sprints (Dailies, Reviews, ...)
* Situations- & Marktanalyse
  * Untersuchung bestehender Blitzer- und Navi-Apps (Funktionsumfang, Geschäftsmodelle, ...) sowie relevanter Stakeholder und Risiken
  * Parallel wird rechtliche Rahmenlage in ausgewählten Zielländern grob eingeordnet
* Strukturierte Anforderungsanalyse
  * Ableitung der funktionalen Anforderungen (z. B. Kartendarstellung, Overpass-Abfragen, Warnlogik, Community-Rückmeldungen) und der nicht-funktionalen Anforderungen (Performance, Energieverbrauch, Verständlichkeit, Barrierefreiheit, Datenschutz, Stabilität)
  * Anschließende Priorisierung in MUSS / SOLL / KANN, um einen klar abgegrenzten MVP-Kern zu definieren
* Architektur- & Technologieentscheidung
  * Vergleich geeigneter Technologie-Stacks (z. B. native Entwicklung vs. Cross-Plattform-Framework) mit Blick auf Performance, Offline-Fähigkeit, Geodaten-Unterstützung, Wartbarkeit und Team-Skills
  * Auf dieser Basis wird Zielarchitektur für App, Datenzugriffe und Caching festgelegt
* MVP-Umsetzung in Iterationen
  * Aufbau eines minimalen funktionsfähigen Prototyps mit Karte, Standortanzeige, Abfragen der Blitzer-Daten, Grundlogik für Warnabstände und lokalem Caching
  * In weiteren Iterationen werden zusätzliche Funktionen wie Hintergrundwarnungen, OSM-Feedback und einfache Einstellungen ergänzt
* Testen & Qualitätssicherung
  * Kombination aus automatisierten Tests (z. B. Distanz- und Geofencing-Berechnungen, Ausfallszenarien der APIs, Caching-Logik) und Feldtests auf realen Strecken
  * Wichtige Kennzahlen sind u. a. Warn-Latenz, Akkuverbrauch, Stabilität und Anzahl falscher oder fehlender Warnungen
* Kontinuierliche Risiko- und Compliance-Betrachtung
  * Regelmäßige Überprüfung technischer, organisatorischer und rechtlicher Risiken (z. B. Änderungen von API-Nutzungsbedingungen oder Gesetzeslagen) sowie Ableitung von Anpassungen an Funktionsumfang, Nutzungsbedingungen und Nutzerhinweisen
* Die folgenden Kapitel vertiefen erst die Situations- & Anforderungsanalyse, leiten daraus Produkt- & Finanzplanung ab und bewerten Risiken sowie mögliche Auswirkungen der Lösung
