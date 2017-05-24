# [Singleton](/singleton.md)

## 🌍 Echtes Weltbeispiel
Es kann nur einen Präsidenten eines Landes gleichzeitig geben. Dieser muss immer handeln, wenn es von ihm gefordert wird. 

## 💬 In einfachen Worten
Singleton Patterns stellt sicher, dass es zur selben Zeit nur ein einziges Objekt einer Klasse gibt und kein zweites davon instanziiert werden kann. 

## 🖥 Beispiel

Um ein Singleton in PHP zu erstellen, muss: 

- Der Konstruktor privat gesetzt werden,
- Klonen muss deaktiviert werden,
- eine statische Variable, die die Instanz referiert muss deklariert werden und
- die Klasse sollte am besten als final definiert werden, damit Sie auch nicht extended werden kann.
- Dazu brauchen wir noch eine get-Methode, die uns die Instanz übergibt. 

```php
final class President {
    private static $instance;

    private function __construct() {
        // Hide the constructor
    }

    public static function getInstance() : President {
        if (!self::$instance) {
            self::$instance = new self();
        }
        return self::$instance;
    }

    private function __clone() {
        // Disable cloning
    }

}

$president1 = President::getInstance();
$president2 = President::getInstance();

if($president1 === $president2){
  echo "there is just one Donald Trump";
}
```

## Wann brauche ich das? 
Immer wenn du von einem Objekt wirklich nur eine Instanz haben möchtest, zum Beispiel für eine Konfiguration. Auch ist ein HTTP Response Object meist ein Singleton. Aber **VORSICHT**: Singletons sorgen auch für eine enge Kopplung! 

