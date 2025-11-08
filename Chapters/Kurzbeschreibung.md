# Kurzbeschreibung / Abstract

Die BlitzerApp ist eine datenschutzfreundliche Warn- und Informations-App für iOS und Android. Sie nutzt ausschließlich
offene, bestehende Schnittstellen – vor allem die Overpass API von OpenStreetMap – um stationäre Blitzerstandorte sowie
optional relevante Verkehrsattribute (z. B. Geschwindigkeitsbegrenzungen) direkt auf dem Gerät darzustellen. Ein
zentrales Server-Backend entfällt bewusst: Standortverarbeitung, Warnlogik und Caching erfolgen lokal (
Privacy-by-Design), wodurch Tracking und Profilbildung vermieden werden.

Ziel ist eine klare, energieeffiziente Warnung beim Annähern an bekannte Blitzerstandorte, inklusive konfigurierbarem
Warnradius, Offline-Cache und transparenter Quellenangabe. Die App soll rechtliche Rahmenbedingungen je Land
respektieren (Disclaimer, optionale Deaktivierung) und – ohne eigenes Backend – Community-Hinweise über bestehende
öffentliche Schnittstellen (z. B. OSM Notes) unterstützen.

Das MVP umfasst Karte, Standort, Overpass-Abfrage, Warnlogik und lokalen Cache. Erweiterungen betreffen Geofencing (
Hintergrundwarnungen), Mehrsprachigkeit, Accessibility, OSM Notes und kontextuelle Hinweise (maxspeed). Risiken (
rechtliche Lage, Datenqualität, API-Limits, Energieverbrauch) werden durch Caching, Backoff-Strategien, klare
Kommunikation und Feldtests adressiert. Die Kombination aus offenen Daten, schlanker Architektur und striktem
Datenschutz soll ein vertrauenswürdiges, nachhaltiges Produkt ermöglichen, das verantwortungsvolles Fahren unterstützt.
