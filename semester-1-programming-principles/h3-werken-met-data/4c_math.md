# Math-library en berekeningen

## Berekeningen

Een groot deel van je leven als ontwikkelaar zal bestaan uit het bewerken van variabelen in code. Meestal zullen die bewerkingen voorafgaan van berekeningen. De `Math` bibliotheek zal ons hier bij kunnen helpen.

### De Math bibliotheek

De Math bibliotheek bevat aardig wat handige methoden. Deze bibliotheek bevat methoden voor een groot aantal typische wiskundige methoden \(sinus, cosinus, vierkantswortel, macht, afronden, etc.\) en kan je dus helpen om leesbaardere expressies te schrijven.

Stel dat je de derde macht van een variabel `getal` wenst te berekenen. ZONDER de Math-bibliotheek zou dat er zou uitzien:

```csharp
double result= getal*getal*getal;  //SLECHTE MANIER
```

MET de bibliotheek kunnen we schrijven:

```csharp
double result= Math.Pow(getal, 3);
```

#### De Math bibliotheek ontdekken

Als je in Visual Studio `Math` schrijft, gevolgd door een punt `.` krijg je alles te zien wat de Math-bibliotheek kan doen:

![](../../.gitbook/assets/methoden3%20%281%29.png)

Een doosje voor een naam wil zeggen dat het om een **Methode** gaat \(zoals `Console.ReadLine()`\). Een vierkantje met twee streepjes in zijn constanten \(zoals `Pi`\(`π`\) en `e`\).

#### Methoden gebruiken

De meeste methoden zijn zeer makkelijk in gebruik en werken op dezelfde manier. Meestal moet je 1 of meerdere "argumenten" tussen de haken meegeven en het resultaat moet je altijd in een nieuwe variabele opvangen. Enkele voorbeelden:

```csharp
double sineHoekA= Math.Sin(345); //IN RADIALEN!
double DerdeMachtVan20= Math.Pow(20, 3);
double complex= 3+ DerdeMachtVan20 * Math.Round(sineHoekA);
```

Twijfel je over de werking van een methode, gebruik dan de help als volgt:

1. Schrijf de Methode zonder argumenten. Bijvoorbeeld `Math.Pow()` \(je mag de rode error negeren\). ![](../../.gitbook/assets/math.png)
2. Plaats je cursor op `Pow`.
3. Druk op `F1` op je toetsenbord.
4. Je krijgt nu de help-files te zien van deze methode op MDSDN.

#### PI \(π\)

Ook het getal Pi \(`3.141...`\) is beschikbaar in de Math-library. Het witte icoontje voor PI bij Intellisense toont aan dat het hier om een ‘field’ gaat; een eenvoudige variabele met een specifieke waarde. In dit geval gaat het zelfs om een const field, met de waarde van Pi van het type double.

```csharp
public const double PI;
```

Je kan deze als volgt gebruiken in berekeningen:

```csharp
double straal= 5.5;
double omtrek= Math.PI * 2 * straal;
```

### Lopende som

Een vaak voorkomende oefening is deze waarbij je een bepaalde variabele continue moet bijpassen. Stel bijvoorbeeld dat je aan de gebruiker de temperatuur van iedere dag vraagt om zo vervolgens het gemiddelde te berekenen. Dit kan je doen door middel van een lopende som: je gaat telkens het ingevoerde getal toevoegen aan wat je reeds hebt bewaard. Meestal dus met behulp van de += operator.

```csharp
double totaal= 0.0;
Console.WriteLine("Geef temperatuur dag 1");
double inp= Convert.ToDouble(Console.ReadLine());
totaal+=inp;
Console.WriteLine("Geef temperatuur dag 2");
inp= Convert.ToDouble(Console.ReadLine());
totaal+=inp;

//enz
Console.WriteLine($"Gemiddelde temperatuur deze week was: {totaal/7}");
```

> Wanneer we met loops leren werken zullen lopende sommen zéér nuttig worden.

## Kennisclip

![](../../.gitbook/assets/infoclip.png)

* [De Math-bibliotheek](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=4d790ab9-e3b9-4e4b-bf59-a976007197fa)

