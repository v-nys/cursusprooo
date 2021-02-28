# OOP Intro

## OOP

Object Oriented Programming of korter OOP is een techniek afkomstig van higher level programmeertalen zoals Java, C\#, VB.NET, ... en vindt zijn oorsprong bij Smalltalk die het eerst de term Object Oriented Programming introduceerde.

In recentere jaren heeft deze techniek echter ook zijn weg gevonden naar webscripting talen zoals Python, Ruby, Perl en zelfs PHP.

OOP streeft ernaar om een project zo structureel mogelijk op te bouwen in objecten. Dit heeft voor de programmeur het grote voordeel dat code vanaf nu in logische componenten wordt opgedeeld en veel makkelijker te hergebruiken is.

Om het concept van objecten te illustreren wordt meestal een voorwerp uit het dagelijks leven als voorbeeld gebruikt. Neem bijvoorbeeld een auto. De auto is het object en dit object heeft bepaalde properties of eigenschappen. Een eigenschap van de auto kan een band, een deur, een spiegel, de uitlaat of eender welk ander onderdeel van de auto zijn. Maar een auto heeft ook methoden. Een methode kan starten of remmen zijn.

Dus hebben we nu eigenlijk een object met properties en methoden. Zo zit een object in programmeertalen er ook uit. Een mail object heeft bijvoorbeeld als property de ontvanger, de verzender en het bericht en als methode versturen. Dit zijn natuurlijk erg vereenvoudigde voorbeelden en in de praktijk zal het er een stuk ingewikkelder aan toe gaan maar de basisprincipes zijn steeds hetzelfde. [Bron van deze introductie](https://www.inventis.be/blog/webdevelopment/de-voordelen-van-object-georienteerd-programmeren/145/).

### Black-box principe

Een belangrijk concept bij OOP is het **Black-box** principe waarbij we de afzonderlijke objecten en hun werking als kleine zwarte dozen gaan beschouwen. Neem het voorbeeld van de auto: deze is in de echte wereld ontwikkeld volgens het blackbox-principe. De werking van de auto kennen tot in het kleinste detail is niet nodig om met een auto te kunnen rijden. De auto biedt een aantal zaken aan de buitenwereld aan \(het stuur, pedalen, het dashboard\), wat we de **interface** noemen, die je kan gebruiken om de interne staat van de auto uit te lezen of te manipuleren. Stel je voor dat je moest weten hoe een auto volledig werkte voor je ermee op de baan kon.

Binnen OOP wordt dit blackbox-concept **encapsulatie** genoemd. Het doel van OOP is andere programmeurs \(en jezelf\) zoveel mogelijk af te schermen van de interne werking van je code. Vergelijk het met de methoden uit vorig semester: "if it works, it works" en dan hoef je niet in de code van de methode te gaan zien wat er juist gebeurt.

## Klassen en objecten

Een elementair aspect binnen OOP is het verschil beheersen tussen een klasse en een object.

Wanneer we meerdere objecten gebruiken van dezelfde soort dan kunnen we zeggen dat deze objecten allemaal deel uitmaken van een zelfde klasse.

Zo hebben we bijvoorbeeld de klasse van de auto's. De verschillende auto's die je op de straat ziet rijden zijn allemaal objecten van die klasse. De klasse zelf is een soort algemene beschrijving waaraan alle objecten van dat type moeten voldoen \(bv: alle auto's hebben 4 banden, 1 motor en kunnen sneller en trager rijden\).

## Definitie klasse en object

* **Een klasse** is een beschrijving en verzameling van dingen \(objecten\) met soortgelijke eigenschappen
* Een individueel **object** is een **instantie** van een klasse

> Je zou dit kunnen vergelijken met het grondplan voor een huis dat tien keer in een straat zal gebouwd worden. Het plan met alle soortgelijke eigenschappen van ieder huis is de _klasse_. De effectieve huizen die we, gebaseerd op dat grondplan, bouwen zijn de instanties of objecten van deze klasse.

Nog een andere invalshoek:

> Een andere invalshoek is de zogenaamde "dungeons" in veel online games. De makers van het spel hebben iedere dungeon in een klasse beschreven. Wanneer een groep avonturiers nu in zo'n grot gaat dan wordt voor die groep een aparte instantie \(_instance_\) van die grot gemaakt, gebasseerd op de klasse. Ze doen dit zodat iedere groep spelers mekaar niet voor de voeten loopt in 1 grot.

