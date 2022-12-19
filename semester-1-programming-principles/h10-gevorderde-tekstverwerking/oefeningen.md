# Oefeningen

## Inleiding

Al deze oefeningen maak je als statische methoden van een klasse `GevorderdeTekstverwerking`. Je kan elk van deze methoden uitvoeren via een keuzemenu, zoals bij vorige hoofdstukken.

## H10-Som-van-getallen

### Leerdoelen

* Werken met .Split en .Join
* Itereren over array

### Functionele analyse

Je vraagt de gebruiker een aantal getallen gescheiden door ';' in te geven. je laat vervolgens de som van deze getallen zien.

### Technische analyse

Schrijf in de klasse `GevorderdeTekstverwerking`een methode `SomVanGetallen`. Deze vraagt de gebruiker een aantal getallen te geven gescheiden door een ';'. Je leest de invoer in, splitst de invoer in getallen, maakt de som en laat die zien. Let op, het aantal getallen mag de gebruiker zelf bepalen.

### Voorbeeldinteractie

![](<../../.gitbook/assets/image (73).png>)

## H10-Centraal-Aligneren-Tekst

### Leerdoelen

* Formateren van tekst
* String interpolatie
* Methode oproep

### Functionele analyse

Je vraagt de gebruiker een tekst in te geven. Vervolgens vraag je de gewenst breedte van de tekst. Je laat de tekst dan centraal gealigneerd aan de gebruiker zien.

### Technische analyse

Schrijf in de klasse `GevorderdeTekstverwerking`een  methode `CentraalAlignerenTekst`. Deze vraagt de gebruiker een tekst in te geven en een gewenste lengte (minimaal de lengte van de tekst - controle!). Maak een tweede methode `CentraalAligneren` Vervolgens wordt de tekst centraal gealigneerd getoond aan de gebruiker. De gebruiker kan het padding karakter ook kiezen.

### Voorbeeldinteractie

![](<../../.gitbook/assets/image (70).png>)

## H10-KerstinkopenNetjes

### Leerdoelen

* stringformattering
* string methodes
* gebruik van karakters

### Functionele analyse

De eerdere oefening [Kerstinkopen](oefeningen.md#h10-kerstinkopenlistnetjes) kan wat mooier gepresenteerd worden. Ze zou ook ingezet moeten kunnen worden in regio's waar de euro niet gebruikt wordt.

### Technische analyse

Maak een kopie van Kerstinkopen in deze klasse.

Pas door middel van stringformattering en string methodes de code aan, zodat:

* Een scheidingslijn getekend wordt onder "Info over je aankopen", die net breed genoeg is. Als we later deze hoofding veranderen (bijvoorbeeld naar "Informatie over je aankopen") moet de lijn mee groeien of krimpen.
* Alle bedragen netjes onder elkaar staan in één kolom. Hiervoor mag je veronderstellen dat de berichten op de linkerkant maximum 25 karakters in beslag zullen nemen.
* Het symbool voor de munteenheid van de gebruiker vanzelf gebruikt wordt. Dit kan dus € zijn maar ook $ of £ of iets anders.

### Voorbeeldinteractie

{% hint style="warning" %}
Deze voorbeeldinteractie gebruikt de List versie van Kerstinkopen. Maak de oefening met de array versie.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screenshot from 2022-12-18 13-39-53.png" alt=""><figcaption></figcaption></figure>

## H10-TextCellPersistent

### Leerdoelen

* Gebruik van input en output van tekstbestanden

### Functionele analyse

We willen onze gemaakte TextCells ook kunnen opslaan en weer openen.&#x20;

### Technische analyse

Maak in je oefeningen map een nieuwe map aan TextCell. In deze map zullen de TextCell bestanden bewaard worden. Je kan in je applicatie ook een relatief pad opgeven (dus niet c:\\...). Dit relatief pad gaat vertrekkende van de map waar je nu op werkt een map zoeken (dit is wat kort door de bocht, de werkelijkheid is een stuk ingewikkelder maar voor nu volstaat dit). Het relatieve pad dat wij gebruiken is "./TextCell/filenaam.aptx).

Kopieer het bestand TextCell.cs naar TextCellPersistent.cs. Maak gerbuik van de in de theorie aangehaalde methodes File.ReadAllLines en File.WriteAllLines. Test bij opslaan van het bestand of het bestand reeds bestaat en bij laden van het bestand of het bestand sowieso bestaat.

### Voorbeeldinteractie

![](<../../.gitbook/assets/image (71) (2).png>)

![](<../../.gitbook/assets/image (69).png>)



## H10-Pixels-Persistent

### Functionele analyse

We wensen de kunstwerken die we in Pixels tekenen op te slaan en in te laden.

### Technische analyse

Kopieer de code voor Pixels naar deze klasse.

Zorg ervoor dat je twee extra opties hebt in je tekenprogramma. Om een tekening op te slaan, moet je elke `ConsoleColor` casten naar een `int`. Dan kan je één rij pixels opslaan als één rij getallen, gescheiden door puntkomma. Om een tekening in te laden, doe je het omgekeerde.

### Voorbeeldinteractie

<figure><img src="../../.gitbook/assets/Screenshot from 2022-12-18 13-54-57.png" alt=""><figcaption></figcaption></figure>
