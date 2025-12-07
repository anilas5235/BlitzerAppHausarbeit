**Priorisierungs-Matrix:**
* **Score ≥ 12:** Hoch (Sofortiger Handlungsbedarf, Mitigation zwingend)
* **Score 8–11:** Mittel (Beobachtung und Einplanung von Maßnahmen)
* **Score ≤ 7:** Niedrig (Akzeptanz oder einfache organisatorische Maßnahmen)

| Nr. | Risiko | Wahrsch. (1–5) | Impact (1–5) | Score | Einstufung | Begründung |
| :-- | :--- | :---: | :---: | :---: | :--- | :--- |
| **1** | **Länderrestriktionen** | **3** | **5** | **15** | **Hoch** | Rechtslage ist volatil; Auswirkung ist potenziell die Unbenutzbarkeit in Kernmärkten. |
| **2** | **App-Store Ablehnung** | **3** | **5** | **15** | **Hoch** | Kritisch für Distribution; Nachbesserungen kosten wertvolle Zeit vor Release. |
| **3** | **Overpass Rate-Limit / Down** | **4** | **4** | **16** | **Hoch** | Hohe Abhängigkeit der Kernfunktion von der API-Verfügbarkeit; keine Fallback-Infrastruktur. |
| **4** | Tile-Kostenüberschreitung | 2 | 3 | 6 | Niedrig | Durch lokales Caching und Vektor-Tiles gut kontrollierbar. |
| **5** | **OSM Datenlücken** | **4** | **3** | **12** | **Hoch** | Unvollständige Daten entwerten das Produkt direkt; Abhängigkeit von Community. |
| **6** | Falsch-positive Warnung | 3 | 3 | 9 | Mittel | Algorithmisch optimierbar, stört Nutzer, verhindert aber keine Nutzung. |
| **7** | **Performance-Latenz** | **3** | **4** | **12** | **Hoch** | Verzögerte Warnung (Startzeit, GPS-Fix) macht die App funktionslos. |
| **8** | **Energieverbrauch hoch** | **3** | **4** | **12** | **Hoch** | Führt zu Deinstallation und schlechten Bewertungen; technisch anspruchsvoll. |
| **9** | Geofencing Komplexität | 3 | 3 | 9 | Mittel | OS-Restriktionen sind bekannt, erfordern aber hohen Entwicklungsaufwand. |
| **10** | Datenschutz-Wahrnehmung | 2 | 4 | 8 | Mittel | Kann durch transparente UI/UX-Texte („Onboarding“) adressiert werden. |
| **11** | Accessibility-Mängel | 2 | 4 | 8 | Mittel | Ausschluss von Nutzergruppen; Risiko für Reputation und Store-Ranking. |
| **12** | Security-Schwachstellen | 2 | 5 | 10 | Mittel | Kritisch bei Man-in-the-Middle (falsche Daten); moderate Wahrscheinlichkeit bei TLS-Only. |
| **13** | OSM Notes Spam | 3 | 2 | 6 | Niedrig | Validierung und Rate-Limiting bei der Eingabe begrenzen den Schaden. |
| **14** | Lib-Breaking Changes | 3 | 3 | 9 | Mittel | Erfordert regelmäßige Wartung der Dependencies. |
| **15** | **Monetarisierungsdefizit** | **3** | **4** | **12** | **Hoch** | Gefährdet Nachhaltigkeit des Projekts und Motivation der Entwickler. |
| **16** | Offline-Cache Skalierung | 2 | 3 | 6 | Niedrig | Speicherplatz auf modernen Geräten meist ausreichend; Limitierung möglich. |
| **17** | Nutzer-Ablenkung | 2 | 5 | 10 | Mittel | Sicherheitsrisiko im Straßenverkehr; Haftungsfragen (Disclaimer notwendig). |
| **18** | Veraltete Datenanzeige | 3 | 3 | 9 | Mittel | Lösbar durch Timestamp-Anzeige und Zwangsaktualisierung. |
| **19** | OAuth-Fehlschläge | 3 | 2 | 6 | Niedrig | Feature (Melden) ist optional; Kernfunktion (Warnen) bleibt intakt. |
| **20** | Reputationsschaden Schulzonen | 2 | 4 | 8 | Mittel | Sensibles Thema; falsche Limits in Schulzonen wirken unprofessionell. |

**Identifizierte Top-Risiken (Score ≥ 12):** Nr. 1, 2, 3, 5, 7, 8, 15.
