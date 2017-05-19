### [Builder](/builder.md)

#### 🌍 Echtes Weltbeispiel
Stell dir vor du sitzt bei Hans im Glück und bestellst einen Burger 🍔. Die Bedienung fragt dich bei deiner Bestellung meist nach der Brotsorte, ob du extra Tomaten 🍅 haben möchtest oder Käse 🧀. Von der Soße ganz abgesehen. Hier kommen wir mit unserer Simple Factory nicht weit, da wir für die verschiedenen Konstellationen eine Menge Konstruktoren bräuchten. Das Builder Pattern hilft uns hierbei aus.

#### 💬 In einfachen Worten
Die Anzahl an Parametern, die dem Konstruktor übergeben werden, kann schnell überhand nehmen und es wird dann schwierig die Reihenfolge der Parameter zu identifizieren. Diese Pattern ermöglicht es uns, verschiedene Ausprägungen eines Objekts zu erstellen und dabei den Konstruktor nicht mit unnötiger Komplexität zu überladen.

#### 🖥 Beispiel

Den `BurgerBuilder` übergeben wir dabei dem Konstruktor des Burgers!

```php

class Burger {
    protected $size;
    protected $cheese = false;
    protected $tomato = false;

    public function __construct(BurgerBuilder $builder) {
        $this->size = $builder->size;
        $this->cheese = $builder->cheese;
        $this->tomato = $builder->tomato;
    }
}

class BurgerBuilder {
    public $size;
    public $cheese = false;
    public $tomato = false;

    public function __construct(int $size) {
        $this->size = $size;
    }

    public function addCheese() {
        $this->cheese = true;
        return $this;
    }

    public function addTomato() {
        $this->tomato = true;
        return $this;
    }

    public function build() : Burger {
        return new Burger($this);
    }
}

$burger = (new BurgerBuilder(14))->addTomato()->build();
                    
```

#### Wann brauche ich das? 
Wenn es verschiedenen Ausprägungen eines Objektes gibt. Der Unterschied zur Fabrik ist, dass der Builder verwendet werden sollte, wenn zur Erstellung des Objekts mehrere Schritte nötig sind.