---
tags: [concept]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf, elte_eva_gy05_munkafuzet.pdf]
derivation: source
kind: comparison
element: air
updated: 2026-10-21
---

# MSTest, NUnit, xUnit egységteszt-keretrendszerek

A Visual Studio 2022 három egységteszt-keretrendszert támogat natívan a
.NET-hez: az *MSTest*-et, az *NUnit*-ot és az *xUnit*-ot; mindhárom
platformfüggetlen, és attribútumokkal jelölik a tesztosztályokat, teszteseteket
és az élettartam-kezelő metódusokat.

## Tartalom

A három keretrendszer fogalmai megfeleltethetők egymásnak:

| MSTest | NUnit | xUnit | Jelentés |
|---|---|---|---|
| `[TestClass]` | `[TestFixture]` | *n/a* | Teszt osztály. |
| `[TestMethod]` | `[Test]` | `[Fact]` | Teszteset (metódus). |
| `[TestInitialize]` | `[SetUp]` | *ctor* | Tesztesetek inicializálása. |
| `[TestCleanup]` | `[TearDown]` | `IDisposable` | Tesztesetek takarítása. |
| `[DataRow]` | `[TestCase]` / `[Values]` | `[Theory]` / `[InlineData]` | Tesztesetek paraméterezése. |
| `[ExpectedException]` | `Assert.Throws` | `Assert.Throws` | Kivétel elvárása. |

Fontos különbség, hogy xUnit-ban nincs külön inicializáló attribútum: a
tesztosztály konstruktora játssza ezt a szerepet, a takarítást pedig az
`IDisposable` interfész `Dispose` metódusa végzi el (egy új tesztosztály-
példány jön létre minden egyes teszteset előtt).

Az 5. gyakorlat további xUnit-különbségeket is kiemel: az `Assert` függvényei másképp hívhatók (`Equal` az `AreEqual`, `True` az `IsTrue` helyett), külön vizsgálat van az egy elemű és az üres gyűjteményre (`Assert.Single`, `Assert.Empty`), a paraméterezett teszt a `[Theory]`. Lásd [[concepts/esemalk/docustat-egysegtesztek]].

**Példa (TicTacToe):** a korábbi, `MSTest` alapú `TicTacToeGame.Test` projekt
mellett készíthető `TicTacToeGame.Test.NUnit` és `TicTacToeGame.Test.xUnit`
projekt is ugyanahhoz a játékhoz — a tesztesetek logikája azonos, csak az
attribútumok és az életciklus-kezelés tér el keretrendszerenként. Mindhárom
projektben az adatelérést (a mentés/betöltés perzisztenciarétegét) a Moq
könyvtárral szimulálják: egy `Mock<IPersistence>` objektumot állítanak be
(`Setup`/`Returns`), amit a modellnek átadva a teszt nem függ ténylegesen a
fájlrendszertől, és a `Verify` hívással azt is ellenőrizhető, hogy a modell
valóban meghívta-e a várt műveletet a várt paraméterekkel (pl.
`_mock.Verify(mock => mock.Load(String.Empty), Times.Once())`).

## Kapocs

- [[subjects/esemalk]] — a kurzus áttekintése
- [[concepts/esemalk/csharp-megjegyzesek]] — a tesztkeretrendszerek attribútumai
  (`[TestClass]`, `[TestMethod]`, ...) a C# attribútum mechanizmusára épülnek
