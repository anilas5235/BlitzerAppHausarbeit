# 5.2 Kostenkontrolle

Dieses Kapitel beschreibt, wie die in 5.1 geplanten Kostenrahmen während des Projekts überwacht und gesteuert werden. Ziel
ist es, Transparenz über den Mittelverbrauch zu schaffen, Abweichungen frühzeitig zu erkennen und fundierte
Entscheidungen über den weiteren Projektverlauf zu ermöglichen. Die Kostenkontrolle ist eng mit dem agilen
Vorgehensmodell verknüpft und orientiert sich an den Phasen und Meilensteinen aus Kapitel 4.

## 5.2.1 Steuerungsinstrumente

Die zentralen Instrumente zur Kostenkontrolle sind:

- Phasenbezogene Kostenrahmen (vgl. 5.1.2):
  - Für jede Phase (Preparation, MVP-Kern, AppStore-Release & Qualität, erster Erweiterungszyklus, initiale
    Nachrelease-/Wartungsphase) wird ein Kostenrahmen in Personentagen und Euro definiert.
  - Diese Rahmen dienen als Orientierung für die Sprintplanung und werden nach jedem Meilenstein überprüft.
- Kosten-Burn vs. Fortschritt:
  - In regelmäßigen Abständen (z. B. pro Sprint-Review) wird gegenübergestellt, wie viele Personentage je Rolle bereits
    verbraucht sind und welche Arbeitspakete/Meilensteine erreicht wurden.
  - Dies ermöglicht eine einfache Kontrolle, ob der „Burn“ der Kosten im erwarteten Verhältnis zu den gelieferten
    Inkrementen steht.
- Velocity- und Forecast-Betrachtung:
  - Auf Basis der in den Sprints tatsächlich umgesetzten Story Points (Velocity) kann abgeschätzt werden, ob der
    verbleibende Kostenrahmen ausreicht, um die noch offenen, priorisierten Backlog-Einträge zu realisieren.
  - Bei deutlichen Abweichungen (z. B. deutlich geringerer Velocity als geplant) werden frühzeitig Anpassungen
    eingeleitet (Scope-Anpassung, Verschiebung von Erweiterungsfeatures, Nachjustierung der Kostenplanung).
- Meilensteinbezogene Reviews:
  - Zu den Meilensteinen M1–M6 (vgl. 4.2.4) wird neben dem fachlichen Fortschritt auch die Kostenseite betrachtet
    (Ist-Kosten vs. geplante Kosten je Phase).
  - Diese Meilenstein-Reviews bilden die Grundlage für Stop/Go-Entscheidungen und ggf. eine Re-Priorisierung des
    Backlogs.

Durch die Kombination dieser Instrumente wird eine laufende, datengestützte Kostenkontrolle ermöglicht, ohne das
tagessgeschäftliche Arbeiten im Scrum-Prozess zu überfrachten.

## 5.2.2 Überwachung externer Nutzung

Neben den Personalkosten müssen insbesondere die nutzungsabhängigen Sachkosten im Blick behalten werden. Im vorliegenden
Projekt betrifft dies vor allem:

- Tile-Provider API:
  - Monitoring der abgerufenen Kacheln und des daraus entstehenden Verbrauchs (z. B. über Dashboard des Providers).
  - Abgleich mit den in 5.1.3 angenommenen Kosten (Low-Usage Plan). Bei Annäherung an definierte Schwellenwerte können
    Maßnahmen ergriffen werden (z. B. stärkere Caching-Strategien, Limitierung bestimmter Kartenansichten).
- CI/CD-Build-Minuten:
  - Überwachung der genutzten Build-Minuten bei Cloud-CI-Anbietern, um unerwartete Mehrkosten zu vermeiden.
  - Gegebenenfalls Anpassung der Build-Frequenz (z. B. Nightly-Builds statt bei jedem Commit) oder Wechsel des Plans.
- Geräte- und Infrastruktur-Nutzung:
  - Sicherstellung, dass Testgeräte effizient genutzt werden (z. B. Bündelung von Testläufen), um den
    Beschaffungsaufwand niedrig zu halten.

Die Überwachung dieser externen Nutzungen kann stark automatisiert erfolgen (z. B. über Provider-Dashboards oder
Reporting-Funktionen) und wird in regelmäßigen Abständen (z. B. monatlich oder pro Phase) gemeinsam mit der
Personalkostenentwicklung betrachtet.

## 5.2.3 Entscheidungs-Trigger

Um Kostensteigerungen frühzeitig zu adressieren und das Projekt zielgerichtet zu steuern, werden klare
Entscheidungs-Trigger definiert. Beispiele:

- Kostenüberlauf in einer Phase:
  - Wenn absehbar ist, dass der Kostenrahmen einer Phase (vgl. 5.1.2) um mehr als 10–15 % überschritten wird, wird im
    Projektteam gemeinsam mit dem Product Owner eine Scope-Anpassung diskutiert.
  - Mögliche Reaktionen: Verschieben optionaler Features in spätere Erweiterungszyklen, Reduktion des Umfangs einzelner
    Arbeitspakete, gezielter Fokus auf die für den Meilenstein kritischen Funktionen.
- Negative Trends bei Velocity oder Qualität:
  - Wenn die tatsächliche Velocity über mehrere Sprints deutlich unter den Annahmen liegt oder die Anzahl kritischer
    Defects stark ansteigt, erfolgt eine Ursachenanalyse. Gegebenenfalls werden technische Schulden priorisiert oder
    zusätzliche Kapazitäten für Stabilisierung eingeplant.
- Meilenstein-Entscheidungen (M3, M4):
  - Nach M3 (MVP funktionsfähig) und M4 (Beta-Release) wird explizit geprüft, ob der bisherige Nutzen die weiteren
    Investitionen in Release- und Erweiterungsphasen rechtfertigt.
  - Entscheidungsoptionen: Voller Ausbau gemäß Plan, fokussierter Ausbau mit reduziertem Scope oder geordneter
    Projektabschluss nach MVP.
- Externe Kosten-Schwellen:
  - Erreichen bestimmter Schwellen bei API-Nutzung oder CI/CD-Kosten löst eine Überprüfung aus, ob technische oder
    vertragliche Optimierungen möglich und wirtschaftlich sinnvoll sind.

Diese Trigger sorgen dafür, dass Kostenkontrolle nicht nur retrospektiv erfolgt, sondern aktiv in den Steuerungsprozess
integriert ist.

## 5.2.4 Reporting & Transparenz

Transparente Kommunikation der Kostenentwicklung ist eine Voraussetzung dafür, dass Stakeholder fundierte Entscheidungen
mittragen und Prioritäten im Backlog nachvollziehen können. Vorgesehen ist daher ein leichtgewichtiges Reporting:

- Sprintbasiertes Kurz-Reporting:
  - Im Rahmen der Sprint Reviews werden neben fachlichen Ergebnissen auch Kennzahlen zum Ressourcenverbrauch
    vorgestellt (z. B. „verbrauchte PT je Rolle in dieser Phase“, „verbleibender Kostenrahmen der aktuellen Phase").
- Phasen- bzw. Meilensteinberichte:
  - Zu den Meilensteinen (M1–M6) wird ein komprimierter Bericht erstellt, der geplante vs. tatsächliche Personentage
    und Sachkosten gegenüberstellt und die wesentlichen Abweichungsgründe dokumentiert.
- Visualisierung:
  - Einfache Diagramme (z. B. kumulativer Kosten-Burn vs. Fortschritt nach Meilensteinen) unterstützen die schnelle
    Erfassung des Projektstatus für Management und externe Stakeholder.

Das Reporting orientiert sich am Prinzip der „information radiators“ aus der agilen Praxis: Relevante Informationen
sollen für alle Beteiligten leicht zugänglich und verständlich sein, ohne unnötige Bürokratie zu erzeugen. Auf dieser
Basis kann die in 5.1 skizzierte Kostenplanung kontinuierlich überprüft und bei Bedarf angepasst werden.
