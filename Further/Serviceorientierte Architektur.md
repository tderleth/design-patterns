# Serviceorientierte Architektur (SOA)

Serviceorientierte Architekturen (SOA) orientieren sich an Geschäftsprozessen des Unternehmens und fördern die Wiederverwendung von Anwendungsteilen.

Selbst wenn Anwendungen sauber aufgebaut sein sollten, ist es schwierig, Teile der Anwendungen für andere Zwecke einzusetzen. In einer **Serviceorientierte Architektur** werden die Anwendungen in wiederverwendbare Services aufgeteilt, zu denen **öffentliche Schnittstellen** existieren.

## Besipiel

Es besteht die Anforderung an mehrere Anwendungen, Ansichten in PDF-Dokumente zu konvertieren. Die einzelnen Anwendungen implementieren die Anforedrung / den Service nun nicht jeweils selbst innerhalb der eigenen Anwendung sondern es wird ein singulärer Service implementiert, der für alle Anwendungen Dokumente an einer zentralen Stelle zeugen kann.

## Pro

- Wissen über den singulären Service liegt bei einem Team, das den Service verwaltet, und ist nicht verstreut in allen Anwendungsteams.
- Es gibt eine zentrale Stelle, die gewartet und verbessert werden muss.
- Dem Servicekonsumenten ist vollkommen egal, welche Implementierung mit welchem Framework sich hinter dem Service verbirgt.
- Gutes Servicedesign erlaubt es der IT, Datenbankschemata und Frameworks einfach hinter einer Fassade auszutauschen.

## Con

- Aufbau des Service kostet Zeit, da Anforderungen für den Service selbst nun alle Anwendungsfälle abdecken muss.
- Service muss skalierbar sein, da nun viele Anwendungen darauf zugreifen und nicht mehr nur eine einzelne.

## Sources

- <http://www.computerwoche.de/a/soa-richtig-verstehen-und-verwenden,3070966>
