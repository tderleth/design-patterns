# Chain of responsibility

## 🌍 Praktisches Beispiel

Kennst du den Passierschein A38? Richtig, den aus Asterix und Obelix. Was hat das mit der chain of responsibility zu tun? Einfach: Die beiden haben eine Anfrage  (unser Request) und es gibt potentiell variabel viele Personen (unsere Request-Handler), die die Anfrage entgegennehmen, bis derjenige gefunden wurde, der die Anfrage verarbeiten kann! Wichtig in der Kette ist für jedes Element nur, ob es den Request verarbeiten kann und wenn nicht, an wen es den Request weiterleitet (verlinkte Liste). 

## 💬 In einfachen Worten

Ein Request wird solange an einer Kette entlang gegeben, bis sich der richtige Handler, der die Anfrage bearbeiten kann, gefunden hat! Rekursive Delegation erzeugt die Magie :)

## 🖥 Beispiel

```php 
<?php 

abstract class BasicHandler {
  private $successor = null;
  public function setSuccessor(Handler $handler){
    $this->successor = $handler;
  }
  abstract public function handle($request);
}

class FirstHandler extends BasicHandler {
  public function handle($request){
    if( /* I can handle the request */ ){
      // provide a response
      return $response;
    } else {
      // call the next handler
      return $this->successor->handle($request);
    }    
  }
}

// create handler objects
$firstHandler = new FirstHandler();
$secondHandler = new SecondHandler();
$thirdHandler = new ThirdHandler();

// Set the chain
$firstHandler->setSuccessor($secondHandler);
$secondHandler->setSuccessor($thirdHandler);

// start to process the chain
$response = $firstHandler->handle($request);

?>
```