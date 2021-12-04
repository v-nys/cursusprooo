# Voorstelling van tekst

## Wat is Unicode?

Alle gegevens in het geheugen van je computer worden voorgesteld als een opeenvolging van binaire cijfers. Dat is gewoon veruit de handigste manier om computers te bouwen. Helaas is het niet de handigste voorstelling. Als je een bestand opent in een text editor, zie je bijvoorbeeld niet `0010001110001101010101110` (enzovoort), maar wel `hallo wereld`, مرحبا بالعالم of 你好，世界. Dat komt omdat er afspraken gemaakt zijn rond welke reeksen bits welke karakters voorstellen. Die afspraken zijn doorheen de tijd ontstaan. Een van de simpelste is 7-bit ASCII, waarbij één byte gebruikt werd om een karakter voor te stellen. 7 bits bepaalden welk karakter werd voorgesteld (er waren er maximum 128), de achtste diende om te controleren dat er geen datacorruptie was opgetreden.

Naarmate computers in meer regio's gebruikt werden, werd duidelijk dat 128 karakters niet volstonden om elke taal van de wereld digitaal voor te stellen. Laat staan de emoji die we vandaag hebben. Als oplossing voor dat probleem is de **Unicode standaard** vastgelegd. Deze koppelt, eenvoudig gesteld, aan een hele grote reeks getallen een overeenkomstig symbool.

Het is duidelijker als je dit in de praktijk ziet. Volgende voorbeelden komen van [unicode-table.com](https://unicode-table.com):

![De letter f is symbool nummer 102. Dit is omdat het "Unicode number" hexadecimaal wordt uitgedrukt. De HTML-code is decimaal.](<../../.gitbook/assets/Screenshot from 2021-12-04 13-07-45.png>) ![Het symbool voor recyclage is symbool nummer 9851. Zelfde uitleg als voor de letter f.](<../../.gitbook/assets/Screenshot from 2021-12-04 13-09-17.png>)

### Wat is een karakterset?

De Unicode standaard is niet genoeg om tekst voor te stellen in de praktijk. Je moet immers ook weten hoe je bits moet samen nemen. Anders gezegd: maak je groepjes van één byte, van twee bytes, van drie bytes,... om zo de getallen te vinden die symbolen voorstellen? Er zijn meerdere antwoorden op die vraag en in de praktijk gaat het eerder om combinaties. Zo kan je zeggen dat je mééstal 1 byte gebruikt, maar soms meer als je aan één byte niet genoeg hebt (omdat je een symboolnummer groter dan 255 hebt). Hoe dat precies werkt, laten we hier achterwege. Maar we onthouden wel dat we hier per bestand een afspraak rond moeten maken. Deze afspraak noemen we de **karakterset** of **encodering** van ons bestand. C#-programma's veronderstellen intern bijvoorbeeld (net als JavaScript programma's) dat je **gewoonlijk** twee bytes gebruikt om een karakter voor te stellen, maar ze hebben een achterpoortje waardoor je meer dan twee bytes kan gebruiken. Deze encodering heet **UTF-16**. Dit betekent niet dat je in C# niet met bestanden in een andere karakterset kan werken of zelfs dat je .cs-files UTF-16 moeten gebruiken. Maar het heeft wel enkele gevolgen, die we hieronder zullen zien.

## Hoe stellen we een individueel karakter voor?

Om één karakter voor te stellen, gebruiken we het type `char`. Je kan hier een waarde aan toekennen door ze tussen enkele quotes te plaatsen, als volgt:

```csharp
char letterF = 'f';
char recycle = '♻';
```

Tegelijkertijd kan je er mee rekenen. Dan ga je eigenlijk met het Unicode nummer van dat symbool werken. Om terug toe te kennen aan een karakter, moet je wel weer casten. Bijvoorbeeld:

```csharp
char letterG = (char) ('f' + 1);
```

Dit werkt, want in de Unicode standaard komt de g na de f.

Je kan karakters ook noteren via hun Unicode nummer, door een "Unicode escape" te gebruiken. Hierbij noteer je eerst een backslash, dan een `u` en dan het Unicode nummer in **hexadecimale** notatie. Als je dit print op je scherm, zie je net hetzelfde als met de notatie hierboven. Het voordeel is dat je het symbool niet op je toetsenbord moet hebben staan.

```csharp
char recycle = '\u267B';
```

Er zijn ook "gewone" escapes voor tekens die je vaak nodig hebt. Deze zijn onder andere `'\n'` (newline) en `'\t'` (tab). `'\u000A'` en `'\u0009'` werken ook, maar zijn wat lastiger te onthouden. Let wel op: als je een backslash wil gebruiken zonder dat deze een escape sequentie activeert, moet je de backslash zelf escapen. Dus `\\` stelt eigenlijk het karakter `\` voor.

Wat hier verder opvalt: we hebben maximum 4 hexadecimale cijfers, dus in theorie 65536 karakters. Het is waar dat we maar 65536 waarden van het type `char` hebben. Maar binnenin een `string` kan je ook karakters noteren en in deze situatie zijn er combinaties van karakters die als één geheel gezien worden. We noemen deze **surrogate pairs** en ze geven weer als één karakter. Bijvoorbeeld:

```csharp
Console.WriteLine("Dit is één symbool: \ud835\udcb3");
```

Je hoeft de werking van surrogate pairs voor deze cursus niet in detail te kennen, maar als je ooit een applicatie schrijft die emoji,... bevat, vind je [hier](https://docs.microsoft.com/en-us/dotnet/standard/base-types/character-encoding-introduction) de details.

In strings kan je ook emoji noteren, zelfs als die gebruik maken van surrogate pairs. Bijvoorbeeld:

```csharp
Console.WriteLine("👩🏽‍🚒");
```

Voor dit specifieke symbool zou je anders 7 Unicode escapes nodig hebben...

{% hint style="warning" %}
Als je emoji probeert te tonen, is het niet voldoende dat je C# programma juist geschreven is. Je terminal moet dit ook ondersteunen. PowerShell doet dit momenteel standaard niet. De terminal van git bash ook niet. De nieuwe Windows terminal (die je kan downloaden uit de Windows store) doet dit **wel**, dus als je programma in orde is en je voert `dotnet run` uit in de Windows terminal, zou je ook emoji moeten zien.
{% endhint %}

## Verbatim strings

Door een `@` (verbatim character) voor een string te plaatsen zeggen we concreet: "de hele string die nu volgt moet je beschouwen zoals hij er staat. Je mag alle escape karakters negeren en er mogen line breaks voorkomen in deze string."

Dit wordt vaak gebruikt om een filepath iets leesbaarder te maken.

* Zonder verbatim: `string path= "c:\\Temp\\myfile.txt";`
* Met verbatim: `string path= @"c:\Temp\myfile.txt";`

{% hint style="warning" %}
Bovenstaande strings zijn **identiek** voor C#! De @ geeft geen enkele extra functionaliteit, maar zorgt gewoon dat we dezelfde tekst (meerbepaald: backslashes en line breaks) wat makkelijker kunnen intypen.
{% endhint %}

Volgende stukken code doen dus hetzelfde:

```
string tekst = @"Back

\

Slash";
Console.WriteLine(tekst);
```

```
string tekst = "Back\n\n\\\n\nSlash";
Console.WriteLine(tekst);
```

Intern is er géén verschil. Voor de `WriteLine` wordt uitgevoerd, worden beide waarden in dezelfde voorstelling gegoten. Maar in dit geval is de eerste versie wel veel makkelijker te lezen voor de programmeur.
