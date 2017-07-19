# Strategy

## 🌍 Praktisches Beispiel
Du bist Koch in einem berühmten Steakhouse. Es gibt verschiedene Strategien
ein Steak zu kochen (Rare, Medium Rare, Medium, Medium Well etc.) und du möchtest
spontan auf die Wünsche der Kunden eingehen. Daher legst du dir
verschiedene, austauschbare Strategien zurecht.

## 💬 In einfachen Worten
Unterschiedliche Algorithmen oder Funktionen um ein Problem zu
lösen werden in separate Objekte (Strategy) gekapselt und hinter
einem Interface versteckt. Zur Laufzeit kann dann die passende
Strategie ausgewählt werden. Damit ist die Strategie entkoppelt
vom Kontext und austauschbar.

## 🖥 Beispiel

```java
// Steak.java
public interface SteakStrategy {
  public String cookSteak();
}
```

```java
// SteakStrategies.java
public class Rare implements SteakStrategy {
  public String cookSteak(){
    return "Rare Steak";
  }
}

public class MediumRare implements SteakStrategy {
  public String cookSteak(){
    return "Medium Rare Steak";
  }
}

public class Medium implements SteakStrategy {
  public String cookSteak(){
    return "Medium Steak";
  }
}
```

```java
// Cook.java
public class Cook {
  // cook is able to switch strategy
  public String makeSteak(SteakStrategy strategy){
    return strategy.cookSteak();
  }
}
```

## Wann brauche ich das?
Ihr habt verschiedene Herangehensweisen für ein Problem, die sich in der Implementierung
stark unterscheiden, aber das gleiche Ergebnis haben. Um Austauschbarkeit und Erweiterbarkeit
zu garantieren, bietet es sich an die Strategien separat zu implementieren und
zur Laufzeit eures Programms die passende zu wählen.
