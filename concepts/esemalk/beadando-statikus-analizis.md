---
tags: [concept]
sources: [elte_eva_beadando_kodminoseg.pdf, elte_eva_beadando_kodminoseg_fuggelek.pdf]
derivation: source
kind: overview
element: earth
updated: 2026-10-21
---

# Beadandók kódminősége: statikus és architektúra-analízis

A beadott megoldások nem tartalmazhatnak fordítási hibát, és a fordító vagy a megadott statikus analízis szabályrendszer (`ELTE.FI.SARuleset`) által generált figyelmeztetést (*warning*) sem; a TMS a feltöltés után automatikusan ellenőrzi ezt, valamint az architektúra (MV, MVVM) betartását is.

## Tartalom

### Használat

- A *Solution Explorerben* a solution-re kattintva a *Manage NuGet Packages* menüből kell telepíteni az `ELTE.FI.SARuleset` csomagot, **minden projekthez** (újabb projekt felvételekor a telepítést meg kell ismételni).
- A szabályok a fordítás (*Build*) során automatikusan lefutnak.
- A `suggestion` súlyosságú jelzések még megengedettek, de célszerű megvizsgálni őket; a `warning` jelzések nem.
- A TMS ellenőrzése hosszabb időt vehet igénybe; a hibák listája a webes felületen is megtekinthető.

### A szabályok kilenc kategóriája

1. **Nullable típusok** — a `nullable` referenciatípusokhoz kapcsolódó fordítói jelzések javítása elvárt, így a futási idejű `NullReferenceException` már íráskor elkerülhető (pl. `S1696`, `S2259`, `S3655`). Lásd [[concepts/esemalk/csharp-nullable-tipusok]].
2. **Konvenciók** — a megoldás helyes, de nem követi a C# konvenciókat: publikus mező helyett *property* (`CA1024`, `S1104`), típusok névterekben (`CA1050`, `S3903`), `Equals`/`GetHashCode` párban (`S1206`); az elnevezési ajánlások (PascalCase, `S100`, `S101`, megfelelő utótag `CA1710`) csak javasoltak.
3. **Helytelen értékadások** — komolyabb hibák: egész-osztás lebegőpontos környezetben (`S2184`), `=` és `==` felcserélése, változó önmagának értékadása (`S1656`), mellékhatás nélküli függvény visszatérési értékének eldobása (`S2201`), azonos kifejezés a bináris operátor két oldalán (`S1764`, pl. `2 == 2`).
4. **Teljesítmény és erőforrás-kezelés** — a `string` módosíthatatlan, ezért ciklusban `StringBuilder` javasolt (`S1643`); `IDisposable` erőforrásokat (`using`) fel kell szabadítani és felszabadítás után nem szabad használni (`S2930`, `S2931`, `CA1001`). Lásd [[concepts/esemalk/idisposable-eroforras-felszabaditasa]].
5. **Feltételes vezérlés, ciklusok, rekurzió** — végtelen rekurzió (`S2190`), rossz irányba mozgó ciklusszámláló (`S2251`), elérhetetlen kód, korai `return`/`break`, ismétlődő `if-else`/`switch` ágak (`S1862`, `S1871`, `S3923`). Idetartozik a polimorfizmus: csak a `virtual` tag definiálható felül az `override` kulcsszóval; ennek hiányában a tag csak elrejtődik, és a polimorfizmus nem a várt módon működik — szándékos elrejtést a `new` kulcsszó jelöl.
6. **Polimorfizmus és öröklődés** — ősosztály metódusainak ne legyen szándékos elfedése (`CA1061`), virtuális eljárás ne fusson a konstruktorban (`CA2214`); az `Equals()` felüldefiniálásakor kötelező a `GetHashCode()` is. Lásd [[concepts/esemalk/csharp-oroklodes]].
7. **Aszinkron programozás** — az aszinkron műveleteket be kell várni, hogy az objektumok belső állapota konzisztens maradjon; visszatérési érték nélküli aszinkron metódus is `Task`-ot adjon `void` helyett (`S3168`), mert a `void` metódus nem várható be és a kivétele nem kezelhető a hívás helyén. Kivétel az eseménykezelő (WinForms, WPF), ahol a `void` kompatibilitási okból kell. Lásd [[concepts/esemalk/csharp-async-await]].
8. **Delegáltak és események** — `EventArgs.Empty` használata (`RCS1204`), delegáltak kivonásának és névtelen delegáltak leiratkozásra használatának tilalma (`S3172`, `S3244`). Lásd [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]].
9. **Egyéb** — pl. ismétlődő `enum` értékek (`CA1069`), üres `catch` a `System.Exception`-re (`RCS1075`), a `Stream` olvasás hosszának ellenőrzése (`S2674`).

A függelék minden szabályt azonosítóval (`CAxxxx`, `Sxxxx`, `RCSxxxx`), címmel és súlyossággal (`warning` vagy `suggestion`) sorol fel; a kategóriák mintájára vannak csoportosítva.

### Architektúra-analízis (`ARCH` kódok)

A TMS a forráskód statikus elemzésére építve automatikusan ellenőrzi az **MV** és **MVVM** architektúra, valamint az alapvető objektumorientált elvek lehetséges megsértését. A hibajelzések `ARCH` előtaggal kezdődnek (mind `suggestion` súlyosságú):

| Kód | Jelentés |
|---|---|
| `ARCH1000` | a típus rétege nem azonosítható — a réteg nevét érdemes a névtér nevébe írni |
| `ARCH1001` | következetlen rétegazonosítás |
| `ARCH1002` | hiányzó, az architektúrához szükséges réteg |
| `ARCH1003` | a rétegek függőségi sorrendje hibás |
| `ARCH1004` | csak szomszédos rétegek kommunikáljanak metódushívással |
| `ARCH1005` | az eseményt a megfelelő rétegben kell kezelni |
| `ARCH1006`, `ARCH1007` | az objektum megsérti az egységbezárást és kiszivárogtatja belső reprezentációját |
| `ARCH1008` | absztrakciótól (interfésztől) függjünk, ne konkrét megvalósítástól |
| `ARCH1009` | az eseményeket a nézetmodell rétegben kell kezelni |

Helyi futtatás: `dotnet tool install --global ELTE.FI.ArchitecturalAnalyzer`, majd `ArchitecturalAnalyzer analyze /path/to/solution.sln --architecture MV --detailed` (MVVM esetén `--architecture MVVM`). Frissítés ugyanazzal a telepítő paranccsal. Az eszköz fejlesztés alatt álló prototípus, ezért *false positive* jelzéseket is adhat.

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — az MV architektúra, amelynek megsértését az `ARCH` szabályok jelzik
- [[concepts/esemalk/wpf-mvvm-alapok]] — az MVVM architektúra rétegei és adatáramlása
- [[concepts/esemalk/beadando-dokumentacio-sudoku-minta]] — a beadandó dokumentáció és a követelmények mintája
- [[concepts/esemalk/fuggoseg-befecskendezes]] — absztrakciótól függés (`ARCH1008`)
- [[subjects/esemalk]]
