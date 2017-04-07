# Model View Controller (MVC)
Muster zur Strukturierung von Software-Entwicklung in die drei Einheiten. 

## Goal
Flexibler Programmentwurf, der eine spätere Änderung oder Erweiterung erleichtert und eine Wiederverwendbarkeit der einzelnen Komponenten ermöglicht.

## Aufbau
### Modell
- Enthält die darzustellenden Daten. 
- Ist von Präsentation & Steuerung unabhängig. 
- Die Bekanntgabe von Änderungen an relevanten Daten im Modell geschieht nach Observer-Prinzip: **Das Modell ist das zu beobachtende Subjekt**.

### Präsentation
- Ist für die Darstellung der benötigten Daten aus dem Modell und die Entgegennahme von Benutzerinteraktionen zuständig. 
- Kennt sowohl ihre Steuerung als auch das Modell, dessen Daten sie präsentiert.
- Ist nicht für die Weiterverarbeitung der vom Benutzer übergebenen Daten zuständig. 
- Präsentation wird über Änderungen von Daten im Modell mithilfe des Observer-Prinzip unterrichtet und kann daraufhin die aktualisierten Daten abrufen. 

### Steuerung 
- Verwaltet eine oder mehrere Präsentationen, nimmt von ihnen Benutzeraktionen entgegen, wertet diese aus und agiert entsprechend. 
- Die Steuerung sorgt dafür, dass Benutzeraktionen wirksam werden, zB durch Änderung der Präsentation oder durch Weiterleiten an das Modell.
