# Model View ViewModel (MVVM)
Entwurfsmuster & Variante des MVC. Dient zur Trennung von Darstellung und Logik des UI. 


## Goal 
Testbarkeit verbessern und Implementierungsaufwand reduzieren, da keine separaten Controller-Instanzen erforderlich sind.Erlaubt eine Rollentrennung von UI-Designern und Entwicklern, wodurch Anwendungsschichten von verschiedenen Arbeitsgruppen entwickelt werden können.

## Aufbau
Das MVVM nutzt die funktionale Trennung des MVC-Musters von Model und View. Zur Erreichung einer losen Kopplung zwischen diesen Komponenten wird ein Datenbindungsmechanismus verwendet. Das MVVM-Muster enthält folgende drei Komponenten:

### Model
- Datenzugriffsschicht für die Inhalte, die dem Benutzer angezeigt und von ihm manipuliert werden. 
- Benachrichtigt über Datenänderungen.
- Validierung der vom Benutzer übergebenen Daten. 
- **Enthält die gesamte Geschäftslogik**.
- Durch Unit Tests überprüfbar.

### View
- Alle durch die GUI angezeigten Elemente. 
- Bindet sich an Eigenschaften des ViewModel, um Inhalte darzustellen und zu manipulieren sowie Benutzereingaben weiterzuleiten. 
- Durch die Datenbindung ist die View einfach austauschbar.

### ViewModel
- Enthält die UI-Logik (Model der View).
- Dient als Bindeglied zwischen View und obigem Model. 
- Einerseits tauscht es Information mit dem Model aus, andererseits stellt es der View öffentliche Eigenschaften und Befehle zur Verfügung. 
- Diese werden von der View an Steuerelemente gebunden, um Inhalte auszugeben bzw. UI-Ereignisse weiterzuleiten.

 
## Pro 
- Die Geschäftslogik kann unabhängig von der Darstellung bearbeitet werden.
- Die Testbarkeit verbessert sich, da die ViewModel die UI-Logiken enthalten und unabhängig von der View instanziiert werden können.
- Views können von reinen UI-Designern gestaltet werden während Entwickler unabhängig davon die Models und ViewModels implementieren.

## Con
- Höherer Rechenaufwand aufgrund des enthaltenen bidirektionalen Beobachters gewertet werden.
