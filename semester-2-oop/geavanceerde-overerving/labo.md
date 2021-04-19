# Labo

## h15-bugfix

### Functionele analyse

We schrijven een bestelsysteem. We kunnen gewone bestellingen en internationale bestellingen plaatsen. Voor geïmporteerde producten wordt een extra toelage van 10% aangerekend, maar is er wel korting voor grote bestellingen. We willen de prijzen van onze producten niet publiek zichtbaar maken, want dat verhindert prijsafspraken.

### Technische analyse

Schrijf een klasse Bestelling met een `uint` property `Aantal` en een `double` privé-attribuut `basisPrijs`. Voorzie ook een overschrijfbare property `TotaalPrijs`, namelijk het aantal maal de basisprijs. Schrijf een subklasse `InternationaleBestelling` die de totaalprijs bepaalt door de basisprijs met 10% te verhogen, maar vanaf 100 stuks een vlakke korting van 1000 euro toepast. **Dit zal niet meteen werken!** Doe een zo klein mogelijke aanpassing om het toch te doen werken.

Schrijf een methode `DemonstreerBestellingen` in de klasse `EigenObjectOefeningen`. Hierin vraag je of de gebruiker een gewone of internationale bestelling wil plaatsen, vraag je om het aantal en de basisprijs en toon je dan de totaalprijs.

### Voorbeeldinteractie

```text
Aantal stuks?
> 4
Basisprijs?
> 5
Gewone bestelling (1) of internationale bestelling (2)?
> 1
Totaalprijs: 20
```

## h15-pizza

### Functionele analyse

We schrijven software om bestellingen van pizza's op te volgen. Deze software spreekt met andere software, bijvoorbeeld van Deliveroo of Uber Eats. We willen niet dat die diensten iets kunnen aanpassen aan de ingrediënten van onze pizza's, maar we willen wel zelf wel allerlei pizza's kunnen samenstellen.

### Technische analyse

Je krijgt volgende klasse `Pizza`:

```text
abstract class Pizza {
    private List<string> ingredienten;
    
    public Pizza(string[] extraToppings) {
        this.ingredienten = new List<string> { "deeg", "tomatensaus", "kaas" };
        foreach(var topping in extraToppings) {
            this.ingredienten.Add(topping);
        }
    }
    
    public abstract double BasisPrijs {
        get;
    }
    
    public double Prijs {
        return this.BasisPrijs + (this.ingredienten.Count * 0.5);
    }
    
    public void ToonIngredienten {
        foreach(var ingredient in ingredienten) {
            Console.WriteLine(ingredient);
        }
    }
    
    
}
```

Schrijf nu twee klassen `Margarita` en `Veggie` die overerven van `Pizza`, met basisprijs 5 en 6. Bij constructie krijgt een Margarita sowieso "mozzarella" toegevoegd aan de lijst met ingrediënten en krijgt een Veggie sowieso "tofu" en "spinazie", maar geen "kaas". Je moet hierbij een aanpassing doen aan `Pizza`, maar hou ze zo klein mogelijk. Schrijf een demonstratiemethode `DemonstreerPizzas` in de klasse `EigenObjectOefeningen`.

### Voorbeeldinteractie

```text
Een margarita zonder extra's kost: 
De ingredienten zijn: 
Een veggie zonder extra's kost:
De ingredienten zijn: 
```

### h15-menukaart

### Functionele analyse

We willen een digitale menukaart tonen in een online restaurant. Op deze kaart verschijnen gerechten in een standaardformaat. Kindergerechten volgen hetzelfde formaat, maar verschijnen in kleur.

### Technische analyse

* Schrijf een klasse `Gerecht` met properties `Naam` en `Prijs` \(deze laatste van type `double`\)
  * De methode `ToonOpMenu` print de naam, gevolgd door 3 tabs, gevolgd door de prijs
* Schrijf een kindklasse `KinderGerecht`
  * Dit werkt hetzelfde als een gewoon gerecht, maar de weergave op het menu gebruikt een willekeurige kleur. Als we bijvoorbeeld het aantal tabs aanpassen naar 5, moet KinderGerecht zonder aanpassingen mee volgen.
* Maak een methode `DemonstreerGerechten`. Hierin maak je een lijst met minstens 4 gerechten \(waarvan minstens 2 kindergerechten\) naar keuze en doorloop je de lijst zodat elk gerecht getoond wordt op het menu.

### Voorbeeldinteractie

```text
Paling in 't groen            22.00
Vol-au-vent             11.00(deze regel verschijnt in een willekeurige kleur)
Waterzooi            22.00
Kabouterschnitzel             12.00(deze regel verschijnt in een willekeurige kleur)
```

{% hint style="info" %}
Tabs zijn eigenlijk niet ideaal. Zoek, als je sneller klaar bent, uit hoe je stringformattering kan gebruiken om de naam van elk gerecht met exact 35 tekens weer te geven.
{% endhint %}

## 

