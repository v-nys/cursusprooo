# Null en NullReferenceException

Zoals nu duidelijk is bevatten variabelen steeds een referentie naar een object. Maar wat als we dit schrijven:

```csharp
Student stud1;
stud1.Naam= "Test";
```

Dit zal een fout geven. `stud1` bevat namelijk nog geen referentie. Maar wat dan wel?

Deze variabele bevat de waarde **`null`** . Net zoals bij value types die een default waarde hebben \(bv 0 bij een `int` \) als je er geen geeft, zo bevat reference types altijd `null`.

## NullReferenceException

Een veel voorkomende foutboodschap tijdens de uitvoer van je applicatie is de zogenaamde `NullReferenceException` . Deze zal optreden wanneer je code een object probeert te benaderen wiens waarde `null` is.

Laten we dit eens simuleren:

```csharp
Student stud1 = null;

Console.WriteLine(stud1.Name);
```

Dit zal resulteren in volgende foutboodschap:

![NullReferenceException error in VS](../../.gitbook/assets/nullref%20%281%29.png)

> We moeten in dit voorbeeld expliciet `=null` plaatsen daar Visual Studio slim genoeg is om je te waarschuwen voor eenvoudige potentiele NullReference fouten en je code anders niet zal compileren.

## NullReferenceException voorkomen

Objecten die niet bestaan zullen altijd `null`. Uiteraard kan je niet altijd al je code uitvlooien waar je misschien `=new SomeObject();` bent vergeten.

Voorts kan het ook soms by design zijn dat een object voorlopig `null` is.

Gelukkig kan je controleren of een object `null` is als volgt:

```csharp
if(stud1 == null)
    Console.WriteLine("oei. object bestaat niet")
```

### Verkorte null controle notatie

Vaak moet je dit soort code schrijven:

```csharp
if(stud1 != null)
{
    Console.WriteLine(stud1.Name)
}
```

Op die manier voorkom je `NullReferenceException`. Het is uiteraard omslachtig om steeds die check te doen. Je mag daarom ook schrijven:

```csharp
Console.WriteLine(stud1?.Name)
```

Het vraagteken direct na het object geeft aan: _"de code na dit vraagteken enkel uitvoeren indien het object voor het vraagteken niét null is"._

Bovenstaande code zal dus gewoon een lege lijn op scherm plaatsen indien `stud1` effetief `null` is, anders komt de naam op het scherm.

## Return null

Uiteraard mag je dus ook expliciet soms `null` teruggeven als resultaat van een methode. Stel dat je een methode hebt die in een array een bepaald object moet zoeken. Wat moet de methode teruggeven als deze niet gevonden wordt? Inderdaad, we geven dan `null` terug.

Volgende methode zoekt in een array van studenten naar een student met een specifieke naam en geeft deze terug als resultaat. Enkel als de hele array werd doorlopen en er geen match is wordt er `null` teruggegeven \(de werking van arrays van objecten worden later besproken\):

```csharp
static Student ZoekStudent(Student[] array, string naam)
{
    for (int i = 0; i < array.Length; i++)
    {
        if (array[i].Name == naam)
            return array[i];
    }

    return null;
}
```

