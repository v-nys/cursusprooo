# Verdere datastructuren

## HashSet en ImmutableHashSet

In sommige situaties wil je dat een element geen twee keer in een datastructuur terecht kan komen. Je wil bijvoorbeeld dat de lijst met cursussen die deel uitmaakt van een studieprogramma geen tweemaal dezelfde cursus kan bevatten.

In dit geval gebruik je geen `List<T>`, maar een `HashSet<T>`. Elementen toevoegen doe je met de methode `Add` en elementen verwijderen doe je met `Remove`. Ook hier beperken we ons voorlopig tot voorgedefinieerde soorten objecten. Wanneer we `System.Object` hebben bestudeerd, kunnen we ook `HashSet`s van onze eigen types maken.

De immutable variant is ImmutableHashSet.

