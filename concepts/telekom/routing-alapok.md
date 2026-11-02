---
tags: [concept]
sources: [Laki_Lecture_6.pdf, Laki_Lecture_7a.pdf]
derivation: source
kind: definition
element: water
updated: 2026-09-25
---

# Forgalomirányítás alapjai: optimalitási elv és nyelőfa

A forgalomirányító (routing) algoritmus a hálózati réteg szoftverének az a része, amely eldönti, hogy egy bejövő csomag **melyik kimeneti vonalon** kerüljön továbbításra. Az alhálózatot súlyozott gráfként modellezzük; az **optimalitási elv** szerint egy célba vezető optimális utak fát, **nyelőfát** alkotnak.

## Tartalom

### A hálózati réteg

- **Szolgáltatás**: csomagtovábbítás, útvonalválasztás, csomagfragmentálás kezelése, csomagütemezés, pufferkezelés.
- **Interfész**: csomag küldése egy adott végpontnak.
- **Protokoll**: globálisan egyedi címek definiálása, routing táblák karbantartása.
- **Példák**: IPv4, IPv6.

### A forgalomirányítás két lépése

1. A **forgalomirányító táblázatok feltöltése és karbantartása** (vezérlési sík).
2. A **továbbítás** (*forwarding*, adatsík) — a tábla alapján.

**Elvárások:** helyesség, egyszerűség, robosztusság, stabilitás, **igazságosság**, **optimalitás** és hatékonyság. (Az igazságosság és az optimalitás gyakran ellentmond egymásnak.)

### Algoritmusosztályok

1. **Adaptív** algoritmusok — a topológia és rendszerint a forgalom is befolyásolhatja a döntést.
2. **Nem-adaptív** (statikus) algoritmusok — offline meghatározás, betöltés a routerekbe induláskor.

Az adaptív algoritmusok különbségei:
- *honnan kapják az információt?* — szomszédoktól, helyileg, minden routertől;
- *mikor változtatják az útvonalakat?* — meghatározott másodpercenként, terhelésváltozásra, topológiaváltozásra;
- *milyen mértéket optimalizálnak?* — távolság, ugrások (*hops*) száma, becsült késleltetés.

### Optimalitási elv

> Ha $J$ router az $I$ routertől $K$ router felé vezető **optimális útvonalon** helyezkedik el, akkor a $J$-től $K$-ig vezető optimális útvonal ugyanerre esik.

(Ha lenne jobb út $J$-ből $K$-ba, akkor $I$-ből is azt használnánk, ellentmondás.)

**Következmény:** az összes forrásból egy célba tartó optimális utak egy olyan fát alkotnak, amelynek gyökere a cél. Ezt nevezzük a cél **nyelőfájának** (*sink tree*). A nyelőfa nem feltétlenül egyértelmű, de hurkot nem tartalmaz, így minden csomag véges ugrással célba ér.

### Legrövidebb út alapú forgalomirányítás

Az alhálózat egy $G = (V, E)$ gráf: minden router egy csomópont, minden él egy kommunikációs vonal (*link*). Az éleken nemnegatív súlyfüggvényt értelmezünk:
$$w: E \to \mathbb{R}_0^+,\qquad w(P) = \sum_{e\in P} w(e)$$
egy $P$ útvonal súlya. A routing célja a legkisebb súlyú út megtalálása.

Példa (a diák gráfja): A–B 1, A–E 1, B–C 5, B–F 2, E–C 2, E–F 3, C–D 1, F–D 1. Az A-ból D-be vezető egyik legrövidebb út **A–E–C–D**, súlya $1 + 2 + 1 = 4$ (ugyanennyi az A–B–F–D út is).

### A dinamikus algoritmusok két csoportja

- **Távolságvektor alapú** (*distance vector routing*): minden router csak a szomszédaival cserél információt — elosztott Bellman–Ford; ld. [[concepts/telekom/tavolsagvektor-routing]].
- **Kapcsolatállapot alapú** (*link-state routing*): minden router megismeri a teljes topológiát, és maga számol legrövidebb utat (Dijkstra); ld. [[concepts/telekom/kapcsolatallapot-routing]].

**Vizsgaszempont:** az optimalitási elv kimondása és a nyelőfa fogalma; a routing és a forwarding szétválasztása; adaptív vs. nem-adaptív algoritmusok.

## Kapocs

- [[concepts/telekom/tavolsagvektor-routing]] — elosztott Bellman–Ford
- [[concepts/telekom/kapcsolatallapot-routing]] — Dijkstra-alapú alternatíva
- [[concepts/telekom/feszitofa-protokoll]] — a 2. réteg legrövidebb utas fája
- [[concepts/telekom/retegzett-halozati-architektura]] — vezérlési és adatsík
