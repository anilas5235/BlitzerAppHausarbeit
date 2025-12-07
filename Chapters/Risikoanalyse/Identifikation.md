# 6 Risikoanalyse

Dieses Kapitel umfasst die systematische Identifikation, Bewertung und Steuerung potenzieller Risiken für das Softwareprojekt. Besonderes Augenmerk liegt auf der spezifischen Architektur: Da die Anwendung rein clientseitig operiert („Serverless“ im Kontext eigener Backend-Infrastruktur) und direkt auf öffentliche Schnittstellen (OpenStreetMap Overpass API, Tile-Server) zugreift, entstehen spezifische Abhängigkeiten und Lastszenarien, die sich von servergestützten Architekturen unterscheiden.

Die Analyse orientiert sich methodisch an gängigen Standards wie der ISO 31000 und gliedert sich in Identifikation, Bewertung sowie Maßnahmenplanung.

## 6.1 Identifikation von Risiken

Die Risiken werden thematisch in die Bereiche Regulatorik, Technische Infrastruktur, Datenqualität, Betriebswirtschaft sowie Sicherheit/Privatsphäre kategorisiert.

### 6.1.1 Regulatorische und rechtliche Risiken
Aufgrund der Funktionalität der Anwendung (Warnung vor Verkehrsüberwachung) besteht ein inhärentes rechtliches Spannungsfeld.

* **Länderrestriktionen & Rechtslage:** In verschiedenen europäischen Jurisdiktionen (z. B. Deutschland, Schweiz, Frankreich) unterliegen Blitzerwarn-Apps unterschiedlichen Verboten oder rechtlichen Grauzonen (z. B. § 23 Abs. 1c StVO in Deutschland). Eine Verschärfung der Rechtssprechung kann die legale Nutzbarkeit der App in Kernmärkten ad hoc beenden.
* **App-Store-Konformität:** Apple und Google prüfen Apps mit Bezug zu Verkehrsüberwachung restriktiv. Unklare Formulierungen in der Store-Beschreibung oder fehlende Disclaimer bezüglich der Hintergrundortung führen häufig zur Ablehnung („Rejection“) oder Entfernung („Takedown“).
* **Haftungsrisiken:** Trotz Disclaimer besteht das Risiko, dass Nutzer Bußgelder oder Unfälle auf die Nutzung der App zurückführen und Regressansprüche stellen oder negative Publicity erzeugen.

### 6.1.2 Technische Infrastruktur & Abhängigkeiten (Client-Side Only)
Da kein eigener Proxy-Server existiert, kommuniziert jede App-Instanz direkt mit Drittanbietern.

* **API-Verfügbarkeit & Rate Limits (Overpass API):** Die Overpass API ist eine öffentliche, gemeinschaftlich finanzierte Ressource. Exzessive Abfragen durch schlecht optimierte Clients können zu IP-Sperren seitens der API-Betreiber führen oder die öffentliche Instanz überlasten (Timeouts). Da keine Middleware existiert, fehlt eine zentrale Pufferung.
* **Tile-Server Kosten & Limits:** Die direkte Einbindung von Kartenkacheln (Tiles) erzeugt bei hohen Nutzerzahlen signifikanten Traffic. Bei Überschreitung der Free-Tier-Limits externer Provider (z. B. Mapbox, OSM-Standard) drohen Dienstabschaltung oder hohe Kosten.
* **Plattform-Fragmentierung (Geofencing):** Unterschiede im Energiemanagement von Android („Doze Mode“, „App Standby Buckets“) und iOS (strikte Background Execution Limits) erschweren ein zuverlässiges Geofencing. Es besteht das Risiko, dass Warnungen im Standby-Modus vom Betriebssystem unterdrückt werden.
* **Breaking Changes in Libraries:** Die Abhängigkeit von Open-Source-Bibliotheken (z. B. `osmdroid`, `retrofit`) birgt das Risiko unangekündigter Schnittstellenänderungen oder der Einstellung der Wartung („Abandonware“).

### 6.1.3 Datenqualität und Funktionalität
Die App verlässt sich auf Crowdsourcing-Daten der OpenStreetMap.

* **Datenlücken & Inkonsistenz:** Nicht kartierte Blitzer oder falsch getaggte Objekte (z. B. `traffic_calming` statt `speed_camera`) führen zu fehlenden Warnungen (False Negatives).
* **Falsch-Positive Warnungen:** Ungenaue GPS-Signale oder komplexe Straßenführungen (z. B. Blitzer auf parallel verlaufender Autobahn, Tunnel) können Fehlalarme auslösen, was das Nutzervertrauen erodiert.
* **Veraltete Datenanzeige:** Da Daten lokal gecacht werden müssen (Offline-First-Ansatz), besteht die Gefahr, dass Änderungen (z. B. Abbau eines Blitzers) nicht zeitnah auf dem Endgerät reflektiert werden.

### 6.1.4 Betriebswirtschaftliche und Ressourcen-Risiken
Diese Risiken ergeben sich aus der Projektplanung und dem gewählten Geschäftsmodell.

* **Monetarisierungsdefizit:** Ein Scheitern der Strategie (z. B. geringe Conversion-Rate bei Spenden/Premium) gefährdet die langfristige Wartung. Zwar fallen kaum Serverkosten an, jedoch müssen Weiterentwicklung und API-Sponsoring gedeckt werden.
* **Ressourcenengpass:** Spezialwissen (z. B. für energieeffizientes Geofencing oder Accessibility-Standards nach WCAG) könnte im Team fehlen, was zu Verzögerungen in der Entwicklung führt.
