# Proxy

Ein Proxy versteht sich als Platzhalter für ein anderes Objekt.

## 🌍 Praktisches Beispiel

Es gibt einige Situationen, in denen man ein Proxy einsetzen kann. Eine ist bswp. ein schützender Proxy, der die Zugriffsberechtigung auf Objekte steuert. Stellen wir uns dazu wieder eine Türe vor, die man mit einem Pin öffnen kann. Das Panel erlaubt es einem die Türe zu öffnen, obwohl die Funktionalität des Öffnen eigentlich bei dem Tür-Objekt liegt. Das Panel ist der Proxy.

## 💬 In einfachen Worten

Im Proxy Pattern repräsentiert eine Klasse die Funktionalität einer anderen Klasse. Im Vergleich zu einem Adapter, der ein verändertes Interface anbietet oder einem Decorator, der das Interface erweitert, bietet ein Proxy das selbe Interface an.

## 🖥 Beispiel


```php
interface Door{
  public function open();
  public function close();
}

class ProtectedDoor implements Door{
  public function open(){
    echo "Opening protected door";
  }
  public function close(){
    echo "Closing the protected door";
  }
}

class Panel{
  protected $door;
  public function __construct(Door $door){
    $this->door = $door;
  }
  public function open($password){
    if ($password === 'pr0xyIsC00l')
      $this->door->open();
    else
      echo "No entering :/";
  }
  public function close(){
    $this->door->close();
  }
}

$door = new Panel(new ProtectedDoor());
$door->open('invalid'); // No entering :/ 

$door->open('pr0xyIsC00l'); // Opening protected door
$door->close(); // Closing protected door
```


## Wann brauche ich das? 

Es gibt einige Situationen, in welchen sich ein Proxy anbietet: 

1. Ein virtueller Proxy als Platzhalter für ein “teuer zu erstellendes” Objet. Das “echte” Objekt wird dann nur bei der ersten Anfrage erstellt. 
2. Ein remote-Proxy als lokaler Ansprechpartner für ein Objekt, das sich in einem anderen Adressbereich befindet.
3. Ein schützender Proxy der den Zugriff auf sensible Objekte steuert. Überprüft, ob der Client Zugriffsberechtigungen für das Objekt hat. 