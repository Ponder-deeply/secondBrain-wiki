---
tags: [concept]
sources: [DimatIIEa07.pdf]
derivation: source
updated: 2026-09-08
---

# Schönemann–Eisenstein-kritérium

Elégséges feltétel egész együtthatós primitív polinom $\mathbb{Z}$ fölötti felbonthatatlanságára: ha egy $p$ prím a főegyüttható kivételével minden együtthatót oszt, de $p^2$ nem osztja a konstans tagot, akkor a polinom irreducibilis.

## Tartalom

### A tétel

**Tétel (Schönemann–Eisenstein).** Legyen

$$f(x) = f_nx^n + f_{n-1}x^{n-1} + \dots + f_1x + f_0 \in \mathbb{Z}[x], \quad f_n \neq 0$$

legalább elsőfokú primitív polinom. Ha található olyan $p \in \mathbb{Z}$ prím, melyre

- $p \nmid f_n$,
- $p \mid f_j$, ha $0 \le j < n$,
- $p^2 \nmid f_0$,

akkor $f$ felbonthatatlan $\mathbb{Z}$ fölött.

### Bizonyítás

Tegyük fel, hogy $f = gh$. Mivel $p$ nem osztja $f$ főegyütthatóját, ezért sem $g$, sem $h$ főegyütthatóját nem osztja. Legyen $m$ a legkisebb olyan index, amelyre $p \nmid g_m$, és $o$ a legkisebb olyan index, amelyre $p \nmid h_o$. Ha $k = m + o$, akkor

$$p \nmid f_k = \sum_{i+j=k} g_ih_j,$$

mivel $p$ osztja az összeg minden tagját, kivéve azt, amelyben $i = m$ és $j = o$. Így $k = m + o \ge n$, ami csak $m = \deg(g)$ és $o = \deg(h)$ mellett lehetséges. Ekkor viszont $p \mid g_0$ és $p \mid h_0$, tehát $p^2 \mid g_0h_0 = f_0$ — hacsak nem $\deg(g) = 0$ vagy $\deg(h) = 0$, azaz valamelyik tényező egység. $\square$

### Megjegyzések

- A feltételben $f_n$ és $f_0$ **szerepe felcserélhető**: a tétel ugyanúgy alkalmazható, ha $p \nmid f_0$, $p \mid f_j$ minden $0 < j \le n$ esetén, és $p^2 \nmid f_n$.
- A tétel **nem használható test fölötti polinom** irreducibilitásának bizonyítására, mert testben nem léteznek prímek: minden nem-nulla elem egység.
- A $\mathbb{Q}$ fölötti irreducibilitás a Gauss-tétel következményén keresztül adódik: primitív $f \in \mathbb{Z}[x]$ pontosan akkor felbontható $\mathbb{Z}$ fölött, amikor $\mathbb{Q}$ fölött.

## Kapocs

- [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]] — a primitivitás fogalma és a $\mathbb{Z}$–$\mathbb{Q}$ átvezetés
- [[concepts/dimatii/irreducibilis-polinom]] — a bizonyítandó tulajdonság
- [[concepts/dimatii/racionalis-gyokteszt]] — másik, elemibb irreducibilitási eszköz $\mathbb{Z}[x]$-ben
