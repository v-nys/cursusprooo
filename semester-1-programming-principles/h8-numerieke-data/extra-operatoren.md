# Extra operatoren

#### Modulo operator `%`

De modulo operator, die we in C# aanduiden met `%, `verdient wat meer uitleg. Deze operator zal als resultaat de rest teruggeven wanneer we het linkse natuurlijke getal door het rechtse natuurlijke getal delen:

```
7 % 2 => zal 1 geven, daar 7 gedeeld door 2,  3 met rest 1 geeft 
10 % 5 => zal 0 geven, daar 10 gedeeld door 5, 2 met rest 0 geeft
```

De modulo-operator zal je geregeld gebruiken om bijvoorbeeld te weten of een getal een veelvoud van iets is. Als de rest dan 0 is weet je dat het getal een veelvoud is van het getal waar je het door deelde.

Bijvoorbeeld om te testen of getal even is gebruiken we `%` 2:

```csharp
int getal = 1234234;
int rest = getal % 2;
Console.WriteLine($"Indien het getal als rest 0 geeft weten we dat het even is. De rest is: {rest}");
```

Je zou de modulo dus ook (trager) te weten kunnen komen als volgt:

```csharp
public static int RestBijDeling(uint getal1, uint getal2) {
  // werkt niet als getal2 0 is, maar dan is deling toch niet geldig
  while(getal1 >= getal2) {
    getal1 = getal1 - getal2;
  }
  return getal1;
}
```

Naast het gebruik om te testen of een getal een veelvoud is van een ander getal, is de modulo ook vaak nuttig om een herhalende reeks te implementeren. Dit is zoals kloklezen. Als we een 24-urenvoorstelling gebruiken, is het nooit 24 uur. Het is 0 uur, dan 1 uur, dan 2 uur,... dan 23 uur en dan terug 0 uur. Kort samengevat, als het nu `u` uur is, is het over één uur `(u + 1) % 24` uur. Idem voor de minuten, maar daar herstarten we vanaf 60.

Een vereenvoudigde chronometer in code kan er zo uitzien:

```csharp
int aantalSeconden = 0;
while (true) {
  Console.WriteLine(aantalSeconden);
  Thread.Sleep(1000); // dit pauzeert het programma 1 seconde, komt uit System.Threading
  aantalSeconden = aantalSeconden + 1;
}
```

Een ander voorbeeld is het laatste cijfer van een getal. Als je telt vanaf 0 tot 9, ga je steeds over naar het volgende cijfer. Maar daarna ga je terug naar 0 voor het laatste cijfer. Je kent andere manieren om dit te doen, maar volgend programma zal het getoonde getal steeds resetten:

```csharp
int getal = 0;
while (true) {  
  Console.WriteLine(getal % 10);
  Thread.Sleep (1000);
  getal = getal + 1;
  // we negeren de uiteindelijke "overflow", waarbij het getal te groot wordt voor het datatype
}
```

De modulo is dus erg handig als we aan het "einde" van een bepaalde reeks terug willen herstarten vanaf het "begin". We kunnen ook eenvoudig een array blijven doorlopen (zonder omslachtig werk met een `if`) als volgt:

```csharp
string[] tekstOmTeScanderen = {"wij","hebben","honger"};
int index = 0;
while (true) {
  Console.WriteLine($"{tekstOmTeScanderen[index].ToUpper()}!");
  index = (index + 1) % tekstOmTeScanderen.Length;
  Thread.Sleep(1000);
}
```

{% hint style="info" %}
De modulo werkt ook met negatieve getallen, maar dit komt niet vaak voor en is vrij complex. We veronderstellen dat je hem enkel gebruikt met natuurlijke getallen.
{% endhint %}

#### Verkorte operator notaties

Heel vaak wil je de inhoud van een variabele bewerken en dan terug bewaren in de variabele zelf. Bijvoorbeeld een variabele vermenigvuldigen met 10 en het resultaat ervan terug in de variabele plaatsen. Hiervoor zijn enkele verkorte notaties in C#. Stel dat we een variabele `int getal` hebben:

| **Verkorte notatie** | **Lange notatie** | **Beschrijving**                         |
| -------------------- | ----------------- | ---------------------------------------- |
| `getal++;`           | `getal= getal+1;` | variabele met 1 verhogen                 |
| `getal--;`           | `getal= getal-1;` | variabele met 1 verlagen                 |
| `getal+=3;`          | `getal= getal+3;` | variabele verhogen met een getal         |
| `getal-=6;`          | `getal= getal-6;` | variabele verminderen met een getal      |
| `getal*=7;`          | `getal= getal*7;` | variabele vermenigvuldigen met een getal |
| `getal/=2;`          | `getal= getal/2;` | variabele delen door een getal           |

{% hint style="danger" %}
Je zou nooit iets mogen schrijven als `i = i++`. Dan ben je duidelijk twee dingen door elkaar aan het halen. Schrijf enkel neer wat je begrijpt.
{% endhint %}
