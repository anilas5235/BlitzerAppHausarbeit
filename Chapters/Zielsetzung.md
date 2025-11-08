# Zielsetzung – BlitzerApp (iOS & Android)

## Kurzbeschreibung
Die BlitzerApp ist eine mobile, datenschutzfreundliche Warn- und Informations-App für iOS und Android. Sie nutzt ausschließlich bestehende, offene Schnittstellen (insbesondere OpenStreetMap/Overpass) zur Abfrage von stationären Blitzerstandorten sowie relevanter Verkehrsdaten und kommt ohne eigenes Server-Backend aus. Nutzerinnen und Nutzer erhalten visuelle und akustische Warnungen beim Annähern an bekannte Blitzerstandorte.

## Projektziel
- Bereitstellung einer plattformübergreifenden App (iOS & Android), die auf dem Gerät läuft und ohne eigene Server-Infrastruktur auskommt.
- Direkte Anbindung offener Datenquellen (v. a. Overpass API für OSM), um Blitzerstandorte und optional weitere verkehrsrelevante Informationen (z. B. Geschwindigkeitsbegrenzungen) anzuzeigen.
- Datenschutz „by design“: Standortverarbeitung ausschließlich lokal auf dem Gerät; keine dauerhafte zentrale Speicherung oder Profilbildung.
- Möglichkeit zu Nutzermeldungen über bestehende öffentliche Schnittstellen, ohne eigenes Backend.

## Zielgruppe
- Verkehrsteilnehmende, die Geschwindigkeitsbegrenzungen besser einhalten wollen und frühzeitig auf bekannte Blitzer hingewiesen werden möchten.
- Fokus auf Nutzerinnen und Nutzer in Regionen/Ländern, in denen der Einsatz entsprechender Apps rechtlich zulässig ist.

## Umfang (Scope)
- Native oder Cross-Plattform-App für iOS und Android.
- Kartenansicht mit aktueller Position, Anzeige bekannter stationärer Blitzer als POIs.
- Hintergrundwarnungen bei Annäherung an einen Blitzerstandort (visuell/akustisch), Radius konfigurierbar.
- Datenbezug über Overpass API (read-only) und ggf. ergänzende OSM-Dienste (z. B. Nominatim für Geocoding, Tiles über einen konformen Provider).
- Offline-Cache der relevanten Daten für definierte Regionen/Zeiträume.
- Optional: Absetzen von Nutzermeldungen über bestehende öffentliche Schnittstellen (z. B. OSM Notes API), ohne eigenes Backend.

## Abgrenzung (Out of Scope)
- Kein eigenes Server-Backend, keine eigene zentrale Datenhaltung.
- Keine Nutzerkonten/Registrierung, kein Social-Feature-Backend.
- Kein Upload sensibler Telemetriedaten (Standortverlauf) auf externe Server.
- Kein rechtsverbindlicher Anspruch auf Vollständigkeit/Aktualität der Daten.

## Funktionale Ziele (MUSS/SOLL/KANN)
- MUSS
  - Standortbestimmung und -verfolgung auf dem Gerät (Foreground; optional Background gem. Plattformrichtlinien).
  - Kartenanzeige mit POIs für stationäre Blitzer (OSM/Overpass-basiert).
  - Live-Warnung bei Annäherung (visuell + Audio), konfigurierbarer Warnradius.
  - Lokaler Daten-Cache und grundlegende Offline-Nutzung (z. B. letzte geladene Region).
  - Datenschutz: Keine Übermittlung des aktuellen Standorts an Dritte.
- SOLL
  - Hintergrundwarnungen via Geofencing (plattformkonform; Energieeffizienz beachten).
  - Berücksichtigung von Geschwindigkeitsbegrenzungen (OSM maxspeed, sofern verfügbar) zur kontextsensitiven Warnung.
  - Nutzermeldungen über bestehende öffentliche Schnittstellen (z. B. OSM Notes: anonym oder via OAuth), inkl. Moderations-/Qualitätshinweisen.
  - Mehrsprachigkeit (mind. Deutsch/Englisch), Dark Mode, Barrierefreiheit-Grundlagen.
- KANN
  - Konfigurierbare Stimmen/Sounds, Widgets/Quick Toggles.
  - Erweiterte Offline-Regionpacks.
  - Integration mit Fahrmodi (z. B. CarPlay/Android Auto) soweit Richtlinien und Zulassungen erfüllbar sind.

## Nicht-funktionale Ziele
- Performance
  - App-Start (Kaltstart) < 2 s auf Referenzgeräten.
  - Overpass-Abfrage und Rendering typischer Stadtregion < 3 s bei stabiler Verbindung.
  - Hintergrundbetrieb: zusätzlicher Energieverbrauch < 3%/h (Richtwert; gerätespezifisch).
- Zuverlässigkeit & Qualität
  - Robuste Fehlerbehandlung bei Netzwerkproblemen und API-Rate-Limits.
  - Deutliche Kennzeichnung von Datenstand/Quelle.
- Datenschutz & Sicherheit
  - Kein Tracking/Analytics standardmäßig; optional nur mit expliziter Einwilligung, lokal standardmäßig deaktiviert.
  - Speicherung von Einstellungen/Caches ausschließlich lokal, verschlüsselt soweit sinnvoll.
- Rechtliches & Compliance
  - Nutzung nur in Ländern, in denen Warn-Apps erlaubt sind; klarer Disclaimer beim ersten Start.
  - Einhaltung Nutzungsrichtlinien der verwendeten Dienste (OSM/Overpass, Tiles, Nominatim, etc.).

## Schnittstellen & Datenquellen
- Overpass API (Read-only) für OSM-Daten (stationäre Blitzer/Verkehrszeichen, sofern in OSM gepflegt). Beachte Rate-Limits, Timeout-Strategien und ggf. Spiegel-Endpunkte.
- OSM Notes API (für Nutzermeldungen ohne eigenes Backend): ermöglicht anonyme oder authentifizierte Meldungen als „Note“ mit Koordinate + Text. Moderation über OSM-Community-Mechanismen.
- Optional: Nominatim (Geocoding/Reverse-Geocoding) gemäß Fair-Use-Policy.
- Karten-Tiles: Nutzung eines konformen Tile-Providers (z. B. eigens bereitgestellt durch Drittanbieter mit API-Key); direkte OSM-Tiles nur gemäß Policy/Rate-Limit.

## Annahmen
- Stationäre Blitzerstandorte sind in OSM hinreichend gepflegt; mobile Blitzer sind kaum verlässlich per OSM abbildbar und werden daher nicht Kernbestandteil.
- Nutzerberichte erfolgen vorzugsweise über OSM Notes; damit bleibt die App backendfrei und nutzt bestehende Community-Prozesse.
- Zielplattformen: iOS ≥ 15, Android ≥ 8.0 (Oreo) als Mindestanforderung.

## Risiken & Gegenmaßnahmen
- Rechtliche Restriktionen je Land: Deutlicher Hinweis, konfigurierbare Deaktivierung; ggf. Geo-basiertes Soft-Disable.
- Datenqualität/Abdeckung: Transparenz über Quelle/Stand, einfache Meldungsfunktion, Community-Einbindung.
- API-Rate-Limits/Verfügbarkeit: Caching, inkrementelle Updates, Retry/Backoff, alternative Overpass-Instanzen.
- Hintergrund-Restriktionen (iOS/Android): Geofencing statt ständiger GPS-Polls, Nutzerhinweise zur Energieverwaltung, Plattformrichtlinien einhalten.

## Erfolgskriterien (KPIs/Abnahme)
- Funktional
  - Anzeige der eigenen Position und der bekannten stationären Blitzer in der Umgebung.
  - Warnung innerhalb von ≤ 2 s ab Eintritt in den Warnradius; kein Daueralarm bei Entfernung.
  - Offline-Nutzung: Letzte geladene Region ist ohne Netz verfügbar (POIs + Grundkarte in einfacher Darstellung).
  - Nutzermeldung (OSM Note) kann aus der App heraus abgesetzt werden (anonym oder mit OSM-Login), inkl. Bestätigung.
- Qualität
  - App stürzt in typischen Nutzungsszenarien nicht ab (Crashrate < 0,5% bei internen Tests).
  - Energieverbrauch im Hintergrundbetrieb innerhalb des Zielkorridors.

## MVP-Umfang (Phase 1)
- Kartenansicht + Standort.
- Overpass-Abfrage für stationäre Blitzer in Sicht-/Umgebungsbereich; Anzeige als POIs mit Basisdetails.
- Warnung beim Annähern (visuell/akustisch), konfigurierbarer Radius.
- Lokaler Cache; einfache Offline-Anzeige zuletzt geladener Kacheln/POIs.
- Basis-Einstellungen (Warnradius, Ton aus/an, Datenschutz-Hinweise).

## Erweiterungen (Folgephasen)
- Phase 2: Hintergrundwarnungen (Geofencing), bessere Energieeffizienz, UI-Feinschliff.
- Phase 3: Nutzermeldungen via OSM Notes (inkl. optionaler OSM-OAuth), Meldungsübersicht.
- Phase 4: Kontextwarnungen mit maxspeed, mehrsprachige UI, Barrierefreiheit.
- Phase 5: Erweiterte Offline-Regionen, Qualitäts-/Feedbackmechanismen, optionale Telemetrie mit Opt-in.

## Teststrategie (Auszug)
- Unit-Tests: Distanz-/Geofencing-Berechnung, Caching-Strategien, Overpass-Parser.
- Integrations-Tests: API-Abfragen gegen Staging/öffentliche Endpunkte mit Mocks/Fallbacks.
- Feldtests: Routen in urbanen und ländlichen Regionen, Messung von Latenz, Genauigkeit, Energieverbrauch.

## Glossar
- OSM: OpenStreetMap, offene Geodatenplattform.
- Overpass API: Abfragesprache/-dienst für OSM-Daten (read-only).
- OSM Notes: Leichtgewichtiges Meldesystem für OSM zur Erfassung/Hinweisen vor Ort.
- Nominatim: Geocoding/Reverse-Geocoding-Dienst für OSM.

