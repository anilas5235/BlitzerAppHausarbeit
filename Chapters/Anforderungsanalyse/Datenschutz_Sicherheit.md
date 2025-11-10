## 3.3 Datenschutz und Sicherheit

- Grundsatz: Privacy-by-Design (keine Profilbildung, keine zentrale Speicherung von Standortverläufen, minimale
  Datenerhebung).  
  Nachweis: Architekturdiagramm + Datenflussanalyse.
- Datenminimierung: Speicherung nur notwendiger Einstellungen, Caches, Regionpacks lokal (verschlüsselt sofern
  Plattform-APIs verfügbar).  
  Nachweis: Audit der gespeicherten Dateien.
- Keine Tracking-Dienste standardmäßig: Analytics nur nach explizitem Opt-in; Default = deaktiviert.  
  Nachweis: Opt-in Dialog + Konfiguration.
- Standortverarbeitung lokal: Distanzberechnung und Warnlogik ausschließlich auf dem Gerät; Overpass-Abfragen enthalten
  keine persönlichen Standortdaten (Anfragen basieren auf Bounding Box um aktuelle Position, aber ohne persistente
  Zuordnung).  
  Nachweis: Netzwerk-Trace zeigt keine persistente Nutzer-ID.
- Sichere Kommunikation: HTTPS für alle externen Requests (Tiles, Overpass, Nominatim).  
  Nachweis: TLS-Handshake protokolliert; keine Mixed-Content-Warnungen.
- Eingaben für OSM Notes validieren (Länge, Sonderzeichen) zur Vermeidung von Missbrauch.  
  Nachweis: Unit-Tests Input-Validierung.
- Offenlegung & Transparenz: Datenschutzhinweis beim ersten Start + jederzeit abrufbar; erklärt Datenquellen,
  Rechtslage, Nutzungshinweise.  
  Nachweis: UI-Screenshot / Textprüfung.