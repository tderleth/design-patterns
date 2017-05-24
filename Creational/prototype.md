# Prototype

## 🌍 Echtes Weltbeispiel
Kannst du dich noch an Dolly 🐑 das erste geklonte Schaf erinnern? Richtig, bei diesem Pattern geht es ums Klonen 👯!

## 💬 In einfachen Worten
Ein Objekt wird, basierend auf einem anderen Objekt, durch Klonen erstellt. Erlaubt es uns also ein Objekt durch Kopieren zu erzeugen und für unsere Bedürfnisse anzupassen ohne es von Grund auf neu zu erstellen und anzupassen. 

## 🖥 Beispiel

```php
<?php 

class Sheep {
    protected $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function setName($name) {
        $this->name = $name;
    }

    public function getName() {
        return $this->name;
    }
}

$original = new Sheep('Molly');
echo $original->getName(); // Molly

// Clone and modify what is required
$cloned = clone $original;
$cloned->setName('Dolly');
echo $cloned->getName(); // Dolly

?>
```

## Wann brauche ich das? 
Wenn du ein Objekt ähnlich eines bereits existierenden benötigst oder das Erzeugen zu kostspielig oder zu kompliziert ist.