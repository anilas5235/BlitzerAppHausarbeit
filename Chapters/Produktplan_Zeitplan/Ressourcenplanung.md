## 4.3 Ressourcenplanung

### 4.3.1 Rollen und Kapazitäten

Rollen & grobe Kapazitäten (Annahme kleines Kernteam):

- Product Owner (0.4 FTE): Priorisierung, Store-Vorbereitung, Kommunikation.
- Mobile Entwickler:
    - Dev1 (Flutter Lead) (1.0 FTE)
    - Dev2 (Flutter/Testing) (0.8 FTE ab Phase B)
- UX/Design (0.3 FTE): UI, Accessibility, Onboarding.
- QA/Tester (0.5 FTE ab Phase C): Testplanung, Beta-Begleitung.
- Privacy/Compliance Beratung (0.1 FTE ad hoc): Prüfung Datenschutztexte, rechtliche Hinweise.
- Community Liaison (evtl. Product kombiniert) (0.1 FTE): OSM Notes Guidelines, Feedbackkanäle.

Die hier skizzierten FTE-Kapazitäten werden über die in Abschnitt 4.2 geplanten Sprints mit den in 4.1 beschriebenen
Arbeitspaketen verknüpft und bilden damit die Grundlage für die weitere Kapazitäts- und Budgetplanung.

Die Ressourcenplanung folgt dem Scrum-Prinzip eines stabilen, cross-funktionalen Teams. Der Product Owner verantwortet
Vision und Priorisierung des Product Backlogs sowie die Abnahme der Inkremente im Sprint Review. Das Entwicklungsteam
(Entwickler:innen, UX/Design, QA) liefert gemeinsam die Sprintziele und organisiert sich in der Umsetzung eigenständig.
Privacy/Compliance sowie Community Liaison werden bedarfsgerecht in Sprints eingebunden, insbesondere bei
Datenschutzthemen und Community-Funktionen.

### 4.3.2 Skills und Spezialisierungen

Die folgende Skill-Matrix zeigt, welche Kernthemen im Kernteam abgedeckt sind. Sie wird bei der Zuordnung komplexer
Arbeitspakete (z. B. Geofencing, Performance-Optimierung) zu Sprints genutzt und dient zugleich als Grundlage für die
Einschätzung von technischen Risiken und Engpässen.

Skill-Matrix (Kernthemen):

- Geodaten/Overpass: Dev1
- Performance/Energieprofiling: Dev2 + QA
- Accessibility: UX + QA
- OAuth/OSM Notes: Dev2
- Architektur/Build/CI: Dev1


### 4.3.3 Externe Ressourcen und Tools

Zusätzlich zu den personellen Kapazitäten werden einige externe Ressourcen und Werkzeuge benötigt, die vor allem die
Qualitätssicherung und Performance-Optimierung unterstützen und in die Sachkostenplanung einfließen.

Externe Ressourcen / Tools:

- Tile-Provider API-Key (Kostenmodell prüfen; Low-Usage Plan).
- Geräte/Testumgebung: Mind. 2 Android Varianten (Mid/Low), 2 iOS Generationen.
- Profiling Tools: Android Profiler, Xcode Instruments.
- CI/CD Plattform: GitHub Actions, Bitrise o. ä. (Open Source Plan bevorzugt).