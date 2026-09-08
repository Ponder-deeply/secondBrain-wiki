---
tags: [concept]
sources: [Rezolúció_I.pdf]
references: [Tk. 225-227. o.]
derivation: source
updated: 2026-09-08
---

# Ítéletlogikai szemantikus fa

Az ítéletlogikai szemantikus fa egy $S$ klózhalmaz összes lehetséges interpretációját egy fába rendezi; ha a fa **zárt**, akkor $S$ kielégíthetetlen. Ez az elsőrendű szemantikus fa ítéletlogikai, egyszerűbb megfelelője.

## Tartalom

### Klózok illesztése szemantikus fára

Ha az $S$ klózhalmaz összes interpretációját az $S$-ben szereplő összes ítéletváltozó rögzített sorrendje (bázis) alapján előálló szemantikus fával adjuk meg, akkor egy $C$ ítéletlogikai klóz abban az interpretációban hamis, amelyikben a klóz literáljai ellenkező negáltságúak. Egy adott interpretáció (a fa egy ága) kiválasztását — amelyben $C$ hamis — a **$C$ klóz illesztésének** hívjuk a szemantikus fára.

**Példa:** az $X \vee Z$ klóz hamis a $\neg X\,Y\,\neg Z$ és a $\neg X\,\neg Y\,\neg Z$ interpretációkban.

### Zárt szemantikus fa

Ha $S$ minden klóza illeszthető a fa valamely ágára — azaz a fa minden ága lezárható egy hozzá illesztett klózzal —, a szemantikus fát **zártnak** nevezzük. A lezáró csúcsot **cáfoló csúcsnak** ($\bullet$), az afölötti, két lezárt ágat összekötő csúcsot **levezető csúcsnak** ($\circ$) hívjuk.

Példa zárt szemantikus fára: $S = \{Y \vee \neg Z,\ X \vee Z,\ \neg X \vee \neg Y,\ \neg X \vee Z,\ \neg Z\}$ kielégíthetetlen, és bázisa $X, Y, Z$ szerint felépített szemantikus fája minden ágán van illeszthető klóz.

### Tétel

Ha egy $S$ véges klózhalmaz szemantikus fája zárt, akkor $S$ kielégíthetetlen.

A klózhalmaz kielégíthetetlenségének gyakorlati eldöntésére nem a szemantikus fát használjuk — ehelyett a [[concepts/logika/rezolucios-kalkulus]] szolgál —, de a szemantikus fa fontos háttéreszköz marad a rezolúciós kalkulus tulajdonságainak (helyesség, teljesség) vizsgálatában: a teljesség bizonyítása éppen egy tetszőleges zárt szemantikus fából állít elő rezolúciós cáfolatot.

### Viszonya az elsőrendű szemantikus fához

Az [[concepts/logika/elsorendu-szemantikus-fa]] ugyanezt az ötletet — az interpretációk fába rendezését — általánosítja: ott a fa szintjei nem ítéletváltozóknak, hanem egy rögzített véges $U$ univerzum feletti **alapatomoknak** felelnek meg, és a bázis is alapatomokból áll. Az ítéletlogikai szemantikus fa tehát az elsőrendű eset speciális esete, amikor minden "alapatom" egyszerűen egy ítéletváltozó.

## Kapocs

- [[concepts/logika/kloz-es-klozhalmaz]] — a klóz és klózhalmaz fogalma, amire a fa épül
- [[concepts/logika/rezolucios-kalkulus]] — a gyakorlatban használt döntési eljárás; a teljesség bizonyítása a zárt szemantikus fából indul ki
- [[concepts/logika/elsorendu-szemantikus-fa]] — az elsőrendű általánosítás, alapatom-bázissal
- [[concepts/logika/szemantikus-tulajdonsagok]] — kielégíthetőség, kielégíthetetlenség fogalma
