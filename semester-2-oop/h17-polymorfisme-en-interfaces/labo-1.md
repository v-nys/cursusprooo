# Labo

* oefening: schrijf een interface
* oefening: implementeer een gegeven interface
* oefening: maak een collectie van objecten met een gegeven interface
* oefening: schrijf een methode om het "grootste" element in te zoeken
* oefening: schrijf IComparer
* oefening: ontkoppel gegeven code \(door vorige drie zaken te doen\)
* zaken uit het oud labo porten

## h17-IComparable-implementatie

### Functionele analyse

We willen op een eenvoudige manier objecten van een bepaalde klasse kunnen sorteren.

### Technische analyse

Gegeven volgende klasse `Product`:

```csharp
namespace IndividueleOefeningen {
    public class Product {
        private uint kostprijs;
        public uint Kostprijs
        {
            get { return kostprijs; }
            set { kostprijs = value; }
        }
        
        private string naam;
        public string Naam
        {
            get { return naam; }
            set { naam = value; }
        }
    }
}
```

We moeten producten kunnen sorteren op kostprijs voor we ze aan de gebruiker tonen. We kunnen dit doen door de interface `IComparable<Product>` te implementeren. Door dit te doen, beloven we eigenlijk dat we een object van deze klasse kunnen vergelijken met een product. Anders gezegd: dat we producten met elkaar kunnen vergelijken. Hierdoor kunnen we gebruik maken van algemene methodes om objecten te sorteren.

De interface `IComparable<Product>` vereist dat je `CompareTo(Product p)` implementeert. De afspraak is dat je `-1` teruggeeft als `this` voor `p` moet worden gesorteerd, `0` als ze gelijkwaardig zijn en `1` als `this` na `p` komt.

Implementeer deze interface. Je moet ook rekening houden met de mogelijkheid dat `p` `null` is. `null` moet voor deze oefening helemaal vooraan komen.

Test met volgende code:

```csharp
var p1 = new Product("Fiets", 999);
var p2 = new Product("Playstation 5", 500);
var p3 = new Product("Elektrische gitaar", 750);
var p4 = new Product("Doos ontbijtgranen",3);
Product p5 = null;
var p6 = new Product("Xbox Series X", 500);
var producten = new List<Product> {p1, p2, p3, p4, p5, p6};

```



