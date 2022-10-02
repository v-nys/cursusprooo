---
description: We hebben twee zaken nodig om C# programma's te schrijven.
---

# Visual Studio en .NET Core installeren

Met een editor, zoals Visual Studio, krijgen we ondersteuning bij het schrijven van de code die we later zullen uitvoeren. Een editor vergemakkelijkt dus het schrijven van een specifiek soort tekst.

De "SDK" (software development toolkit) bevat alles wat je nodig hebt om de code daadwerkelijk uitvoerbaar te maken.

## Vooraleer je begint

1. Voor deze opdrachten gebruiken we .NET Core 6.0, maar we gebruiken de (explicietere) template van .NET Core 5.0. Je moet dus beide SDK's installeren.
2. Sommige afbeeldingen hieronder dateren van de tijd van .NET Core 2.0 en Visual Studio 2017. Soms kunnen zaken er op jouw scherm dus wat anders uitzien dan in deze cursus.

## Installatie

### Visual Studio 2022 Community

1. [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/)
2. Kies voor de "community" versie\
   ![](<../../.gitbook/assets/image (71).png>)
3. Het installatiescherm ziet er als volgt uit, in de volgende punten wordt beschreven welke elementen je specifiek moet aanduiden.\
   ![](<../../.gitbook/assets/image (91).png>)
   * Kies bij de installatie voor **.NET desktop development**\
     ![](<../../.gitbook/assets/image (78).png>)
   * Bij de _installation details_ kies je voor volgende elementen\
     ![](<../../.gitbook/assets/image (77).png>)
   *   In het tabblad _individual components_ klik je **.NET 5.0 Runtime (out of support)** nog extra aan.\




       <figure><img src="../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>
4. Vervolgens kies je rechts onderaan voor de knop **Install**
5. Log in met jouw account van de hogeschool, nl. **s-nummer@ap.be**\
   ****![](<../../.gitbook/assets/image (90).png>)****

Opmerking\
.NET 5.0 Runtime kan je ook afzonderlijk installeren via [https://dotnet.microsoft.com/en-us/download/dotnet/5.0](https://dotnet.microsoft.com/en-us/download/dotnet/5.0)

### Flowgorithm

Flowgorithm is een visuele programmeertaal. We zullen deze gebruiken om bepaalde concepten duidelijk zichtbaar te maken. Je moet de Windows Installer van [deze pagina](http://www.flowgorithm.org/download/index.html) halen. Tijdens de installatie klik je gewoonweg elke keer op "Next".

Gebruikers van Mac OS installeren dit best via [Wine](https://wiki.winehq.org/Download) of in een virtuele machine. Als dit echt niet lukt, kunnen ze tijdelijk [FlowRun](https://flowrun.io/scratchpad) gebruiken, maar deze software werkt wat anders en ondersteunt geen arrays.

Een voorbeeld van hoe je begint te werken met Flowgorithm kan je hier bekijken.\
[https://www.youtube.com/watch?v=7SuYTvYCqOw](https://www.youtube.com/watch?v=7SuYTvYCqOw)

## Eerste gebruik Visual Studio&#x20;

1.  Kies voor **Create New Project**\


    <figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>
2.  Vervolgens selecteer je **Console App**\
    ****

    <figure><img src="../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>
3.  Je geeft je project een goede naam, hieronder dien je de **Project name** dan aan te passen en je zal zien dat de **Solution name** automatisch mee wordt gewijzigd. \
    Denk er ook aan om je project op de juiste plaats op te slaan door de **Location** te wijzigen.\


    <figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>
4.  In de volgende stap dien je als **Framework** .NET 5.0 (Out of support) te kiezen\


    <figure><img src="../../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>
5.  Nu is je project opgestart en dien je nog enkele settings aan te passen. Ga in het menu **Project** naar **Edit Project File**\


    <figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>
6.  Het \<TargetFramework> wijzig je in **net6.0**\
    ****

    <figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

## Code Snippet

Hierbij ga je ervoor zorgen dat je met afkortingen kan coderen die dan automatisch in het goede formaat worden omgezet.

Bv. **cr** (gevolgd door twee TABs) **** wordt dan **Console.ReadLine()**

Je kan volgende code kopiëren in een tekstbestand met als extensie .snippet of je kan het hieronder downloaden.

{% file src="../../.gitbook/assets/programmeren.snippet" %}

```csharp
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
 <CodeSnippet Format="1.0.0">
 <Header>
 <Title>cr</Title>
 <Shortcut>cr</Shortcut>
 <Description>Code snippet for Console.ReadLine</Description>
 <Author>Community</Author>
 <SnippetTypes>
 <SnippetType>Expansion</SnippetType>
 </SnippetTypes>
 </Header>
 <Snippet>
 <Declarations>
 <Literal Editable="false">
 <ID>SystemConsole</ID>
 <Function>SimpleTypeName(global::System.Console)</Function>
 </Literal>
 </Declarations>
 <Code Language="csharp">
 <![CDATA[$SystemConsole$.ReadLine();$end$]]>
 </Code>
 </Snippet>
 </CodeSnippet>
</CodeSnippets>

```

Vervolgens dien je binnen Visual Studio in het menu Tools naar Code Snippets Manager gaan.

Je kiest voor Language CSharp en klikt op de knop Import.

![](<../../.gitbook/assets/image (83).png>)

Je kiest het snippet bestand en voegt dit toe.&#x20;

