# 3 Anforderungsanalyse

## 3.1 Funktionale Anforderungen

Anforderungsanalyse:  (Quelle Methodik: Broy, M., Kuhrmann, M. (2021). Anforderungsanalyse und Anforderungsmanagement. In: Einführung in die Softwaretechnik. Xpert.press. Springer Vieweg, Berlin, Heidelberg. https://doi.org/10.1007/978-3-662-50263-1_5), https://eur-lex.europa.eu/legal-content/DE/TXT/PDF/?uri=CELEX:32016R0679


-> nochmal zusammen drüberschauen ob Anforderungen so passen, ggf. ergänzen!


Die Anforderungsanalyse bildet das Fundament für die zielgerichtete Entwicklung der Blitzer-App und stellt sicher, dass das geplante System sowohl technisch realisierbar als auch für Nutzer sinnvoll einsetzbar ist. Durch die systematische Erfassung der Anforderungen wird klar bestimmt welche Funktionen zwingend benötigt werden, welche Qualitätsstandards erreicht werden müssen und welche rechtlichen Rahmenbedingungen zwingend einzuhalten sind. Auf dieser Basis lassen sich Entwicklungsrisiken erheblich reduzieren, technische Abhängigkeiten frühzeitig erkennen und der später notwendige Entwicklungsaufwand realistisch einschätzen.

Die Anforderungen setzen sich aus mehreren Quellen zusammen. Sie ergeben sich vor allem aus den Erkenntnissen der Markt- und Situationsanalyse, insbesondere aus den dort identifizierten Nutzerbedürfnissen, Funktionalitäten der Konkurrenzapps sowie technischen und rechtlichen Rahmenbedingungen. Zusätzlich ergeben sich Anforderungen aus der Stakeholderanalyse, da die unterschiedliche Interessengruppen jeweils spezifische Erwartungen und Einschränkungen mitbringen.

Um die Anforderungen klar strukturiert und nachvollziehbar abbilden zu können, werden diese in drei Kategorien unterteilt: funktionale Anforderungen, Qualitätsanforderungen sowie rechtliche Anforderungen. Diese Gliederung dient nicht nur der besseren Übersicht, sondern ermöglicht auch eine zielgerichtete Entwicklung und spätere Überprüfung der App.

Die funktionalen Anforderungen beschreiben die Kernfunktionalitäten die die App bereitstellen muss, um den identifizierten Nutzerbedürfnissen gerecht zu werden. Dazu zählen insbesondere der Abruf relevanter Blitzerdaten über externe APIs, die präzise Bestimmung des aktuellen Nutzerstandorts, die visuelle Darstellung von Blitzern in einer Karte sowie die Berechnung und Ausgabe von Echtzeitwarnungen basierend auf Entfernung, Fahrtrichtung und Geschwindigkeit. Ergänzt wird dies durch Funktionen wie akustische Warnungen, visuelle Hinweise, eine optionale Registrierung sowie Crowdsourcing-Mechanismen, die die Datenqualität durch Benutzerbeiträge verbessern sollen. Auch eine Monetarisierungslogik ist notwendig um die App wirtschaftlich nutzbar machen zu können.

Qualitätsanforderungen konkretisieren welche Features dazu beitragen die App qualitativ zu gestalten und von anderen Apps abzuheben. Bei einer sicherheitsrelevanten Anwendung wie einer Blitzer-App sind diese Anforderungen besonders wichtig, da Nutzer unmittelbar auf zuverlässige und möglichst präzise Warnungen angewiesen sind. Zu diesen Anforderungen gehören unter anderem eine hohe technische Verfügbarkeit, eine stabile Performance, intuitive Bedienbarkeit und eine angemessene Energieeffizienz. Konkrete Zielwerte helfen dabei, diese Anforderungen eindeutig messbar zu formulieren. So wird eine Verfügbarkeit der App-Funktionen von mindestens 99 %, eine Datenaktualität von unter 5 Sekunden beim Laden neuer Blitzer, ein maximaler Akkuverbrauch von unter 5 % pro Stunde Nutzung und eine sichere Kommunikation zwischen App und externen APIs angestrebt. Weitere Qualitätskriterien betreffen die Skalierbarkeit, etwa die einfache Anpassung an jeweilige Länder, Mehrsprachigkeit, geringe mobile Datenlast sowie eine solide Nutzerfreundlichkeit, die eine sichere und intuitive Nutzung ermöglicht.

Die dritte Kategorie umfasst rechtliche Anforderungen, die bei einer App, die Standortdaten verarbeitet, äußerst relevant sind. Die Anwendung muss vollständig DSGVO-konform sein, was die klare Einholung einer Einwilligung zur Standortverarbeitung, eine transparente Datenschutzerklärung und eine Minimierung der erfassten Daten einschließt. Da die Rechtslage innerhalb der EU nicht einheitlich ist muss die App zusätzlich Mechanismen bereitstellen, um diese Unterschiede zu berücksichtigen. Beispielsweise ist die Nutzung reiner Warnfunktionen in einigen Ländern zulässig, in anderen jedoch teilweise verboten oder nur eingeschränkt erlaubt. Dazu gehören etwa länderspezifische Hinweise, automatische Einschränkungen bestimmter Funktionen oder eindeutige Haftungsinformationen, die klarstellen, dass die Verantwortung für die Nutzung beim Anwender liegt.

Durch die Kombination der drei Anforderungskategorien entsteht ein umfassendes Bild darüber, was die App leisten soll, wie zuverlässig sie funktionieren muss und welche gesetzlichen Rahmenbedingungen zwingend einzuhalten sind. Die Sammlung der Anforderungen dient vor allem der Projektplanung und stellt dabei insbesondere sicher, dass die spätere Entwicklung anhand von eindeutigen Anforderungen umgesetzt werden kann.

<img width="614" height="598" alt="image" src="https://github.com/user-attachments/assets/0dd337d4-9f99-4051-b703-18d09d9404c2" />




