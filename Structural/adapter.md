# Adapter

## 🌍 Praktisches Beispiel
Adapter sind uns allen ein Begriff – sei es im Urlaub für die Steckdose oder für unsere geliebten Smartphones 📱. Für unser Beispiel stellen wir uns einen Mechaniker 👩‍🔧 vor, der normalerweise Autos 🚗  repariert. Nun wollen wir aber, dass unser Mechaniker nicht nur Autos, sondern auch Flugzeuge ✈️️ repariert. Dabei gehen wir davon aus, dass sich Flugzeuge im Wesentlichen nicht sehr viel von Autos unterscheiden. Wir packen dazu unser Flugzeug in einen Adapter. 

## 💬 In einfachen Worten
Adapter erlauben es uns das Interface einer Klasse so zu adaptieren, dass es zu anderen Klassen kompatibel ist. Dazu wird das Objekt in ein Adapter gekapselt. Dazu muss die der Source Code der eigentlichen Klasse nicht verändert werden. 

## 🖥 Beispiel
```php 
interface Car {
  public function drive();
}

class Cabrio implements Car {
  public function drive() {…}
}

class Suv implements Car {
  public function drive() {…}
}

class Mechanic {
  public function repair(Car $car) {…}
}

class Airplane {
  public function fly() {…}
}

class AirplaneAdapter implements Car {
  protected $airplane;
  public function __construct(Airplane $airplane) {
    $this->airplane = $airplane;
  }
  public function drive() {
    $this->airplane->fly();
  }
  
}

$airplane = new Airplane();
$airplaneAdapter = new AirplaneAdapter($airplane);

$mechanic = new Mechanic();
$mechanic->repair($airplaneAdapter);
```

## Wann brauche ich das? 
Dieses Pattern solltest du einsetzen, wenn du ein bereits existierendes Objekt hast und das Interface des Objektes ändern musst. 