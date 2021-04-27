# SchoolAdmin - Recursie \(versie 2020\)

## Uitbreiding cursussen met volgtijdelijkheden

We willen dat sommige cursussen enkel opgenomen kunnen worden als je een eerdere cursus hebt gevolgd. Daarom zullen we elke cursus voorzien van een volgtijdelijkheden, d.w.z. een lijst met andere cursussen die rechtstreeks vereiste voorkennis vormen voor deze cursus. We zullen dit voorstellen elke `Course` een property `Prerequisites` te geven. Hieronder volgt een filmpje dat dit helemaal demonstreert, maar lees eerst de opgave.

We starten vanaf code die hieronder gegeven wordt en die dit diagram implementeert:

![](../../.gitbook/assets/cursussenzondervolgtijdelijkheden.png)

We zullen dit aanpassen naar:

![](../../.gitbook/assets/cursussenmetvolgtijdelijkheden.png)

Nadat we deze aanpassing gedaan hebben, zullen we er voor zorgen dat we voor een gegeven cursus de lijst kunnen opbouwen die eerder gevolgd moeten zijn. We doen dit met een recursieve objectmethode `CollectAllPrerequisites(HashSet<Course> courses)`. Om dit te doen, passen we ook de `Equals` methode en de `GetHashcode` methode van `Course` aan. We demonstreren dit allemaal met een methode `DemonstratePrerequisites` die we kunnen oproepen uit onze keuzemenu. Deze maakt minstens vijf cursussen aan en verbindt ze met elkaar.

De code om van te starten krijg je hier:

{% file src="../../.gitbook/assets/schooladmin \(2\).zip" caption="SchoolAdmin project" %}

{% hint style="success" %}
[Het filmpje](https://youtu.be/PWvfcZjUGOw)
{% endhint %}

## Studieprogramma's met volgtijdelijkheden

Niet alleen cursussen hebben soms volgtijdelijkheden, het kan ook zijn dat je een studieprogramma moet hebben afgewerkt voor je aan een ander studieprogramma mag beginnen. Doe zelf de overeenkomstige aanpassing aan StudyProgram en implementeer `CollectAllPrerequisites(StudyProgram studyProgram, HashSet<StudyProgram>)`.

