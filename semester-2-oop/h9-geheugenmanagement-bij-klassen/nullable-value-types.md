# nullable value types

{% hint style="success" %}
[Kennisclip](https://youtu.be/vzNCIlFjq5g) **\(met demonstratie in SchoolAdmin, zelf mee te maken!\)**
{% endhint %}

## Betekenis van null

Normaal gezien kom je `null` tegen wanneer je een variabele van een reference type hebt zonder verwijzing naar data. Het gevolg is dat `null` vaak betekent dat er een waarde zou kunnen staan, maar in de huidige situatie geen geldige waarde is.

Hoewel value types niet werken met verwijzingen, zou dezelfde interpretatie ook bij value types zinvol kunnen zijn: soms heb je gewoonweg geen geldige waarde. Daarom kent C\# ook **nullable value types**. Dit zijn speciale value types die ook de waarde `null` kunnen aannemen \(ook al kom je die laatste anders vooral tegen bij reference types\).

Je noteert een nullable value type als een gewoon value type, gevolgd door een vraagteken. Indien je in code bijvoorbeeld een getalwaarde wil voorstellen als een variabele `int mijnVariabele`, maar de mogelijkheid bestaat dat er geen waarde is voor `mijnVariabele`, declareer je als volgt: `int? mijnVariabele`. Dit betekent: "`mijnVariabele` is een getal, maar kan ontbreken."

Dit heeft gevolgen. Je kan code die een value type verwacht niet zomaar gebruiken met een nullable versie van hetzelfde type. Anders gezegd: je mag `mijnVariabele` niet meegeven aan een methode die een gewone `int` verwacht. Je moet ofwel deze methode aanpassen zodat ze een `int?` verwacht, ofwel moet je `mijnVariabele` casten voor je hem meegeeft als argument. Let op: dit werkt alleen als `mijnVariabele` niet `null` is!

## Operaties met `null`

Voor de nullable versies van de value types die je al kent, kan je gekende operaties \(zoals `+`, `-`, ... voor getallen\) blijven gebruiken, maar je moet opletten. Een berekening met `null` in levert je sowieso `null` op als resultaat. Een vergelijking \(via `<=`, `<`, `>`, `>=`\) met `null` levert je sowieso `false` op als resultaat.

