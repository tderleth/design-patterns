# Memento

## 🌍 Praktisches Beispiel

Ihr seid Koch (_Caretaker_) in einem Restaurant, nach einer langen Schicht sieht es in der Küche (_Originator_) immmer aus wie Sau. Anstatt mühselig alles zu putzen, würdet ihr gerne den Zustand der Küche vor dem Kochen in eine magische Kiste (_Memento_) packen und später wiederherstellen (_undo_ oder _rollback_).

## 💬 In einfachen Worten

Mit dem Memento Pattern könnt ihr den Zustand eines Objekts abbilden und zu einem späteren Zeitpunkt wiederherstellen, ohne die interne Struktur des Objektes zu kennen. Dabei verwaltet der **Caretaker** den Zustand des **Originator** mithilfe des **Memento**.

## 🖥 Beispiel

```java
// Memento.java
public interface Memento {
  public String getState();
  public void setState(String state);
}

// Originator.java
public interface Originator {
  public Memento createMemento();
  public void setMemento(Memento meme);
}
```

```java
// Kitchen.java
public class Kitchen implements Originator {
  private String state;

  // memento implementation
  private class KitchenState implements Memento {
    private String savedState;

    public String getState(){
      return savedState;
    }

    public void setState(String state){
      this.savedState = state;
    }
  }

  // originator implementation
  public Memento createMemento(){
    Memento meme = new Memento();
    meme.setState(this.state);
    return meme;
  }

  public void setMemento(Memento meme){
    this.state = meme.getState();
  }
}
```

```java
//Caretaker.java
public class Cook() {
  private Kitchen kitchen;
  private Memento magicBox;

  public cook(){
    this.kitchen = new Kitchen();
    magicBox = kitchen.createMemento();
    // do the cooking ...
  }

  public cleanup(){
    this.kitchen = kitchen.setMemento(magicBox);
    // cleaning done! Hooray!
  }
}
```

## Wann brauche ich das?

Dieses Pattern ist immer dann geeignet, wenn ihr einen oder mehrere alte Zustände wiederherstellen möchtet und bei der Verwaltung dieser Zustände die Kapselung der Objekte einhaltet. Wie der Zustand aussieht is durch Memento sauber vom tatsächlichen Objekt getrennt.
