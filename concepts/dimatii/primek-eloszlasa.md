---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Prímek eloszlása

Prímből végtelen sok van, sőt „sűrűn” vannak; egy adott korlátig pedig szitálással mind megkereshetők.

## Tartalom

### Végtelen sok prím van

**Tétel (Euklidész).** Végtelen sok prím van.

**Bizonyítás.** Indirekt tegyük fel, hogy csak véges sok prím van: $p_1, \dots, p_k$. Tekintsük az $n = p_1\cdots p_k + 1$ számot. Ez nem osztható egyetlen $p_1, \dots, p_k$ prímmel sem (mindegyikkel osztva $1$ maradékot ad), így $n$ prímtényezős felbontásában szerepelnie kell egy újabb prímszámnak — ellentmondás. $\square$

**Tétel (Dirichlet).** Ha $a, d$ egész számok, $d > 0$ és $(a,d) = 1$, akkor végtelen sok $ak + d$ alakú prím van.

Azaz a prímek minden olyan számtani sorozatban végtelen sokan vannak, amelyben egyáltalán lehetnek.

### Mennyi prím van?

**Prímszámtétel.** Az $x$-ig lévő prímek száma aszimptotikusan $\dfrac{x}{\ln x}$.

| $x$ | prímek száma | $x/\ln x$ |
|---:|---:|---:|
| 10 | 4 | 4,343 |
| 100 | 25 | 21,715 |
| 1000 | 168 | 144,765 |
| 10000 | 1229 | 1085,736 |

Prímből tehát „sok” van: az $x$-ig lévő számoknak nagyjából $1/\ln x$ hányada prím.

### Eratoszthenész szitája

Keressük meg egy adott $n$-ig az összes prímet. Soroljuk fel $2$-től $n$-ig az egész számokat. Ekkor $2$ prím; a $2$ valódi többszörösei nem prímek, ezeket húzzuk ki. A következő ki nem húzott szám, $3$, szintén prím; a $3$ valódi többszöröseit is kihúzzuk. Ismételjük az eljárást $\sqrt{n}$-ig. A ki nem húzott számok mind prímek.

## Kapocs

- [[concepts/dimatii/felbonthatatlan-es-prim]] — a prímszám fogalma
- [[concepts/dimatii/szamelmelet-alaptetele]] — az Euklidész-bizonyítás eszköze
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a Dirichlet-tételben szereplő relatív prím feltétel
