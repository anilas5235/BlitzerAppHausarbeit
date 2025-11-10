## 10.2 Kritische Bewertung

Trotz des soliden Konzepts bestehen strukturelle Herausforderungen:

- Datenqualität & Abdeckung: Stationäre Blitzer in OSM sind regional unterschiedlich gepflegt. Das Nutzenversprechen
  hängt direkt von der Aktualität und Vollständigkeit dieser Community-Daten ab. Mobile Blitzer bleiben weitgehend
  unadressierbar – dies limitiert den wahrgenommenen Funktionsumfang gegenüber Wettbewerbern mit Echtzeit-Community.
- Abhängigkeit externer Dienste: Overpass-Instanzen und Tile-Provider sind Engpässe. Rate-Limits, Ausfälle oder
  Policy-Änderungen können temporär die Nutzbarkeit einschränken. Ohne eigenes Backend ist Spielraum für serverseitige
  Optimierung (Aggregation, Preprocessing) begrenzt.
- Rechtliche Unsicherheit: Unterschiedliche Länderregelungen zu Blitzerwarnungen erfordern sorgfältige Kommunikation und
  ggf. Feature-Deaktivierung. Fehlinterpretationen können zu App-Store-Blockaden oder Nutzerkritik führen.
- Monetarisierung & Nachhaltigkeit: Das Freemium-/Spendenmodell ist attraktiv, trägt aber das Risiko schwankender
  Einnahmen. Langfristige Wartung (Updates der Libraries, OS-Versionen, Accessibility-Anpassungen) muss finanziell
  gesichert sein.
- Energie & Performance im Realbetrieb: Geofencing und Standortverarbeitung variieren stark je Gerät und OS-Version.
  Labormessungen müssen durch Feldtests abgesichert werden; sonst droht negative Bewertung wegen Akkubelastung.
- UX-Risiko Ablenkung: Auch mit reduziertem UI besteht Gefahr, dass Nutzer während der Fahrt interagieren. Eine strenge
  „Fahrmodus“-Reduktion komplexer Einstellungen ist nötig.

Positiv hervorzuheben:

- Architektur-Klarheit: Der Verzicht auf Backend senkt Komplexität, Kosten und Datenschutzrisiken.
- Skalierbarkeit auf Datenebene: Nutzung offener Standards erlaubt iterative Erweiterungen ohne Vendor-Lock-in.
- Transparenz & Vertrauen: Ein konsistentes Privacy-Narrativ kann als starkes Differenzierungsmerkmal dienen.
