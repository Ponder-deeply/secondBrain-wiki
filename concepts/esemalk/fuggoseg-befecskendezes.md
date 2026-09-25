---
tags: [concept, esemalk/architektura-es-esemenykezeles]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf]
derivation: source
updated: 2026-09-13
---

# Függőség-befecskendezés

A függőség-befecskendezés (*dependency injection*, DI) az a technika,
amellyel egy komponens a függőségeinek csak az absztrakcióját
(interfészét) látja, a konkrét megvalósítást pedig kívülről kapja meg —
ez teszi lehetővé a rétegek/komponensek közötti laza csatolást
(*loose coupling*).

## Tartalom

Amikor egy komponens (pl. egy rétegben lévő osztály) felhasználja egy
másik komponens funkcionalitását, közöttük *függőség* (*dependency*)
alakul ki. A cél a minél kisebb függőség elérése: a függőséget úgy
valósítjuk meg, hogy a felhasználó komponens ne a konkrét
megvalósítástól, csak annak felületétől (interfészétől) függjön.

```csharp
interface IDependency // függőség interfésze
{
    Boolean Check(Double value);
    Double Compute();
}
...
class DependencyImplementation : IDependency
    // a függőség egy megvalósítása
{
    public Boolean Check(Double value) { … }
    public Double Compute() { … }
}
```

A konkrét megvalósítást a komponensnek külön adjuk át — ezt nevezzük
*függőség-befecskendezésnek*. A befecskendezés helye/módszere szerint
különböző típusai lehetnek (pl. konstruktor, metódus, interfész).

```csharp
class Dependant { // osztály függőséggel
    private IDependency _dependency;

    public Dependant(IDependency d) {
        _dependency = d;
    } // konstruktor befecskendezéssel helyezzük be a függőséget
    …
}
…
Dependant d =
    new Dependant(new DependencyImplementation());
    // megadjuk a konkrét függőséget
```

### Alkalmazás háromrétegű architektúrában

A [[concepts/esemalk/haromreteg-architektura]] esetén a
függőség-befecskendezést jellemzően a modell, illetve az adatkezelés
esetén használjuk: a perzisztencia réteg felületét (`PersistenceInterface`)
elválasztjuk a megvalósítástól (`PersistenceImplementation`), utóbbit a
nézet fecskendezi be a modellbe — a modell így csak a felületet ismeri,
a konkrét adattárolási módtól független marad.

## Kapocs

- [[concepts/esemalk/haromreteg-architektura]] — az architektúra, amelynek
  rétegei közötti laza csatolást a függőség-befecskendezés biztosítja
- [[concepts/esemalk/csharp-interfeszek]] — az interfészek, amelyeken
  keresztül a függőségeket absztraháljuk
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — konkrét példa a
  perzisztencia réteg befecskendezésére
- [[subjects/esemalk]]
