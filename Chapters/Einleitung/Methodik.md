## 1.3 Methodik

Die Herangehensweise folgt einem iterativen, evidenzbasierten Vorgehen:

- Analysephase: Markt- und Situationsanalyse existierender Lösungen (Funktionsumfang, Schwächen beim Datenschutz,
  Nutzerbedürfnisse). Stakeholder- und Risikoanalyse zur Identifikation kritischer Erfolgsfaktoren.
- Anforderungsdefinition: Detaillierte funktionale und nicht-funktionale Anforderungen (Performance, Datenschutz,
  Rechtliches, Usability) werden strukturiert abgeleitet und priorisiert (MUSS/SOLL/KANN).
- Architektur & Technologieauswahl: Bewertung von Cross-Plattform-Ansätzen (z. B. Flutter, React Native, native
  Entwicklung) hinsichtlich Performance, Plattformintegration (CarPlay/Android Auto Perspektive), Energieeffizienz und
  Community-Support. Entscheidung für einen Stack mit starker Offline- und Geodaten-Unterstützung.
- Prototyping (MVP): Implementierung eines minimalen Kernumfangs (Karte, Standort, Overpass-Abfrage, Warnlogik, lokales
  Caching) zur Validierung grundlegender Funktionalität und Performanceziele.
- Iterative Erweiterung: Sukzessive Integration von Hintergrundwarnungen, Mehrsprachigkeit, Nutzer-Meldefunktion via OSM
  Notes, Barrierefreiheit. Kontinuierliche Tests (Unit, Integration, Feldtests) und Feedback-Schleifen.
- Qualitätssicherung: Automatisierte Tests für Distanzberechnung, Geofencing, Caching und API-Ausfälle; manuelle
  Feldtests zur Messung von Latenz, Genauigkeit und Energieverbrauch. Dokumentation von Datenquellen und
  Nutzungseinschränkungen.
- Evaluierung & Monitoring (späteres Kapitel): Definition von Kennzahlen (Warn-Latenz, Crashrate, Energieverbrauch),
  regelmäßige Überprüfung und Ableitung von Optimierungen, ohne invasive Nutzungsanalyse.

Die Methodik legt ihren Schwerpunkt auf Minimalismus in der Infrastruktur, Nutzung offener Standards und transparente
Kommunikation der Grenzen (z. B. Unvollständigkeit mobiler Blitzer). Rechtliche und ethische Aspekte fließen durch einen
früh eingebauten Compliance-Check und klare Nutzerhinweise beim ersten Start mit ein.

> Weiterführende Details zu Anforderungen, Architektur, Risiken und Evaluierung sind in den jeweiligen Kapiteln (2–11)
> der Arbeit vertieft und bauen auf dieser Einleitung auf.
