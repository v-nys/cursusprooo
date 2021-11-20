# De Math klasse

### Berekeningen

Een groot deel van je leven als ontwikkelaar zal bestaan uit het bewerken van variabelen in code. Meestal zullen die bewerkingen voorafgaan van berekeningen. De `Math` klasse zal ons hier bij kunnen helpen.

#### De Math klasse

De Math klasse bevat aardig wat handige methoden. Deze klasse bevat methoden voor een groot aantal typische wiskundige methoden (sinus, cosinus, vierkantswortel, macht, afronden, etc.) en kan je dus helpen om leesbaardere expressies te schrijven.

Stel dat je de derde macht van een variabel `getal` wenst te berekenen. Zonder de Math-klasse zou dat er zo uitzien:

```csharp
double result = getal*getal*getal;
```

Met de klasse kunnen we schrijven:

```csharp
double result = Math.Pow(getal, 3);
```

Het voordeel is dat je dit makkelijk kan aanpassen naar een hogere macht.

**De Math klasse ontdekken**

Als je in Visual Studio Code `Math` schrijft, gevolgd door een punt `.` krijg je alles te zien wat de Math-klasse kan doen.

**Methoden gebruiken**

De meeste methoden zijn zeer makkelijk in gebruik en werken op dezelfde manier. Meestal moet je 1 of meerdere waarden tussen de haken meegeven en het resultaat moet je altijd in een nieuwe variabele opslaan. Enkele voorbeelden:

```csharp
double sineHoekA = Math.Sin(345); //niet in graden maar in radialen
double DerdeMachtVan20 = Math.Pow(20, 3);
double complex = 3+ DerdeMachtVan20 * Math.Round(sineHoekA);
```

Twijfel je over de werking van een methode, gebruik dan de help als volgt:

1. Schrijf de Methode zonder argumenten. Bijvoorbeeld `Math.Pow()` (je mag de rode error negeren).&#x20;
2. Je krijgt nu de help-files te zien van deze methode op MDSDN.
3. Klik desnoods op de pijltjes voor de verschillende versies van deze methode.

**PI (π)**

Ook het getal Pi (`3.141...`) is beschikbaar in de Math klasse. Dit is geen methode, maar een gewone waarde. Het woordje `const` betekent dat je deze waarde niet kan aanpassen.

Je kan deze als volgt gebruiken in berekeningen:

```csharp
double straal = 5.5;
double omtrek = Math.PI * 2 * straal;
```

#### Klassiek afronden

n

#### Afronden naar boven of beneden

Een vaak voorkomende oefening is deze waarbij je een bepaalde variabele continue moet aanpassen. Stel bijvoorbeeld dat je aan de gebruiker de temperatuur van iedere dag vraagt om zo vervolgens het gemiddelde te berekenen. Dit kan je doen door middel van een lopende som: je gaat telkens het ingevoerde getal toevoegen aan wat je reeds hebt bewaard. Meestal dus met behulp van de `+=` operator.

```csharp
double totaal = 0.0;
Console.WriteLine("Geef temperatuur dag 1");
double inp = Convert.ToDouble(Console.ReadLine());
totaal += inp;
Console.WriteLine("Geef temperatuur dag 2");
inp = Convert.ToDouble(Console.ReadLine());
totaal += inp;
//enz
Console.WriteLine($"Gemiddelde temperatuur deze week was: {totaal/7}");
```
