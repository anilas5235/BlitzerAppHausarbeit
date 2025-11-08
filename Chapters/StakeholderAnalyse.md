# 4 Stakeholder-Analyse

Dieses Kapitel identifiziert die relevanten Stakeholder der BlitzerApp, beschreibt ihre Bedürfnisse und Erwartungen und
definiert einen praxistauglichen Kommunikationsplan.

## 4.1 Identifikation der Stakeholder

- Endnutzerinnen und Endnutzer (Fahrerinnen/Fahrer)
    - Nutzen die App zur frühzeitigen Warnung vor stationären Blitzern; hohe Sensibilität für Datenschutz, Genauigkeit
      und Energieverbrauch.
- OpenStreetMap-Community (Mapper, Reviewer)
    - Pflegt die Datenbasis; wertet Hinweise (z. B. OSM Notes) aus und erwartet sinnvolle, gut begründete Meldungen.
- Overpass-API-Betreiber und Mirror-Hosts
    - Stellen die Abfrage-Infrastruktur bereit; erwarten Fair Use (Rate-Limits, Timeouts, Lastverteilung).
- Karten-Tile-Provider
    - Liefern Kartenkacheln; erwarten korrekte Attribution, API-Key-Schutz und Einhaltung von Nutzungsbedingungen.
- App-Store-Betreiber (Apple, Google)
    - Prüfen die App auf Richtlinienkonformität (Hintergrundortung, Datenschutz, lokale Rechtslage bei
      Blitzerwarnungen).
- Rechtliche/Regulatorische Akteure (indirekt)
    - Gesetzliche Rahmenbedingungen je Land; Einfluss auf erlaubte Funktionen und Hinweise in der App.
- Projektteam (Produkt, Entwicklung, Test)
    - Verantwortlich für Umsetzung, Qualitätssicherung, Compliance und nachhaltige Wartbarkeit.
- Test- und Pilotnutzer (Beta)
    - Geben frühes Feedback zu Usability, Latenz, Genauigkeit, Energieverbrauch.
- Accessibility-Nutzer (A11y)
    - Erfordern barrierefreie Gestaltung (Kontraste, Screenreader, große Schrift).

## 4.2 Bedürfnisse und Erwartungen

- Endnutzerinnen/Endnutzer
    - Verlässliche Warnungen mit geringer Latenz; klare, nicht aufdringliche Hinweise.
    - Datenschutz ohne Tracking/Profilbildung; volle Transparenz über Datenquellen.
    - Niedriger Energieverbrauch; Offline-Basisfunktionalität.
    - Einfache Konfiguration (Radius, Ton) und verständliche Rechtshinweise.
- OSM-Community
    - Qualitativ gute Notes: präzise Position, klare Begründung, keine Duplikate/Spam.
    - Respekt der Community-Prozesse; kein automatisiertes Mass-Posting.
    - Attribution und Förderung von Datenqualität (z. B. Hinweise auf Veraltetes).
- Overpass-Operatoren
    - Schonende Nutzung: kleine Bounding Boxes, Caching, Backoff bei 429/Timeout.
    - Klare Kennzeichnung des User-Agent und Einhaltung von Policies.
- Tile-Provider
    - Begrenzte Kachelabrufe (Caching), korrekte Attribution, Schutz des API-Keys.
- App Stores
    - Richtlinienkonforme Hintergrundortung (Begründung, Opt-in-Dialoge).
    - Disclaimer zu rechtlicher Lage; keine verbotenen Funktionen in restriktiven Ländern.
    - Transparenter Datenschutz-Text, minimierte Datenverarbeitung.
- Rechtliche/Regulatorische Akteure
    - Einhaltung nationaler Vorgaben; deaktivierbare Features; deutliche Nutzerhinweise.
- Projektteam
    - Klare Anforderungen, messbare Kriterien, robuste Architektur, geringe Betriebskosten (kein Backend).
- Beta-/Pilotnutzer
    - Einfache Feedback-Kanäle, sichtbare Umsetzung relevanter Rückmeldungen.
- Accessibility-Nutzer
    - WCAG-konforme Kontraste, skalierbare Schrift, korrekte Labels/Lesereihenfolge.

## 4.3 Kommunikationsplan

Ziele: Transparenz, Policy-Konformität, frühes Feedback und kontinuierliche Qualitätsverbesserung – bei minimaler
externer Datenübertragung.

- Richtung Endnutzerinnen/Endnutzer
    - Kanäle: In-App-Info/FAQ, Onboarding, Release Notes (App-Store), optional Website/README.
    - Inhalte: Funktionsüberblick, Datenschutz, rechtliche Hinweise, Changelog, bekannte Einschränkungen.
    - Frequenz: Zu Releases (MVP, Minor/Feature), bei Policy-Änderungen.
    - Verantwortlich: Produkt/Entwicklung.

- Richtung OSM-Community
    - Kanäle: In-App-Hinweise zur Note-Qualität; Projektseite (z. B. GitHub/Docs) mit „Responsible Notes Guidelines“;
      ggf. OSM-Forum/Diary für Vorstellung.
    - Inhalte: Fair-Use, Note-Etikette, technische Details (User-Agent), keine automatisierten Mass-Notes.
    - Frequenz: Einmalige Vorstellung + Updates bei relevanten Änderungen.
    - Verantwortlich: Produkt/Tech Lead.

- Richtung Overpass-/Tile-Provider
    - Kanäle: Öffentliche Dokumentation befolgen; falls nötig Kontakt per E-Mail/Issue (nur bei Störungen/Koordination).
    - Inhalte: User-Agent, Abfrageprofile, Hinweise zu Caching/Backoff, Attribution.
    - Frequenz: Ad hoc bei Bedarf; ansonsten passiv (Policy-konforme Nutzung).
    - Verantwortlich: Tech Lead.

- Richtung App Stores (Apple/Google)
    - Kanäle: Store-Listing, Review-Notizen, Datenschutzfragebögen, Berechtigungsbegründungen.
    - Inhalte: Zweck der Hintergrundortung, Länderhinweise/Disclaimer, Datenschutz-Statement, Attributionsangaben.
    - Frequenz: Zu Einreichungen/Updates.
    - Verantwortlich: Produkt/Release-Management.

- Richtung Beta-/Pilotnutzer
    - Kanäle: TestFlight/Closed Track, In-App-Feedback-Formular (ohne personenbezogene Telemetriedaten), E-Mail.
    - Inhalte: Testziele (Latenz, Genauigkeit, Energie), bekannte Issues, kurzer Fragebogen.
    - Frequenz: Vor jeder Testwelle, Abschlussreport.
    - Verantwortlich: QA/Produkt.

- Richtung Accessibility-Community
    - Kanäle: Accessibility-Scanner-Reports, gezielte Tests mit Screenreader-Nutzenden, kurze Leitfäden in Docs.
    - Inhalte: A11y-Verbesserungen, bekannte Hürden, Roadmap.
    - Frequenz: Vor wichtigen Releases.
    - Verantwortlich: UX/QA.

- Interne Teamkommunikation
    - Kanäle: Kanban/Issue-Tracker, technische Doku, kurze Weekly-Reviews.
    - Inhalte: Fortschritt, Blocker, Qualitätsmetriken (Startzeit, Overpass-Latenz, Warn-Latenz, Energie).
    - Frequenz: Wöchentlich; vor Release Meilenstein-Check.
    - Verantwortlich: Produkt/Tech Lead.

Risiken in der Kommunikation & Gegenmaßnahmen:

- Missverständnisse zu rechtlicher Lage → Klare, landesspezifische Hinweise und Opt-out/Deaktivierung.
- Community-Überlastung durch unsaubere Notes → In-App-Guidelines, Validierung, Limits pro Zeit.
- Übernutzung von Overpass/Tiles → Caching, Backoff, kleinere Bounding Boxes, alternative Endpunkte.
- Datenschutzbedenken → Transparente Texte, lokale Logs ohne Standortverläufe, kein Zwangs-Analytics.

