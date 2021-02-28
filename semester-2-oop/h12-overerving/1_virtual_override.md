# Virtual en override

## Virtual en Override

Soms willen we aangeven dat de implementatie \(code\) van een property of methode in een parent-klasse door child-klassen mag aangepast worden. Dit geven we aan met het **virtual** keyword:

```csharp
class Vliegtuig
{
   public virtual void Vlieg()
   {
      Console.WriteLine("Het vliegtuig vliegt rustig door de wolken.");
   }
}

class Raket: Vliegtuig
{
}
```

Stel dat we 2 objecten aanmaken en laten vliegen:

```csharp
Vliegtuig f1 = new Vliegtuig();
Raket spaceX1 = new Raket();
f1.Vlieg();
spaceX1.Vlieg();
```

De uitvoer zal dan zijn:

```text
Het vliegtuig vliegt rustig door de wolken.
Het vliegtuig vliegt rustig door de wolken.
```

Een raket is een vliegtuig, toch vliegt het anders. We willen dus de methode Vlieg anders uitvoeren voor een raket. Daar hebben we **override** voor nodig. Door override voor een methode in de child-klasse te plaatsen zeggen we "gebruik deze implementatie en niet die van de parent klasse." **Je kan enkel overriden indien de respectievelijke methode of property in de parent-klasse als virtual werd aangeduid**

```csharp
class Raket:Vliegtuig
{
   public override void Vlieg()
   {
      Console.WriteLine("De raket verdwijnt in de ruimte.");
   }     
}
```

De uitvoer van volgende code zal nu anders zijn:

```csharp
Vliegtuig f1= new Vliegtuig();
Raket spaceX1= new Raket();
f1.Vlieg();
spaceX1.Vlieg();
```

Uitvoer:

```text
Het vliegtuig vliegt rustig door de wolken.
De raket verdwijnt in de ruimte.
```

## Properties overriden

Ook properties kan je virtual instellen en override'n.

**Opgelet**: Visual Studio gebruikt Expression Body Member syntax \(herkenbaar aan de `=>`\) om properties te overriden. Deze syntax kennen we niet \(lees er gerust meer over [hier](../../semester-2-appendix/nice-to-know-stuff/6_exprbody.md)\). **Je schrijft dus best manueel de override van properties**

Stel dat je volgende klasse hebt:

```csharp
    class Auto
    {
        virtual public int Fuel { get; set; }
    }
```

We maken nu een meer luxueuze auto die een lichtje heeft dat aangaat wanneer de benzine-tank vol genoeg is, dit kan via override.

```csharp
class LuxeAuto : Auto
{
   public bool HeeftVolleTank { get; set; }

   public override int Fuel
   {
      get { return base.Fuel; }
      set
      {
            if (value > 100)
            {
               HeeftVolleTank = true;
            }
            base.Fuel = value;
      }
   }
}
```

## Kennisclip

![](../../.gitbook/assets/infoclip%20%282%29.png)

* [Virtual en override](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=d549422d-eb27-4dd5-8154-ab7c00ba0728)

