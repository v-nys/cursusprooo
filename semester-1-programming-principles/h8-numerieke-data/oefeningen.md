# Labo

## Inleiding

Al deze oefeningen maak je als statische methoden van een klasse `NumeriekeData`. Je kan elk van deze methoden uitvoeren via een keuzemenu, zoals bij vorige hoofdstukken.

## H8-muziek

### Leerdoelen

* Werken met de modulo operator
* Werken met arrays
* Werken met willekeurige getallen

### Functionele analyse

Schrijf een programma dat je helpt de naam van een muzieknoot te zoeken. Eerst wordt een willekeurige noot getoond om van te vertrekken, dan wordt gevraagd hoe veel noten je naar omhoog moet gaan. Ten slotte wordt de naam van deze noot getoond.

### Technische analyse

We werken alleen met de "toonladder van do groot". Met andere woorden: do, re, mi, fa, sol, la, si. Je kiest de eerste noot willekeurig door een getal te genereren dat overeen stemt met een van deze noten (do = 1, re = 2, enzovoort). Daarna geeft de gebruiker het aantal "trappen" in dat we stijgen op de ladder. Dus bij 1 gaan we van do naar re, bij 2 gaan we van do naar mi, bij 3 gaan we van do naar fa, enzovoort. Een toonladder is cyclisch, dus als de eerste noot si is en we stijgen één trap, is de uitkomst terug do, enzovoort. Maak gebruik van de modulo operator. Gebruik geen lussen.

Noem je methode `Toonladder`.

#### Tips

* plaats de namen van de noten in een array van strings
* er staan 7 noten in de grote toonladder, het is belangrijk hier gebruik van te maken

### Voorbeeldinteractie

```
Je willekeurige noot is fa. Hoe veel trappen wil je stijgen?
> 19
Je komt uit op re.
```

## H8-chronometer

### Leerdoelen

* Werken met de modulo operator

### Functionele analyse

We willen een chronometer die nauwkeuriger is dan het voorbeeldje uit de theorie.

### Technische analyse

Schrijf een chronometer die elke honderdste seconde telt. Gebruik hiervoor `Thread.Sleep(10)`, gevolgd door `Console.Clear()`, gevolgd door een `Console.WriteLine` van het huidige tijdstip. Start met `00:00:00` (minuten, seconden, honderdsten van seconden). De hoogst mogelijke waarde is `59:59:99`. Daarna kom je terug op `00:00:00`. Doe dit zonder gebruik te maken van een `if`.

(Kleine opmerking: het kan zijn dat je programma trager loopt dan een echte klok omwille van het werk dat gepaard gaat met de uitvoering. Dat is niet erg. Dit is een oefening over het rekenaspect, niet over het maken van een echte klok.)

Noem je methode `Chronometer`.

## H8-Cirkels

### Leerdoelen

* gebruik van de Math klasse
* kommagetallen parsen
* afronden

### Functionele analyse

Schrijf een programma dat de omtrek en oppervlakte van een cirkel met een gegeven straal bepaalt.

### Technische analyse

Je moet de gebruiker eerst om de straal van de cirkel vragen. De omtrek van een cirkel wordt gegeven door de formule omtrek = 2 \* π \* straal. De oppervlakte wordt gegeven door de formule straal \* straal \* π. Voor je het getal toont, rond je het (klassiek) af tot 2 cijfers na de komma.

Noem je methode voor deze oefening `Cirkels`.

### voorbeeldinteractie(s)

```
Geef de straal:
> 5
De omtrek van een cirkel met straal 5 is 31,42.
De oppervlakte is 78,54.
```

## H8-LengteOppervlakteVolume

### Leerdoelen

* Werken met machten

### Functionele analyse

Schrijf een programma om, gegeven de lengte van een zijde, de oppervlakte van een vierkant met die zijde en het volume van een kubus met die zijde te berekenen. Je mag maximum vier keer gebruik maken van de variabele met daarin de lengte van de zijde, inclusief de initialisatie.

### Technische analyse

De oppervlakte bepaal je door de zijde met zichzelf te vermenigvuldigen. Bijvoorbeeld, een zijde van 10m betekent een oppervlakte van 10m \* 10m = 100m². Het volume bepaal je door nog een keer met de zijde te vermenigvuldigen. Een zijde van 10m betekent dus een oppervlakte van 1000m³. Maak gebruik van een methode uit `Math`.

Noem je methode `LengteOppervlakteVolume`.

### Voorbeeldinteractie

```
Hoe lang is de zijde in meter?
> 10
De lengte is: 10m
De oppervlakte is: 100m²
Het volume is: 1000m³
```

## H8-RWaarde

**Dit is een uitdagende oefening!**

### Leerdoelen

* Werken met machten
* Afronding
* De for-lus

### Functionele analyse

Er breekt een nieuwe besmettelijk virus uit. We willen kunnen schatten hoe veel mensen na een gegeven aantal "generaties" zieken besmet zijn. We zijn alleen geïnteresseerd in het totaal aantal besmettingen en houden geen rekening met genezing,...

### Technische analyse

Voor besmettelijke ziekten wordt er een "R-waarde" vastgelegd. Deze drukt uit hoe veel mensen een zieke persoon gemiddeld aansteekt. Bij een R-waarde van 3, maakt een zieke persoon gemiddeld drie anderen ziek.

We zeggen dat de eerste zieke persoon de eerste "generatie" van het virus is. De mensen die door deze persoon worden aangestoken zijn de tweede generatie, die daarna zijn de derde generatie, enzovoort. Het totaal aantal besmette mensen is het aantal besmette mensen van elke generatie, samen geteld.

Jouw programma moet om de R-waarde vragen en om het aantal generaties dat je wil tellen. De R-waarde kan een kommagetal zijn, maar je kan geen halve persoon besmetten, dus soms moet je het aantal besmettingen **in één generatie** afronden. Dit kan "optimistisch" (naar beneden), "pessimistisch" (naar boven) of "gematigd" (klassiek afgerond). Let op: je berekent wel eerst het aantal besmettingen in een generatie aan de hand van de oorspronkelijke R-waarde en niet aan de hand van het afgerond aantal besmettingen in de vorige generatie.

Pak dit aan door met een lus het aantal besmettingen per generatie te tellen.

Noem je methode `RWaarde`.

### Voorbeeldinteractie

```
Wat is de R-waarde?
> 2.25
Hoe veel generaties kijken we vooruit?
> 4
Ben je optimistisch, gematigd of pessimistisch?
> pessimistisch
Het aantal besmettingen per generatie is:
Generatie 1: 1
Generatie 2: 3
Generatie 3: 6
Generatie 4: 12
Het totaal aantal besmettingen over alle generaties heen is 22.
```

## Oefening: H8-schaar-steen-papier

### Leerdoelen

* een taak herhaaldelijk uitvoeren met een lus

### Functionele analyse

Maak een applicatie waarbij de gebruiker steen-schaar-papier met de computer kan spelen. De gebruiker kiest telkens steen, schaar of papier en drukt op enter. Vervolgens kiest de computer willekeurig steen, schaar of papier.

Vervolgens krijgt de winnaar 1 punt:

* Steen wint van schaar, verliest van papier
* Papier wint van steen, verliest van schaar
* Schaar wint van papier, verliest van steen
* Indien beide hetzelfde hebben wint niemand een punt.

De eerste (pc of gebruiker) die 10 punten haalt wint.

Noem je methode `SchaarSteenPapier`.

### Technische analyse

* Genereer een willekeurig getal tussen 1 en 3 om de computer te laten kiezen.
* Teken een flowchart!

### Voorbeeldinteractie

```
Maak een keuze:
1 voor schaar
2 voor steen
3 voor papier
> 2
De computer kiest steen!
Niemand wint deze ronde!
Jij hebt 0 punten, de computer heeft 0 punten.
Maak een keuze:
1 voor schaar
2 voor steen
3 voor papier
> 1
De computer kiest papier!
Jij wint deze ronde!
Jij hebt 1 punt, de computer heeft 0 punten.
Maak een keuze:
1 voor schaar
2 voor steen
3 voor papier
> 1
De computer kiest steen!
De computer wint deze ronde!
Jij hebt 1 punt, de computer heeft 1 punt.
```

(Helemaal op het einde)

```
Jij hebt 10 punten, de computer heeft 8 punten.
Jij bent gewonnen!
```

of

```
Jij hebt 8 punten, de computer heeft 10 punten.
De computer is gewonnen!
```

## Oefening: TextCell met willekeurige getallen

**Maak voor deze oefening een aparte klasse TextCellMetRandom. Kopieer hierin de code van je klasse TextCell en pas daarna pas aan.**

### Functionele analyse

We willen onze spreadsheets gebruiken voor simulaties. Hiervoor hebben we willekeurige data nodig.

### Technische analyse

Zorg ervoor dat een cel in TextCell ook een formule van de vorm `=rand()` kan bevatten. Dit initialiseert de cel op een willekeurige waarde tussen 1 en 10.

## Oefening: TextCell met kommagetallen

**Maak voor deze oefening een aparte klasse TextCellMetKomma. Kopieer hierin de code van je klasse TextCell en pas daarna pas aan.**

### Functionele analyse

We willen complexere berekeningen doen in TextCell. Zorg ervoor dat kommagetallen ondersteund worden, maar wel steeds getoond worden met _maximum_ twee cijfers na de komma.

### Technische analyse

Pas op de juiste plaatsen alle code die een `int` veronderstelt aan naar een `double`. Zorg ervoor dat, na het uitrekenen van alle formules, alle cellen klassiek afgerond worden tot 2 cijfers na de komma.
