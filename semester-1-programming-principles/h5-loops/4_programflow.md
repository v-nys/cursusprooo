# Programma flow analyse

## Programma flow analyse

Door een flowchart op te stellen is het vaak veel eenvoudiger om een programma ofwel te analyseren \(van code naar idee\) ofwel om een programma te schrijven \(van idee naar code\).

Een flowchart \(letterlijk: _stroomkaart_\) of stroomdiagram is een schematische beschrijving van een proces. Met een flowchart kan je vaak ingewikkelde stukken code visualiseren waardoor het geheel plots niet meer zo ingewikkeld is.

Een flowchart bestaat uit een aantal elementen:

* Pijl: een pijl geeft aan naar welk volgende blok wordt gegaan. Indien boven de pijl een bepaalde waarde staat wil dit zeggen dat deze pijl enkel wordt gevolgd als de uitkomst van het vorige blok de getoonde waarde geeft.
* Start en einde: aangegeven met een cirkel met daarin de woorden "Start" of "Einde"
* Verwerk-stap: een statement zoals "Voeg 1 toe aan X" wordt in een rechthoek geplaatst. Alle code die geen invoer nodig heeft zet je in een rechthoek.
* Input/output: Een parallellogram gebruik je om in-of uitvoer van de gebruiker of scherm te tonen. Bv "Verkrijg X van gebruiker" of "Toon volgende zin op het scherm".
* Condities en beslissingen: Een ruit wordt gebruikt wanneer een beslissing moet genomen worden. De condities van if en while-loops zet je dus in een ruit. De pijlen die eruit volgen geven aan welke pijl moet gevolgd worden gegeven een bepaalde waarde van de conditie.

## Flow-elementen

We tonen nu kort de verschillende program flow elementen en hoe ze in een flowchart voorkomen.

### If-element

![](../../.gitbook/assets/if%20%281%29.png)

### If-else element

![](../../.gitbook/assets/ifelse.png)

### While-element

![](../../.gitbook/assets/while.png)

### Do while-element

![](../../.gitbook/assets/dowhile.png) Merk op dat bij if en if-else de flow niet naar een eerder punt in de code gaat. Dit is dus de manier om een while/do while te herkennen: er wordt naar een eerder punt in de code gegaan, een punt waar we reeds geweest waren

### For-element

![](../../.gitbook/assets/for%20%282%29.png)

## Voorbeeld flowchart

Door de eerder beschreven elementen nu samen te voegen kunnen we een programma als een flowchart voorstellen. Stel dat we een programma "Faculteit" maken. Hierin is het de bedoeling om de faculteit van een gegeven getal N dat door de gebruiker wordt ingevoerd, te berekenen \(bijvoorbeeld N=5 geeft dan `5! = 5x4x3x2x1 = 120` \). De finale flowchart ziet er als volgt uit:

![](../../.gitbook/assets/fullflow%20%281%29.png)

Zoals verteld kunnen we een flowchart in beide richtingen gebruiken. We hebben de flowchart hiervoor gemaakt, gebaseerd op onze oplossing van het vorige labo. Maar stel dat je deze flowchart krijgt, dan kan je dus ook deze chart rechtstreeks omzetten in C\#.

## Code 2 flow

Via de website en app "Code2flow" \([site](https://code2flow.com/app)\) kan je heel eenvoudig een flowchart genereren van pseudocode.

