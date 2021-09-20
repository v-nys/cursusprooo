# Oefeningen

## Structuur van je oefeningen

Om je oefeningen ordelijk bij te houden, gaan we al een aantal zaken gebruiken die je pas verder in de cursus in detail leert. Hieronder krijg je een korte inleiding.

### Stap 1: een project LaboOefeningen maken

Volg hiervoor de instructies op [Een C\# project maken in Visual Studio Code](3-een-c-project-maken-in-visual-studio.md).

### Stap 2: een klasse maken `EenProgrammaSchrijvenInCSharp`

Dit is nieuw. Klassen zijn een extra organisatie-eenheid van code. Ze spelen een grote rol in objectgeoriënteerd programmeren, maar kunnen ook gebruikt worden om stukken code verder te groeperen. Dit is voorlopig het enige dat wij er mee zullen doen.

{% hint style="warning" %}
Dit zal alleen werken als je de extensies juist hebt geïnstalleerd!
{% endhint %}

### Stap 3: een eigen methode maken

### Stap 4: je eigen methode oproepen

### Stap 5: je eigen methode voorwaardelijk oproepen

### Stap 6: je eigen methode verwijderen

## Oefening: H1-MijnEersteProgramma

### **Leerdoelen**

* een eigen programma kunnen uitvoeren
* input en output via `Console.ReadLine` en `Console.WriteLine`

### **Functionele analyse**

Binnen een zgn. dos-box wordt een titel weergegeven, nl. dit is mijn eerste c\# programma.  
Vervolgens wordt gevraagd je naam te noteren.  
Wanneer je je naam hebt genoteerd en op enter hebt gedrukt, verschijnt de tekst “hallo \[en je ingegeven naam\]”.

### **Technische analyse**

#### voorbeeldinteractie\(s\)

![MijnEersteProgramma runt in de console](../../.gitbook/assets/image%20%2856%29.png)

### Technische hulp

maak een methode met de naam `MijnEersteProgramma`

#### Programmaverloop

Wat het lezen en schrijven van tekst betreft moet gebruik gemaakt worden `Console.WriteLine` en `Console.ReadLine`.

#### Testscenario's

* Probeer meer dan 200 tekens in te voeren
* Probeer geen tekst in te voeren

## Oefening: H1-rommelzin

### Leerdoelen

* een eigen programma kunnen uitvoeren
* input en output via `Console.ReadLine` en `Console.WriteLine`
* de computer leren zien als "domme verwerker"

### Functionele analyse

Dit programma verwerkt tekst die door de gebruiker wordt ingetypt. Het print nieuwe berichten die deze tekst bevatten uit. Het print niet de berichten die je verwacht: het zal de antwoorden door elkaar halen en je favoriete kleur tonen wanneer het beweert je favoriete eten te tonen, enzovoort. De verbanden worden duidelijk uit de voorbeeldinteractie.

### Technische analyse

#### Organisatie van de code

Schrijf dit programma als een methode met de naam `Rommelzin` binnen de klasse `EenProgrammaSchrijvenInCSharp`. Test uit door deze methode op te roepen binnen de `Main` methode.

#### voorbeeldinteractie\(s\)

```text
Wat is je favoriete kleur?
> blauw
Wat is je favoriete eten?
> spaghetti
Wat is je favoriete auto?
> Toyota Aygo
Wat is je favoriete film?
> Robocop 2
Wat is je favoriete boek?
> The Gone-Away World
Je favoriete kleur is spaghetti. Je eet graag Toyota Aygo. Je lievelingsfilm is The Gone-Away World en je favoriete boek is Robocop 2.
```

### Technische hulp

#### Programmaverloop

Per regel die getoond wordt op het scherm, maak je gebruik van `Console.WriteLine`. Per regel die je zelf intypt, maak je gebruik van `Console.ReadLine`. Zorg zelf voor de juiste ondersteunende code.

#### Testscenario's

* Test uit met een héél lang stuk tekst \(meer dan 200 tekens\) voor je favoriete kleur.
* Test uit met tekst met internationale karakters, bijvoorbeeld de ç.
* Ga na wat er gebeurt als je een lege regel invoert, dus als je meteen op ENTER duwt wanneer gevraagd wordt om invoer.

## Oefening: H1-gekleurde-rommelzin

### Leerdoelen

* de kleur van tekst in de console aanpassen
* herhaling van de leerdoelen uit H1-rommelzin

### Functionele analyse

Dit programma werkt net als H1-rommelzin, maar elke regel die aan de gebruiker wordt getoond, krijgt een andere kleur. De namen van de kleuren die je gebruikt \(in deze volgorde\) zijn:

1. `DarkGreen`
2. `DarkRed`
3. `DarkYellow`
4. `Blue`
5. `Cyan`
6. `Red`

### Technische analyse

#### Organisatie van de code

Schrijf deze oefening als een nieuwe methode met de naam `GekleurdeRommelzin` in de klasse `EenProgrammaSchrijvenInCSharp`. Test uit door deze methode op te roepen binnen de `Main` methode.

#### voorbeeldinteractie\(s\)

![De eerste regel behoort niet tot het programma. De rest moet er bij jou hetzelfde uitzien.](../../.gitbook/assets/gekleurde-rommelzin.png)

### Technische hulp

#### Programmaverloop

Voor elke regel die in kleur getoond wordt, wissel je de voorgrondkleur. Op de juiste plaatsen in de code herstel je de oorspronkelijke kleuren van de terminal.

#### Testscenario's

* Test opnieuw uit met een kleur, maaltijd, auto, film en boek naar keuze.

