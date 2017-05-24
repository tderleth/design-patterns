# Abstract Factory

## 🌍 Echtes Weltbeispiel
Um unser Beispiel mit den Türen 🚪 fortzuführen, stellen wir uns vor, wir benötigen nun nicht nur verschiedene Türen wie eine Stahltüre oder eine Türe aus Holz sondern wir brauchen natürlich auch einen Türrahmen, je nach Türe natürlich unterschiedlich. Wir sehen also, dass es Abhängigkeiten zwischen der Art der Türe und der Art des Rahmens gibt.

## 💬 In einfachen Worten
Eine Fabrik, die die einzelnen, aber abhängigen Fabriken zusammenzieht, ohne ihre konkreten Klassen anzugeben. Wir kapseln also eine Gruppe von Fabriken! 

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

interface DoorFrame{
  public function getDescription();
}

class WoodenDoorFrame implements DoorFrame {

  public function getDescription() {
    echo 'I am an wooden door frame';
  }
}

class IronDoorFrame implements DoorFrame {

  public function getDescription() {
    echo 'I am an iron door frame';
  }
}

interface DoorFactory {
  public function createDoor();
  public function createDoorFrame();
}

class WoodenDoorFactory implements DoorFactory{

  public function createDoor() {
    return new WoodenDoor();
  }
  
  public function createDoorFrame(){
    return new WoodenDoorFrame();
  }
}

class IronDoorFactory implements DoorFactory{

  public function createDoor(){
    return new IronDoor();
  }
  
  public function createDoorFrame(){
    return new IronDoorFrame();
  }
}

$woodenFactory = new WoodenDoorFactory();
$door = $woodenFactory->createDoor();
$doorFrame = $woodenFactory->createDoorFrame();

$door->getDescription();    // Output: I am a wooden door
$doorFrame->getDescription(); // Output: I am an wooden door frame

?>
```

Wir sehen also, dass die `WoodenDoorFactory` die Holztüre und den Holzrahmen gekapselt hat, genauso wie die `IronDoorFactory` die Stahltüre und den Stahlrahmen! Erstellen wir nun also eine Türe mit Hilfe der Fabrik, bekommen wir den passenden Rahmen gleich mitgeliefert!

## Wann brauche ich das? 
Wenn es Abhängigkeiten zwischen nicht ganz einfach zu erstellenden Klassen gibt!