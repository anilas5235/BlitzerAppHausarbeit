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

### Risiken die aus andern Kapiteln stammen, die hier einfließen sollten

### 4.3.5 Ressourcenrisiken und Skalierung

Die Ressourcenplanung ist mit spezifischen Risiken verbunden. Einige zentrale Risiken und die vorgesehenen
Gegenmaßnahmen sind:

Risikofaktoren Ressourcen:

- Engpass Geofencing-Spezialwissen → frühzeitige Spike in Phase B.
- Verzögerung durch Performance-Probleme → gezieltes Profiling in AP-D2 statt zu spät.
- i18n/A11y unterschätzt → separate kleine Meilensteine (C2/C3) statt „am Ende“.

Diese Risiken werden in der Risikoanalyse vertieft betrachtet und als Backlog-Items in die Sprintplanung integriert.

Strategie für Skalierung (falls mehr Nutzer/Feature-Wünsche oder höherer Änderungsdruck):

- Add-On weiterer Dev für Feature-Phase D/E.
- Separater Support/Community-Manager bei steigendem Meldungsvolumen.

### 5.2.5 Kostenrisiken & Gegenmaßnahmen

| Risiko                             | Auswirkung                       | Gegenmaßnahme                                 |
|------------------------------------|----------------------------------|-----------------------------------------------|
| Geofencing komplexer als erwartet  | Mehr Entwicklungs-PT             | Früher Spike (Prototyp) in Phase B            |
| Übernutzung Overpass → Rate-Limits | Verzögerung, Re-Engineering      | Caching, kleinere BBox, Backoff, Mirrors      |
| Energieverbrauch zu hoch           | Ablehnung durch Nutzer/App Store | Profiling früh, iterative Optimierung (AP-D2) |
| Verzögerte Store-Freigabe          | Release verschoben               | Frühe Prüfung Richtlinien, Beta Testlauf      |
| Zugänglichkeit (A11y) unterschätzt | Nacharbeit, Image-Risiko         | Früh AP-C3, Checklisten etablieren            |
| Datenqualität unzureichend lokal   | Geringer Nutzen                  | OSM Notes Integration zur Verbesserung        |

Die hier beschriebenen Kostenrisiken stehen in engem Zusammenhang mit der Risikoanalyse in Kapitel 6. Relevante
Maßnahmen werden im Backlog abgebildet und in Sprints eingeplant, sodass Risiken und Kosteneffekte frühzeitig adressiert
werden können.

### 5.3.5 Bewertung Monetarisierungs-Risiken
(mus evtl. angepasst werden je nach Monetarisierungsmodell für das wir uns entscheiden)

| Option                    | Risiko                   | Mitigation                                    |
|---------------------------|--------------------------|-----------------------------------------------|
| Classic Ads               | Datenschutz-Imageverlust | Nicht einsetzen                               |
| Verkauf Standortdaten     | Widerspricht Kernwerten  | Ausschließen                                  |
| Zu hohe Abo-Preise        | Geringe Adoption         | Moderate Preisstrategie, Mehrwert klar zeigen |
| Reine Spendenabhängigkeit | Unsichere Planung        | Mischmodell, transparente Roadmap             |
