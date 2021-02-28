# Stack en Heap

## Geheugenmanagement in C-Sharp

Tot nog toe lagen we er niet van wakker wat er achter de schermen van een C\# programma gebeurde. We duiken nu dieper in wat er juist gebeurt wanneer we variabelen aanmaken.

### Twee soorten geheugen

Wanneer een C\# applicatie wordt uitgevoerd krijgt het twee soorten geheugen toegewezen dat het 'naar hartelust' kan gebruiken:

1. Het kleine, maar snelle **stack** geheugen
2. Het grote, maar tragere **heap** geheugen

Afhankelijk van het soort variabele wordt ofwel de stack, ofwel de heap gebruikt. **Het is uitermate belangrijk dat je weet in welk geheugen de variabele zal bewaard worden!**

Er zijn namelijk twee soorten variabelen:

1. Value types
2. Reference types

Als je volgende tabel begrijpt dan beheers je geheugenmanagement in C\#:

|  | Value types | Reference types |
| :--- | :--- | :--- |
| Inhoud van de variabele | De eigenlijke data | Een referentie naar de eigenlijke data |
| Locatie | \(Data\) **Stack** | **Heap** \(globaal\)geheugen |
| Beginwaarde | `0`,`0.0`, `""`,`false`, etc. | `null` |
| Effect van = operator | Kopieert de actuele waarde | Kopieert het adres naar de actuele waarde |

![](../../.gitbook/assets/gc1.png)

### Waarom twee geheugens?

Waarom plaatsen we niet alles in de stack? De reden hiervoor is dat bij het compileren van je applicatie er reeds zal berekend worden hoeveel geheugen de stack zal nodig hebben. Wanneer je programma dus later wordt uitgevoerd weet het OS perfect hoeveel geheugen het minstens moet reserveren. Er is echter een probleem: we kunnen niet alles perfect berekenen/voorspellen. Een variabele van het type `int` is perfect geweten hoe groot die zal zijn \(32 bit\).Maar wat met een string? Of met een array waarvan we pas tijdens de uitvoer de lengte aan de gebruiker misschien vragen? Het zou nutteloos \(en zonde\) zijn om reeds bij aanvang een bepaalde hoeveelheid voor een array te reserveren als we niet weten hoe groot die zal worden. Beeld je maar eens in dat we 2k byte reserveren om dan te ontdekken dat we maar 5byte ervan nodig hebben. RAM is goedkoop, maar toch... De heap laat ons dus toe om geheugen op een wat minder gestructureerde manier in te palmen. Tijdens de uitvoer van het programma zal de heap als het ware dienst doen als een grote zandbak waar eender welke plek kan ingepalmd worden om zaken te bewaren. De stack daarentegen is het kleine bankje naast de zandbak: handig, snel, en perfect geweten hoe groot.

#### Value types

**Value** types worden in de stack bewaard. De effectieve waarde van de variabele wordt in de stack bewaard. Dit zijn alle gekende, 'eenvoudige' datatypes die we totnogtoe gezien hebben, inclusief enums en structs \(zie later\):

* `sbyte`, `byte`
* `short`, `ushort`
* `int`, `uint`
* `long`, `ulong`
* `char`
* `float`, `double`, `decimal`
* `bool`
* structs \(zien we niet in deze cursus\)
* enums

**= operator bij value types**

Wanneer we een value-type willen kopieren dan kopieren de echte waarde:

```csharp
int getal=3;
int anderGetal= getal;
```

Vanaf nu zal `anderGetal` de waarde `3` hebben. Als we nu een van beide variabelen aanpassen dan zal dit **geen** effect hebben op de andere variabelen.

We zien het zelfde effect wanneer we een methode maken die een parameter van het value type aanvaardt- we geven een kopie van de variabele mee:

```csharp
void DoeIets(int a)
{
    a++;
    Console.WriteLine($"In methode {a}");
}

//Elders:
int getal= 5;
DoeIets(getal);
Console.WriteLine($"Na methode {getal}");
```

De parameter `a` zal de waarde 5 gekopieerd krijgen. Maar wanneer we nu zaken aanpassen in `a` zal dit geen effect hebben op de waarde van `getal`. De output van bovenstaand programma zal zijn:

```text
In methode 6
Na methode 5
```

#### Reference types

**Reference** types worden in de heap bewaard. De effectieve waarde wordt in de heap bewaard, en in de stack zal enkel een **referentie** of **pointer** naar de data in de heap bewaard worden. Een referentie \(of pointer\) is niet meer dan het geheugenadres naar waar verwezen wordt \(bv `0xA3B3163`\) Concreet zijn dit alle zaken die vaak redelijk groot zullen zijn:

* objecten, interfaces en delegates
* arrays

**= operator bij reference types**

Wanneer we de = operator gebruiken bij een reference type dan kopieren we de referentie naar de waarde, niet de waarde zelf.

**Bij objecten** We zien dit gedrag bij alle reference types, zoals objecten:

```csharp
Student stud= new Student();
```

Wat gebeurt er hier?

1. `new Student()`  : `new` roept de constructor van `Student` aan. Deze zal een constructor in de **heap** aanmaken en vervolgens de geheugenlocatie teruggeven.
2. Een variabele `stud` wordt in de **stack** aangemaakt.
3. De geheugenlocatie uit de eerste stap wordt vervolgens in `stud` opgeslagen in de stack.

**Bij arrays**

Maar ook bij arrays:

```csharp
int[] nummers= {4,5,10};
int[] andereNummers= nummers;
```

In dit voorbeeld zal `andereNummers` dus nu ook verwijzen naar de array in de heap waar de actuele waarden staan.

Als we dus volgende code uitvoeren dan ontdekken we dat beide variabele naar dezelfde array verwijzen:

```csharp
andereNummers[0]=999;
Console.WriteLine(andereNummers[0]);
Console.WriteLine(nummers[0]);
```

We zullen dus als output krijgen:

```text
999
999
```

Hetzelfde gedrag zien we bij objecten:

```csharp
Student a= new Student("Abba");
Student b= new Student("Queen");
a=b;
Console.WriteLine(a.Naam);
```

We zullen in dit geval dus `Queen` op het scherm zien omdat zowel `b` als `a` naar het zelfde object in de heap verwijzen. Het originele "abba"-object zijn we kwijt en zal verdwijnen \(zie Garbage collector verderop\).

**Methoden en reference parameters**

Ook bij methoden geven we de dus de referentie naar de waarde mee. In de methode kunnen we dus zaken aanpassen van de parameter en dan passen we eigenlijk de originele variabele aan:

```csharp
void DoeIets(int[] a)
{
   a[0]++;
   Console.WriteLine($"In methode {a[0]}");
}

//Elders:
int[] getallen= {5,3,2};
DoeIets(getallen);
Console.WriteLine($"Na methode {getallen[0]}");
```

We krijgen als uitvoer:

```text
In methode 6
Na methode 6
```

**Opgelet:** Wanneer we een methode hebben die een value type aanvaardt en we geven één element van de array met dan geven dus een kopie van de actuele waarde mee!

```csharp
void DoeIets(int a)
{
    a++;
    Console.WriteLine($"In methode {a}");
}

//Elders:
int[] getallen= {5,3,2};
DoeIets(getallen[0]); //<= VALUE TYPE!
Console.WriteLine($"Na methode {getallen[0]}");
```

De output bewijst dit:

```text
In methode 6
Na methode 5
```

### De Garbage Collector \(GC\)

Een essentieel onderdeel van .NET is de zogenaamde GC, de Garbage Collector. Dit is een geautomatiseerd onderdeel van ieder C\# programma dat ervoor zorgt dat we geen geheugen voor niets gereserveerd houden. De GC zal geregeld het geheugen doorlopen en kijken of er in de heap data staat waar geen references naar verwijzen. Indien er geen references naar wijzen zal dit stuk data verwijderd worden.

In dit voorbeeld zien we dit in actie:

```text
int[] array1= {1,2,3};
int[] array2= {3,4,5};
array2=array1;
```

Vanaf de laatste lijn zal er geen referentie meer naar `{3,4,5}` in de heap zijn, daar we deze hebben overschreven met een referentie naar `{1,2,3}`.De GC zal dus deze data verwijderen.

Wil je dat niet dan zal je dus minstens 1 variabele moeten hebben dat naar de data verwijst. Volgende voorbeeld toont dit:

```text
int[] array1= {1,2,3};
int[] array2= {3,4,5};
int[] bewaarArray= array2;
array2=array;
```

De variabele `bewaarArray` houdt dus een referentie naar `{3,4,5}` bij en we kunnen dus later via deze variabele alsnog aan de originele data.

## Meer weten?

Meer info, lees zeker volgende artikels:

* [Reference en value types](https://www.c-sharpcorner.com/uploadfile/prvn_131971/types-in-C-Sharp/)
* [Stack vs heap](https://www.c-sharpcorner.com/article/C-Sharp-heaping-vs-stacking-in-net-part-i/)

