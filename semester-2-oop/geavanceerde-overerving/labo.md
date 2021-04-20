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

```csharp
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
        get {
            return this.BasisPrijs + (this.ingredienten.Count * 0.5);
        }
    }
    
    public void ToonIngredienten() {
        foreach(var ingredient in ingredienten) {
            Console.WriteLine(ingredient);
        }
    }
    
    
}
```

Schrijf nu twee klassen `Margarita` en `Veggie` die overerven van `Pizza`, met basisprijs 5 en 6. Bij constructie krijgt een Margarita sowieso "mozzarella" toegevoegd aan de lijst met ingrediënten en krijgt een Veggie sowieso "tofu" en "spinazie", maar geen "kaas". Je moet hierbij een aanpassing doen aan `Pizza`, maar hou ze zo klein mogelijk. Schrijf een demonstratiemethode `DemonstreerPizzas` in de klasse `EigenObjectOefeningen`.

### Voorbeeldinteractie

```text
Een margarita zonder extra's kost: (hier het resultaat)
De ingredienten zijn: 
(hieronder het effect van ToonIngredienten)
Een veggie zonder extra's kost:
De ingredienten zijn: 
(hieronder het effect van ToonIngredienten)
```

## h15-menukaart

### Functionele analyse

We willen een digitale menukaart tonen in een online restaurant. Op deze kaart verschijnen gerechten in een standaardformaat. Kindergerechten volgen hetzelfde formaat, maar verschijnen in kleur.

### Technische analyse

* Schrijf een klasse `Gerecht` met properties `Naam` en `Prijs` \(deze laatste van type `double`\)
  * De methode `ToonOpMenu` print de naam, gevolgd door 3 tabs, gevolgd door de prijs
* Schrijf een kindklasse `KinderGerecht`
  * Dit werkt hetzelfde als een gewoon gerecht, maar de weergave op het menu gebruikt een willekeurige kleur. Als we bijvoorbeeld het aantal tabs aanpassen naar 5, moet KinderGerecht zonder aanpassingen mee volgen.
    * Je kan een willekeurige kleur krijgen door een willekeurig getal tussen 1 en 15 te bepalen en dat dan te casten naar een waarde van de enum `ConsoleColor`.
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

## H15-figuren

{% hint style="info" %}
Kopieer eerst je code van [h14-figuren](../h12-overerving/oefeningen.md#oefening-h-14-figuren) naar een nieuwe klasse `VergelijkbareFiguur` met kindklassen `VergelijkbareCirkel` enzovoort. 
{% endhint %}

### Functionele analyse

We willen wat basisfunctionaliteit toevoegen aan onze figuren.

### Technische analyse

Voorzie de niet-abstracte subklassen van `VergelijkbareFiguur` van een `Equals` methode. Twee figuren zijn gelijk als ze van hetzelfde type zijn \(bijvoorbeeld beide cirkels, beide rechthoeken,...\) en dezelfde afmetingen hebben.

Hierna moet je ook de hash code aanpassen. Dit zie je als waarschuwing bovenaan de klasse in Visual Studio. Verwijder eerst de setters voor de afmetingen en zorg dat de afmetingen alleen bij constructie worden vastgelegd. Gebruik daarna de som van de hash codes van alle afmetingen als hash code voor de figuur.

{% hint style="warning" %}
De reden dat je de setters verwijdert is dat een object niet van hash code mag veranderen wanneer het al in gebruik is.
{% endhint %}

Voorzie ten slotte een aantal implementaties van `ToString`:

* voor cirkels toon je: `"Dit is een object van klasse VergelijkbareCirkel met straal <straal>"`  \(je vult &lt;straal&gt; correct in en de code moet juist blijven ook als je de klasse van naam verandert\)
* voor driehoeken toon je: `"Dit is een object van klasse VergelijkbareDriehoek met basis <basis> en hoogte <hoogte>"`  \(je vult de afmetingen correct in en de code moet juist blijven ook als je de klasse van naam verandert\)
* voor parallellogram zoals bij de vorige twee
* voor een rechthoek \(en dus vanzelf ook voor een vierkant\) genereer je een tekening bestaande uit puntjes. Je doet dit door de breedte en lengte naar boven af te ronden en daaruit het aantal rijen en kolommen in je tekening af te leiden.

Bijvoorbeeld, voor een rechthoek met breedte exact 31 en hoogte 4.5:

```text
...............................
...............................
...............................
...............................
...............................
```

### Voorbeeldinteractie

Schrijf een methode `DemonstreerVergelijkbareFiguren` die de werking van Equals test door figuren met dezelfde afmetingen met elkaar te vergelijken, figuren van verschillende types met elkaar te vergelijken, figuren met verschillende afmetingen met elkaar te vergelijken. Gebruik elk type figuur. Toon dan ook voor elke figuur de voorstelling als string.

## Uitbreidingen SchoolAdmin

### XML-serialisatie

Voorzie de klasse `Persoon` van een abstracte methode `NaarXML()`. Deze genereert een stringvoorstelling van de persoon in een XML-formaat. De klassen `Lector`, `AdministratiefPersoneel` en `Student` moeten een concrete implementatie voorzien. Mogelijk moet je aanpassingen doen om de code te laten werken.

Voor een lector is volgend resultaat mogelijk:

```text
<Lector>
<Id>7</Id>
<Naam>Plinius</Naam>
<Geboortedatum>01/02/0023</Geboortedatum>
<Cursussen>
<Paar>
  <Cursus>Filosofie</Cursus>
  <Duurtijd>4</Duurtijd>
</Paar>
</Cursussen>
</Lector>
```

Voor administratief personeel:

```text
<AdministratiefPersoneel>
<Id>7</Id>
<Naam>Plinius</Naam>
<Geboortedatum>01/02/0023</Geboortedatum>
<Taken>
<Paar>
  <Taak>Schrijven</Taak>
  <Duurtijd>4</Duurtijd>
</Paar>
</Taken>
</AdministratiefPersoneel>
```

Voor studenten stellen we dit uit. Je mag gewoon `<Student></Student>` teruggeven.

### Vergelijkbare objecten

Voorzie `Persoon` en `Cursus` van een eigen versie van Equals. Hiermee zullen we later nagaan dat een van deze objecten niet dubbel voorkomt in de lijst met geregistreerde objecten.

Een persoon is gelijk aan een andere persoon met hetzelfde ID. Je hoeft hier niet na te gaan dat de objecten van exact hetzelfde type zijn. In plaats daarvan kan je schrijven: `if (obj is Person) { ... }`

Een cursus is gelijk aan een andere cursus met hetzelfde ID.

Voorzie ook overal een hash code volgens de vuistregel in de cursus.

### `ToString`

Voorzie `Persoon` van een `ToString` methode die een resultaat van volgende vorm toont:

```text
Persoon
-------
Naam: Wouter Roelants
Leeftijd: 43
```

Zorg dat de concrete klassen hier ook het statuut van de persoon aan koppelen, bijvoorbeeld:

```text
Persoon
-------
Naam: Geertrui Willems
Leeftijd: 51
Meerbepaald, administratief personeel
```

Doe dit niet met `GetType`, want dan is de schrijfwijze anders. Doe het met de hand per klasse.

