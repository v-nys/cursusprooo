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
