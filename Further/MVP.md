# Model View Presenter (MVP)
Entwurfsmuster, das aus dem Model-View-Controller (MVC) hervorgegangen ist. Ansatz, um Modellund die Ansicht komplett voneinander zu trennen und über einen Präsentator zu verbinden.

## Goal 
Testbarkeit durch strengere Trennung der einzelnen Komponenten. Damit MVP seine Vorteile gegenüber MVC entfalten kann, werden für Modell und Ansicht jeweils Interfaces verwendet. Diese definieren den Aufbau beider Schichten und der Präsentator verknüpft lediglich die Schnittstellen miteinander. Dadurch vollständige Austausch und Wiederverwertbarkeit des Modells und der Ansicht gewährleistet. 


## Aufbau 
MVP basiert wie MVC auch auf drei Komponenten: 
### Model 
- Logik der Ansicht (kann auch die Geschäftslogik sein). 
- Über das Modell muss jedoch alle Funktionalität erreichbar sein, um die Ansicht betreiben zu können. 
- Die Steuerung des Modells erfolgt allein vom Präsentator. Das Modell selbst kennt weder die Ansicht noch den Präsentator.
### View
- Enthält keine steuernde Logik und ist nur für die Darstellung und Ein- / Ausgaben zuständig. 
- Sie erhält weder Zugriff auf die Funktionalität des Präsentators noch auf das Modell. 
- Sämtliche Steuerung der Ansicht erfolgt vom Präsentator.
### Präsentator
- Beinhaltet die Logik der Anwendung.
- Bindeglied zwischen Modell und Ansicht. 
- Steuert die logischen Abläufe zwischen den beiden anderen Schichten und sorgt dafür, dass die Ansicht ihre Funktionalität erfüllen kann.

## Sources

- http://www.wildcrest.com/Potel/Portfolio/mvp.pdf
- http://www.martinfowler.com/eaaDev/uiArchs.html#Model-view-presentermvp

