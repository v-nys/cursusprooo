# Labo

## Oefening: som-per-rij

### Functionele analyse

We wensen de gegevens in één rij te groeperen door hun som te bepalen, een beetje zoals je dat in een Excel spreadsheet zou kunnen doen.

### Technische analyse

Schrijf in de klasse `DataStructuren` een methode `SomPerRij`. Deze maakt een tweedimensionale array met het gevraagde aantal rijen en het gevraagde aantal kolommen aan. Je mag veronderstellen dat er een geldig aantal wordt ingegeven. Vervolgens vraagt ze, rij per rij en kolom per kolom, een getalwaarde. Wanneer elke positie is ingevuld, toont ze de som per rij van de ingegeven getallen.

### Voorbeeldinteractie

```text
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

## Oefening: som-per-kolom

### Functionele analyse

We wensen de gegevens in één kolom te groeperen door hun som te bepalen, een beetje zoals je dat in een Excel spreadsheet zou kunnen doen.

### Technische analyse

Schrijf in de klasse `DataStructuren` een methode `SomPerKolom`. Deze werkt zoals de vorige oefening, maar maakt de som per kolom.

### Voorbeeldinteractie

```text
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

## Oefening: Pixels

### Functionele analyse

We willen een simpel tekenprogramma maken in de terminal. De gebruiker kan pixel per pixel een gewenste kleur aangeven.

### Technische analyse

Schrijf in \(nieuwe klasse met `ToonSubmenu`\)  `DataStructuren` een methode `Pixels`.

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

## SchoolAdmin project

Als je alles eerder mee hebt kunnen volgen, werk dan vanaf je recentste commit. Anders is er een modeloplossing voorzien waarvan je kan verder werken.

### `StudyProgram.GetOverview` en `Course.GetOverview` met `foreach` en `var`

Pas je ShowOverview methodes aan zodat er geen gebruik wordt gemaakt van een klassieke `for`, maar wel van een foreach. Gebruik `var` voor je iteratieveriabele. Om het gebruik van een index te vermijden, zal je de array van `string` ook moeten vervangen door een `List<string>`.

### Alle studenten in het systeem bijhouden

Voorzie de klasse Student van een statische property `Students`. Deze is van het type `List<Student>` en bevat altijd elke student die in het systeem aanwezig is. Dit gebeurt door bij de constructie van elk `Student`-object de lijst uit te breiden.

### Lijst van studenten

Vervang alle properties van `StudyProgram`, `Course` en `Student` van een array type naar een `List` type.

### Lijst van studenten, zonder dubbels

Verbeter je vernieuwde property `Students` van `StudyProgram` zodat er geen dubbels meer in de lijst met alle studenten in een studieprogramma voorkomen. Maak hierbij gebruik van de methode `Contains` van de klasse `List<T>`.

### Flexibelere punten

Het is op termijn niet houdbaar om elke student een veld voor het cijfer per vak te geven \(bijvoorbeeld `MarkCommunication`\). Niet alle studenten volgen dezelfde vakken en puur technisch is het geen goed ontwerp dat je de `Student` klasse moet aanpassen omdat er rekening gehouden moet worden met een nieuw object van de `Course` klasse.

Een betere optie bestaat erin de cijfers van een student bij te houden als een `Dictionary<Course,byte>`. Geef `Student` een `private` attribuut `Grades` van dit type. Voorzie ook een methode `SetGrade(Course course, byte grade)` om het cijfer voor een bepaald vak in te stellen. Op deze manier kan je voorkomen dat een cijfer hoger dan 20 wordt ingesteld.





