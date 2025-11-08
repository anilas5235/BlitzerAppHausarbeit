# 3 Anforderungsanalyse

Dieses Kapitel konkretisiert die Anforderungen an die BlitzerApp auf Basis der Zielsetzung (Kapitel 1) und der Markt-/Situationsanalyse (Kapitel 2). Es unterteilt sich in funktionale und nicht-funktionale Anforderungen sowie spezifische Aspekte zu Datenschutz/Sicherheit und rechtlicher Compliance.

## 3.1 Funktionale Anforderungen
Die funktionalen Anforderungen sind nach MUSS / SOLL / KANN priorisiert. Jede Anforderung erhält (wo möglich) ein messbares Abnahmekriterium.

### MUSS-Anforderungen
1. Standortbestimmung (Foreground) – Die App ermittelt und aktualisiert die Geräteposition mindestens alle 2 Sekunden, solange der Warnmodus aktiv ist.  
   Abnahmekriterium: Positionsaktualisierung < 2 s Intervall bei stabiler GNSS-Verbindung.
2. Kartenanzeige – Darstellung einer interaktiven Karte mit aktueller Position und stationären Blitzer-POIs aus OSM (Overpass-Abfragen).  
   Abnahmekriterium: POIs werden innerhalb von 3 s nach erfolgreicher Overpass-Abfrage gerendert.
3. Warnlogik – Visuelle und akustische Warnung beim Eintritt in den konfigurierbaren Warnradius um einen Blitzer.  
   Abnahmekriterium: Auslösung der Warnung ≤ 2 s nach Unterschreiten des Distanzschwellwerts.
4. Konfigurierbarer Warnradius – Nutzer kann Radius (z. B. 200–1000 m) einstellen.  
   Abnahmekriterium: Änderung im Einstellungsbildschirm wirkt sofort (nächste Distanzberechnung) ohne Neustart.
5. Lokaler Cache – Letzte geladene Blitzer-POIs und relevante Kartenausschnitte sind offline verfügbar.  
   Abnahmekriterium: Nach Trennen der Datenverbindung bleiben POIs sichtbar; mindestens 1 Stadtgebiet (~5 km²) cached.
6. Keine Standortübertragung – Der aktuelle Standort wird nicht an externe Server gesendet.  
   Abnahmekriterium: Code-Review + Logging-Analyse zeigen keine Netzwerkrequests mit Standortdaten (außer Tile/Overpass ohne Rückübermittlung persönlicher Koordinaten).
7. Fehlerbehandlung API – Timeouts oder Rate-Limits bei Overpass führen zu gewählter Fallback-Strategie (Retry mit Backoff, Hinweis an Nutzer).  
   Abnahmekriterium: Simulierter Overpass-Timeout erzeugt Nutzerhinweis und verzögerte Wiederholung ≤ 30 s.
8. Basis-Einstellungen – Nutzer kann Warnungen aktivieren/deaktivieren, Ton stumm schalten, Datenschutz-Hinweis einsehen.  
   Abnahmekriterium: Änderungen persistieren lokal und bleiben nach App-Neustart bestehen.

### SOLL-Anforderungen
9. Hintergrundwarnungen (Geofencing) – Warnungen sollen auch bei minimierter App erfolgen, sofern Plattform-Berechtigungen erteilt.  
   Abnahmekriterium: Eintritt in Geofence löst Testwarnung im Hintergrund aus (Mindestens 1 Plattform verifiziert).
10. Geschwindigkeitslimit-Kontext – Anzeige aktueller OSM maxspeed (falls verfügbar) und kontextsensitiv verstärkte Warnung bei Überschreitung.  
    Abnahmekriterium: Bei vorhandener maxspeed wird Limit angezeigt; Testfall mit bewusst überschrittener Geschwindigkeit verstärkt Warnsignal.
11. Nutzer-Meldungen über OSM Notes – Möglichkeit, über die App eine neue Note (Blitzer-Hinweis / Korrektur) zu erstellen (anonym oder via OAuth).  
    Abnahmekriterium: Erfolgreiches Anlegen einer Note mit Koordinate und Text erhält Bestätigungs-ID.
12. Mehrsprachigkeit – Mind. Deutsch und Englisch vollständig lokalisiert.  
    Abnahmekriterium: Umschalten der Sprache aktualisiert alle UI-Texte ohne Neustart.
13. Dark Mode / Barrierefreiheit – Unterstützung systemweiter Themes; Mindestkontraste (WCAG AA) für Kernansichten.  
    Abnahmekriterium: Farbkontrastprüfung zeigt Kontrast ≥ 4.5:1 für Primärtexte.

### KANN-Anforderungen
14. Integration Fahrzeugmodi (CarPlay/Android Auto) – Anzeige aktiver Warnungen in kompatiblen Fahrzeug-Interfaces.  
    Abnahmekriterium: Prototyp zeigt Warnsymbol + Distanz im Fahrzeugdisplay (Testgerät/Simulator).
15. Erweiterte Offline-Regionpacks – Nutzer kann zusätzliche Regionen vorab herunterladen.  
    Abnahmekriterium: Auswahl einer Region lädt POIs + minimal Tileset; Größenangabe vor Download.
16. Anpassbare Warnsounds / Stimmen – Auswahl aus vordefinierten Signalen.  
    Abnahmekriterium: Änderung im Einstellungsmenü wirkt beim nächsten Warnereignis.
17. Widgets / Quick Toggles – Schnelles Aktivieren/Deaktivieren von Warnmodus und Ton.  
    Abnahmekriterium: Widget-Aktion spiegelt sich in App-Zustand ≤ 2 s.

## 3.2 Nicht-funktionale Anforderungen

### Performance & Effizienz
- Startzeit (Cold Start): < 2 s auf Referenzgeräten (Midrange Android, aktuelles iPhone).  
  Messung: Durchschnitt aus 10 Starts ≤ 2 s.
- Overpass-Abfrage: Antwort & Rendering typischer Stadtregion (≤ 300 relevante Nodes) < 3 s bei LTE/WLAN.  
  Messung: 95. Perzentil der Latenz ≤ 3 s.
- Hintergrundenergieverbrauch: Zusatzverbrauch durch aktive Warnbereitschaft < 3% Akku pro Stunde.  
  Messung: Monitoring über System-Profiler in Testfahrt.

### Zuverlässigkeit & Robustheit
- Fehlerquote API: < 5% Abfragen scheitern ohne erfolgreichen Retry.  
  Messung: Log-Auswertung in Test-Sessions.
- Crashrate: < 0.5% in internen Testzyklen (≥ 100 Sitzungen).  
  Messung: Crash-Log Aggregation.

### Benutzbarkeit & UX
- Warn-Latenz: Warnung erfolgt ≤ 2 s nach Eintritt in Radius (95% der Fälle).  
- Verständlichkeit: Nutzer erkennt Warnung eindeutig (Icon + Farbe + Ton) – positive Bewertung in Usability-Test (> 80% Zustimmung).
- Konfiguration: Kernparameter (Radius, Ton) in maximal 2 Interaktionen auffindbar.

### Wartbarkeit & Erweiterbarkeit
- Modularität: Warnlogik, Overpass-Abfrage, Geofencing, UI getrennte Module/Layer (Clean Architecture / MVVM o. ä.).  
  Review: Code-Struktur dokumentiert, klare Schnittstellen.
- Testabdeckung: Mindestens 70% Branch Coverage kritischer Logik (Distanz-/Geofence-Berechnung, Parser).  
  Messung: CI-Bericht.

### Portabilität
- Unterstützte Plattformen: iOS ≥ 15, Android ≥ 8.0.  
  Abnahmekriterium: Erfolgreiches Build & Grundfunktion auf Referenzgeräten/Simulatoren.

### Skalierbarkeit (Client-seitig)
- Datenvolumen handhabbar bis zu 5.000 POIs in Cache ohne wahrnehmbare UI-Lag (> 30 fps).  
  Messung: Profiling Szenario mit künstlich erhöhter POI-Anzahl.

### Beobachtbarkeit (lokal / optional)
- Optionales lokal aggregiertes Performance-Logging (Startzeit, Overpass-Latenz) ohne externe Übertragung.  
  Review: Keine personenbezogenen Standortmetadaten im Log.

## 3.3 Datenschutz und Sicherheit
- Grundsatz: Privacy-by-Design (keine Profilbildung, keine zentrale Speicherung von Standortverläufen, minimale Datenerhebung).  
  Nachweis: Architekturdiagramm + Datenflussanalyse.
- Datenminimierung: Speicherung nur notwendiger Einstellungen, Caches, Regionpacks lokal (verschlüsselt sofern Plattform-APIs verfügbar).  
  Nachweis: Audit der gespeicherten Dateien.
- Keine Tracking-Dienste standardmäßig: Analytics nur nach explizitem Opt-in; Default = deaktiviert.  
  Nachweis: Opt-in Dialog + Konfiguration.
- Standortverarbeitung lokal: Distanzberechnung und Warnlogik ausschließlich auf dem Gerät; Overpass-Abfragen enthalten keine persönlichen Standortdaten (Anfragen basieren auf Bounding Box um aktuelle Position, aber ohne persistente Zuordnung).  
  Nachweis: Netzwerk-Trace zeigt keine persistente Nutzer-ID.
- Sichere Kommunikation: HTTPS für alle externen Requests (Tiles, Overpass, Nominatim).  
  Nachweis: TLS-Handshake protokolliert; keine Mixed-Content-Warnungen.
- Eingaben für OSM Notes validieren (Länge, Sonderzeichen) zur Vermeidung von Missbrauch.  
  Nachweis: Unit-Tests Input-Validierung.
- Offenlegung & Transparenz: Datenschutzhinweis beim ersten Start + jederzeit abrufbar; erklärt Datenquellen, Rechtslage, Nutzungshinweise.  
  Nachweis: UI-Screenshot / Textprüfung.

## 3.4 Rechtliches und Compliance
- Länderrestriktionen: Hinweis auf rechtliche Lage; Nutzer bestätigt Konformität; Option zur Deaktivierung von Warnungen in restriktiven Ländern.  
  Abnahmekriterium: Disclaimer muss bestätigt werden; Zustand gespeichert.
- Konformität OSM/Overpass-Nutzungsrichtlinien: Abfragebegrenzung (Rate-Limit), Caching & angemessene Intervalle (z. B. nicht mehr als X großflächige Abfragen / Stunde).  
  Messung: Logging Abfragefrequenz.
- Lizenzhinweise: Anzeige erforderlicher OpenStreetMap-Attribution (© OpenStreetMap contributors) im Karten-/Info-Bereich.  
  Abnahmekriterium: Attribution sichtbar und korrekt.
- Urheberrecht / Datenquellen: Dokumentation der verwendeten Dienste (Tiles, Geocoding, Overpass-Instanzen).  
  Nachweis: Abschnitt in App-Info.
- App-Store-Richtlinien: Einhaltung von iOS/Android Vorgaben (Hintergrundortung, Datenschutz-Dialoge).  
  Nachweis: Review-Checkliste vollständig.
- Barrierefreiheit: Mindestkontraste, Skalierbare Schriftgrößen, Screenreader-Lesbarkeit (Labels vorhanden).  
  Messung: Accessibility-Scanner Ergebnisse sauber.

## Zusammenfassung
Die Anforderungen stellen sicher, dass die BlitzerApp den Fokus auf Datenschutz, Transparenz und Effizienz wahrt. Funktionale Kernziele (Warnung, lokale Verarbeitung, offene Daten) werden durch klare MUSS/SOLL/KANN-Priorisierung und messbare Kriterien operationalisiert. Nicht-funktionale Anforderungen definieren Qualitätsziele (Performance, Energie, Wartbarkeit) und verankern Datenschutz sowie Compliance. Dies bildet die Grundlage für Architektur- und Umsetzungsentscheidungen (Kapitel 10) sowie Evaluierung und Monitoring (späteres Kapitel).

