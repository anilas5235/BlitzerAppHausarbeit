## 6.3 Maßnahmenplanung

Die Risikobehandlung folgt dem Ansatz der Risikovermeidung (Prevention), der frühzeitigen Erkennung (Monitoring) und der planvollen Reaktion (Contingency).

### 6.3.1 Präventive Maßnahmen (Risikominimierung)
Diese Maßnahmen fließen direkt in das Architekturdesign und das Backlog ein.

| Risiko-Ref. | Maßnahme | Umsetzung / Detail |
| :--- | :--- | :--- |
| **1, 2 (Legal)** | **Dynamisches Feature-Toggling & Compliance** | Implementierung eines Geofencing-Checks beim Start: In Verbotszonen (z. B. Schweiz) deaktiviert sich die Warnfunktion automatisch. Anzeige juristischer Disclaimer beim ersten App-Start (Terms of Use). |
| **3 (API)** | **Intelligentes Caching & Backoff** | Nutzung lokaler Datenbanken (z. B. Room/SQLite) zur Speicherung von Kartendaten (TTL-Strategie: z. B. 7 Tage). Implementierung von *Exponential Backoff* bei HTTP-Fehlern, um Server-Bans zu vermeiden. Nutzung kleiner Bounding-Boxes statt großer Gebietsabfragen. |
| **5 (Daten)** | **Community Integration & Filter** | Implementierung eines „Datenqualitäts-Layers“: Anzeige, wann Daten zuletzt aktualisiert wurden. Einfache UI zur Meldung von Fehlern via OSM Notes API, um die Datenbasis organisch zu verbessern. |
| **7 (Perf.)** | **Asynchrone Verarbeitung** | Strikte Trennung von UI-Thread und Datenverarbeitung. Einsatz von *Kotlin Coroutines* für Netzwerk/DB-Operationen. Lazy Loading von Kartenelementen nur im sichtbaren Bereich (Viewport). |
| **8 (Energie)** | **Fused Location Provider** | Verwendung der OS-eigenen optimierten Standort-APIs (Google Fused Location / iOS Core Location) statt rohem GPS, wo möglich. Reduktion der Polling-Frequenz bei Stillstand oder langsamer Bewegung. |
| **12 (Sec)** | **Transport Security & Storage** | Erzwingung von HTTPS für alle Verbindungen (Network Security Config). Keine Speicherung sensibler Daten im Klartext; Nutzung der `EncryptedSharedPreferences` bzw. iOS Keychain. |
| **15 (Geld)** | **Lean Monetization** | MVP-Start mit Spendenmodell oder optionalem „Pro“-Feature (z. B. Dark Mode, Offline-Karten) statt aggressiver Werbung, um Nutzerbasis nicht zu verschrecken. Validierung der Zahlungsbereitschaft in Beta-Phase. |

### 6.3.2 Monitoring und Risiko-Indikatoren
Da keine zentrale Server-Infrastruktur für Logging zur Verfügung steht, muss das Monitoring dezentral oder über anonymisierte Telemetrie (opt-in) erfolgen.

| Risiko | Indikator | Messmethode / Tool | Schwellenwert (Alert) |
| :--- | :--- | :--- | :--- |
| **Overpass** | Fehlerrate (HTTP 429/50x) | Client-seitiges Error-Reporting (z. B. via Sentry - DSGVO-konform). | > 5 % aller Requests fehlgeschlagen |
| **Performance** | App-Startzeit (Cold Start) | Automatisiertes Profiling in CI/CD Pipeline & Beta-Telemetrie. | Ø > 2.0 Sekunden |
| **Energie** | „Battery Drain“ Meldungen | Auswertung von App-Store-Rezensionen und Support-Mails (Keyword-Analyse). | Häufung nach Release (> 3 Nennungen/Woche) |
| **Daten** | Abdeckungsgrad | Stichprobenartiger manueller Vergleich von OSM-Daten mit Referenzstrecken. | Signifikante Lücken in Großstädten |
| **Legal** | Store-Status | Überwachung des App-Store-Status und der Policy-Updates von Apple/Google. | Änderung Status „Rejected“ / Policy Change |

### 6.3.3 Reaktive Maßnahmen (Contingency Plans)
Strategien für den Fall, dass ein Risiko trotz Prävention eintritt.

* **Bei API-Ausfall (Overpass Down):** Automatischer Wechsel auf definierte Mirror-Server (Fallback-URL-Liste in der App hinterlegt). Sollten alle Mirror ausfallen: Anzeige „Offline-Modus / Datenstand [Datum]“ und Deaktivierung der Live-Update-Versuche für einen definierten Zeitraum (Backoff).
* **Bei App-Store Ablehnung:** Sofortige Analyse der Ablehnungsgründe. Bereithaltung einer „Lite-Version“ ohne kritische Funktionen (nur Kartenanzeige, keine Warnung) als Fallback, um zumindest im Store präsent zu sein, während rechtliche Klärung erfolgt.
* **Bei kritischen Sicherheitslücken:** Etablierter „Hotfix-Prozess“: Umgehung des regulären Sprint-Zyklus, Fix innerhalb von 48h, Beantragung eines „Expedited Review“ bei Apple/Google.
* **Bei Monetarisierungsproblemen:** Pivotierung des Modells (z. B. Wechsel von Einmalkauf zu Abo oder Einführung von Sponsoring durch lokale Partner), begleitet von Nutzerumfragen zur Preissensitivität.

## 6.4 Review-Zyklus und Residualrisiken

Die Risikoanalyse ist ein lebendes Dokument und erfordert regelmäßige Überprüfung:
1.  Am Ende jeder Entwicklungsphase (Meilenstein).
2.  Bei Einführung neuer externer Bibliotheken.
3.  Bei signifikanten Änderungen der OSM-Datenstruktur oder Store-Guidelines.

**Residualrisiken (Restrisiken):**
Trotz umfassender Maßnahmen verbleiben Restrisiken, insbesondere die **Abhängigkeit von Dritten** (OSM-Community für Daten, Overpass-Betreiber für API). Da die App keine eigene Datenhoheit besitzt, muss akzeptiert werden, dass die Datenqualität schwanken kann. Dieses Risiko wird durch Transparenz gegenüber dem Nutzer (Disclaimer: „Daten basieren auf OpenStreetMap“) mitigiert, aber nicht eliminiert. Ebenso bleibt das **rechtliche Restrisiko** bestehen, da sich Gesetze schneller ändern können, als Software-Updates verteilt werden.
