# Visitor

## 🌍 Praktisches Beispiel

Stell dir vor, du gehst in einem Supermarkt einkaufen. Am Ende gehst du zum Kassierer und übergibst ihm deine Einkäufe. Der Kassierer handelt nun wie ein Visitor, übernimmt deine Einkäufe und berechnet dir den Gesamtbetrag.

## 💬 In einfachen Worten

Mit diesem Design Pattern ist es uns möglich Operationen auf Objekten auszuführen, die diese gar nicht besitzen. Dabei ändern wir das Objekt selbst nicht. Wir trennen damit das Objekt Struktur vom Algorithmus.

## 🖥 Beispiel

```php
<?php

interface ShoppingItem
{
    public function accept(ShoppingItemOperation $operation);
}

// Visitor
interface ShoppingItemOperation
{
    public function visitFruit(Fruit $fruit);
    public function visitMeat(Meat $meat);
    public function visitBiscuit(Biscuit $biscuit);
}

class Fruit implements ShoppingItem
{
    public function getBarcode()
    {
        echo 'Fruity barcodes here';
    }

    public function accept(ShoppingItemOperation $operation)
    {
        $operation->visitFruit($this);
    }
}

class Meat implements ShoppingItem
{
    public function getBarcode()
    {
        echo 'Meaty barcodes here';
    }

    public function accept(ShoppingItemOperation $operation)
    {
        $operation->visitMeat($this);
    }
}

class Biscuit implements ShoppingItem
{
    public function getBarcode()
    {
        echo 'Baked barcodes here';
    }

    public function accept(ShoppingItemOperation $operation)
    {
        $operation->visitFruit($this);
    }
}

// Now our Visitor
class Cashier implements ShoppingItemOperation
{
    public function visitFruit(Fruit $fruit)
    {
        echo "This fruit costs a dollar.";
    }

    public function visitMeat(Meat $meat)
    {
      echo "This meat costs two dollars.";
    }

    public function visitBiscuit(Biscuit $biscuit)
    {
      echo "This biscuit is free today.";
    }

}

// And then it can be used as

$fruit = new Fruit();
$meat = new Meat();
$biscuit = new Biscuit();

$cashier = new Cashier();

$fruit->accept($cashier);     // This fruit costs a dollar.
$meat->accept($cashier);      // This meat costs two dollars.
$biscuit->accept($cashier);   // This biscuit is free today.

?>
```

Das ganze hätte man nun auch mit Vererbung auflösen können, also wozu das alles? Jedes mal, wenn wir dann den Einkaufsgegenständen ein Verhalten hinzufügen wollen, müssten wir dann die Soppingitems modifizieren. So können wir beliebig Aktionen hinzufügen. Schauen wir uns dazu folgendes Beispiel an: Der Supermarkt hat auch noch einen Schalter, an dem man sich zu jedem Produkt weitere Informationen holen kann. Dazu schreiben wir einfach einen neuen Visitor:

```php
<?php

class InformationDesk implements ShoppingItemOperation
{
  public function visitFruit(Fruit $fruit)
  {
      echo "This fruit is from Honolulu";
  }

  public function visitMeat(Meat $meat)
  {
    echo "This meat is finest Angus Beef.";
  }

  public function visitBiscuit(Biscuit $biscuit)
  {
    echo "This biscuit was baked in France.";
  }
}

// And for the usage

$informationDesk = new InformationDesk();

$fruit->accept($cashier);             // This fruit costs a dollar.
$fruit->accept($informationDesk);     // This fruit is from Honolulu.

$meat->accept($cashier);              // This meat costs two dollars.
$meat->accept($informationDesk);      // This meat is finest Angus Beef.

$biscuit->accept($cashier);           // This biscuit is free today.
$biscuit->accept($informationDesk);   // This biscuit was baked in France.

?>
```
