# State

## 🌍 Praktisches Beispiel
Stell dir als Gegenstand eine Fernsteuerung zu einem TV vor. Ist der TV eingeschaltet, so kann er mit Hilfe der Power-Taste abgeschaltet werden. Ist er ausgeschalten, so löst die gleiche Taste eine andere Aktion aus. Das Verhalten der Fernbedienung ist also abhängig von ihrem Zustand. Auch wenn wir hier nur zwei verschiedene Zustände (States) haben, können bei diesem Pattern beliebig viele Zustände definiert werden. 

## 💬 In einfachen Worten
Dieses Pattern erlaubt es uns, abhängig von einem internen Zustand das Verhalten  eines Objektes zu ändern. Das Objekt sieht dann so aus, also wäre es eine andere Klasse. 

## 🖥 Beispiel

```php 
<?php

interface State {
  public function doAction();
}

class TVStartState implements State {
  
  public function doAction() {
		echo "TV is turned ON";
	}
	
}

class TVStopState implements State {
  
  public function doAction() {
		echo "TV is turned OFF";
	}
	
}

class RemoteControl implements State {

  protected $state;
  
  public function setState(State $state) {
    $this->state = $state;
  }
  
  public function doSomething() {
    $this->state->doAction();
  }
  
}

$remotecontrol = new RemoteControl();

$remotecontrol.setState(new TVStartState());
$remotecontrol.doSomething();
// TV is turned ON

$remotecontrol.setState(new TVStopState());
$remotecontrol.doSomething();
// TV is turned OFF

?>
```
	