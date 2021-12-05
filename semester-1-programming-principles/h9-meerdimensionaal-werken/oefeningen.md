# Oefeningen

## Inleiding

Al deze oefeningen maak je als statische methoden van een klasse Meerdimensionaal. Je kan elk van deze methoden uitvoeren via een keuzemenu, zoals bij vorige hoofdstukken.

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

## H09-som-per-kolom

### Leerdoelen

* Werken met multidimensionale arrays

### Functionele analyse

We wensen de gegevens in één kolom te groeperen door hun som te bepalen, een beetje zoals je dat in een Excel spreadsheet zou kunnen doen.

### Technische analyse

Schrijf in de klasse `MeerDimensionaal` een methode `SomPerKolom`. Deze werkt zoals de vorige oefening, maar maakt de som per kolom.

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
Sommen per kolom:
12
12
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

![](<../../.gitbook/assets/image (71).png>)

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

Surf naar de webstek: [https://www.compadre.org/osp/EJSS/3577/12.htm](https://www.compadre.org/osp/EJSS/3577/12.htm)

We gaan een vereenvoudigde console versie maken.



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
