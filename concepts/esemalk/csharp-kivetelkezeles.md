---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# kivételkezelés

A .NET keretrendszerben minden hiba *kivételként* jelenik meg; a kivétel
általános osztálya az `Exception`, csak ennek vagy leszármazottjának
példánya váltható ki.

## Tartalom

**Kivétel kiváltása.** A `throw` utasítással:

```csharp
throw new <kivétel típusa>(<paraméterek>);
```

**Kivétel kezelése.** Egy kivételkezelő (`try`–`catch`–`finally`) szakasszal:

```csharp
try { <kivételkezelt utasítások> }
catch (<elfogott kivétel típusa>) {
    <kivételkezelő utasítások>
}
finally { <mindenképp lefuttatandó utasítások> }
```

```csharp
class WorkingClass {
    public void DoSomething(Int32 number) {
        if (number < 1)
            throw new ArgumentOutOfRangeException();
            // kivétel kiváltása (a paraméter hibás tartományban van)
        ...
        throw new Exception("Too lazy...");
        // kivétel kiváltása (üzenettel)
    }
    public void Finish() { ... }
}
...
WorkingClass wc = new WorkingClass();
try // kivételkezelő blokk
{
    wc.DoSomething(42);
}
// a kivételt típustól függően kezelhetjük
catch (ArgumentOutOfRangeException ex)
{ ... }
// az Exception típusú kivételt nem kezeljük le
finally {
    wc.Finish(); // de ez mindenképpen lefut
}
```

A `finally` blokk mindenképpen lefut, függetlenül attól, hogy történt-e
kivétel, és attól is, hogy azt lekezelte-e valamelyik `catch` ág.

## Kapocs

- [[concepts/esemalk/csharp-osztalyok]] — a kivétel is egy osztály
  (`Exception` leszármazottja) példánya
- [[subjects/esemalk]] — a kurzus áttekintése
