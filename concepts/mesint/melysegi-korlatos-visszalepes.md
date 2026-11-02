---
tags: [concept]
sources: [04.visszalep.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-12
---

# Mélységi korlátos visszalépés (VL2)

A visszalépéses keresés (VL2) változata, amely a körfigyelés helyett az útvonal hosszát korlátozza egy mélységi korláttal ($MK$). A korlát ellenőrzése önmagában biztosítja a terminálást.

## Tartalom

### A mélységi korlát szerepe

- A **mélységi korlát ellenőrzése önmagában is biztosítja a terminálást**, körfigyelés nélkül: az aktuális út hossza nem nőhet $MK$ fölé, így a keresés nem futhat végtelen ágon.
- Ilyenkor a rekurzív hívásnál **nem kell a teljes aktuális utat átadni**; elég
  - az aktuális csúcs,
  - annak szülője (a kettő hosszú körök kiszűréséhez),
  - és az aktuális út hossza.
- Hatékonyság:
  - nem kell utakat tárolni, így csökken a memóriaigény;
  - nincs körfigyelés, így egy lépés futási ideje csökken;
  - viszont ha a reprezentációs gráfban a mélységi korlátnál rövidebb körök is vannak, a **lépések száma nő** (ugyanazokat az állapotokat többször is bejárhatja).
- A VL2 a mélységi korlátnál **hosszabb megoldási utat nem találja meg**. Ha nincs a korlátnál rövidebb megoldás, a keresés sikertelenül terminál.

### Vágó heurisztika

A heurisztikus függvény ($h$) a mélységi korláttal együtt vágásra is használható: ha

$$\text{aktuális út hossza} + h(\text{csúcs}) > MK,$$

akkor az adott csúcsból a korláton belül már nem érhető el cél (feltéve, hogy $h$ nem becsüli túl a hátralévő költséget), ezért az ág levágható, a keresés visszalép.

### Példa: tologatós játék, $MK = 5$

A [[concepts/mesint/tologato-jatek]] kiindulóállapotából, mélységi korlát 5 mellett két heurisztikával fut a keresés (a csúcsok mellett a heurisztikus érték áll; a sorrendi heurisztika a legkisebb értékű gyereket veszi előre, lásd [[concepts/mesint/sorrendi-heurisztikak]]):

- **$W$ (rossz helyen lévő lapkák száma):** a kezdőállapot értéke 4. A keresés a legkisebb értékű gyereket választja, a bejárási sorrend 0–11. Két mélyebb csúcsot a vágó heurisztika (út hossza + $W$ > $MK$) levág, ilyenkor a keresés visszalép, és a szomszéd ágon folytatja; a megoldást a 11. lépésben találja meg.
- **$P$ (a lapkák célhelytől való Manhattan-távolságainak összege):** a kezdőérték 5, a heurisztika pontosabb, ezért a keresés visszalépés nélkül, egyenesen halad a célba (0–5. lépés).

A két ábra azt mutatja, hogy a jobb (informáltabb) heurisztika kevesebb visszalépést okoz.

### Szemléltetés: Hanoi tornyai

A [[concepts/mesint/hanoi-tornyai]] állapotgráfján (Sierpinski-háromszög szerkezet) a visszalépéses keresés lépésről lépésre követhető: 4 korongnál, összegző ($Sum$) heurisztikával, 20-as mélységi korláttal a program 252 lépés alatt ér célba, a bejárt ág piros, a visszalépéssel elhagyott részek halványabbak.

## Kapocs

- [[concepts/mesint/visszalepeses-kereses]] — az alapváltozat, amelyhez a mélységi korlát a körfigyelés alternatívája
- [[concepts/mesint/visszalepes-feltetelei]] — mikor lép vissza a keresés (a mélységi korlát elérése is ilyen feltétel)
- [[concepts/mesint/sorrendi-heurisztikak]] — a gyerekek sorrendjének heurisztikus megválasztása
- [[concepts/mesint/visszalepeses-kereses-ertekelese]] — az eljárás előnyei és hátrányai
- [[concepts/mesint/tologato-jatek]] — a példa problémája
- [[concepts/mesint/hanoi-tornyai]] — a szemléltető probléma
