# Properties

## Properties

In dit hoofdstuk bespreken we eerst waarom properties nodig zijn. Vervolgens bespreken we de 2 soorten properties die er bestaan:

1. Full properties
2. Auto properties

### In een wereld zonder properties

Properties \(_eigenschappen_\) zijn de C\# manier om objecten hun interne staat in en uit te lezen. Ze zorgen voor een gecontroleerde toegang tot de interne structuur van je objecten.

Stel dat we volgende klasse hebben:

```csharp
public class SithLord
{
    private int energy;
    private string sithName;
}
```

Een `SithLord` heeft steeds een verborgen Sith Name en ook een hoeveelheid energie die hij nodig heeft om te strijden. **Het is uit den boze dat we eenvoudige data fields \(`energy` en `name`\) `public` maken.** Zouden we dat wel doen dan kunnen externe objecten deze geheime informatie uitlezen!

```csharp
SithLord palpatine = new SithLord();
Console.WriteLine(palpatine.sithName); //DIT ZAL DUS NIET WERKEN, daar sithName private is.
```

We willen echter wel van buiten uit het energy-level van een `SithLord` kunnen instellen. Maar ook hier hetzelfde probleem: wat als we de energy-level op `-1000` instellen? Terwijl `energy` nooit onder `0` mag gaan.

**Properties lossen dit probleem op**

#### Oldschool oplossing

Vroeger loste men voorgaande probleem op door Get-methoden te schrijven:

Je zal deze manier nog in veel andere talen tegenkomen. Wij prefereren properties zoals we nu zullen uitleggen.

```csharp
public class SithLord
{
    private int energy;
    private string sithName;

    public void SetSithName(string newname)
    {
        sithName = newname;
    }

    public string GetSithName()
    {
        return "YOU WISH!";
    }

    public void SetEnergy(int value)
    {
        if(value > 0 && value < 9999)
            energy = value;
    }

    public int GetEnergy()
    {
        return energy;
    }
}
```

Je zou dan kunnen doen:

```csharp
SithLord vader = new SithLord();
vader.SetEnergy(20); 
Console.WriteLine($"Vaders energy is {vader.GetEnergy()}"); //get
```

## Full properties

Een **full property** ziet er als volgt uit:

```csharp
class SithLord
{
    private int energy;
    private string sithName;

    public int Energy
    {
        get
        {
            return energy;
        }
        set
        {
            energy = value;
        }
    }
}
```

Dankzij deze code kunnen we nu elders dit doen:

```csharp
SithLord vader = new SithLord();
vader.Energy = 20; //set
Console.WriteLine($"Vaders energy is {Vader.Energy}"); //get
```

Vergelijk dit met de vorige alinea waar we dit met Get en Set methoden moesten doen. Deze property syntax is veel eenvoudiger in het gebruik.

We zullen de property nu stuk per stuk analyseren:

* `public int Energy`: een property is normaal `public`. Vervolgens zeggen we wat voor type de property moet zijn en geven we het een naam. Indien je de property gaat gebruiken om een intern dataveld naar buiten beschikbaar te stellen, dan is het een goede gewoonte om dezelfde naam als dat veld te nemen maar nu met een hoofdletter. \(dus `Energy` i.p.v. `energy`\).
* { }: Vervolgens volgen 2 accolades waarbinnen we de werking van de property beschrijven.
* `get {}`: indien je wenst dat de property data **naar buiten** moet sturen, dan schrijven we de get-code. Binnen de accolades van de get schrijven we wat er naar buiten moet gestuurd worden. In dit geval `return energy` maar dit mag even goed bijvoorbeeld `return 4` of een hele reeks berekeningen zijn. Het element dat je returnt in de get code moet uiteraard van hetzelfde type zijn als waarmee je de property hebt gedefinieerd \(`int` in dit geval\).
  * We kunnen nu van buitenaf toch de waarde van `energy` uitlezen via de property en het get-gedeelte: `Console.WriteLine(palpatine.Energy);`
* set{}: in het set-gedeelte schrijven we de code die we moeten hanteren indien men van buitenuit een waarde aan de property wenst te geven om zo een interne variabele aan te passen. De waarde die we van buitenuit krijgen \(als een parameter zeg maar\) zal **altijd** in een lokale variabele `value` worden bewaard. Deze zal van het type van de property zijn. Vervolgens kunnen we `value` toewijzen aan de interne variabele indien gewenst: `energy=value` 
  * We kunnen vanaf nu van buitenaf waarden toewijzen aan de property en zo `energy`vtoch bereiken: `palpatine.Energy=50`.

#### Snel property schrijven

Visual Studio heeft een ingebouwde shortcut om snel een full property, inclusief een bijhorende private dataveld, te schrijven. **Typ `propfull` gevolgd door twee tabs!**

### Full property met toegangscontrole

De full property `Energy` heeft nog steeds het probleem dat we negatieve waarden kunnen toewijzen \(via de `set`\) die dan vervolgens zal toegewezen worden aan `energy`.

> Properties hebben echter de mogelijkheid om op te treden als wachters van en naar de interne staat van objecten.

We kunnen in de `set`code extra controles inbouwen. Asl volgt:

```csharp
   public int Energy
    {
        get
        {
            return energy;
        }
        set
        {
            if(value >= 0)
                energy = value;
        }
    }
```

Enkel indien de toegewezen waarde groter of gelijk is aan 0 zal deze ook effectief aan `energy` toegewezen worden. Volgende lijn zal dus geen effect hebben: `palpatine.Energy=-1;`

We kunnen de code binnen `set` \(en `get`\) zo complex als we willen maken.

### Property variaties

We zijn niet verplicht om zowel de `get` en de `set` code van een property te schrijven.

#### Write-only property

```csharp
   public int Energy
    {
        set
        {
            if(value >= 0)
                energy = value;
        }
    }
```

We kunnen dus enkel `energy` een waarde geven, maar niet van buitenuit uitlezen.

#### Read-only property

```csharp
   public int Energy
    {
        get
        {
            return energy;
        }
    }
```

We kunnen dus enkel `energy` van buitenuit uitlezen, maar niet aanpassen.

#### Read-only property met private set

Soms gebeurt het dat we van buitenuit enkel de gebruiker de property read-only willen maken. We willen echter intern \(in de klasse zelf\) nog steeds controleren dat er geen illegale waarden aan private datafields worden gegeven. Op dat moment definieren we een read-only property met een private setter:

```csharp
   public int Energy
    {
        get
        {
            return energy;
        }
        private set
        {
            if(value >= 0)
                energy = value;
        }
    }
```

Van buitenuit zal enkel code werken die de`get`-van deze property aanroept: `Console.WriteLine(palpatine.Energy);`. Code die de `set` van buitenuit nodig heeft zal een fout geven zoals: `palpatine.Energy=65`; ongeacht of deze geldig is of niet.

**Nu goed opletten**: indien we in het object de property willen gebruiken dan moeten we deze dus ook effectief aanroepen, anders omzeilen we hem als we rechtstreeks `energy` instellen.

Kijk zelf naar volgende **slechte** code:

```csharp
class SithLord
{
    private int energy;
    private string sithName;

    public void ResetLord()
    {
        energy = -1;
    }

    public int Energy
    {
        get
        {
            return energy;
        }
        private set
        {
            if(value >= 0)
                energy = value;
        }
    }
}
```

De nieuw toegevoegde methode `ResetLord` willen we gebruiken om de lord z'n energy terug te verlagen. Door echter `energy=-1` te schrijven geven we dus -1 rechtstreeks aan `energy`. Nochtans is dit een illegale waarde. We moeten dus in de methode ook expliciet via de property gaan en dus schrijven:

```csharp
public void ResetLord()
{
    Energy = -1; // Energy i.p.v. energy
}
```

> **Het is een goede gewoonte om zo vaak mogelijk via de properties je interne variabele aan te passen en niet rechtstreeks het dataveld zelf.**

#### Read-only Get-omvormers

Je bent uiteraard niet verplicht om voor iedere interne variabele een bijhorende property te schrijven. Omgekeerd ook: mogelijk wil je extra properties hebben voor data die je 'on-the-fly' kan genereren.

Stel dat we volgende klasse hebben

```csharp
public class Person
{
    private string firstName;
    private string lastName;
}
```

We willen echter ook soms de volledige naam op het scherm tonen \("Voornaam + Achternaam"\). Via een read-only property kan dit supereenvoudig:

```csharp
public class Person
{
    private string firstName;
    private string lastName;
    public string FullName
    {
        get{ return $"{firstName} {lastName}";}
    }
    public string Email
    {
        get
        {
            return $"{firstName}.{lastName}@ap.be";
        }
    }
}
```

Of nog eentje:

```csharp
public class Earth
{
    public double GravityConstant
    {
        get
        {
            return 9.81;
        }
    }
}
```

Nog een voorbeeldje:

```csharp
public class Person
{
    private int age;

    public bool IsProbablyAlive
    {
        get
        {
            if(age > 120) return false;
            return true;
        }
    }
}
```

Vaak gebruiken we dit soort read-only properties om data te transformeren. Stel bijvoorbeeld dat we volgende klasse hebben:

```csharp
public class Person
{
    private int age; //in jaren

    public int AgeInMonths
    {
        get
        {
            return age * 12;
        }
    }
}
```

## Auto properties

Automatische eigenschappen \(autoproperties\) in C\# staan toe om eigenschappen \(properties\) die enkel een waarde uit een private variabele lezen en schrijven verkort voor te stellen.

Zo kan je eenvoudige de klasse Person herschrijven met behulp van autoproperties. De originele klasse:

```csharp
public class Person
    {

        private string firstName;
        private string lastName;
        private int age;

        public string FirstName
        {
            get
            {
                return firstName;
            }
            set
            {
                firstName = value;
            }
        }

        public string LastName
        {
            get
            {
                return lastName;
            }
            set
            {
                lastName = value;
            }
        }

        public int Age
        {
            get
            {
                return age;
            }
            set
            {
                age = value;
            }
        }
    }
```

De herschreven klasse met autoproperties \(autoprops\):

```csharp
public class Person
    {

        public string FirstName { get; set; }
        public string LastName { get; set; }
        public int Age { get; set; }

    }
```

Beide klassen hebben exact dezelfde functionaliteit, echter de klasse aan de rechterzijde is aanzienlijk eenvoudig om te lezen en te typen.

### Beginwaarde van autoprops

Je mag autoproperties beginwaarden geven door de waarde achter de property te geven, als volgt:

```csharp
public int Age {get;set;} = 45;
```

### Altijd auto-properties?

Merk op dat je dit enkel kan doen indien er geen extra logica in de property aanwezig is. Stel dat je bij de setter van age wil controleren op een negatieve waarde, dan zal je dit zoals voorheen moeten schrijven en kan dit niet met een automatic property:

```csharp
set
{
    if( value > 0)
        age = value;
}
```

**Voorgaande property kan dus NIET herschreven worden met een automatic property.**

### Alleen-lezen eigenschap

Je kan automatic properties ook gebruiken om bijvoorbeeld een read-only property te definiëren . Als volgt:

Originele klasse:

```csharp
public string FirstName
{

    get
    {
        return firstName;
    }
}
```

Met autoprops:

```csharp
public string FirstName { get; private set;}
```

En andere manier die ook kan is als volgt:

```csharp
public string FirstName { get; }
```

De enige manier om FirstName een waarde te geven is via de constructor van de klasse. Alle andere manieren zal een error genereren.[Meer info.](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-6#read-only-auto-properties)

### Snel autoproperties typen in Visual Studio:

Als je in Visual Studio in je code `prop` typt en vervolgens twee keer de tabtoets indrukt dan verschijnt al de nodige code voor een automatic property. Je hoeft dan enkel nog volgende zaken in orde te brengen:

* Het type van de property
* De naam van de property \(identifier\) 
* De toegankelijkheid van get/set \(public, private, protected\)

Via `propg` krijg je aan autoproperty met private setter.

## Methode of property

Een veel gestelde vraag bij beginnende OO-ontwikkelaars is: "Moet dit in een property of in een methode gestoken worden?"

De regel is eenvoudig:

* Betreft het een actie, iets dat het object moet doen \(tekst tonen, iets berekenen, etc\) dan plaats je het in een **methode**
* Betreft het een eigenschap die een bepaalde waarde heeft, dan gebruik je een **property**

[Hier een iets meer uitgebreid PRO antwoord](http://firebreaksice.com/csharp-property-vs-method-guidelines/)

