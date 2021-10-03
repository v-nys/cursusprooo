# Omzetten \(van en naar strings

## Conversie

Zoals eerder aangegeven, kan je geen strings toekennen aan variabelen van type int of omgekeerd. Toch wil je soms een getal beschouwen als tekst, of tekst omzetten naar een getal .NET heeft hiervoor methoden die je kunnen helpen om data van het ene type naar het andere te brengen. Deze methoden zitten binnen de **`Convert`**-klasse.

Het gebruik hiervan is zeer eenvoudig. Enkele voorbeelden:

```csharp
int userAge = Convert.ToInt32("19"); // string to int
string ageAsText = Convert.ToString(19); // int to string
```

Je plaatst bij gebruik van `Convert` tussen de ronde haakjes de variabele of literal die je wenst te converteren naar een ander type. Merk op dat naar een `int` converteren met `.ToInt32()` moet gebeuren. Voor andere types zijn er overeenkomstige methoden. Bijvoorbeeld: om naar een `short` te converteren is dit met behulp van `.ToInt16()`.

Om iets naar een string te converteren, 

Je kan [alle conversie-mogelijkheden hier bekijken](https://msdn.microsoft.com/en-us/library/system.convert.aspx).

