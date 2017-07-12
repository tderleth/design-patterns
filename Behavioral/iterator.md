# Iterator

## 🌍 Praktisches Beispiel
Du gehst mit einem unbändigen Hunger in ein Restaurant mit diversen Köstlichkeiten (*Container*).
Dort angekommen willst du alles beim Kellner (*Iterator*) bestellen, dabei interessiert dich nur ob es noch etwas zu essen gibt (*hasNext()*) und das tatsächliche nächste Gericht (*next()*).

## 💬 In einfachen Worten
Dieses Pattern kapselt den Zugang zu einer Sequenz von Elementen.
Die vorliegende Datenstruktur der Elemente, Sortierung oder Aufbau der Sequenz spielen dabei keine Rolle. Somit ist die Iteration über die Elemente sauber von ihrer Struktur im Container
getrennt.

## 🖥 Beispiel

```java
// Iterator.java
public interface Iterator {
   public boolean hasNext();
   public Object next();
}

// Container.java
public interface Container {
   public Iterator getIterator();
}

// Restaurant.java
public class FancyRestaurant implements Container {
   private String dishes[] = {"Poutine", "Kebab", "Pasta", "Lobster"};

   @Override
   public Iterator getIterator() {
      return new Waiter();
   }

   private class Waiter implements Iterator {

      private int index;

      @Override
      public boolean hasNext() {
         if(index < names.length){
            return true;
         }
         return false;
      }

      @Override
      public Object next() {
         if(this.hasNext()){
            return dishes[index++];
         }
         return null; // auch möglich exception zu werfen!
      }		
   }
}
```

## Wann brauche ich das?
Ihr habt ein Container Element mit einer komplexen internen Darstellung seiner
Elemente, zum Beispiel viele verschachtelte Maps. Für interne Funktionen ist die Struktur
passend, allerdings macht Sie eine einfache Iteration umständlich.
Um dies für Clients trotzdem zu ermöglichen, stellt ihr ihnen einen Iterator bereit.
Dieser löst die verstrickte interne Struktur für den Client unsichtbar auf.
