# 3 Anforderungsanalyse

## 3.1 Funktionale Anforderungen

Die funktionalen Anforderungen sind nach MUSS / SOLL / KANN priorisiert. Jede Anforderung erhält (wo möglich) ein
messbares Abnahmekriterium.

### MUSS-Anforderungen

1. Standortbestimmung (Foreground) – Die App ermittelt und aktualisiert die Geräteposition mindestens alle 2 Sekunden,
   solange der Warnmodus aktiv ist.  
   Abnahmekriterium: Positionsaktualisierung < 2 s Intervall bei stabiler GNSS-Verbindung.
2. Kartenanzeige – Darstellung einer interaktiven Karte mit aktueller Position und stationären Blitzer-POIs aus OSM (
   Overpass-Abfragen).  
   Abnahmekriterium: POIs werden innerhalb von 3 s nach erfolgreicher Overpass-Abfrage gerendert.
3. Warnlogik – Visuelle und akustische Warnung beim Eintritt in den konfigurierbaren Warnradius um einen Blitzer.  
   Abnahmekriterium: Auslösung der Warnung ≤ 2 s nach Unterschreiten des Distanzschwellwerts.
4. Konfigurierbarer Warnradius – Nutzer kann Radius (z. B. 200–1000 m) einstellen.  
   Abnahmekriterium: Änderung im Einstellungsbildschirm wirkt sofort (nächste Distanzberechnung) ohne Neustart.
5. Lokaler Cache – Letzte geladene Blitzer-POIs und relevante Kartenausschnitte sind offline verfügbar.  
   Abnahmekriterium: Nach Trennen der Datenverbindung bleiben POIs sichtbar; mindestens 1 Stadtgebiet (~5 km²) cached.
6. Keine Standortübertragung – Der aktuelle Standort wird nicht an externe Server gesendet.  
   Abnahmekriterium: Code-Review + Logging-Analyse zeigen keine Netzwerkrequests mit Standortdaten (außer Tile/Overpass
   ohne Rückübermittlung persönlicher Koordinaten).
7. Fehlerbehandlung API – Timeouts oder Rate-Limits bei Overpass führen zu gewählter Fallback-Strategie (Retry mit
   Backoff, Hinweis an Nutzer).  
   Abnahmekriterium: Simulierter Overpass-Timeout erzeugt Nutzerhinweis und verzögerte Wiederholung ≤ 30 s.
8. Basis-Einstellungen – Nutzer kann Warnungen aktivieren/deaktivieren, Ton stumm schalten, Datenschutz-Hinweis
   einsehen.  
   Abnahmekriterium: Änderungen persistieren lokal und bleiben nach App-Neustart bestehen.

### SOLL-Anforderungen

9. Hintergrundwarnungen (Geofencing) – Warnungen sollen auch bei minimierter App erfolgen, sofern
   Plattform-Berechtigungen erteilt.  
   Abnahmekriterium: Eintritt in Geofence löst Testwarnung im Hintergrund aus (Mindestens 1 Plattform verifiziert).
10. Geschwindigkeitslimit-Kontext – Anzeige aktueller OSM maxspeed (falls verfügbar) und kontextsensitiv verstärkte
    Warnung bei Überschreitung.  
    Abnahmekriterium: Bei vorhandener maxspeed wird Limit angezeigt; Testfall mit bewusst überschrittener
    Geschwindigkeit verstärkt Warnsignal.
11. Nutzer-Meldungen über OSM Notes – Möglichkeit, über die App eine neue Note (Blitzer-Hinweis / Korrektur) zu
    erstellen (anonym oder via OAuth).  
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