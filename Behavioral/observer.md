# Observer


## 🌍 Praktisches Beispiel

Stell dir vor, du willst online neue Schuhe kaufen, sie sind aber ausverkauft. Zum Glück hat der Online Shop eine Funktion um dich zu benachrichtigen sobald deine neuen heißen Treter wieder vorrätig sind.

## 💬 In einfachen Worten

Beim Observer geht es darum, dass ein Objekt (der Online Shop) eine Liste seiner Abonnenten (du) führt und sobald sich sein Zustand ändert diese darüber informiert. 

## 🖥 Beispiel

```php 
<?php

class Shoes {
  protected $size;

  public function __construct(string $size) {
    $this->size = $size;
  }

  public function getSize() {
    return $this->size;
  }

}

class Customer implements Observer {
  protected $name;

  public function __construct(string $name) {
    $this->name = $name;
  }

  public function onNewShoeDelivery(Shoes $shoes) {
    echo 'Hi ' . $this->name . ', shoes are now available in size: '. $shoes->getsize();
  }

}

class Shop implements Observable {
  protected $observers = [];

  protected function notify(Shoes $shoes) {
    foreach ($this->observers as $observer) {
      $observer->onNewShoeDelivery($shoes);
    }
  }

  public function attach(Observer $observer) {
    $this->observers[] = $observer;
  }

  public function addShoes(Shoes $shoes) {
    $this->notify($shoes);
  }
}

// Create subscribers
$max = new Customer('Max Power');
$donald = new Customer('Donald Trump');

// Create publisher and attach subscribers
$shop = new Shop();
$shop->attach($max);
$shop->attach($donald);

$shop->addShoes(new Shoes(9));

// Output
// Hi Max Power, shoes are now available in size: 9
// Hi Donald Trump, shoes are now available in size: 9

?>
```
