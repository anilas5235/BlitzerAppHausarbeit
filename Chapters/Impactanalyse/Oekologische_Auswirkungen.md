# 7 Impactanalyse

Dieses Kapitel bewertet die Auswirkungen der BlitzerApp auf ökologische, soziale und wirtschaftliche Dimensionen.
Grundlage sind die Architektur (rein clientseitig, keine eigene Server-Infrastruktur), Privacy-by-Design und die
Zielsetzung, Geschwindigkeitsbegrenzungen einzuhalten, ohne neue Risiken (Ablenkung, Datenschutzverletzungen) zu
schaffen.

## 7.1 Ökologische Auswirkungen

### Positive Effekte

- Reduzierte Geschwindigkeitsüberschreitungen können den Kraftstoffverbrauch senken (effizientere Fahrweise → geringerer
  CO₂-Ausstoß).
- Konstantere Geschwindigkeit (frühzeitige Warnung statt abruptes Abbremsen) verringert unnötige
  Beschleunigungs-/Bremsvorgänge.
- Keine eigene Server-Infrastruktur → niedriger zusätzlicher Energiebedarf; Auslagerung auf bereits existierende offene
  Dienste (Overpass/OSM) minimiert ökologischen Fußabdruck.
- Lokales Caching reduziert wiederholte Netzaufrufe → weniger Datentransfer, indirekt geringere Rechenzentrumsbelastung.

### Negative / Neutrale Effekte

- Zusätzliche App-Nutzung erhöht marginal den Energieverbrauch des Endgeräts (GPS, Geofencing, Rendering).
- Falls Nutzer häufiger auf das Display schauen → potenziell leichte Ablenkung, indirekt ineffiziente Fahrmanöver.
- Nutzung externer Tile- und Overpass-Server verursacht dennoch Netzwerktraffic (wenn auch begrenzt durch Caching).

### Kennzahlen / Indikatoren

| KPI                                             | Ziel / Interpretation          | Messansatz                                      |
|-------------------------------------------------|--------------------------------|-------------------------------------------------|
| Durchschnittliche Geschwindigkeit vs. Limit     | Höhere Limit-Einhaltungsquote  | Optionale lokal aggregierte Statistik (Opt-in)  |
| Anzahl abrupten Geschwindigkeitswechsel (Proxy) | Reduktion gegenüber Basislinie | Lokale Heuristik (Differenz >X km/h in <Y s)    |
| Energieverbrauch der App (% Akku/h)             | <3%/h Hintergrundwarnung       | Geräteprofiling in Feldtests                    |
| Netzwerkvolumen pro aktive Stunde               | Niedrig durch Cache            | Log der übertragenen Bytes (ohne Standortdaten) |

### Maßnahmen zur Maximierung positiver Effekte

- Effiziente Distanzberechnung (Throttling) zur Minimierung Akkuverbrauch.
- UI-Design: klare Warnungen, reduzierter Interaktionsbedarf während Fahrt (Audio bevorzugt vor ständigen Blicken).
- Deutliche Einstellung zur Aktivierung energiesparender Modi (z. B. „Hintergrund sparsam“).
- Transparenz über Datenaktualität → verhindert unnötige wiederholte Updates.

### Maßnahmen zur Minimierung negativer Effekte

- Energiemonitoring lokal (Opt-in) mit Hinweis bei überdurchschnittlichem Verbrauch.
- Sanfte Warnfrequenz (kein „Spam“ bei Nähe mehrerer POIs) → weniger Displayaktivierungen.
- Bounding Box dynamisch begrenzen (nur relevante Umgebung) → weniger Netztraffic.