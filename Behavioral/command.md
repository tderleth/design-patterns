# Command

## 🌍 Praktisches Beispiel

Wenn du ("Client") in einem Restaurant Essen ("Command") bei einem Kellner ("Invoker") bestellst und dieser die Bestellung dann an den Koch ("Receiver") weitergibt.

## 💬 In einfachen Worten

Diese Pattern kapselt Aktionen in Objekte. Das Objekt beinhaltet den Namen der Methode, das Objekt, das die aufzurufende Methode enthält, sowie die zu übergebenden Parameter.

## 🖥 Beispiel

```php
<?php

// Receiver
class Cook {
  public function prepareFood() {
    echo "Pancakes are ready for take off";
  }
}

interface Command {
  public function execute();
}

// Command
class PrepareFood implements Command {

  protected $cook;

  public function __construct(Cook $cook) {
    $this->cook = $cook;
  }

  public function execute(){
    $this->cook->prepareFood();
  }
}

// Invoker
class Waitress {
  public function submit(Command $command) {
    $command->execute();
  }
}

$cook = new Cook();
$prepareFood = new PrepareFood($cook);
$waitress = new Waitress();
$waitress->submit($prepareFood); // Pancakes are ready for take off

?>
```
