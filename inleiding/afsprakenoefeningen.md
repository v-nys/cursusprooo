# Afspraken oefeningen

Voor de graduaatsopleiding hanteren we een vaste structuur voor de oefeningen.

## vorm van de oefeningen

### unieke titel

Elke oefening begint met een unieke titel. Deze gebruik je voor de organisatie van je bestanden.

### korte toelichting

Eerst krijg je een omschrijving in tekst van wat de algemene bedoeling is van je programma. Deze bevat niet noodzakelijk elk detail, maar geeft je een _big picture_. Bijvoorbeeld:

> In deze oefening maak je een echo. Dit is een programma dat tekst inleest vanaf het toetsenbord en deze tekst dan op het scherm toont.

### vertrekpunt

Je hoeft niet altijd alle code zelf te schrijven. Code die je nog niet verondersteld wordt zelf te kunnen schrijven, of code die gewoon veel tijd in beslag neemt, krijg je. Bij de stukken code staat telkens de naam van het bestand waarin ze thuishoort. Commentaar bij de te wijzigen stukken code geeft aan welke aanpassingen je moet doen. Bijvoorbeeld:

#### Program.cs

```csharp
using System;

namespace Programmeren {
    class Program {
        public static void Main(string[] args) {
            // zorg er zelf voor dat een regel tekst die gebruiker intypt weer verschijnt
            string message;
            Console.WriteLine(message);
        }
    }
}
```

### voorbeeldinteractie

Ten slotte worden één of meerdere voorbeelden getoond van hoe je programma zich gedraagt. In deze voorbeelden stellen regels die niet beginnen met `>` iets voor dat op het scherm verschijnt. Regels die wel beginnen met `>` stellen iets voor dat door de gebruiker zelf wordt ingetypt. Bijvoorbeeld, voor het programma dat we hier als leidraad gebruiken:

```text
> Hallo, wereld!
Hallo, wereld!
```

We gebruiken de speciale syntax `<EOF>` om aan te geven dat er een end-of-file signaal wordt gestuurd.

## organisatie van je bestanden

Voor de eenvoud zorgen we dat elke oefening op zichzelf staat. Dit betekent dat sommige code herhaald wordt in je bestanden, maar het vermijdt dat iets dat je in week 1 geschreven hebt in week 5 plots niet meer werkt. Concreet doen we dat zo:

* Je maakt ergens op je machine één map voor alle oefeningen van het vak Programmeren \(in semester 1\) of Objectgericht programmeren \(in semester 2\). Het maakt niet uit waar, maar je kiest één map en je blijft deze heel het semester gebruiken.
* Voor elke oefening in het eerste semester maak je in die map een submap. De naam van deze submap is **letterlijk** de unieke titel van de oefening, inclusief gebruik van hoofdletters, leestekens,... Je voegt **geen** andere structuur toe, dus geen mapjes per labosessie,...
* Wanneer een oefening verderbouwt op een eerdere oefening, kopieer en hernoem je de map van die eerdere oefening. Daarna werk je dan voort in die nieuwe map.

