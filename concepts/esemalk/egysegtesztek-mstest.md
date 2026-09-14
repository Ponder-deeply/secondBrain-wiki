---
tags: [concept]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf]
derivation: source
updated: 2026-09-13
---

# Egységtesztek (MSTest)

Az *egységteszt* (**unit test**) egy automatikusan futtatható ellenőrzés,
amely lehetőséget ad osztályok és objektumok viselkedésének vizsgálatára —
azaz annak eldöntésére, hogy a tényleges viselkedés megegyezik-e az
elvárttal.

## Tartalom

### Dinamikus tesztelés szintjei

A programoknak minden esetben alapos tesztelésen kell átesniük; a
dinamikus tesztelést a rendszer különböző szintjein végezzük: egységteszt,
integrációs teszt, rendszerteszt.

### MSTest keretrendszer

A Visual Studio lehetőséget ad, hogy egységteszteket automatikusan
generáljunk és futtassunk le; ezek külön projektbe kerülnek (*MSTest Test
Project*), amelyből meghivatkozzuk a tesztelendő projektet.

- A tesztosztályokat a `TestClass` attribútummal jelöljük.
- A tesztesetek eljárások, a `TestMethod` attribútummal jelölve, amelyeket
  automatikusan futtatunk.
- A tesztek az `Assert` osztály segítségével végeznek ellenőrzéseket
  (`AreEqual`, `IsNotNull`, `IsFalse`, `IsInstanceOfType`, ...), és
  különböző eredményei lehetnek (`Fail`, `Inconclusive`).
- Lehetőség van a teszteket inicializálni (`TestInitialize`) és takarító
  műveleteket megadni (`TestCleanup`).
- A teszt rendelkezik egy környezettel (`TestContext`), amely segítségével
  lekérdezhetünk információkat.

```csharp
[TestClass] // tesztosztály
public class RationalTest {
    [TestMethod] // tesztművelet a konstruktorra
    public void RationalConstructorTest(){
        Rational actual = new Rational(10, 5);
        Rational target = new Rational(2, 1);
        // az egyszerűsítést teszteljük
        Assert.AreEqual(actual, target);
        // ha a kettő egyezik, akkor eredményes a teszteset
    }
}
```

### Paraméterezett tesztesetek és kivétel-elvárás

- A tesztesetek különböző paraméterezéssel is végrehajthatók a `DataRow`
  attribútum használatával:

```csharp
[TestMethod]
[DataRow(42, "almafa", 10.3)]
[DataRow(10, "valami", 54.21)]
public void SomeTestMethod(int a, string b, double c) {
    // ...
}
```

- Elvárhatjuk azt is, hogy egy teszteset kivételt váltson ki:

```csharp
[TestMethod]
[ExpectedException(
    typeof(IndexOutOfRangeException),
    "Érvénytelen pozíció.")]
public void SomeTestMethod() { /* ... */ }
```

### Példa: Tic-Tac-Toe tesztelése

A Tic-Tac-Toe játék egységtesztjét egy új tesztprojektben
(`TicTacToeGame.Test`) hozzuk létre, amely meghivatkozza a modell
projektet. A tesztosztályban (`TicTacToeModelTest`) ellenőrizzük:

- a konstruktor működését és az üres tábla létrejöttét
  (`TicTacToeConstructorTest`) — ciklussal minden mezőt `Player.NoPlayer`
  értékre vizsgálva,
- léptetés értékbeállításait (`TicTacToeStepGameTest`),
- lépésszám számlálást (`TicTacToeStepNumberTest`),
- játéktábla lekérdezését (`TicTacToeIndexerValidTest`,
  `TicTacToeIndexerInvalidTest`),
- játék vége eseményét és annak paraméterét (`TicTacToeGameWonTest`).

```csharp
[TestClass]
public class TicTacToeModelTest {
    // egységteszt osztály
    [TestMethod]
    public void TicTacToeConstructorTest() {
        // egységteszt művelet
        ...
        for (Int32 i = 0; i < 3; i++)
            for (Int32 j = 0; j < 3; j++)
                Assert.AreEqual(Player.NoPlayer, _model[i, j]);
                // valamennyi mező üres
    }
}
```

Ez az egységteszt a modell projektet önmagában, a nézettől és a
perzisztenciától függetlenül vizsgálja — ez a
[[concepts/esemalk/retegek-szerelvenyekre-bontasa]] szerinti felbontás
egyik közvetlen haszna.

## Kapocs

- [[concepts/esemalk/retegek-szerelvenyekre-bontasa]] — a modell önálló
  szerelvénybe különítése, amely az egységteszteket lehetővé teszi
- [[concepts/esemalk/mock-objektumok]] — függőséggel rendelkező
  programegységek egységtesztelése mock objektumok segítségével
- [[concepts/esemalk/csharp-egysegteszt-keretrendszerek]] — az MSTest
  fogalmainak megfeleltetése NUnit és xUnit keretrendszerekben
- [[subjects/esemalk]]
