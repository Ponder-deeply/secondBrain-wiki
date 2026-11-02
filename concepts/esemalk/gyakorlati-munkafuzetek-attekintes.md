---
tags: [concept]
sources: [elte_eva_gy00_munkafuzet.pdf, elte_eva_gy01_munkafuzet.pdf, elte_eva_gy02_munkafuzet.pdf, elte_eva_gy03_munkafuzet.pdf, elte_eva_gy04_munkafuzet.pdf, elte_eva_gy05_munkafuzet.pdf, elte_eva_gy06_munkafuzet.pdf, elte_eva_gy07_munkafuzet.pdf, elte_eva_gy08_munkafuzet.pdf]
derivation: source
kind: overview
element: earth
updated: 2026-10-21
---

# Gyakorlati munkafüzetek (0–8. gyakorlat) áttekintése

A gyakorlatok munkafüzetei lépésről lépésre vezetnek végig egy-egy alkalmazáson; a 0.–6. gyakorlatot egyetlen, fokozatosan bővülő alkalmazás (DocuStat) köti össze, a 7.–8. gyakorlat WPF-es képletöltő. A munkafüzetek szekciói jelölést (KM, EM, OP) viselnek; a jelölések jelentését a források nem magyarázzák.

## Tartalom

| Gyakorlat | Téma | Lap |
|---|---|---|
| 0. | konzolos tombola hibakeresése | lásd alább |
| 1. | konzolos szövegstatisztika, LINQ, fájlkezelés | [[concepts/esemalk/docustat-modell-szovegstatisztika]] |
| 2. | első WinForms alkalmazások, időzítés, egyedi vezérlő | [[concepts/esemalk/winforms-gombvadaszat-digitalis-orak]] |
| 3. | modell-nézet, események, grafikus DocuStat | [[concepts/esemalk/docustat-winforms-nezet-esemenyek]] |
| 4. | háromrétegű architektúra, perzisztencia, factory, DI | [[concepts/esemalk/docustat-perzisztencia-filemanager]], [[concepts/esemalk/ioc-tarolo-servicecollection]] |
| 5. | egységtesztelés: MSTest, Moq, xUnit | [[concepts/esemalk/docustat-egysegtesztek]] |
| 6. | több lap, aszinkron betöltés, haladásjelzés | [[concepts/esemalk/docustat-tobbfajlos-aszinkron-betoltes]], [[concepts/esemalk/filesystemwatcher-fajlvaltozas-figyeles]] |
| 7. | WPF képletöltő, kétrétegű | [[concepts/esemalk/wpf-kepletolto-modell-nezet]] |
| 8. | WPF képletöltő MVVM-ben | [[concepts/esemalk/wpf-kepletolto-mvvm]] |

### 0. gyakorlat: tombola hibakeresés

A munkafüzethez mellékelt konzolos tombola sorsoló alkalmazás több futási idejű hibát tartalmaz; a feladat ezek megkeresése és kijavítása. Parancsok: `new` (új játék a szelvények számával), `reset` (az utolsó játék újraindítása), `draw` (következő szelvény kihúzása), `check` (egy szelvény kihúzásának ellenőrzése), `quit`. A helyes alkalmazás hibatűrő (hiba esetén nem omlik össze) és bolondbiztos (kezeli a hibás bevitelt).

Tippek a hibákhoz (a klasszikus futási idejű hibák listája):
- más művelet új játék indítása nélkül — van-e fordítási figyelmeztetés (*warning*), amely erre utal?
- az összes szelvény kihúzása után még egy húzás;
- újraindított játék kihúzása az összes szelvény elfogyásáig;
- azonnali kilépés indítás után;
- nem létező (túl kicsi vagy túl nagy) szelvény ellenőrzése.

Kapcsolódó elv: a fordítói figyelmeztetések komolyan veendők, lásd [[concepts/esemalk/beadando-statikus-analizis]] és [[concepts/esemalk/csharp-nullable-tipusok]].

### A DocuStat fejlődése

1. konzolos modell (`DocumentStatistics`) $\to$ 3. WinForms nézet, modell-események $\to$ 4. perzisztencia leválasztása `IFileManager` mögé $\to$ 5. tesztek $\to$ 6. aszinkron, több fájl.
A fejlődés végig a modell/nézet szétválasztásra épül: a modell nem kezeli a konzolt vagy a felületet, így minden lépésben újrahasználható.

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — az architektúra, amelyet a gyakorlatok építenek
- [[concepts/esemalk/zh-mintafeladatok]] — a gyakorlatok után a géptermi zárthelyi mintái
- [[subjects/esemalk]]
