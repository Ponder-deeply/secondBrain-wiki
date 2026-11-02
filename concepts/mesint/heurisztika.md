---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-12
---

# Heurisztika

A heurisztika a feladathoz kapcsolódó ötlet, amelyet közvetlenül beépítünk a keresőrendszer algoritmusába, hogy javuljon az eredményessége és a hatékonysága; garanciát azonban általában nem ad.

## Tartalom

### Mi a heurisztika

- Olyan, a feladathoz kapcsolódó **ötlet**, amelyet **közvetlenül beépítünk** az algoritmusba (a keresőrendszer vezérlésébe, ld. [[concepts/mesint/kereso-rendszer]]).
- Célja kettős: az **eredményesség** (megtaláljuk-e a megoldást) és a **hatékonyság** javítása. A hatékonyság két összetevője a **futási idő** és a **memóriaigény**; a heurisztika egyszerre képes mindkettőt javítani.
- **Nem ad garanciát**: egy rossz heurisztika félrevezethet, a jó is csak átlagosan segít.

### A heurisztika és a keresőrendszer hatékonysága

A keresőrendszer ciklusa: `ADAT := kezdeti érték; while ¬terminálási feltétel(ADAT) loop SELECT SZ FROM alkalmazható szabályok; ADAT := SZ(ADAT)`. Az **informáltság** (mennyi feladatspecifikus tudást használ a szabályválasztás) növelésével két költség mozog ellentétesen (Nilsson, *Principles of AI*, 54. o. alapján):

- a **szabályalkalmazások száma** (iterációk száma) csökken, mert a vezérlés jobban célba talál;
- **egy szabály kiválasztásának költsége** (egy iterációs lépés ára) nő, mert a jobb döntés több számítást igényel.

Az **eredő számítási költség** a kettő eredője: U alakú, a minimuma közbülső informáltságnál van. Teljes informáltság (a dőlt szaggatott vonal) elvben nem kell: túl drága lépésenként a tökéletes döntés. A cél tehát nem a lehető legjobb heurisztika, hanem a legjobb *ár/érték arányú*.

### Heurisztika lokális keresésnél

- Lokális kereséssel ([[concepts/mesint/hegymaszo-modszer]], [[concepts/mesint/tabu-kereses]], [[concepts/mesint/szimulalt-hutes]]) csak akkor oldható meg a feladat, ha egy lokálisan hozott rossz döntés **nem zárja ki a cél megtalálását**. Ez erősen összefüggő reprezentációs gráfban automatikusan teljesül, de kifejezetten előnytelen, ha a gráf irányított fa. (Az $n$-királynő problémát csak tökéletes kiértékelő függvénnyel lehetne lokális kereséssel megoldani, ld. [[concepts/mesint/n-kiralyno-problema]].)
- **Erős heurisztika nélkül nincs sok esély** a cél megtalálására; a jó heurisztikára épített kiértékelő függvénnyel elkerülhetők a zsákutcák és a körök.
- Gráfszínezésnél a kiértékelő függvény: $f(n)=\sum_j w_j(\lambda\,|A(O_j)|-|O_j|)$, ahol $A(O_j)$ az $O_j$ osztálybeli élek halmaza és a $w_j>0$ súlyok szigorúan növő sorozatot alkotnak; minél több csúcs van az első néhány osztályban és minél kevesebb osztályon belüli él, annál jobb az osztályozás (ld. [[concepts/mesint/grafszinezes]]).

### Példák heurisztikákra

- [[concepts/mesint/tologato-jatek]]: rossz helyen levő lapkák száma, Manhattan-távolság, keret ([[concepts/mesint/modellfuggo-vezerles]]).
- [[concepts/mesint/hanoi-tornyai]]: darab, súlyozott darab, összeg, súlyozott összeg, módosított összeg.
- [[concepts/mesint/fekete-feher-kirako]]: inverziószám, módosított inverziószám.

## Kapocs

- [[concepts/mesint/kereso-rendszer]] — a heurisztika a keresőrendszer vezérlésébe épül be
- [[concepts/mesint/vezerlesi-strategiak]] — a heurisztika a vezérlési stratégia döntéseit informálja
- [[concepts/mesint/modellfuggo-vezerles]] — a modellfüggő vezérlés a heurisztikát a feladatmodell szerkezetéből nyeri
- [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]] — ugyanez a gondolat gráfkeresésnél
- [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]] — a heurisztikus függvény formális tulajdonságai
