# value en reference met eigen objecten

{% hint style="info" %}
Het verschil tussen value en reference is eerder al eens behandeld op [deze pagina](../../semester-1-programming-principles/h7-arrays/value-types-en-reference-types.md) \(waar je ook een uitgebreide kennisclip terugvindt\). Die leerstof blijft te kennen, maar onderstaande uitleg maakt het verschil duidelijker.
{% endhint %}

{% hint style="success" %}
[Kennisclip](https://youtu.be/1uNugk3wMho)
{% endhint %}

{% hint style="success" %}
[Oudere kennisclip](https://youtu.be/N6f6S9aQukU) over stack en heap. Bekijk deze als het voorgaande materiaal niet helemaal duidelijk is. **De voorbeeldklasse Student heeft niets met SchoolAdmin te maken.**
{% endhint %}

## Herhaling

### Klassen zijn reference types

Onze eigen klassen zijn **reference types**. Dat wil zeggen dat, in de ruimte die voorzien wordt wanneer we een variabele van een bepaalde klasse declareren, er een **verwijzing** wordt bijgehouden. Zo'n verwijzing is een adres voor de bytes die ons object vormen. Dit is in tegenstelling tot **value** types. Daarvoor wordt de waarde zelf bijgehouden op de plaats die voorzien is voor de variabele.

### Stack vs. heap

Voor de uitvoering van een programma wordt gebruik gemaakt van twee types geheugen: een stack en een heap. De **stack** is klein, gestructureerd en snel. De **heap** is groot, ongestructureerd en traag. Beide geheugens zijn nodig: **op de stack wordt ruimte voorzien voor de lokale variabelen van alle methoden die momenteel in uitvoering zijn** \(met Main onderaan\). Op de heap staan gegevens waarnaar ergens anders verwezen wordt. Dat kan van op de stack zijn \(als je een lokale variabele hebt van een reference type\) of van ergens anders op de heap \(bijvoorbeeld als je in een object een instantievariabele hebt van een reference type\).

{% hint style="info" %}
Deze "stack" is dezelfde stack waarover je informatie kan terugvinden wanneer je de debugger uitvoert in Visual Studio!
{% endhint %}

## Demonstratie: wat als klassen value types waren?

Het feit dat klassen reference types zijn, heeft praktische gevolgen. We zullen dit demonstreren door dezelfde functionaliteit te implementeren met een `class` en een `struct`. Je kan `struct` zien als bijna hetzelfde als `class`, in die zin dat je er ook objecten van kan maken, maar `struct`-objecten zijn value types.

{% hint style="warning" %}
We gaan je nergens in deze cursus vragen zelf een `struct` te maken. We gebruiken ze alleen omdat ze het verschil tussen value en reference duidelijker kunnen maken.
{% endhint %}

Vergelijk volgende twee vereenvoudigde varianten op `DateTime`:

```csharp
struct MiniDatumValue
{
    public int Dag;
    public int Maand;
    public int Jaar;
}
    
class MiniDatumReference
{
    public int Dag;
    public int Maand;
    public int Jaar;
}
```

Beide stellen een datum voor en hebben dezelfde attributen. We voorzien ook een methode `WijzigDatums`, met twee parameters: één voor ons value type en één voor ons reference type. Ten slotte voorzien we een demonstratie in `Main`:

```csharp
static void Main(string[] args) {
    MiniDatumValue d1 = new MiniDatumValue();
    d1.Dag = 6;
    d1.Maand = 3;
    d1.Jaar = 2016;
    MiniDatumValue d2 = new MiniDatumReference();
    d2.Dag = 6;
    d2.Maand = 3;
    d2.Jaar = 2016;
    Program.WijzigDatums(d1,d2);
    Console.WriteLine($"value na uitvoering: {d1.Dag}/{d1.Maand}/{d1.Jaar}");
    Console.WriteLine($"reference na uitvoering: {d2.Dag}/{d2.Maand}/{d2.Jaar}");
}

static void WijzigDatums(MiniDatumValue val, MiniDatumReference reference)
{
    val.Maand = 2;
    reference.Maand = 2;
}
```

Als je dit programma uitvoert, merk je dat de waarde van `d1` niet gewijzigd is door de methode en `d2` wel. Dat komt omdat val een kopie bevatte van de waarde van `d1`, terwijl reference naar dezelfde data verwees als `d2`.

