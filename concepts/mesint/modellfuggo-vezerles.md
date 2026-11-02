---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Modellfüggő vezérlés és heurisztikák a 8-as tologatóra és a Hanoi tornyaira

A modellfüggő vezérlés a keresőrendszer vezérlését a feladat modelljéhez (állapottér, műveletek) köti: a műveletek kipróbálásának sorrendje rögzített, a választást pedig a modellre szabott kiértékelő függvény dönti el.

## Tartalom

### Modellfüggő vezérlés

A hegymászó módszer ([[concepts/mesint/hegymaszo-modszer]]) tologatós példájában a vezérlés **modellfüggő**: a **műveletek rögzített sorrendben** szerepelnek (*left, up, right, down*, az üres hely mozgatása). A rendszer minden lépésben kiértékeli az alkalmazható műveletek következő állapotait, és a legkisebb heurisztikus értékű szomszédra lép. Egyenlő értékeknél a rögzített sorrend dönt (az előbb szereplő művelet nyer), ezért ugyanaz a heurisztika más műveletsorrenddel más utat adhat. Ez a vezérlés a modellre épül, nem általános (modellfüggetlen) szabály.

### Heurisztikák a 8-as (15-ös) tologató játékra

A cél: `1 2 3 / 8 _ 4 / 7 6 5`. A kiértékelés a kezdőállapotra (`2 8 3 / 1 6 4 / 7 _ 5`):

| Jel | Név | Definíció | Érték a kezdőállapotra |
|---|---|---|---|
| $W$ | Rossz helyen levő lapkák száma | a nem a célbeli helyükön álló lapkák száma | 4 |
| $P$ | Manhattan | a lapkák célbeli helyüktől mért minimális távolságainak (függőleges + vízszintes lépések) összege | 5 |
| $F$ | Keret | büntetőpontok: +1 minden olyan szélső lapkára, amelyet nem a célbeli szomszédja követ az óra járásával megegyező irányban; +2 minden sarokra, ahol nem a cél szerinti lapka áll | 6 |

Mindhárom a céltól való "távolság" becslése: 0 pontosan a célállapotban.

### Hegymászó módszer a három heurisztikával

Ugyanarról a kezdőállapotról indulva, rögzített `l, u, r, d` sorrenddel:

- **$W$**: az értékek $4,3,3,3,3,3,3,2,1,0$, azaz 10 állapotot érint; hosszú, lapos szakaszokon (3-as plató) jut át, a nem javító lépések ellenére nem akad el.
- **$P$**: $5,4,3,2,1,0$; 5 lépés, mindig szigorúan csökken, a legrövidebb út. A második állapotban $u{:}3$ a legjobb, $W$ ott $l{:}3$ és $u{:}3$ között egyenlő.
- **$F$**: $6,5,3,3,1,0$; szintén 5 lépés.

Következtetés: a finomabb heurisztika ($P$, $F$) kisebb platókkal és rövidebb úttal old meg, mint a durva $W$. A kereső által **érzékelt állapotgráf** csak a ténylegesen kiértékelt állapotokból áll, az útvonalak a duplikátumok (már látott állapotok) miatt keresztezik egymást; $P$ útja a legrövidebb a gráfban.

### Heurisztikák a Hanoi tornyai problémára

Az állapot $this[1..n]$: az $i$. korong rúdja (1 = a cél rúd), a korongok mérete az indexszel nő. Heurisztikák ([[concepts/mesint/hanoi-tornyai]]):

- **Darab**: $C(this)=\sum_{i=1..n,\ this[i]\neq 1} 1$ — a nem a célrúdon levő korongok száma.
- **Súlyozott darab**: $WC(this)=\sum_{i=1..n,\ this[i]\neq 1} i$ — ugyanez a korong méretével súlyozva.
- **Összeg**: $S(this)=\sum_{i=1..n} this[i]$ — a rúdszámok összege.
- **Súlyozott összeg**: $WS(this)=\sum_{i=1..n} i\cdot this[i]$.
- **Módosított összeg**: $EWS(this)=WS(this)-\sum_{i=2..n,\ this[i-1]>this[i]} 1+\sum_{i=2..n-1,\ this[i-1]=this[i+1]\wedge this[i]\neq this[i-1]} 2$ — a súlyozott összeg korrekciója a szomszédos korongok viszonyától függően.

A súlyozás azt fejezi ki, hogy a nagy korongok rossz helyen hagyása drágább.

## Kapocs

- [[concepts/mesint/heurisztika]] — az általános fogalom és a költség-informáltság összefüggés
- [[concepts/mesint/hegymaszo-modszer]] — az algoritmus, amelyre a példák épülnek
- [[concepts/mesint/tologato-jatek]] — a feladat állapottér-modellje
- [[concepts/mesint/hanoi-tornyai]] — a Hanoi tornyai modell
- [[concepts/mesint/fekete-feher-kirako]] — újabb példa saját heurisztikával
- [[concepts/mesint/vezerlesi-strategiak]] — a vezérlés típusai (modellfüggő vs. modellfüggetlen)
