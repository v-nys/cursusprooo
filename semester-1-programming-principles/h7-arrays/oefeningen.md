# Oefeningen

## Oefeningen

### **Oefening: H6-ArrayTrueFalse**

#### **Leerdoelen**

* Declareren van arrays
* Initialiseren van arrays
* Opvullen van arrays
* Arrays gebbruiken - afprinten

#### **Functionele analyse**

Maak een array gevuld met afwisselend true en false (de array is 30 lang)

Per array: output de array naar het scherm, maar ieder element naast elkaar met komma gescheiden. Dus niet:

1 true

2 false

3 true

4 \\\etc

maar wel: true, false, true, ...

Implementeer onderstaande flowchart in C#.

#### Technische analyse

{% file src="../../.gitbook/assets/H6-ArrayTrueFalse.fprg" %}

#### Voorbeeldinteractie

![](<../../.gitbook/assets/image (69) (1).png>)

### **Oefening: H6-ArrayOefener1**

#### **Leerdoelen**

* Declareren van arrays
* Initialiseren van arrays
* Opvullen van arrays
* Arrays gebruiken

#### **Functionele analyse**



Maak een programma dat aan de gebruiker vraagt om 10 waarden (int) in te voeren in een array. Vervolgens toont het programma de som, het gemiddelde en het grootste getal van deze 10.

Vervolgens vraagt het programma de gebruiker om een getal in te voeren. Het programma toont dan alle getallen die groter of gelijk zijn aan dit ingevoerde getal zijn die in de array aanwezig zijn. Indien geen getallen groter zijn dan verschijnt een bericht Niets is groter op het scherm.

Implementeer onderstaande flowchart in C#.

#### &#x20;**Technische analyse**

{% file src="../../.gitbook/assets/H6-ArrayOefener1.fprg" %}

#### **Voorbeeldinteractie**

![](<../../.gitbook/assets/image (70).png>)

### **Oefening: H6-Boodschappenlijst**

#### **Leerdoelen**

* Declareren van arrays
* Initialiseren van arrays
* Opvullen van arrays
* Arrays gebruiken

#### **Functionele analyse**

Maak een programma dat de gebruiker een boodschappenlijstje laat samenstellen.

* Het programma vraagt eerst hoeveel items de boodschappenlijst moet bevatten en laat dan de lijst vullen.
* Vervolgens wordt een gesorteerde lijst van de items getoond.
* Daarna, in de winkel, kan de gebruiker aangeven welke items er gekocht worden. De gebruiker kan dit blijven doen zolang er 'ja' geantwoord wordt op de vraag 'Nog winkelen?'. Als de gebruiker een item intypt dat niet op de lijst staat, wordt er een bericht getoond.
* Na het winkelen toont het programma welke items van de lijst niet gekocht zijn.

Implementeer onderstaande flowchart in C#.

#### **Technische analyse**

{% file src="../../.gitbook/assets/H6-Boodschappenlijst.fprg" %}

#### **Voorbeeldinteractie**

![](<../../.gitbook/assets/image (75).png>)

### **Oefening: H6-Kerstinkopen**

#### **Leerdoelen**

* Declareren van arrays
* Initialiseren van arrays
* Opvullen van arrays
* Arrays gebruiken
* Array methodes gebruiken

#### **Functionele analyse**

Maak een programma dat kan gebruikt worden om kerstinkopen te doen, rekening houdend met een budget. Na de inkopen, wordt het totaal gespendeerd bedrag getoond en het hoogste, laagste en gemiddelde bedrag.

#### **Technische analyse**

Probeer zelf een flowchart te maken en zet die dan om naar C#.

#### Voorbeeldinteractie

![](<../../.gitbook/assets/image (68).png>)

### **Oefening: H6-Lotto**

**Leerdoelen**

* Arrays in flowcharts gebruiken
* Declareren van arrays
* Initialiseren van arrays
* Opvullen van arrays
* Opzoeken waarde in arrays

**Functionele analyse**

Je vraagt de gebruiker zijn 6  lotto getallen (getal tussen 1 en 42) in te geven. Je hoeft geen controle te doen op de getallen die de gebruiker ingeeft. Je bewaart deze getallen in een array lottoFormulier.

Vervolgens simuleer je een trekking. Dat doe je door random 6 getallen te genereren (Random…) en die ook in een array lottoTrekking te bewaren. Let op: hier moet je wel controleren of het inderdaad 6 verschillende getallen zijn (hoe kan je nagaan of iets aanwezig is in je array?).

Dan doe je een validatie. Heeft de gebruiker 3 juiste cijfers wint hij 10 €, bij 4 juiste cijfers 1000 €, bij 5 juiste cijfers 100.000 € en bij 6 juiste cijfers 10.000.000 €.

&#x20;Zorg dat alles mooi wordt getoond aan de gebruiker. Lotto getallen in stijgende volgorde, Trekking getallen in stijgende volgorde, winst. Zie voorbeeldinteractie.

&#x20;**Technische analyse**

Maak een flowchart en zet die om naar C#

Wat betreft het random genereren van 6 getallen tussen 1 en 42. Daar krijg je het volgend stukje code voor (probeer te begrijpen hoe het werkt en zoek op internet het gebruik van Random eens op):&#x20;



```csharp
Random random = new Random();
int lottoGetal;
        
for (int i = 0; i < lottoTrekking.Length; i++) {
    do {
        lottoGetal = random.Next(42) + 1;
    }
    while (Array.IndexOf(lottoTrekking, lottoGetal) >= 0);
    lottoTrekking[i] = lottoGetal;
}
```

#### Voorbeeldinteractie

![](<../../.gitbook/assets/image (73).png>)

#### Uitbreiding

Test de ingegeven lotto getallen en zorg er voor dat er geen getallen kleiner dan 1 of groter dan 42 ingegeven kunnen worden en dat er ook geen dubbels voorkomen..

### **Oefening: H6-IntegerIndexOf**

#### **Leerdoelen**

* Arrays in flowcharts gebruiken
* Opzoeken waarde in integer arrays – zelf geschreven methode

#### **Functionele analyse**

Probeer d.m.v. Flowgorithm de flowchart te gebruiken en zet dan om naar C#.

#### Technische analyse

{% file src="../../.gitbook/assets/H6-IntegerIndexOf.fprg" %}

#### Voorbeeldinteractie

![](<../../.gitbook/assets/image (72).png>)

![](<../../.gitbook/assets/image (67) (1).png>)

### **Oefening: H6-BinarySearch**

**Leerdoelen**

* Arrays in flowcharts gebruiken
* De array gebruiken, in een array zoeken.

**Functionele analyse**

Heel eenvoudig uitgelegd zal het algoritme de te zoeken waarde vergelijken met de middelste waarde (van een gesorteerde array). Als de waarde niet gelijk is wordt dat gedeelte van de array waar de waarde zich niet in kan bevinden weggegooid. De zoektocht gaat verder totdat de waarde is gevonden (of niet gevonden indien alle mogelijkheden zijn doorzocht)

Implementeer onderstaande flowchart  in C#.

#### **Technische analyse**

{% file src="../../.gitbook/assets/H6-BinarySearch.fprg" %}

#### Voorbeeldinteractie

![](<../../.gitbook/assets/image (74).png>)

![](<../../.gitbook/assets/image (71).png>)





