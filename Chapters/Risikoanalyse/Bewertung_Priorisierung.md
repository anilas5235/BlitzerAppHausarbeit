## 6.2 Bewertung und Priorisierung

Bewertung nach Eintrittswahrscheinlichkeit (Wahrsch.) und Auswirkung (Impact). Score = Multiplikation (1–5).
Priorisierung: Score ≥ 12 (hoch), 8–11 (mittel), ≤7 (niedrig). Schätzungen initial; spätere Kalibrierung über
Monitoring.

| Nr. | Risiko (Kurz)                 | Wahrsch. (1–5) | Impact (1–5) | Score | Einstufung | Begründung                                                 |
|-----|-------------------------------|----------------|--------------|-------|------------|------------------------------------------------------------|
| 1   | Länderrestriktionen           | 3              | 5            | 15    | Hoch       | Unterschiedliche Rechtslage, hohe Auswirkung (Blockade)    |
| 2   | App-Store Ablehnung           | 3              | 5            | 15    | Hoch       | Kritisch für Veröffentlichung                              |
| 3   | Overpass Rate/Down            | 4              | 4            | 16    | Hoch       | Hohe Abhängigkeit, häufige Nutzung                         |
| 4   | Tile-Kostenüberschreitung     | 2              | 3            | 6     | Niedrig    | Caching möglich, kontrollierbar                            |
| 5   | OSM Datenlücken               | 4              | 3            | 12    | Hoch       | Qualität direkt auf Nutzenwirkung                          |
| 6   | Falsch-positive Warnung       | 3              | 3            | 9     | Mittel     | Berechnung verbesserbar                                    |
| 7   | Performance-Latenz            | 3              | 4            | 12    | Hoch       | Beeinträchtigt UX/Ziele                                    |
| 8   | Energieverbrauch hoch         | 3              | 4            | 12    | Hoch       | Nutzerakzeptanz & Store-Ratings                            |
| 9   | Geofencing Komplexität        | 3              | 3            | 9     | Mittel     | Technische Hürden aber lösbar                              |
| 10  | Datenschutz-Wahrnehmung       | 2              | 4            | 8     | Mittel     | Kommunikation gestaltbar                                   |
| 11  | Accessibility-Mängel          | 2              | 4            | 8     | Mittel     | Früh adressieren vermeidet Nacharbeit                      |
| 12  | Security-Schwachstellen       | 2              | 5            | 10    | Mittel     | Kritische Auswirkung, moderate Eintrittswahrscheinlichkeit |
| 13  | OSM Notes Spam                | 3              | 2            | 6     | Niedrig    | Eingabevalidierung & Limits helfen                         |
| 14  | Lib-Breaking Changes          | 3              | 3            | 9     | Mittel     | Abhängigkeiten regelmäßig pflegen                          |
| 15  | Monetarisierungsdefizit       | 3              | 4            | 12    | Hoch       | Nachhaltigkeit gefährdet                                   |
| 16  | Offline-Cache Skalierung      | 2              | 3            | 6     | Niedrig    | Kontrollierbare Architektur                                |
| 17  | Nutzer-Ablenkung              | 2              | 5            | 10    | Mittel     | UI/Interaktionsdesign & Hinweise                           |
| 18  | Veraltete Datenanzeige        | 3              | 3            | 9     | Mittel     | Timestamp Anzeige lösbar                                   |
| 19  | OAuth-Fehlschläge             | 3              | 2            | 6     | Niedrig    | Optionales Feature                                         |
| 20  | Reputationsschaden Schulzonen | 2              | 4            | 8     | Mittel     | Datenvalidierung & Disclaimer                              |

Top-Risiken (Score ≥ 12): Nr. 1,2,3,5,7,8,15.