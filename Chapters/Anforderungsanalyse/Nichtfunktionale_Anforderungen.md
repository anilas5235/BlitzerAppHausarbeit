## 3.2 Nicht-funktionale Anforderungen

### Performance & Effizienz

- Startzeit (Cold Start): < 2 s auf Referenzgeräten (Midrange Android, aktuelles iPhone).  
  Messung: Durchschnitt aus 10 Starts ≤ 2 s.
- Overpass-Abfrage: Antwort & Rendering typischer Stadtregion (≤ 300 relevante Nodes) < 3 s bei LTE/WLAN.  
  Messung: 95. Perzentil der Latenz ≤ 3 s.
- Hintergrundenergieverbrauch: Zusatzverbrauch durch aktive Warnbereitschaft < 3% Akku pro Stunde.  
  Messung: Monitoring über System-Profiler in Testfahrt.

### Zuverlässigkeit & Robustheit

- Fehlerquote API: < 5% Abfragen scheitern ohne erfolgreichen Retry.  
  Messung: Log-Auswertung in Test-Sessions.
- Crashrate: < 0.5% in internen Testzyklen (≥ 100 Sitzungen).  
  Messung: Crash-Log Aggregation.

### Benutzbarkeit & UX

- Warn-Latenz: Warnung erfolgt ≤ 2 s nach Eintritt in Radius (95% der Fälle).
- Verständlichkeit: Nutzer erkennt Warnung eindeutig (Icon + Farbe + Ton) – positive Bewertung in Usability-Test (> 80%
  Zustimmung).
- Konfiguration: Kernparameter (Radius, Ton) in maximal 2 Interaktionen auffindbar.

### Wartbarkeit & Erweiterbarkeit

- Modularität: Warnlogik, Overpass-Abfrage, Geofencing, UI getrennte Module/Layer (Clean Architecture / MVVM o. ä.).  
  Review: Code-Struktur dokumentiert, klare Schnittstellen.
- Testabdeckung: Mindestens 70% Branch Coverage kritischer Logik (Distanz-/Geofence-Berechnung, Parser).  
  Messung: CI-Bericht.

### Portabilität

- Unterstützte Plattformen: iOS ≥ 15, Android ≥ 8.0.  
  Abnahmekriterium: Erfolgreiches Build & Grundfunktion auf Referenzgeräten/Simulatoren.

### Skalierbarkeit (Client-seitig)

- Datenvolumen handhabbar bis zu 5.000 POIs in Cache ohne wahrnehmbare UI-Lag (> 30 fps).  
  Messung: Profiling Szenario mit künstlich erhöhter POI-Anzahl.

### Beobachtbarkeit (lokal / optional)

- Optionales lokal aggregiertes Performance-Logging (Startzeit, Overpass-Latenz) ohne externe Übertragung.  
  Review: Keine personenbezogenen Standortmetadaten im Log.