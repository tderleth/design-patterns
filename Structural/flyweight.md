# Flyweight

Dieses Pattern lässt sich am einfachsten mit einem Web-Browser und dessen Cache erklären. Beim Flyweight dreht sich alles ums Teilen, Performance & um den Speicherbedarf. Lädt ein Browser eine Seite, iteriert er über alle Bilder, die in der Seite platziert sind und lädt alle Bilder neu, die nicht bereits in seinem Cache liegen. Für die bereits geladenen Bilder wird ein Flyweight-Objekt erstellt, das einige intrinsische Informationen wie Position innerhalb der Seite oder Anzeigegröße beinhaltet. Alles andere erbt es vom bereits gecacheten Objekt. Jedes Flyweight besteht dabei aus zwei Teilen: 

1. Zustandsabhängiger Teil – Wird dem Flyweight zur Verfügung gestellt und hängt vom Kontext ab, in dem das Flyweight genutzt werden soll (bspw. Position) 
2. Zustandsunabhängiger Teil – Wird im Flyweight selbst gespeichert (bspw. max-age)

Zusammenfassend schauen wir zuerst, ob wir schon ein Objekt haben, das unseren Zweck erfüllt, ist das nicht der Fall erstellen wir ein neues. Das Flyweight wird dabei von einer Factory erzeugt und meist in einer Liste oder Array abgelegt. 


## 🌍 Echtes Weltbeispiel

Stellen wir uns vor, wir malen ein Bild. Wir benötigen dazu Pinsel und haben einen ganzen Köcher davon. Das sind unsere Flyweights. Fehlt ein Pinsel, den wir gerade benötigen, so kaufen wir ihn und stecken in danach wieder in unseren Köcher. Jeder Pinsel hat zustandsunabhängige Informationen, wie zum Beispiel sein Duktus und zustandsabhängige Eigenschaften, wie die Farbe, mit der wir ihn gerade verwenden wollen. 

## 💬 In einfachen Worten

Wir verringern die Anzahl an Objekten, indem wir erst schauen, ob bereits ein für unseren Zweck passendes Objekt existiert. 

## 🖥 Beispiel

Greifen wir das obige Beispiel mit den Pinseln noch einmal auf: 

```php 
<?php

class Brush{}

class Quiver
{
  protected $availableBrush = [];

  public function takeBrush($size)
  {
    if (empty($this->availableBrush[$size])) {
      $this->availableBrush[$size] = new Brush();
    }
    return $this->availableBrush[$size];
  }
}

$quiver = new Quiver();

$brush_1 = $quiver->takeBrush(1);  // creates new Brush bc it does not exist yet
// painting …

$brush_2 = $quiver->takeBrush(2);  // creates new Brush bc it does not exist yet
// painting …

$brush_3 = $quiver->takeBrush(1);  // already exists
// painting …

if($brush_1 === $brush_3)
	echo "Same brush object used"
else
	echo "Two different brushes"

// "Same brush object used"

?>
```