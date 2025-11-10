# 6 Risikoanalyse

Dieses Kapitel identifiziert wesentliche Risiken für die BlitzerApp (rein clientseitige Architektur, Nutzung offener
Schnittstellen), bewertet sie strukturiert und leitet präventive sowie reaktive Maßnahmen ab.

## 6.1 Identifikation von Risiken

Die Risiken sind thematisch gruppiert (Regulatorik, Technik, Daten, Nutzer/Produkt, Betrieb/Qualität,
Sicherheit/Privatsphäre).

1. Rechtliche Restriktionen in einzelnen Ländern (Verbot oder Einschränkung von Blitzerwarnungen).
2. App-Store Ablehnung (Hintergrundortung, fehlende oder unklare Disclaimer).
3. API-Rate-Limits / Overpass-Verfügbarkeit (Timeouts, Instanz-Ausfälle).
4. Tile-Provider Limit-/Kostenüberschreitung durch hohe Abrufzahlen.
5. Unvollständige / inkonsistente OSM-Daten (stationäre Blitzer fehlen oder falsch).
6. Falsch-positive Warnungen (Fehltrigger durch Distanz-/Richtungsberechnung).
7. Performance-/Latenzprobleme (Startzeit > Ziel, Warnung verzögert).
8. Hoher Energieverbrauch im Hintergrund (Geofencing ineffizient).
9. Geofencing technische Komplexität / Plattformrestriktionen (iOS/Android Unterschiede).
10. Datenschutz-Wahrnehmung (Misstrauen trotz Privacy-by-Design – UI unklar).
11. Accessibility-Mängel (Kontraste, Screenreader, resultiert in Ausschluss bestimmter Nutzergruppen).
12. Security-Schwachstellen (unsichere Speicherung von Settings, mögliche Man-in-the-Middle bei falscher
    TLS-Konfiguration).
13. Community-Missbrauch von OSM Notes (Spam, unpräzise Meldungen).
14. Abhängigkeit von externen Open-Source-Libraries (Breaking Changes / fehlende Wartung).
15. Monetarisierung unzureichend (fehlende Einnahmen nach Release → eingeschränkte Wartung).
16. Fehlende Skalierbarkeit von Offline-Caching (Speicherplatz knapp, langsame Updates).
17. Nutzerfehler / Ablenkung (Übermäßige Interaktion während Fahrt → Sicherheitsrisiko).
18. Unklare Kommunikation von Datenaktualität (Nutzer nimmt veraltete Daten als aktuell an).
19. Fehlschlag OAuth-Flow (OSM Notes) → geringere Nutzungsbereitschaft für Meldungen.
20. Reputationsschaden durch fehlerhafte Warnmeldungen in sensiblen Bereichen (z. B. Schulzonen falsche Limits).
