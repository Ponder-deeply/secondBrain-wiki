---
tags: [concept]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf]
derivation: source
updated: 2026-09-13
---

# Mock objektumok

Amennyiben függőséggel rendelkező programegységet tesztelünk, a
függőséget helyettesíthetjük annak szimulációjával, amit *mock
objektum*nak nevezünk.

## Tartalom

### Fogalom

- A mock objektum megvalósítja a függőség interfészét, egyszerű,
  hibamentes funkcionalitással.
- Használatukkal a teszt valóban a megadott programegység
  funkcionalitását ellenőrzi, nem befolyásolja a függőségben felmerülő
  esetleges hiba.
- Mock objektumokat manuálisan is létrehozhatunk, vagy használhatunk erre
  alkalmas programcsomagot, pl. *NSubstitute*, *Moq* — letölthetők NuGet
  segítségével.

### Manuális mock objektum

```csharp
class DependencyMock : IDependency
    // mock objektum
{
    // egy egyszerű viselkedést adunk meg
    public Double Compute() { return 1; }
    public Boolean Check(Double value) {
        return value >= 1 && value <= 10;
    }
}
...
Dependant d = new Dependant(new DependencyMock());
    // a mock objektumot fecskendezzük be a függő osztálynak
```

### Mock objektum Moq segítségével

A *Moq* segítségével könnyen tudunk interfészekből mock objektumokat
előállítani:

- a `Mock` generikus osztály segítségével példányosíthatjuk a
  szimulációt, amely az `Object` tulajdonsággal érhető el, és
  alapértelmezett viselkedést produkál:

```csharp
Mock<IDependency> mock =
    new Mock<IDependency>();
    // a függőség mock objektuma
Dependant d = new Dependant(mock.Object);
    // azonnal felhasználható
```

- a `Setup` művelettel beállíthatjuk bármely tagjának viselkedését
  (`Returns(...)`, `Throws(...)`, `Callback(...)`), a paraméterek
  szabályozhatók (`It`).

A mock objektumok haszna a
[[concepts/esemalk/retegek-szerelvenyekre-bontasa]] szerint interfész mögé
rejtett függőségeknél (pl. perzisztencia) mutatkozik meg igazán: a modell
egységtesztelhető anélkül, hogy a valódi (pl. fájlrendszer alapú)
adatkezelést kellene meghívnia.

## Kapocs

- [[concepts/esemalk/egysegtesztek-mstest]] — az egységtesztelés
  keretrendszere, amelybe a mock objektumok illeszkednek
- [[concepts/esemalk/retegek-szerelvenyekre-bontasa]] — az interfész mögé
  rejtett, felcserélhető függőségek (pl. perzisztencia), amelyeket mock
  objektummal helyettesítünk
- [[concepts/esemalk/csharp-egysegteszt-keretrendszerek]] — a Moq alapú
  mockolás gyakorlati alkalmazása a Tic-Tac-Toe teszteseteiben, `Verify`
  hívásokkal
- [[subjects/esemalk]]
