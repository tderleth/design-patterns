# Decorator

## 🌍 Praktisches Beispiel
Für diese Pattern stellen wir uns vor wir schreiben die Getränkekarte eines Cafés ☕. Wir bieten einen normalen Kaffee für 3💲 an. Wir möchten unseren Gästen aber auch einen Kaffee mit Milch 🥛 anbieten. Der Preis eines Milchkaffees entspricht dem Kaffeepreis plus 1💲. Wir dekorieren dazu zur Laufzeit unseren Kaffee dynamisch mit Milch! 

## 💬 In einfachen Worten
Durch das Kapseln eines Objektes in ein anderes Objekt (Decorator) können wir dem ursprünglichen Objekt zur Laufzeit dynamisch Eigenschaften und Verhalten beibringen.

## 🖥 Beispiel


```php
interface Coffee {
  public function getCost();
  public function getDescription();
}

class SimpleCoffee implements Coffee {
  public function getCost() {
    return 3;
  }
  public function getDescription() {
    return 'Simple coffee';
  }
}

class MilkCoffee implements Coffee {
  protected $coffee;
  public function __construct(Coffee $coffee) {
    $this->coffee = $coffee;
  }
  public function getCost() {
    return $this->coffee->getCost() + 1;
  }
  public function getDescription() {
    return $this->coffee->getDescription() . ', milk';
  }
}

$someCoffee = new SimpleCoffee();
echo $someCoffee->getCost(); // 3
echo $someCoffee->getDescription(); // Simple Coffee

$someCoffee = new MilkCoffee($someCoffee);
echo $someCoffee->getCost(); // 4
echo $someCoffee->getDescription(); // Simple Coffee, milk
```
