# Iterator

## 🌍 Praktisches Beispiel
Du gehst mit einem unbändigen Hunger in ein Restaurant mit diversen Köstlichkeiten ("Container").
Dort angekommen willst du alles beim Kellner bestellen ("Iterator"), dabei interessiert dich nur ob es noch etwas zu essen gibt ("hasNext()") und das tatsächliche nächste Gericht ("next()").

## 💬 In einfachen Worten
Dieses Pattern kapselt den Zugang zu einer Sequenz (Liste) von Elementen.
Die vorliegende Datenstruktur der Elemente, Sortierung oder Aufbau der Sequenz spielen dabei keine Rolle. Somit ist die Iteration über die Elemente sauber von ihrer Struktur im Container
getrennt.

## 🖥 Beispiel

## Wann brauche ich das?
Ihr habt ein Container Element mit einer komplexen internen Darstellung seiner
Elemente, zum Beispiel viele verschachtelte Maps. Für interne Funktionen ist die Struktur
passend, allerdings macht Sie eine einfache Iteration umständlich.
Um dies für Clients trotzdem zu ermöglichen, stellt ihr ihnen einen Iterator bereit.
Dieser löst die verstrickte interne Struktur für den Client unsichtbar auf.
