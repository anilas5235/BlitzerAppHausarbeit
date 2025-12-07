# Produktplan & Zeitplan

Dieses Kapitel beschreibt die strukturierte Zerlegung (Work Breakdown Structure), den Zeitplan mit Meilensteinen sowie
die Ressourcenplanung für die BlitzerApp. Fokus: rein clientseitige Entwicklung ohne eigenes Backend, Nutzung offener
Schnittstellen (Overpass/OSM), Privacy-by-Design.

Im Sinne eines agilen Vorgehens nach Scrum werden die Arbeitspakete nicht als starre, vollständig vorab geplante
Einheiten verstanden, sondern als Grundlage für ein Product Backlog. Die Umsetzung erfolgt iterativ in Sprints, in
denen jeweils ein potenziell auslieferbares Inkrement entsteht.

Hinweis: Vorgehen gemäß Scrum-Grundlagen; vgl. Scrum Guide (2020) und Agile Manifest (siehe Quellenverzeichnis).

## 4.2 Arbeitspakete (WBS)

Die Arbeitspakete beschreiben die fachlichen und technischen Bausteine, die zur Umsetzung der BlitzerApp erforderlich
sind. Jedes Arbeitspaket enthält eine kurze Beschreibung, die Ziele, erwarteten Ergebnisse (Deliverables), User Value, geschätzten
Aufwand sowie gegebenenfalls Abhängigkeiten zu anderen Paketen. Die Arbeitspakete sind in Phasen gegliedert, die jeweils
einen logischen Abschnitt des Entwicklungsprozesses darstellen. Die Arbeitspakete sind als Epics/Storys zu verstehen,
die im Rahmen der Plannings/ Refinements weiter in Tasks zerlegt und geschätzt werden müssen. Auch die Priorisierung
erfolgt dynamisch im Product Backlog. Wichtig ist, dass die Arbeitspakete als lebendige Artefakte betrachtet werden, die
im Projektverlauf angepasst und erweitert werden können, nach Absprache mit den Stakeholdern, dem Product Owner und dem
Entwicklungsteam (z. B. bei neuen Erkenntnissen, geänderten Anforderungen oder technischen Herausforderungen).

### 4.2.1 Grundlagen & MVP

#### Phase: Preparation – Grundlagen & Refinement

1. AP-A1: Refinement der MVP Anforderungen
    - Ziel: Detaillierte Verfeinerung aus Kapitel 3; MUSS/SOLL finalisieren für den MVP-Scope.
    - Deliverables: Abgenommene Anforderungsliste, Priorisierung.
    - User Value: Als Product Owner möchte ich eine klare, priorisierte Anforderungsliste für den MVP haben,
    - damit das Team Sprints zielgerichtet planen kann.
    - Abhängigkeiten: Kapitel 3 fertig.
    - Aufwand: M
2. AP-A2: Architektur-Validierung (Client-only)
    - Ziel: Bestätigung Layer-Modell, Auswahl Flutter vs. Alternative.
    - Deliverables: Architektur-Diagramm, Technologieentscheidung, Risiko-Check.
    - User Value: Als Entwickler:in möchte ich eine validierte Architektur und Technologie-Stack haben,
      damit ich mit der Implementierung des MVP beginnen kann.
    - Abhängigkeiten: AP-A1.
    - Aufwand: L
3. AP-A3: Setup Entwicklungsumgebung & Projektgerüst
    - Ziel: Repo-Struktur, CI-Basis, Linter, erste Build-Konfiguration.
    - Deliverables: Grundgerüst, README, CI-Status „grün“.
    - User Value: Als Entwickler:in möchte ich eine funktionierende Entwicklungsumgebung und ein
      initiales Projektgerüst haben, damit ich effizient mit der Implementierung beginnen kann.
    - Abhängigkeiten: AP-A2.
    - Aufwand: S

#### Phase: MVP – MVP Kern

Phase MVP stellt den MVP-Scope dar, der in einem ersten Release ausgeliefert werden kann (Sideloading).
Die Elemente AP-B1 bis AP-B6 sind Must-have für den MVP; Erweiterungen (Phase EI und EII) bauen darauf auf.
Es wird empfohlen, die Arbeitspakete in der angegebenen Reihenfolge umzusetzen, da spätere Pakete auf den
Ergebnissen früherer Pakete aufbauen. Jedoch wird nicht ausgeschlossen, dass einzelne Pakete parallelisiert oder in
abweichender Reihenfolge bearbeitet werden, sofern die Abhängigkeiten beachtet werden. Ab AP-B3 sollten Testnutzer bei
den Entwicklungen einbezogen werden (z.B. im Review), um frühes Feedback zu Funktionalität und Usability zu erhalten.

1. AP-B1: Standortbestimmung (Foreground)
    - Ziel: Live-Position mit Update-Stream.
    - Deliverables: LocationService Modul, Permission-Dialog.
    - Aufwand: S
2. AP-B2: Overpass-Abfrage + Parser
    - Ziel: Abfrage stationärer Blitzer und maxspeed (optional) für Bounding Box.
    - Deliverables: OverpassClient, QueryBuilder, Parser-Tests.
    - User Value: Als Fahrer:in möchte ich, dass Blitzerstandorte zuverlässig geladen werden, damit ich mich auf die
      Warnungen der App verlassen kann.
    - Abhängigkeiten: AP-B1.
    - Aufwand: M
3. AP-B3: Kartenintegration & Tile-Provider
    - Ziel: Anzeige Grundkarte + Attribution.
    - Deliverables: MapView, Attribution-Leiste.
    - User Value: Als Fahrer:in möchte ich eine übersichtliche Karte sehen, damit ich meine aktuelle Umgebung und
      relevante Blitzer besser einordnen kann.
    - Abhängigkeiten: AP-B1.
    - Aufwand: M
4. AP-B4: Warnlogik (Distanzberechnung + HUD + Audio)
    - Ziel: Erste visuelle/akustische Warnung beim Eintritt in konfigurierten Radius.
    - Deliverables: WarningEngine, HUD-Komponente, Basis-Sound.
    - User Value: Als Fahrer:in möchte ich frühzeitig und klar erkennbar vor Blitzern gewarnt werden, damit ich mein
      Fahrverhalten rechtzeitig anpassen kann.
    - Abhängigkeiten: AP-B2.
    - Aufwand: M
5. AP-B5: local Disclaimer & Datenschutzinfo
    - Ziel: Anzeige rechtlicher und datenschutzrelevanter Hinweise beim ersten Start.
    - Deliverables: Disclaimer-View, Persistenz-Logik.
    - User Value: Als Nutzer:in möchte ich transparent über die Datenquellen und deren Nutzung informiert, sowie die
      rechtlichen Risiken, die mit der Nutzung der App verbunden sind, informiert werden, damit ich eine bewusste
      Entscheidung
      über die Verwendung der App treffen kann.
    - Besonderheit: Muss länderspezifische Hinweise unterstützen (z.B. DE, AT, CH). Initial nur ENG/DE.
    - Abhängigkeiten: AP-B4.
    - Aufwand: S
6. AP-B6: POI-Overlay & Cache
    - Ziel: Darstellung gefundener POIs, lokaler Cache (Hive/SQLite).
    - Deliverables: CacheRepository, POI-Modelle, Overlay-Komponenten.
    - User Value: Als Fahrer:in möchte ich, dass Blitzer-Standorte auch bei kurzzeitigen Netzwerkproblemen
      verfügbar sind, damit ich kontinuierlich gewarnt werde.
    - Abhängigkeiten: AP-B2.
    - Aufwand: M
7. AP-B7: Geofencing (Hintergrundwarnungen)
    - Ziel: Energieeffiziente Hintergrundwarnungen.
    - Deliverables: GeofencingService, Testfälle.
    - Besonderheit: Enthält initial einen Spike zur Evaluierung der Plattform-Geofencing-Möglichkeiten, um technische
      Risiken frühzeitig zu reduzieren.
    - User Value: Als Fahrer:in möchte ich auch bei gesperrtem Bildschirm rechtzeitig und energieeffizient gewarnt
      werden, damit ich mich auf die Fahrt konzentrieren kann.
    - Abhängigkeiten: AP-B4.
    - Aufwand: L

### 4.2.2 AppStore-Release & Betrieb

Nach Fertigstellung des MVP-Kerns (Phase MVP) und Validierung der Grundfunktionalität folgt die Phase R, die auf
Qualitätssicherung, Release-Vorbereitung und den eigentlichen Launch abzielt. Diese Phase stellt sicher, dass die App
den Anforderungen an Stabilität, Usability und Store-Compliance entspricht.

#### Phase: R – AppStore-Release & Qualität

1. AP-R1: Testautomatisierung Ausbau
    - Ziel: ≥90% Branch Coverage kritische Logik.
    - Deliverables: Test-Suite, Coverage-Bericht.
    - User Value: Als Entwickler:in möchte ich eine umfassende Testabdeckung der kritischen Geschäftslogik
      sicherstellen, damit ich Änderungen mit Vertrauen vornehmen kann und die Stabilität der App gewährleistet ist.
    - Abhängigkeiten: Abschluss Phase MVP.
    - Aufwand: M
2. AP-R2: Beta-Test & Feedback-Auswertung
    - Ziel: Stabilitäts-/Usability-Prüfung.
    - Deliverables: Testprotokolle, Anpassungsliste.
    - User Value: Als Product Owner möchte ich durch einen Beta-Test wertvolles Feedback von echten Nutzer:innen
      erhalten, damit wir die App vor dem offiziellen Release weiter verbessern und an die Bedürfnisse der Zielgruppe
      anpassen können.
    - Abhängigkeiten: Abschluss Phase MVP.
    - Aufwand: M
3. AP-R3: App-Store Vorbereitung (Listing, Compliance)
    - Ziel: Einreichungsbereitschaft.
    - Deliverables: Beschreibung, Screenshots, Datenschutz-Formulare.
    - User Value: Als Product Owner möchte ich sicherstellen, dass die App den Anforderungen der App-Stores entspricht,
      damit der Veröffentlichungsprozess reibungslos verläuft und die App für Nutzer:innen zugänglich ist.
    - Abhängigkeiten: AP-R2.
    - Aufwand: S
4. AP-R4: Release-Kandidaten & Final Review
    - Ziel: Freigabe.
    - Deliverables: RC-Builds, Abschlusscheckliste.
    - User Value: Als Entwickler:in möchte ich sicherstellen, dass der Release-Kandidat den Qualitätsstandards
      entspricht, damit die App stabil und zuverlässig für die Nutzer:innen bereitgestellt werden kann.
    - Abhängigkeiten: AP-R3.
    - Aufwand: S

Die Phase W folgt dem Release und konzentriert sich auf die Wartung, Fehlerbehebung und das Monitoring der App im
laufenden Betrieb. Ziel ist es, die Stabilität zu gewährleisten und auf Nutzerfeedback zu reagieren. Diese Phase ist
laufend und wird über die gesamte Lebensdauer der App fortgesetzt.

#### Phase: W – Betrieb/Wartung (laufend)

1. AP-W1: Fehlerbehebungen / Patch-Zyklus
    - Ziel: Stabilität, Crashrate < 0.5%.
    - Deliverables: Bugfix-Releases, Changelog.
    - User Value: Als Nutzer:in möchte ich, dass die App regelmäßig aktualisiert wird, um Fehler zu beheben und die
      Stabilität zu gewährleisten, damit ich mich auf die Warnungen verlassen kann.
    - Aufwand: laufend.
2. AP-W2: Monitoring lokale Metriken (Opt-in)
    - Ziel: Verbesserungsdaten ohne Tracking.
    - Deliverables: Monitoring-Modul, Dashboard.
    - User Value: Als Entwickler:in möchte ich anonymisierte, lokal aggregierte Metriken sammeln können, damit ich die
      App kontinuierlich verbessern kann, ohne die Privatsphäre der Nutzer:innen zu gefährden.
    - Aufwand: S (Initial) + laufend.
3. AP-W3: Community-Feedback Auswertung
    - Ziel: Priorisierung Bugfixes/Verbesserungen.
    - Deliverables: Feedback-Log, Priorisierte ToDo-Liste.
    - User Value: Als Entwickler:in möchte ich das Feedback der Nutzer:innen systematisch auswerten können, damit ich
      gezielt auf deren Bedürfnisse eingehen und die App verbessern kann.
    - Aufwand: laufend.

### 4.2.3 Erweiterungs-Backlog

Das Erweiterungs-Backlog (Phase E) enthält optionale Features und Verbesserungen, die über den MVP-Kern hinausgehen.
Diese Features sind nicht zwingend erforderlich, bieten jedoch zusätzlichen Nutzen für dieNutzer:innen und sollten in
späteren Releases implementiert werden. Es wird empfohlen, diese Arbeitspakete nach Abschluss derPhase MVP zu
priorisieren, neu zu bewerten und in das Product Backlog aufzunehmen.

1. AP-E1: Offline-Grundfunktion (Letzte Region)
    - Ziel: Anzeige letzter POIs ohne Netz.
    - Deliverables: Cache-Ladepfad, Offline-Hinweis.
    - User Value: Als Nutzer:in möchte ich auch ohne aktive Internetverbindung vor Blitzern gewarnt werden,
      damit ich mich in Gebieten mit schlechter Netzabdeckung sicher fühle.
    - Abhängigkeiten: AP-B4.
    - Aufwand: S
2. AP-E2: OSM Notes Integration (Meldungen)
    - Ziel: Nutzer kann Note erstellen (anonym/OAuth).
    - Deliverables: NotesClient, Meldedialog, Validierung.
    - User Value: Als Nutzer: fehlende Blitzer anonym melden können, damit die Datenqualität gemeinsam verbessert wird.
    - Abhängigkeiten: AP-B3.
    - Aufwand: M
3. AP-E3: Einstellungen (Radius, Ton, Datenschutzhinweis)
    - Ziel: Persistente Konfiguration.
    - Deliverables: SettingsView, SettingsStore, Datenschutzhinweis.
    - User Value: Als Nutzer:in möchte ich die Warnradius- und Toneinstellungen an meine Bedürfnisse anpassen
      können, damit die App meinen Präferenzen entspricht.
    - Abhängigkeiten: AP-B5.
    - Aufwand: S
4. AP-E4: Performance & Energieoptimierung
    - Ziel: Einhaltung Startzeit, Latenz, Akku-Verbrauch.
    - Deliverables: Profiling-Bericht, Optimierungspatches.
    - Besonderheit: Fokus auf kritische Performance-Pfade (App-Start, Warn-Latenz) und Energieverbrauch im
      Hintergrundbetrieb. Dabei sollten auch Metriken aus dem Monitoring (AP-W2) berücksichtigt werden.
    - User Value: Als Nutzer:in möchte ich, dass die App schnell startet, Warnungen ohne Verzögerung anzeigt und
      den Akkuverbrauch minimiert, damit meine Fahrerfahrung nicht beeinträchtigt wird.
    - Abhängigkeiten: AP-W2.
    - Aufwand: M
5. AP-E5: Erweiterte Offline-Cache/Regionen
    - Ziel: Vorkonfiguration zusätzlicher Regionen.
    - Deliverables: Regionpack-Logik, Speichergrößeninfo.
    - User Value: Als Nutzer:in möchte ich zusätzliche Regionen für die Offline-Nutzung herunterladen können,
      damit ich auch in Gebieten ohne Netzabdeckung zuverlässig vor Blitzern gewarnt werde.
    - Abhängigkeiten: AP-E1, AP-B6.
    - Aufwand: M
6. AP-E6: Mehrsprachigkeit (DE/ES/FR/...)
    - Ziel: i18n Grundlagen.
    - Deliverables: Lokalisierte Strings, Umschaltlogik.
    - User Value: Als nicht-englischsprachige:r Nutzer:in möchte ich die App in meiner bevorzugten Sprache nutzen
      können, damit ich alle Funktionen und Warnungen problemlos verstehe.
    - Abhängigkeiten: AP-E3.
    - Aufwand: M
7. AP-E7: Accessibility Basis
    - Ziel: Kontraste, Labels, Screenreader-Test.
    - Deliverables: A11y-Checkliste, UI-Anpassungen.
    - User Value: Als Nutzer:in mit Assistive-Technologien möchte ich die App barrierearm bedienen können, damit
      Warnungen zuverlässig zugänglich sind.
    - Abhängigkeiten: AP-B4.
    - Aufwand: M