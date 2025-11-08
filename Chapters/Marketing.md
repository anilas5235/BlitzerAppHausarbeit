# 9 Marketing- und Vertriebsstrategie

Dieses Kapitel beschreibt Zielgruppen, Positionierung, Marketing-Mix und Vertriebswege für die BlitzerApp. Leitplanken sind: Privacy-by-Design (kein Tracking), rein clientseitige Architektur (kein Backend), Nutzung offener Datenquellen (OSM/Overpass) und rechtliche Konformität.

## 9.1 Zielgruppenanalyse
Primäre Segmente:
- Datenschutzbewusste Fahrerinnen/Fahrer in Ländern, in denen Blitzerwarnungen erlaubt sind  
  Bedürfnisse: Verlässliche, diskrete Warnungen; keine Profilbildung; transparente Datenquellen; geringer Akkuverbrauch.
- Pendler und Vielfahrer (urban/suburban)  
  Bedürfnisse: Stabilität im Alltag, Offline-Basisfunktion, klare und kurze Warnhinweise.
- Open-Data-/OSM-affine Nutzer  
  Bedürfnisse: Nachvollziehbare Datenherkunft; Möglichkeit, Hinweise via OSM Notes beizutragen.
- Accessibility-orientierte Nutzer  
  Bedürfnisse: Hohe Kontraste, Screenreader, reduzierte Interaktionen während der Fahrt.

Sekundäre Segmente:
- Flotten-/Dienstfahrende mit Fokus auf Compliance (sofern rechtlich zulässig).  
- Technisch Interessierte, die eine leichte, transparente Alternative zu datenintensiven Lösungen suchen.

Personas (kurz):
- „Lea, 34, Pendlerin“ – möchte stressfrei und regelkonform fahren; braucht klare, frühzeitige Warnung, keinen Konfigurationsaufwand.  
- „Jonas, 29, Datenschutz-Fan“ – akzeptiert weniger Features, wenn Privatsphäre hoch ist; wünscht Transparenz und Open-Data.

Erwartungsmanagement (Klartext):
- Fokus auf stationäre Blitzer (OSM gepflegt); mobile Messungen sind nicht Kernbestandteil.  
- Rechtliche Hinweise je Land; App kann in restriktiven Ländern deaktiviert werden.

## 9.2 Marketing-Mix (Produkt, Preis, Promotion)
Produkt (USP & Positionierung):
- Kernnutzen: Frühzeitige, verlässliche Warnung vor bekannten stationären Blitzern – datensparsam, transparent, offline-tauglich.  
- USPs: Kein Tracking/Profilbildung; offene Daten (OSM/Overpass); schlanker Energieverbrauch; klare Attributions- und Quellenangaben.
- Features für Kommunikation: Kartenansicht, konfigurierbarer Warnradius, Offline-Cache, optionale OSM Notes Meldungen, DE/EN, A11y-Basis.

Preis-/Leistungsmodell:
- Freemium: Kostenlose Kernfunktionen.  
- Optionale Einmalzahlungen (z. B. erweiterte Offline-Regionen, zusätzliche Warnsounds).  
- Keine Werbung, kein Verkauf von Daten.  
- Transparente Kostenübersicht (Verweis auf Finanzplanung/Kosten der Dienste).

Promotion (privacy-freundlich, organisch):
- App-Store-Optimierung (ASO): Relevante Keywords (z. B. „Blitzer“, „Geschwindigkeitswarner“ – je nach Store-Richtlinien), klare Screenshots (Warn-HUD, Karte), kurzes Video, DE/EN Lokalisierung.  
- Owned Media: Projektseite/README, kurze Blogposts (z. B. „Wie wir ohne Tracking warnen“), Changelogs.  
- Community: OSM-Forum/Diary (Vorstellung, Responsible Notes Guidelines), datenschutzorientierte Foren/Blogs.  
- PR leichtgewichtig: Pitch an Tech-/Privacy-Magazine mit Fokus auf „ohne Tracking“.  
- Beta-Programm: TestFlight/Play Closed Track für frühes Feedback (Latenz, Energie, A11y).  
- Social (niedrigschwellig): Kurze Updates auf Plattformen mit datenschutzfreundlicher Ausrichtung.

ASO/Messaging-Leitlinien:
- Headline: „Blitzer-Warnungen – ohne Tracking. Offen. Lokal.“  
- Key Points: „OSM-Daten“, „Offline-Cache“, „Datenschutz by Design“, „Energieeffizient“, „Rechtliche Hinweise beachten“.  
- Visuelle Assets: Karten-Screenshot mit POIs, Warn-Overlay, Einstellungen (Radius); klar sichtbare Attribution „© OpenStreetMap contributors“.

Messung (ohne personenbezogenes Tracking):
- App-Store Statistiken: Seitenaufrufe → Installationen (Conversion), Retention (D1/D7), Ratings.  
- In-App (lokal/Opt-in): Performance (Startzeit, Latenz), Energiehinweise, freiwilliges Feedback-Formular.  
- Ziele (Beispiele): 30% Store-Page → Install Conversion; Ø Bewertung ≥ 4.4; Abbruchquote Onboarding < 15%.

Go-to-Market (kurz):
- Pre-Launch: Beta mit 100–300 Testenden (2–3 Wochen), Fokus auf Latenz/Energie/A11y; Feinschliff ASO & Texte.  
- Soft-Launch: Veröffentlichung in wenigen, rechtlich unkritischen Märkten; phasenweiser Rollout (10% → 50% → 100%).  
- Launch: Presse-/Community-Post, Update der Projektseite; Monitoring von Reviews und Crash-Freiheitsrate.  
- Post-Launch: Iterative Updates, FAQ/Docs erweitern, gezielte Optimierung schwacher KPIs.

Risiken in Marketing/Kommunikation (Auszug) und Gegenmaßnahmen:
- Verwechslungsgefahr mit Echtzeit-Meldungen → Messaging betont „stationäre Blitzer, OSM-Quelle“.  
- Rechtslage-Missverständnisse → klarer Disclaimer, landesspezifische Hinweise; ggf. Feature-Deaktivierung.  
- Erwartung an „kostenlos + alles“ → früh transparent über Grenzen, Freemium-Mehrwert klar definieren.

## 9.3 Vertriebswege
Primärkanäle:
- Apple App Store (Kategorie: Navigation/Tools je Richtlinien).  
- Google Play Store (Kategorie: Karten & Navigation).  
- Optional für Privacy-Community: F-Droid/alternativer Android-Store (falls Lizenz/Build-Prozess kompatibel).  
- Beta-Distribution: TestFlight (iOS), geschlossener Track in Google Play Console.

Rollout-Strategie:
- Regionale Freigabe nach Rechtslage (Whitelist-Ansatz).  
- Staged Rollout (z. B. 10% → 50% → 100%) zur Stabilitätsbeobachtung.  
- Mindestanforderungen: iOS ≥ 15, Android ≥ 8.0; Performance-Gates (Startzeit < 2 s, Warn-Latenz ≤ 2 s).

Store-Anforderungen & Assets:
- Localized Listing (DE/EN): Kurzbeschreibung, Langbeschreibung, Screenshots, ggf. kurzes Video.  
- Privacy Policy (klar, kurz, offen): Keine Profilbildung, keine Standort-Uploads, Datenquellen & Attribution.  
- Rechtshinweise: Nutzung nur, wo zulässig; Verantwortung bleibt beim Nutzenden; Links zu Quellen.  
- Attributions: „© OpenStreetMap contributors“, ggf. Tile-Provider-Hinweise.

Support & Feedbackkanäle (ohne Tracking):
- In-App-FAQ/Info, E-Mail-Support, optional GitHub-Issues für technische Fragen.  
- Beta-Fragebogen (kurz) zu Latenz, Warnklarheit, Energieverbrauch.

KPIs Vertrieb/Qualität (Auswahl):
- Installationen pro Woche, Conversion Store-Page → Install, D1/D7 Retention.  
- Ø Bewertung und Anteil 1–2★ Reviews (Ziel: < 15%).  
- Crash-freie Sitzungen (Ziel: > 99,5%).  
- Anteil Märkte mit positivem Review-Trend nach 4 Wochen.

Abhängigkeiten & Compliance:
- Einhaltung App-Store-Richtlinien (Hintergrundortung, Berechtigungen, rechtliche Hinweise).  
- Fair-Use der Overpass/Tile-Dienste (Rate-Limits, Caching, Attribution).  
- Lizenzkonformität (OSM/Tile-Anbieter), korrekte Darstellung von Marken/Attributionen.

Zusammenfassung:
Die Vertriebs- und Marketingstrategie setzt auf organisches, datenschutzfreundliches Wachstum: klare Positionierung, starke ASO, Community-Einbindung und phasenweisen Rollout. Messung basiert primär auf Store-Kennzahlen und freiwilligem Feedback – ohne personenbezogenes Tracking. So bleibt das Wertversprechen „Warnen ohne Tracking“ glaubwürdig und differenzierend.
