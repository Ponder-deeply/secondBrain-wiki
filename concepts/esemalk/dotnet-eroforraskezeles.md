---
tags: [concept]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# .NET erőforrások kezelése

A programban felhasznált erőforrásokat (képek, hangok, …) célszerű a
projekthez rögzíteni, ahelyett hogy futás közben, elszórt fájlokból töltenénk
be őket.

## Tartalom

Bármilyen fájl hozzáadható a projekthez, két módon:

- **tartalomként** (*content*) — a fájl átmásolható a kimeneti könyvtárba, az
  elem tulajdonságainak megfelelő beállításával
- **beágyazott erőforrásként** (*embedded resource*) — a fájl az
  alkalmazásba (a végrehajtható fájlba) épül be

Az erőforrásfájlok (*resource file*, `.resx`) lehetővé teszik az erőforrások
(szöveg, kép, ikon) csoportos kezelését és programkódban történő elérését; az
így hozzáadott erőforrások is beágyazottan helyezkednek el az alkalmazásban.
Például egy `MyResource.resx` fájl hozzáadásával a tartalmak a
`MyResource.ResourceManager` útvonalon érhetők el a kódból.

## Kapocs

- [[concepts/esemalk/winforms-kepek-megjelenitese]] — a projekthez rögzített
  képek tipikus felhasználási módja
- [[concepts/esemalk/dotnet-fajlrendszer-kezeles]] — futásidőben, a
  fájlrendszerből (nem a projektbe ágyazva) betöltött fájlok kezelése
- [[concepts/esemalk/dotnet-lokalizacio-kulturak]] — az erőforrásfájlok
  kultúra-specifikus (lokalizációs) felhasználása
