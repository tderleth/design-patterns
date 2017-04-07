### [Chain of Responsibility](/chain-of-responsibility.md)

#### 🌍 Echtes Weltbeispiel


#### 💬 In einfachen Worten
#### 🖥 Beispiel

```php 
<?php

?>
```

#### Wann brauche ich das? 





# Chain of responsibility
Eine Möglichkeit einen Request entlang einer Kette weiterzugeben.

> Design Pattern, dass einen Request durch eine Reihe (kette) von Handlern / Objekten leitet. Der Request wird dabei von einem Handler zum nächsten weitergegeben und von einem, mehreren oder sogar allen Hanldern verarbeitet. 

## Intent

- Entkopplung des Auslösers einer Anfrage mit seinem Empfänger, da alle Objekte die Möglichkeiten haben den Request zu verarbeiten. 
- Starten und Verlassen eines Requests anhand einer einzelnen Pipeline, die alle möglichen Handler beinhaltet. 
- Pipeline wird nicht zwingend bis zum Ende durchgegangen, sondern sobald eine Response vorhanden ist abgebrochen. 
- Jeder Handler kennt dabei nur den nach ihm folgenden. 

## Problem

- Effizientes Verarbeiten der verarbeitenden Elemente. 
- Spart das Mappen von Request auf Handler. 

## Pro 

- Klient muss tatsächlichen Handler nicht kennen. 
- Selbst einzelne Handler müssen nur direkten Nachfolger und nicht den Gesamt-Aufbau der Kette kennen (geringeren Kopplung). 

## Con 

- Keine Garantie, dass die Anfrage tatsächlich bearbeitet wird. 
- Wenn letzter Handler einen Request erhält, für die er nicht zuständig ist, wird die Anfrage verworfen (expection muss implementiert werden).
- Es muss sichergestellt werden, dass jeder Handler in der Kette nur einmal vorkommt, sonst Endlosschleife.

## Beispiel

~~~php
<?php

abstract class BasicHandler {

    private $successor = null;

    public function setSuccessor(Handler $handler){
        $this->successor = $handler;
    }

    abstract public function handle($request);
}


class FirstHandler extends BasicHandler {

    public function handle($request){
		    if( // i can handle the request ){
		      // provide a response
				  return $response;
			  }
			  else{
	        // call the next handler
	        return $this->successor->handle($request);
			  }      
    }
    
}

// create handler objects
$firstHandler = new FirstHandler();
$secondHandler = new SecondHandler();
$thirdHandler = new ThirdHandler();

// Set the chain
$firstHandler->setSuccessor($secondHandler);
$secondHandler->setSuccessor($thirdHandler);

// start to process the chain
$response = $firstHandler->handle($request);

?>
~~~


## TL;DR 

- Die Basisklasse hält einen "nächsten" Zeiger.
- Jede abgeleitete Klasse implementiert ihre eigene Logik für die Bearbeitung des Requests.
- Wenn der Request weitergegeben werden muss, dann leitet die abgeleitete Klasse zurück an die Basisklasse, die den Request an den nächsten Zeiger delegiert.
- Der Client erstellt und verknüpft die Kette und startet die Verarbeitung des Requests mit dem Anfang der Kette. 
- Rekursive Delegation erzeugt die Magie :)

## Sources 

- [sourcemaking](https://sourcemaking.com/design_patterns/chain_of_responsibility)



