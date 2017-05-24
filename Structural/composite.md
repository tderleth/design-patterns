# Composite

## 🌍 Praktisches Beispiel
Jedes Dateisystem setzt sich aus Ordnern und Dateien zusammen. Jeder dieser Knoten (ob Datei oder Ordner) hat dieselben Eigenschaften, wie zum Beispiel Größe oder Erstellungsdatum. Mit Hilfe des Kompositionsmusters können dabei Unterschiede zwischen einzelnen Objekten (Dateien) und zusammengesetzten Objekten (Ordnern) verborgen werden. 

## 💬 In einfachen Worten
Ein Kompositum erlaubt es einem Client verschiedene Objekte innerhalb einer Baumstruktur gleich zu behandeln, seien sie nun ein Knoten oder ein Blatt. 

## 🖥 Beispiel
```php
interface Node {
  public function __construct(string $name, float $size);
  public function getSize();
}

class File implements Node {
  protected $size;
  protected $name;
  public function __construct(string $name, float $size) {
    $this->name = $name;
    $this->size = $size;
  }
  public function getSize() {
    return $this->size;
  }
}

class Folder implements Node {
  protected $size;
  protected $name;
  public function __construct(string $name, float $size) {
    $this->name = $name;
    $this->size = $size;
  }
  public function getSize() {
    return $this->size;
  }
}
// Unsere Festplatte mit verschiedenen Knoten
class Disk {
  protected $nodes;
  public function addNode(Node $node) {
    $this->nodes[] = $node;
  }
  public function getSizeOfAll() {
    $size = 0;
    foreach ($this->nodes as $node) {
      $size += $node->getSize();
    }
    return $size;
  }
}

$file = new File('Hello.txt', 12000);
$folder = new Folder('Hello-folder', 10000);

$disk = new Disk();
$disk->addNode($file);
$disk->addNode($folder);

echo "Disk space used: ".$disk->getSize(); // Disk space used: 22000
```