---
tags: [concept]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf, elte_eva_gy04_munkafuzet.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
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
alakul ki. A cél az, hogy ez a függőség minél kisebb legyen: úgy
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
függőség-befecskendezést jellemzően a modellben, illetve az adatkezelésben
használjuk: a perzisztenciaréteg felületét (`PersistenceInterface`)
elválasztjuk a megvalósítástól (`PersistenceImplementation`), utóbbit pedig a
nézet fecskendezi be a modellbe. A modell így csak a felületet ismeri, és
független marad a konkrét adattárolási módtól.

### Gyakorlati példa és tárolók (4. gyakorlat)

A DocuStat modell konstruktora `IFileManager`-t vár; a konkrét megvalósítást (`TextFileManager`, `PdfFileManager`) a `FileManagerFactory.CreateForPath` gyártófüggvény választja a fájl kiterjesztése alapján. Sok függőség esetén a példányosítást IoC tárolóra (`ServiceCollection`) bízhatjuk. Lásd [[concepts/esemalk/docustat-perzisztencia-filemanager]], [[concepts/esemalk/ioc-tarolo-servicecollection]].

## Kapocs

- [[concepts/esemalk/haromreteg-architektura]] — az architektúra, amelynek
  rétegei közötti laza csatolást a függőség-befecskendezés biztosítja
- [[concepts/esemalk/csharp-oroklodes]] — az interfészek, amelyeken
  keresztül a függőségeket absztraháljuk
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — konkrét példa a
  perzisztenciaréteg befecskendezésére
- [[subjects/esemalk]]
