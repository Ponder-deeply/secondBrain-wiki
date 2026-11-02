---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-12
---

# Az A* memóriaigénye

A memóriaigényt a lezárt (kiterjesztett) csúcsok halmazával, $\mathit{CLOSED}$-dal mérjük, és két algoritmust ennek a halmaznak a tartalmazása szerint hasonlítunk össze.

## Tartalom

### Összehasonlítás $\mathit{CLOSED}$ alapján

$\mathit{CLOSED}_S$ az $S$ gráfkereső által lezárt csúcsok halmaza. Rögzített feladatra és két gráfkereső algoritmusra, $X$-re és $Y$-ra:

- $X$ **nem rosszabb** $Y$-nál, ha $\mathit{CLOSED}_X\subseteq\mathit{CLOSED}_Y$;
- $X$ **jobb** $Y$-nál, ha $\mathit{CLOSED}_X\subset\mathit{CLOSED}_Y$.

Így összevethető (1) két különböző heurisztikájú $A^*$ ugyanazon a feladaton, azaz a két heurisztika; (2) két gráfkereső algoritmus (pl. az $A^*$ és egy másik, szintén optimális megoldást adó) a megengedhető problémák egy részhalmazán.

### Különböző heurisztikájú $A^*$-ok

Az $A_1$ ($h_1$) és $A_2$ ($h_2$) $A^*$ algoritmusok közül $A_2$ **jobban informált**, ha minden $n\in N\setminus T$ csúcsra $h_1(n)<h_2(n)$ (és $h_2(n)\le h^*(n)$). Bizonyítható: ekkor $\mathit{CLOSED}_{A_2}\subseteq\mathit{CLOSED}_{A_1}$, vagyis a jobban informált algoritmus nem rosszabb.

**Gyakorlati megjegyzés.** Enyhébb feltétel mellett is gyakran látványosabb a különbség: sokszor akkor is jóval több csúcsot terjeszt ki $A_1$, ha csak $h_1\le h_2$ teljesül, esetleg nem is minden csúcsra. Példák: 8-as tologató $0<W\le P(\le F)$; fekete-fehér $I\le M(\le 2I)$. Minél jobban (alulról, közelebbről) becsli a heurisztika $h^*$-ot, várhatóan annál kisebb a memóriaigény.

### 15-ös kirakó

A dia táblázata (értékek a keresés során kezelt csúcsok számát adják; a mérték neve nincs kiírva; n.a. = a futás nem volt kivitelezhető):

| megoldás hossza | $g+0$ | $g+W$ | $g+P$ |
|---|---|---|---|
| 6 lépés | 117 | 7 | 6 |
| 13 lépés | 32389 | 119 | 13 |
| 21 lépés | n.a. | 3343 | 145 |
| 30 lépés | n.a. | n.a. | 1137 |
| 34 lépés | n.a. | n.a. | 3971 |

Ahogy a heurisztika közelebb kerül $h^*$-hoz ($0<W<P$), a memóriaigény nagyságrendekkel csökken.

### Különböző algoritmusok

Megmutatható, hogy az $A^*$ memóriaigénye nem rosszabb más megengedhető algoritmusokénál. Példák $f$-ekre: EGK $f=g+0$; $A^{(*)}$ $f=g+h$; $A^{**}$ $f(n)=\max_{m\in start\to n}(g(m)+h(m))$ és a célcsúcs előnyben; $B$ váltogatva $f=g+h$ vagy $f=g$; $B'$ $f=g+h$ változó $h$-val.

## Kapocs

- [[concepts/mesint/a-csillag-algoritmus]] — az eredmények összefoglalása
- [[concepts/mesint/a-csillag-futasi-ideje]] — a másik hatékonysági szempont
- [[concepts/mesint/tologato-jatek]] — $W$, $P$ heurisztikák a tologatón
- [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]] — heurisztika és keresési gráf mérete
- [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]] — $h\le h^*$, monotonitás
