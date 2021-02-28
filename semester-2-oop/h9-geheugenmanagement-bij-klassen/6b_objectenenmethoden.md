# Objecten en methoden

## Objecten als argumenten

Klassen zijn "gewoon" nieuwe types. Alle regels die we dus al kenden in verband met het doorgeven van variabelen als parameters in een methoden blijven gelden. Het enige verschil is dat we objecten **by reference** meegeven aan een methode. Aanpassingen aan het object in de methode zal dus betekenen dat je het originele object aanpast dat aan de methode werd meegegeven. Hier moet je dus zeker rekening mee houden.

Een voorbeeld. Stel dat we volgende klasse hebben waarin we metingen willen opslaan, alsook wie de meting heeft gedaan:

```csharp
class Meting
{
    public int Temperatuur { get; set; }
    public string OpgemetenDoor { get; set; }
}
```

In ons hoofdprogramma schrijven we een methode `ToonMetingInKleur` die ons toelaat om deze meting op het scherm te tonen in een bepaalde kleur. Het gebruik en de methode zelf zouden er zo kunnen uitzien:

```csharp
static void Main(string[] args)
{
    Meting m1 = new Meting();
    m1.Temperatuur = 26; 
    m1.OpgemetenDoor = "Elon Musk";
    Meting m2 = new Meting();
    m2.Temperatuur = 34; 
    m2.OpgemetenDoor = "Dennis Rodman";

    ToonMetingInKleur(m1, ConsoleColor.Red);
    ToonMetingInKleur(m2, ConsoleColor.Gray);
}

static void ToonMetingInKleur (Meting inmeting, ConsoleColor kleur)
{
    Console.ForegroundColor = kleur;
    Console.WriteLine($"Temperatuur {inmeting.Temperatuur}°C werd opgemeten door {inmeting.OpgemetenDoor}");
    Console.ResetColor();
}
```

### Objecten in methoden aanpassen

Je kan dus ook methoden schrijven die meegegeven objecten aanpassen daar we deze **by reference** doorsturen. Een voorbeeld:

```csharp
static void ToonMetingEnVerhoog(Meting inmeting)
{
    ToonMetingInKleur(inmeting, ConsoleColor.Green);

    inmeting.Temperatuur++;
}
```

Als we deze methode als volgt aanroepen

```csharp
Meting m1 = new Meting();
m1.Temperatuur = 26; m1.OpgemetenDoor = "Elon Musk";

ToonMetingEnVerhoog(m1);

Console.WriteLine(m1.Temperatuur);
```

Da zullen we zien dat de temperatuur in `m1` effectief met 1 werd verhoogd.

Dit gedrag zouden we NIET zien bij volgende methode daar `int` **by value** wordt doorgegeven:

```csharp
static void VerhoogGetal(int inmeting)
{
    inmeting++;
}
```

### Delen van objecten als parameter

Stel dat we volgende methode hebben

```csharp
static double Gemiddelde(double getal1, double getal2)
{
    return (getal1 + getal2) / 2;
}
```

Je mag deze methode dus ook oproepen als volgt \(we gebruiken de `Meting` objecten `m1` en `m2` uit vorige paragraaf\):

```csharp
double result= Gemiddelde(m1.Temperatuur, m2.Temperatuur);
```

Het type van de property `Temperatuur` is `int` en mag je dus als parameter aan deze methoden meegeven.

## Objecten als resultaat

Weer hetzelfde verhaal: ook klassen mogen het resultaat van een methoden zijn.

```csharp
static Meting GenereerRandomMeting()
{
    Meting result = new Meting();
    Random r = new Random();
    result.Temperatuur = r.Next(-100, 200);
    result.OpgemetenDoor = "Onbekend";

    return result;
}
```

Deze methode kan je als volgt dan gebruiken:

```csharp
Meting m3 = GenereerRandomMeting();
```

Merk op dat het dus kan zijn dat een methode `null` teruggeeft. Het kan dus zeker geen kwaad om steeds in je code te controleren of je effectief iets hebt terug gekregen:

```csharp
Meting m3 = GenereerRandomMeting();
if(m3 != null)
{
    ToonMetingInKleur(m3, ConsoleColor.Red);
}
```

