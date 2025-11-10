## 4.3 Ressourcenplanung

Rollen & grobe Kapazitäten (Annahme kleines Kernteam):

- Product Owner (0.4 FTE): Priorisierung, Store-Vorbereitung, Kommunikation.
- Mobile Entwickler:
    - Dev1 (Flutter Lead) (1.0 FTE)
    - Dev2 (Flutter/Testing) (0.8 FTE ab Phase B)
- UX/Design (0.3 FTE): UI, Accessibility, Onboarding.
- QA/Tester (0.5 FTE ab Phase C): Testplanung, Beta-Begleitung.
- Privacy/Compliance Beratung (0.1 FTE ad hoc): Prüfung Datenschutztexte, rechtliche Hinweise.
- Community Liaison (evtl. Product kombiniert) (0.1 FTE): OSM Notes Guidelines, Feedbackkanäle.

Skill-Matrix (Kernthemen):

- Geodaten/Overpass: Dev1
- Performance/Energieprofiling: Dev2 + QA
- Accessibility: UX + QA
- OAuth/OSM Notes: Dev2
- Architektur/Build/CI: Dev1

Auslastungsüberblick vs. Phasen (qualitativ):

- Phase A: PO, Dev1, UX (gering), Privacy.
- Phase B: Dev1 hoch, Dev2 mittel, UX startet UI-Feinschliff.
- Phase C/D: Dev1+Dev2 hoch, QA steigt ein, UX für Accessibility/i18n.
- Phase E: QA hoch (Tests/Beta), PO für Store, Devs Performance & Stabilität.
- Phase F: Devs Wartung, QA Monitoring leicht, PO Feedback.

Externe Ressourcen / Tools:

- Tile-Provider API-Key (Kostenmodell prüfen; Low-Usage Plan).
- Geräte/Testumgebung: Mind. 2 Android Varianten (Mid/Low), 2 iOS Generationen.
- Profiling Tools: Android Profiler, Xcode Instruments.

Risikofaktoren Ressourcen:

- Engpass Geofencing-Spezialwissen → frühzeitige Spike in Phase B.
- Verzögerung durch Performance-Probleme → gezieltes Profiling in AP-D2 statt zu spät.
- i18n/A11y unterschätzt → separate kleine Meilensteine (C2/C3) statt „am Ende“.

Strategie für Skalierung (falls mehr Nutzer/Feature-Wünsche):

- Add-On weiterer Dev für Feature-Phase D/E.
- Separater Support/Community-Manager bei steigendem Meldungsvolumen.