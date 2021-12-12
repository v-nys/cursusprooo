# Oefeningen

## Oefeningen

### **Oefening H7-Opwarmers**

#### **Leerdoelen**

* Methodes definiëren met return type en parameters
* Oproepen van de methodes

#### **Functionele analyse**



Schrijf een methode en toon de werking ervan aan door vanuit een methode Opwarmers de desbetreffende methode op te roepen::

* Methode `BerekenStraal` die de straal van een cirkel kan berekenen waarvan je de diameter meegeeft (de diameter geef je mee als parameter).
* Idem voor BerekenOmtrek en BerekenOppervlakte.
* Methode Maximum die het grootste van 2 getallen teruggeeft (beide getallen geef je mee als parameter).
* Methode `IsEven` die bepaalt of een getal even of oneven is (geeft een `bool` terug die `true` is indien even).
* Methode `ToonOnEvenNummers` die alle oneven getallen van 1 tot n toont waarbij n als parameter wordt meegegeven.

#### Technische analyse&#x20;

#### Voorbeeldinteractie

![](<../../.gitbook/assets/image (67) (1).png>)

### **Oefening H7-EmailadresGenerator**

#### **Leerdoelen**

* Methodes definiëren met return type en parameters
* Oproepen van de methodes

#### **Functionele analyse**

Schrijf een programma dat op basis van je voornaam, naam en het feit of je al dan niet een student bent een AP e-mailadres genereert. Het e-mailadres moet uit allemaal kleine letters bestaan en moet een geldig e-mailadres zijn.

Je mag geen String methodes gebruiken maar je schrijft je eigen methodes. Als aanzet is de methode StringToLower al uitgewerkt.&#x20;

**Uitbreiding**: kijk of voor al je lectoren en medestudenten het gegenereerde e-mailadres geldig is. Pas eventueel je code aan indien niet.

#### Technische analyse&#x20;

Werk volgend flowchart verder af en zet om in C#.

{% file src="../../.gitbook/assets/H07-EmailGeneratorTemplate.fprg" %}

#### Voorbeeldinteractie

![](<../../.gitbook/assets/image (69).png>)



### Oefening: H7-film-default

#### Leerdoelen

* methodes met default argumenten

#### Functionele analyse

Maak een methode `FilmRuntime` met 3 parameters:

1. Een string die de naam van de film bevat
2. Een integer die duur in minuten van de film bevat
3. Een enum-type `FilmGenre` die het genre van de film bevat. Deze enum heeft de mogelijke waarden `Drama`, `Action`, `Comedy` en `Uncategorized`.

Deze methode toont dan een samenvatting van de film **op het scherm**, gevolgd door zijn duur en genre in volgend formaat:

```
The Matrix (120 minuten, Action)
```

Indien de duur niet gespecifieerd wordt, wordt gezegd dat hij 90 minuten duurt. Indien het genre niet wordt meegegeven, wordt "Uncategorized" vermeld op het scherm.

#### Technische analyse

Schrijf je methode met drie parameters, maar geef de duur en het genre een default waarde. Toon aan in je main dat de methode werkt met zowel 1, 2 als 3 parameters. Toon ook aan dat je met "named arguments" de methode kan aanroepen. Schrijf hiervoor een extra methode `DemonstreerFilm` die gewoon `FilmRuntime` een paar keer oproept en die je kan opstarten van uit je keuzemenu.

**voorbeeldinteractie(s)**

```
The Matrix (120 minuten, Action)
Crouching Tiger, Hidden Dragon (90 minuten, Unknown)
```

### Oefening: H7-begroeten

#### Leerdoelen

* overloading

#### Functionele analyse

Schrijf drie manieren om gebruikers te begroeten. Naargelang hoe je de oproep schrijft, wordt de juiste methode uitgevoerd. Schrijf ook een methode om te demonstreren.

#### Technische analyse

Noem je methode om te begroeten `Hallo`. Je kan deze oproepen zonder argumenten en dan wordt je naam gevraagd via de console. Je kan ze ook oproepen met één of twee argumenten. Je maakt ook een methode `DemonstreerHallo` en vraagt hierin om drie namen die je als argument kan gebruiken. De methode `Hallo` geeft ook aan hoe ze is opgeroepen.

**Voorbeeldinteractie**

```
DemonstreerHallo heeft drie namen nodig!
> Misty
> Ash
> Brock
Hallo is opgeroepen zonder argument. Wat is je naam?
> Oak
Hallo, Oak!
Hallo is opgeroepen met één argument.
Hallo, Misty!
Hallo is opgeroepen met twee argumenten.
Hallo, Ash en Brock!
```
