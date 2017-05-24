# Bridge

## 🌍 Praktisches Beispiel
Um das Bridge Pattern zu verstehen, stellen wir uns vor wir würden uns in einem 🚗 Auto Konfigurator 🖥️ einen Neuwagen zusammenstellen. Wir können dabei erst eine Kategorie auswählen, also ob wir ein schickes schnelles Cabrio haben möchten oder doch lieber eine Familienkutsche. Danach können wir neben weiteren Dingen auch noch die Lackfarbe auswählen. Neben einem sportlichen Blau gibt es auch noch ein sattes rot! Es sollen aber natürlich alle Variationen an Farbe und Typ möglich sein! Das können wir entweder mit Vererbung oder mit einer Bridge lösen. Benutzen wir eine Bridge können wir Farbe und Typ beliebig kombinieren. 

*Vererbung*
/images/hierarchy.png

*Bridge*
/images/brdige.png


## 💬 In einfachen Worten
Bei dem Bridge Pattern wird eine Komposition der Vererbung vorgezogen. Die Details der Implementierung werden damit in eine zweite Hierarchie verschoben. 

## 🖥 Beispiel
```php 
interface Car {
  public function __construct(Color $color);
  public function getDescription();
}

class Minivan implements Car {
  protected $color;
  public function __construct(Color $color) {
    $this->color = $color;
  }
  public function getDescription() {
    return "I´m a Minivan in " . $this->color->getColor();
  }  
}

class Cabrio implements Car {
  protected $color;
  public function __construct(Color $color) {
    $this->color = $color;
  }
  public function getDescription() {
    return "I´m a Cabrio in " . $this->color->getColor();
  }
}

interface Color {
  public function getColor();
}

class RedColor implements Color {
	function getColor() {
		return "red";
	}
}

class BlueColor implements Color {
	function getColor() {
		return "blue";
	}
}

$minivan = new Minivan(new RedColor());
$Cabrio = new Cabrio(new BlueColor());

$minivan->getDescription();   // Output: I´m a Minivan in red
$Cabrio->getDescription();  // Output: I´m a Cabrio in blue
```