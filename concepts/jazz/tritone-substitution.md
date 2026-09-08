---
tags: [concept]
sources: []
derivation: unsourced
updated: 2026-08-05
---

# Tritone substitution

Bármely domináns szeptim helyettesíthető azzal a domináns szeptimmel, amelynek alaphangja tritonusz-távolságra van tőle. Az elv alapja, hogy a két akkord ugyanazt a tritonuszt tartalmazza, csak fordított szereposztásban. Jelölése subV7 (vagy subV7/x, ha a helyettesített akkord másodlagos domináns volt).

## Az elv: a közös tritonusz

G7 hangjai: G – B – F. A feszültséget a B (3) és az F (b7) közötti tritonusz adja.

Db7 hangjai: Db – F – Cb (= B). Ebben az F a 3 és a B a b7.

A két akkord tehát ugyanazon a tritonuszon osztozik, csak a 3 és a 7 szerepet cserél. Mivel a domináns funkciót lényegében a tritonusz hordozza, a két akkord ugyanoda tud oldódni:

- G7 → Cmaj7: B (3) felfelé C-re, F (b7) lefelé E-re
- Db7 → Cmaj7: F (3) lefelé E-re, B (b7) felfelé C-re

Ugyanaz a két félhangos oldás, ellentétes szerepekben.

A tritonusz szimmetrikus, ezért a hat lehetséges tritonusz mindegyike pontosan két domináns szeptimet szolgál ki. A tizenkét domináns hat párba rendeződik:

| Pár | Pár | Pár | Pár | Pár | Pár |
|---|---|---|---|---|---|
| C7 – F#7 | Db7 – G7 | D7 – Ab7 | Eb7 – A7 | E7 – Bb7 | F7 – B7 |

## Jelölés és fokszám

C-dúrban a G7 helyettesítője Db7, ami a bII. fok — innen a szokásos elemzési jelölés: **subV7** vagy **bII7**. Ha egy másodlagos dominánst helyettesítünk, a jelölés megőrzi a célt: A7 = V7/ii, helyettesítője Eb7 = subV7/ii.

## A kromatikus basszusmenet

A helyettesítés fő gyakorlati haszna: a kvintlépéses basszus félhangos lépéssé alakul.

C-dúrban:

| Eredeti | Basszus | Helyettesítve | Basszus |
|---|---|---|---|
| Dm7 – G7 – Cmaj7 | D – G – C | Dm7 – Db7 – Cmaj7 | D – Db – C |

A ii–V–I-ből ereszkedő kromatikus vonal lesz. Hosszabb menetekben ez folytonos kromatikát ad, lásd [[concepts/jazz/extended-dominant|extended-dominant]].

A ii fok is helyettesíthető együtt a V-tel („kettős sub"): Abm7 – Db7 – Cmaj7, ahol az Abm7 a Db7 related ii-je. Ekkor az egész ii–V modul félhanggal feljebb kerül, és onnan lép le a tonikára.

## Chord-scale: lydian dominant

A subV7 alapértelmezett skálája a **lydian dominant** (a melodikus moll 4. módusa): 1 2 3 #4 5 6 b7.

Db lydian dominant: Db – Eb – F – G – Ab – Bb – Cb.

Miért ez: a Db7 fölött a természetes 4 (Gb) avoid note lenne, a #11 (G) viszont éppen a helyettesített G7 alaphangja, és diatonikusan illeszkedik a célhangnembe. Sőt a Db lydian dominant hangkészlete jórészt egybeesik a G altered skáláéval — ugyanaz az Ab melodikus moll két módusa. Ezért a tritone sub és az alterált domináns hangzásban közel áll egymáshoz; a különbség a basszusban van.

| Akkord | Skála | Forrás |
|---|---|---|
| G7alt | G altered | Ab melodikus moll 7. módusa |
| Db7#11 | Db lydian dominant | Ab melodikus moll 4. módusa |

Ez a rokonság ad gyakorlati fogást: aki G7 fölött altered skálát játszik, hangkészletben ugyanazt teszi, mintha Db7-re gondolna. Alternatívák: Db mixolydian (ha egyszerűbb szín kell), Db HW diminished (sűrűbb kromatika).

## Mikor működik és mikor nem

**Működik**, ha:

- a helyettesített akkord valóban domináns funkciójú és lefelé kvintbe old
- a dallam hangjai megférnek a subV7 fölött; a leggyakoribb ütközés, hogy a dallamban ott áll az eredeti domináns 5-e vagy 9-e, ami a subV7 fölött b9 vagy szűk hangköz lesz
- a kromatikus basszusmenet kívánatos, vagy a menet elszíneződését keressük

**Nem működik jól**, ha:

- az akkord nem oldódik tovább, hanem statikus domináns felület (pl. blues I. foka) — ekkor a helyettesítés csak elrontja a tonikaérzetet
- sus akkordot helyettesítenénk: a sus4 nem tartalmaz tercet, tehát tritonusza sincs, így a csere alapja hiányzik
- a dallam a domináns alaphangját vagy kvintjét tartja hosszan (G7 fölött G vagy D): a Db7 fölött ezek #11 és b9 lesznek, ami erős súrlódás — nem hiba, de tudatos döntést kíván
- a basszus más irányba mozogna a formában, és a kromatikus lépés a formai tagolást elmossa

**Fordított irányban** is használható: egy leírt bII7-et visszaértelmezhetünk V7-nek, és az arra illő ii–V-vel bővíthetjük ki. Ez a reharmonizáció visszabontó lépése.

## Kapocs

- [[concepts/jazz/ii-v-i-durban]] — a sub leggyakoribb környezete
- [[concepts/jazz/secondary-dominant]] — a subV7/x jelölés alapja
- [[concepts/jazz/extended-dominant]] — kromatikus dominánsláncok
- [[concepts/jazz/alteraciok]] — az altered és a lydian dominant tension-készlete
- [[concepts/jazz/melodic-minor-modusai]] — mindkét skála forrása
- [[concepts/jazz/reharmonizacio]] — a sub helye a technikák rendszerében
- [[concepts/jazz/turnaround]] — tritonuszos turnaroundok
