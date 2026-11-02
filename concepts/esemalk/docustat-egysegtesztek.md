---
tags: [concept]
sources: [elte_eva_gy05_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
---

# DocuStat egységtesztjei: MSTest, Moq és xUnit

Az 5. gyakorlat a `DocumentStatistics` modellt egységteszteli: a fájlbetöltést `Moq`-kal mockolja, a teszteket MSTest-tel, majd xUnit-tal is megvalósítja.

## Tartalom

### MSTest projekt

- Új *MSTest* teszt projekt (`DocuStatTest`) a solutionben, projekt referencia a `DocuStat`-ra; a tesztosztály `[TestClass]`, a tesztek `[TestMethod]` attribútumúak; futtatás: jobb klikk → *Run test*, ill. *Test Explorer*.
- Ellenőrzés az `Assert` osztály statikus függvényeivel; sikertelen vizsgálatnál `AssertFailedException` keletkezik, a teszt elbukik.
- Elvárt kivétel: `Assert.ThrowsExactly<T>(() => _docStats.Load())` (aszinkron esetben `await Assert.ThrowsExactlyAsync<T>()`).
- Gyűjtemények összehasonlítására `CollectionAssert`: `AreEqual` a sorrendet is számon kéri, `AreEquivalent` csak a tartalmat.
- `[TestInitialize]` minden teszt előtt, `[TestCleanup]` minden teszt után fut (a mellékhatásos tesztek elszigetelésére).

```csharp
private Mock<IFileManager> _mock = null!;
private DocumentStatistics _docStats = null!;
[TestInitialize]
public void InitDocuStatTest()
{
    _mock = new Mock<IFileManager>();
    _docStats = new DocumentStatistics(_mock.Object);
}
// viselkedés felülírása:
_mock.Setup(m => m.Load()).Returns("test");
```

Lásd [[concepts/esemalk/mock-objektumok]], [[concepts/esemalk/egysegtesztek-mstest]].

### Tesztesetek (egyszerűtől a bonyolultig)

A teszteket érdemes az egyszerű esettől haladva felépíteni (ha az egyszerű sem működik, a bonyolultabb sem fog), a metódusnév utaljon a tesztelt működésre.

- **Fájlbetöltés**: a `FileContent` a mockolt stringet tartalmazza; a mock kivételt dob (`Throws`); a `FileContentReady` és `TextStatisticsReady` események kiváltása — utóbbinál a kezelőben kapott `TextStatisticsReadyEventArgs`-t elmentjük, és ellenőrizzük, hogy a metrikák megegyeznek a modell tulajdonságaival.
- **`DistinctWordCount`**: üres szöveg; csak nem betű karakterekből álló szavak; ismétlődő szó; ismétlődés nem betű karakterekkel; kis- és nagybetűs ismétlődés; több különböző szó.
- **Szűrő** — `FilteredWordCountChanged` kiváltása: mindhárom szűrő beállítása kiváltja; ugyanarra az értékre ismételt beállítás nem (az `IgnoredWords`-nél a normalizálás miatt `" HELLO "` a `"hello"` után változatlan); az `IgnoredWords` normalizáltan olvasható vissza; a betöltés is kiváltja (a szóstatisztika újraépül). Az eseményszámlálás: `_docStats.FilteredWordCountChanged += (sender, args) => ++raised;`. A `FilteredWordCount` tartalma: csökkenő sorrend, a `MinWordLength`, `MinWordOccurrence`, `IgnoredWords` szűrése.
- **Számlálók**: `CharacterCount`, `NonWhiteSpaceCharacterCount`, `SentenceCount`, `ProperNounCount` általános és üres/whitespace bemenetre; `ColemanLiauIndex` és `FleschReadingEase` többmondatos és egymondatos (ill. magánhangzó nélküli) szövegre.

### xUnit különbségek az MSTest-hez képest

1. MSTest-ben csoportos futtatásnál a tesztosztályból egyetlen példány készül; xUnit-ban **minden tesztesethez külön objektum** — a konstruktor minden teszt előtt lefut.
2. A takarítás az `IDisposable.Dispose()` megvalósításával történik.
3. A teszt metódus `[Fact]`, a paraméterezett `[Theory]`.
4. Az `Assert` osztály függvényei más nevűek (`Equal` az `AreEqual` helyett, `True` az `IsTrue` helyett); külön vizsgálat van egy elemű és üres gyűjteményre (`Assert.Single`, `Assert.Empty`).

Lásd [[concepts/esemalk/csharp-egysegteszt-keretrendszerek]].

## Kapocs

- [[concepts/esemalk/docustat-perzisztencia-filemanager]] — az `IFileManager`, amelyet a teszt mockol
- [[concepts/esemalk/docustat-winforms-nezet-esemenyek]] — az események, amelyeket a tesztek ellenőriznek
- [[concepts/esemalk/docustat-modell-szovegstatisztika]] — a tesztelt modell
- [[concepts/esemalk/filesystemwatcher-fajlvaltozas-figyeles]] — a mockolt interfész események kiváltása (`Raise`)
- [[subjects/esemalk]]
