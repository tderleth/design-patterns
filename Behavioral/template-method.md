# Template Method

## 🌍 Praktisches Beispiel

Stell dir vor, wir wollen ein neues Paper schreiben. Die einzelnen Schritte dazu sehen meist wie folgt aus:

1. Forschung
2. Schreiben
3. Veröffentlichen

Die Reihenfolge dieser Schritte wird immer eingehalten, man kann nicht Schreiben, bevor man nicht weiß über was und bevor nichts geschrieben ist, kann man nichts veröffentlichen. Aber, jeder der Schritte kann modifiziert werden, so kann die Forschung einmal eine Studie enthalten oder ein Experiment oder das Schreiben kann in verschiedenen Sprache stattfinden.

## 💬 In einfachen Worten

Die Template method definiert ein Gerüst, wie ein bestimmter Algorithmus ausgeführt werden mus, gibt aber die eigentliche Implementierung an die Kind-Klassen ab.

## 🖥 Beispiel

Stell dir ein Build Tool vor, das uns hilft eine Applikation zu testen, linten, compilieren und deployen. Je nach Plattform haben wir vom Build-Objekt eine andere Kind-Klasse.

```php
<?php

abstract class Builder {

  final public function build() {
    $this->compile();
    $this->test();
    $this->lint();
    $this->deploy();
  }

  abstract public function compile();
  abstract public function test();
  abstract public function lint();
  abstract public function deploy();
}

class AndroidBuilder extends Builder {

  public function compile() {
    echo 'Compiling  the android build';
  }

  public function test() {
    echo 'Running android tests';
  }

  public function lint() {
    echo 'Linting the android code';
  }

  public function deploy() {
    echo 'Deploying android build to server';
  }
}

class IosBuilder extends Builder {

  public function compile() {
    echo 'Compiling the ios build';
  }

  public function test() {
    echo 'Running ios tests';
  }

  public function lint() {
    echo 'Linting the ios code';
  }

  public function deploy() {
    echo 'Deploying ios build to server';
  }
}

$androidBuilder = new AndroidBuilder();
$androidBuilder->build();

// Output:
// Compiling  the android build
// Running android tests
// Linting the android code
// Deploying android build to server

$iosBuilder = new IosBuilder();
$iosBuilder->build();

// Output:
// Compiling  the ios build
// Running ios tests
// Linting the ios code
// Deploying ios build to server

?>
```
