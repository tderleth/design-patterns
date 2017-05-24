# Factory Method

## 🌍 Echtes Weltbeispiel
Für unser Haus 🏠 brauchen wir nun nicht nur einfach Türen 🚪, sondern verschiedene Türen! Wir geben unserer Fabrik zum Beispiel eine Türe aus Holz und eine aus Stahl in Auftrag.

## 💬 In einfachen Worten
Die Fabrik Methode erzeugt ein Objekt für einen Client, wobei die Fabrik entscheidet, welche Unterklasse instanziiert wird. 

## 🖥 Beispiel

```php
<?php

interface Door {
    public function getDescription();
}

class WoodenDoor implements Door{
    public function getDescription() {
        echo 'I am a wooden door';
    }
}

class IronDoor implements Door{
    public function getDescription() {
        echo 'I am an iron door';
    }
}

class DoorFactory{
    public static function createDoor($type){
		    if ($type === "wooden") {
	        return new WoodenDoor();
        } 
        else if ($type === "iron") {
	        return new IronDoor();
        } 
        else {
	        return "error";
		    }
    }
}

$woodendoor = DoorFactory::createDoor("wooden");
echo $woodendoor->getDescription(); // Output: I am an wooden door

?>
```


## Wann brauche ich das?
Wenn der Client nicht wissen muss, welches Objekt er genau von der Fabrik haben möchte. 