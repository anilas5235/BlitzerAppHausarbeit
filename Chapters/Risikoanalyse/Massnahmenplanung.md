## 6.3 Maßnahmenplanung

Maßnahmen gegliedert nach Prävention (vor Eintritt), Monitoring (laufend), Reaktion (bei Eintritt). Fokus auf
Top-Risiken zuerst.

### 6.3.1 Prävention (Auswahl)

| Risiko                | Präventive Maßnahmen                                                                                                                         |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 1 Länderrestriktionen | Länder-Liste + Disclaimer beim ersten Start; Feature-Deaktivierung per Geofencing/Locale falls untersagt; klare Rechtsquellen dokumentieren. |
| 2 App-Store Ablehnung | Frühzeitige Prüfung Store-Guidelines; Testbuilds/Pre-Review; klare Nutzungserklärung für Hintergrundortung und Datenschutz-Text.             |
| 3 Overpass Rate/Down  | Caching (TTL), kleinere Bounding Boxes, Exponential Backoff, Fallback Mirror-Liste; User-Agent Kennzeichnung.                                |
| 5 OSM Datenlücken     | Nutzerfreundliche OSM Notes Einbindung; Datenqualität-Tooltips; Distanzfilter und Tag-Validierung; FAQ Transparenz zu Grenzen.               |
| 7 Performance-Latenz  | Profiling früh (Prototyp), Lazy Loading, effiziente Rendering-Pipeline (Cluster / minimal Rebuilds), Code Reviews.                           |
| 8 Energieverbrauch    | Geofencing statt Polling; Standort-Update Throttling; Nutzung Plattform APIs (significant changes).                                          |
| 15 Monetarisierung    | Früh Monetarisierungsstrategie definieren (Freemium/Spenden); Kosten-/Wertkommunikation im Beta-Test validieren.                             |
| 12 Security           | TLS-only, sichere Storage APIs (Keystore/Keychain); Dependency Audit; kein sensibler Klartext; automatisierte Dependency Scans.              |
| 11 Accessibility      | Checklisten ab MVP, Design-Kontraste prüfen, Screenreader-Labels sofort setzen.                                                              |

### 6.3.2 Monitoring

| Risiko               | Monitoring-Indikator             | Schwellenwert            | Tool/Mechanismus                       |
|----------------------|----------------------------------|--------------------------|----------------------------------------|
| 3 Overpass Rate/Down | Fehlerrate (%)                   | >20% Fehler in 1 Tag     | Lokales Log + Analyse Skript           |
| 7 Performance        | Startzeit (s)                    | >2.2 s Ø                 | Profiling / automatisierte Messung     |
| 8 Energie            | Akku-Verbrauch (%/h)             | >3.5%                    | Feldtests / Geräteprofile              |
| 5 Datenlücken        | % POI-Abdeckung Testregion       | < definiertem Basiswert  | Vergleich mit Referenz-Export          |
| 15 Monetarisierung   | Conversion (%)                   | < Zielwert (2%)          | Release-Bewertungen/Interne Auswertung |
| 12 Security          | Anzahl offene kritische Findings | >0                       | Dependency Scan Report                 |
| 11 Accessibility     | Anzahl WCAG Verstöße (kritisch)  | >5                       | A11y-Scanner / man. Tests              |
| 18 Datenaktualität   | Zeit seit letztem Update (min)   | >30 (Stadt), >120 (Land) | Timestamp Anzeige + Log                |

### 6.3.3 Reaktion (Contingency)

| Risiko                       | Reaktionsstrategie bei Eintritt                                                                           |
|------------------------------|-----------------------------------------------------------------------------------------------------------|
| 3 Overpass Down              | Umschalten auf Mirror; Reduktion Query-Frequenz; Nutzerhinweis „Datenstand alt“.                          |
| 1 Länderrestriktion entdeckt | Sofortige Deaktivierung kritischer Warnfunktionen; Info-Dialog; Prüfung zukünftiger Feature-Limits.       |
| 2 Store Ablehnung            | Analyse der Reviewer-Kommentare; Anpassung Texte/Berechtigungen; erneute Einreichung ≤ 1 Woche.           |
| 7 Performanceverzug          | Fokus-Sprint Optimierung (Profiling → Code Hotspots); ggf. Feature-Freeze.                                |
| 8 Energie zu hoch            | Reduktion Update-Frequenz, optimieren Distanzberechnung, Deaktivierung nicht-kritischer Hintergrundtasks. |
| 5 Datenlücken gravierend     | Kommunikationshinweis („Region unvollständig“); gezielte Community-Aufruf via Notes Anleitung.            |
| 15 Monetarisierung verfehlt  | Anpassung Preis/Mehrwert, Launch Spendenkampagne, Evaluierung Fördermittel.                               |
| 12 Security Finding          | Patch/Update innerhalb definierter SLA (kritisch ≤72h); Security Review nach Fix.                         |
| 11 Accessibility Kritik      | Priorisierte UI-Anpassung nächster Sprint; Nutzerfeedback einholen zur Lösung.                            |
| 18 Veraltete Daten           | Erzwungenes Refresh bei Überschreitung Schwelle; visuelle Warnung.                                        |

### 6.3.4 Risiko-Review Zyklus

- Frequenz: alle 4 Wochen + zu Meilensteinen.
- Verantwortlich: Produkt + Tech Lead (Abstimmung mit QA & Privacy).
- Aktualisierung: Scores anpassen anhand realer Monitoring-Daten; Neue Risiken ergänzen (z. B. Abhängigkeit von
  zusätzlicher Library für Geofencing).
- Dokumentation: Änderungsprotokoll in separatem Risiko-Register (anhängbar an Repo-Dokumentation).

### 6.3.5 Residualrisiken

Auch nach Maßnahmen verbleiben Restunsicherheiten (z. B. rechtliche Änderungen plötzlich, Overpass längere Ausfälle).
Akzeptanz begründet durch Fokus auf Transparenz (Disclaimer, Datenstand-Anzeige) und Alternativstrategien (Mirror,
Feature-Deaktivierung).

## Zusammenfassung

Die Risikoanalyse priorisiert besonders regulatorische, technische Infrastruktur- und Qualitätsrisiken. Klare präventive
Maßnahmen (Caching, Disclaimer, Architektur-Optimierung) und definierte Monitoring-Indikatoren minimieren
Eintrittswahrscheinlichkeit und Impact. Ein strukturierter Review-Zyklus schafft Anpassungsfähigkeit und unterstützt die
nachhaltige Pflege ohne eigenes Backend.