### Simple Factory


#### 🌍 Echtes Weltbeispiel

Stellen wir uns vor, wir wollen ein Haus 🏠 mit Türen 🚪 bauen. Es wäre ziemlich chaotisch, wenn wir jedes Mal, wenn wir eine Türe benötigen uns eine Tischlerkleidung anziehen und eine Türe 🚪 tischlern. Daher geben wir das Ganze bei einer Fabrik in Auftrag. Was braucht die Fabrik dazu? Richtig, eine Bestellung mit den Eigenschaften der Türe!

#### 💬 In einfachen Worten
Eine einfache Fabrik erzeugt ein Objekt für einen Client, wobei der Client die Logik der Instanziierung nicht kennen muss.

#### 🖥 Beispiel
```php
<?php

interface Door {
    public function getWidth();
    public function getHeight();
}

class WoodenDoor implements Door {
    private $width;
    private $height;

    public function __construct($width,$height) {
        $this->width = $width;
        $this->height = $height;
    }

    public function getWidth() {
        return $this->width;
    }

    public function getHeight() {
        return $this->height;
    }
}

class DoorFactory{
    public static function createDoor($width, $height){
        return new WoodenDoor($width, $height);
    }
}

$door = DoorFactory::createDoor(100,200);
echo 'Width: ' . $door->getWidth();

?>
```


#### Wann brauche ich das? 
Wenn das Erzeugen eines Objektes nicht nur aus ein paar Zuweisungen, sondern aus einer Menge Logik besteht, sollte eine Fabrik 🏭 eingesetzt werden. Dadurch muss diese Logik nicht bei jedem Instanziieren wiederholt werden, sondern wird zentral in der 🏭 erledigt. Stellen wir uns vor wir wollen die Klasse `Door`  umbenennen, austauschen oder modifizieren, dann ändern wir den Code zentral in der Factory und nicht an jeder Stelle in unserem Code, der die Klasse `Door` verwendet. Wir lösen damit eine konkrete Implementierung und programmieren gegen eine (zentrale) Schnittstelle!