# Facade

## 🌍 Echtes Weltbeispiel

Magst du Latte macchiato? Stell dir einen Vollautomaten vor. Du drückst eine Taste und bekommst einen Latte serviert. Du benutzt dazu eine einfache Schnittstelle, die dir die Maschine nach außen hin anbietet, intern hat die Maschine aber viel mehr Dinge zu erledigen, bis du dein Kaffee genießen kannst. Der einfache Knopf vor einem komplizierterem System ist eine Fassade! 

## 💬 In einfachen Worten
Eine Fassade bietet ein einfaches Interface zu einem komplizierteren System! 

## 🖥 Beispiel

Stellen wir uns den Vollautomaten vor:

```php 
<?php

class CoffeeMachine{

    public function crush_beans(){…}
    public function heat_milk(){…}
		public function fill_cup(){…}
	  public function display_output_on_display(){
        echo "Coffee ready!";
    }
    
}

class CoffeeMachineFacade
{
    protected $coffeeMachine;

    public function __construct(CoffeeMachine $coffeeMachine)
    {
        $this->coffeeMachine = $coffeeMachine;
    }

    public function getLatte(){
        $this->coffeeMachine->heat_milk();
        $this->coffeeMachine->crush_beans();
        $this->coffeeMachine->fill_cup();
        $this->coffeeMachine->display_output_on_display();
    }
}

$coffeeMachine = new CoffeeMachineFacade(new CoffeeMachineFacade());
$computer->getLatte(); // Coffee ready!

?>
```