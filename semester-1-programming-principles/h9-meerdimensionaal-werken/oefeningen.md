# Oefeningen

## Inleiding

Al deze oefeningen maak je als statische methoden van een klasse Meerdimensionaal. Je kan elk van deze methoden uitvoeren via een keuzemenu, zoals bij vorige hoofdstukken.

## H09-Som-n-de-rij

### Leerdoelen

* Werken met multidimensionale arrays

### Functionele analyse

We wensen de gegevens in één rij te groeperen door hun som te bepalen, een beetje zoals je dat in een Excel spreadsheet zou kunnen doen.

### Technische analyse

Schrijf in de klasse `Meerdimensionaal` een methode `SomNdeRij`. Deze heeft twee parameters: een meerdimensionale array van `double` en een rijnummer (een `int`). De returnwaarde is de som van alle waarden op de rij met het gevraagde nummer.

Deze methode toont niets op de console, maar je kan ze wel testen via deze voorbeeldcode, die je mag gebruiken wanneer deze oefening wordt opgestart via het keuzemenu:

```csharp
double[,] numbers = {{4.2, 8.1, 3.3},
                     {2.0, 4.0, 6.0},
                     {3.1,3.2,3.3}};
Console.WriteLine("Van welke rij wil je de som zien?");
int row = Convert.ToInt32(Console.ReadLine());
Console.WriteLine(SomNdeRij(numbers,row));
```

## H09-Som-per-rij

### Leerdoelen

* Werken met multidimensionale arrays

### Functionele analyse

We wensen de gegevens in één rij te groeperen door hun som te bepalen, een beetje zoals je dat in een Excel spreadsheet zou kunnen doen.

### Technische analyse

Schrijf in de klasse `Meerdimensionaal` een methode `SomPerRij`. Deze maakt een tweedimensionale array met het gevraagde aantal rijen en het gevraagde aantal kolommen aan. Je mag veronderstellen dat er een geldig aantal wordt ingegeven. Vervolgens vraagt ze, rij per rij en kolom per kolom, een getalwaarde. Wanneer elke positie is ingevuld, toont ze de som per rij van de ingegeven getallen.

### Voorbeeldinteractie

```
Hoe veel rijen telt je array?
> 3
Hoe veel kolommen telt je array?
> 2
Waarde voor rij 1, kolom 1?
> 4
Waarde voor rij 1, kolom 2?
> 2
Waarde voor rij 2, kolom 1?
> 1
Waarde voor rij 2, kolom 2?
> 1
Waarde voor rij 3, kolom 1?
> 7
Waarde voor rij 3, kolom 2?
> 9
Sommen per rij:
6
2
16
```

## H09-Pixels

### Leerdoelen

* Werken met multidimensionale arrays
* Werken met enumeratietypes

### Functionele analyse

We willen een simpel tekenprogramma maken in de terminal. De gebruiker kan pixel per pixel een gewenste kleur aangeven.

### Technische analyse

Schrijf in `Meerdimensionaal` een methode `Pixels`.

Vraag hierin eerst aan de gebruiker welke afmetingen hij wil gebruiken voor zijn afbeelding. Dit bepaalt het aantal rijen en kolommen en dus het aantal pixels. Maak vervolgens een array van `ConsoleColor` waarden aan met deze afmetingen. Vraag tenslotte in een lus wat de gebruiker wil doen:

* een pixel kleuren
  * vraag hierbij de rij-index en kolom-index
  * vraag ten slotte in welke kleur deze moet worden ingevuld
    * je kan sneller een array van alle kleuren krijgen met volgende code: `ConsoleColor[] kleuren = (ConsoleColor[]) Enum.GetValues(typeof(ConsoleColor));`
    * je hoeft deze instructie niet volledig te begrijpen: ze doet hetzelfde als `ConsoleColor[] kleuren = {ConsoleColor.Back, ConsoleColor.DarkBlue, ...}` maar vraagt gewoon minder typwerk
* de afbeelding zoals ze momenteel is tonen
  * toon hiervoor elke pixel als een spatie met `Console.Write(" ")`

### Voorbeeldinteractie

![](../../.gitbook/assets/paint.png)

## H09-color-filter

### Leerdoelen

* Werken met multidimensionale arrays
* Werken met enumeratietypes

### Functionele analyse

We zullen ons tekenprogramma uitbreiden met een extra functie die de array bewerkt. Met andere woorden, een (simpele) afbeeldingsfilter. Deze zal bepaalde pixels automatisch rood kleuren.

### Technische analyse

Schrijf een functie `RedFilter`. Deze heeft een afbeelding (een `ConsoleColor[,]`) als invoer en vervangt alle vakjes die zich op en oneven rij **én** een oneven kolom bevinden door de kleur rood. Ze toont de afbeelding niet.

Deze oefening kan je niet rechtstreeks oproepen via het keuzemenu voor deze klasse. Het wordt een extra optie om iets met je afbeelding te doen.

### Voorbeeldinteractie

```
Wat wil je doen?
1. een pixel kleuren
2. afbeelding tonen
3. roodfilter toepassen
```

## H09-triangle-filter

### Leerdoelen

* Werken met multidimensionale arrays
* Werken onderling afhankelijke indexen

### Functionele analyse

We zullen ons tekenprogramma uitbreiden met nog een extra functie die de array bewerkt. Deze functie "knipt" de afbeelding diagonaal in twee.

### Technische analyse

Schrijf een functie `LowerTriangleFilter`. Deze heeft een afbeelding (een `ConsoleColor[,]`). Ze zorgt ervoor dat alle pixels op of onder de diagonaal van links boven tot rechts onder wit worden gemaakt. Dit vereist wat te veel rekenwerk als de afbeelding geen vierkant is, dus geef de foutmelding `"deze filter kan niet worden toegepast op deze afbeelding"` als het aantal rijen verschilt van het aantal kolommen.

Deze oefening kan je niet rechtstreeks oproepen via het keuzemenu voor deze klasse. Het wordt een extra optie om iets met je afbeelding te doen.

### Voorbeeldinteractie

```
Wat wil je doen?
1. een pixel kleuren
2. afbeelding tonen
3. roodfilter toepassen
4. driehoeksfilter toepassen
```

## H09-HeatmapPaardensprong

### Leerdoelen

* Werken met multidimensionale arrays
* Werken met geneste iteratie
* Werken met Random

### Functionele analyse

Ik wil een paard een aantal willekeurige (random) sprongen laten maken op een schaakbord vertrekkende van een gegeven positie.

Na de sprongen wil ik een "heatmap" van deze sprongen. Hoe vaak is het paard op een positie geweest.

Volg de  conventie:

&#x20;

![](<../../.gitbook/assets/image (71) (1).png>)

### Technische analyse

Schrijf een nieuwe klasse `HeatmapPaardensprong`. Het startpunt in deze klasse  is de methode `HeatmapPaardensprongMain`.

Vraag hierin eerst aan de gebruiker hoe vaak het paard moet springen en vraag ook de beginpositie in de vorm A1..H8

Je gaat vervolgens vertrekkende van deze positie een aantal willekeurige sprongen kiezen. Per sprong zijn er maximaal 8 mogelijkheden (zie afbeelding). Je zorgt er voor dat de sprong geldig is (binnen het bord). Deze positie is de startpositie voor de volgende sprong. De positie zelf is ook bezocht, dat houd je bij.



### Voorbeeldinteractie

![](<../../.gitbook/assets/image (68).png>)

## H09-ConwayGameOfLife

### Leerdoelen

* Werken met multidimensionale arrays
* Werken met geneste iteratie
* Werken met Random

### Functionele analyse

Surf naar de webstek: [https://www.compadre.org/osp/EJSS/3577/12.htm](https://www.compadre.org/osp/EJSS/3577/12.htm). Hier wordt het "Game of Life" uitgelegd. We gaan een vereenvoudigde console versie maken. Dit wordt bijvoorbeeld veel gebruikt om automatisch omgevingen met structuur te genereren in games met procedurele generatie.

### Technische analyse

Schrijf een nieuwe klasse `ConwayGameOfLife`. Het startpunt in deze klasse  is de methode `ConwayGameOfLifeMain`.

Vraag hierin eerst aan de gebruiker hoe veel cellen hij wil: 10 geeft een veld van 10 op 10 cellen.&#x20;

Vervolgens vraag je de gebruiker hoeveel generaties hij wil zien.

Je gaat vervolgens het bord willekeurig opvullen. Gebruik een enum type om de status van een cel (levend, dood) bij te houden.

Vervolgens ga je generatie per generatie laten zien. Van de éne generatie op de andere gelden volgende regels:

* Any live cell with fewer than two live neighbors dies, as if by loneliness
* Any live cell with more than three live neighbors dies, as if by overcrowding.
* Any live cell with two or three live neighbors lives, unchanged, to the next generation.
* Any dead cell with exactly three live neighbors comes to life.

Laat elke generatie 2 seconden zien en bereken dan de volgende generatie (kijk even naar de oefening met de chronometer!).

### Voorbeeldinteractie

![](<../../.gitbook/assets/image (67).png>)

##

##
