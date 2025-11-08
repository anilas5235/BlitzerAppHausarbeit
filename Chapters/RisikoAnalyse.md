# 7 Risikoanalyse

Dieses Kapitel identifiziert wesentliche Risiken für die BlitzerApp (rein clientseitige Architektur, Nutzung offener
Schnittstellen), bewertet sie strukturiert und leitet präventive sowie reaktive Maßnahmen ab.

## 7.1 Identifikation von Risiken

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

## 7.2 Bewertung und Priorisierung

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

## 7.3 Maßnahmenplanung

Maßnahmen gegliedert nach Prävention (vor Eintritt), Monitoring (laufend), Reaktion (bei Eintritt). Fokus auf
Top-Risiken zuerst.

### 7.3.1 Prävention (Auswahl)

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

### 7.3.2 Monitoring

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

### 7.3.3 Reaktion (Contingency)

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

### 7.3.4 Risiko-Review Zyklus

- Frequenz: alle 4 Wochen + zu Meilensteinen.
- Verantwortlich: Produkt + Tech Lead (Abstimmung mit QA & Privacy).
- Aktualisierung: Scores anpassen anhand realer Monitoring-Daten; Neue Risiken ergänzen (z. B. Abhängigkeit von
  zusätzlicher Library für Geofencing).
- Dokumentation: Änderungsprotokoll in separatem Risiko-Register (anhängbar an Repo-Dokumentation).

### 7.3.5 Residualrisiken

Auch nach Maßnahmen verbleiben Restunsicherheiten (z. B. rechtliche Änderungen plötzlich, Overpass längere Ausfälle).
Akzeptanz begründet durch Fokus auf Transparenz (Disclaimer, Datenstand-Anzeige) und Alternativstrategien (Mirror,
Feature-Deaktivierung).

## Zusammenfassung

Die Risikoanalyse priorisiert besonders regulatorische, technische Infrastruktur- und Qualitätsrisiken. Klare präventive
Maßnahmen (Caching, Disclaimer, Architektur-Optimierung) und definierte Monitoring-Indikatoren minimieren
Eintrittswahrscheinlichkeit und Impact. Ein strukturierter Review-Zyklus schafft Anpassungsfähigkeit und unterstützt die
nachhaltige Pflege ohne eigenes Backend.

