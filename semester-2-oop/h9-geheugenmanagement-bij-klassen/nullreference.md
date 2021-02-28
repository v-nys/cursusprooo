# Null en NullReferenceException

## Null en NullReferenceException

Zoals nu duidelijk is bevatten variabelen steeds een referentie naar een object. Maar wat als we dit schrijven:

```csharp
Student stud1;
stud1.Naam= "Test";
```

Dit zal een fout geven. `stud1` bevat namelijk nog geen referentie. Maar wat dan wel?

Deze variabele bevat de waarde **`null`** . Net zoals bij value types die een default waarde hebben \(bv 0 bij een `int` \) als je er geen geeft, zo bevat reference types altijd `null`.

### NullReferenceException

Een veel voorkomende foutboodschap tijdens de uitvoer van je applicatie is de zogenaamde `NullReferenceException` . Deze zal optreden wanneer je code een object probeert te benaderen wiens waarde `null` is.

Laten we dit eens simuleren:

```csharp
Student stud1 = null;

Console.WriteLine(stud1.Name);
```

Dit zal resulteren in volgende foutboodschap:

![NullReferenceException error in VS](../../.gitbook/assets/nullref%20%282%29.png)

> We moeten in dit voorbeeld expliciet `=null` plaatsen daar Visual Studio slim genoeg is om je te waarschuwen voor eenvoudige potentiele NullReference fouten en je code anders niet zal compileren.

### NullReferenceException voorkomen

Objecten die niet bestaan zullen altijd `null`. Uiteraard kan je niet altijd al je code uitvlooien waar je misschien `=new SomeObject();` bent vergeten.

Voorts kan het ook soms by design zijn dat een object voorlopig `null` is.

Gelukkig kan je controleren of een object `null` is als volgt:

```csharp
if(stud1 == null)
    Console.WriteLine("oei. object bestaat niet")
```

### Return null

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

## Kennisclip

![](../../.gitbook/assets/infoclip%20%282%29.png)

* [Referenties en null](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=49247267-d9db-411a-8de6-ab5e0084792a)

