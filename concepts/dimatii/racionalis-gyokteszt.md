---
tags: [concept]
sources: [DimatIIEa07.pdf, dm2gy11_Polinomok.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-21
---

# Racionális gyökteszt

Egész együtthatós polinom minden $p/q$ alakú, tovább nem egyszerűsíthető racionális gyökére igaz, hogy $p$ osztja a konstans tagot és $q$ a főegyütthatót — így a lehetséges racionális gyökök véges listája legyártható.

## Tartalom

### A tétel

**Tétel.** Legyen $f(x) = f_nx^n + f_{n-1}x^{n-1} + \dots + f_1x + f_0 \in \mathbb{Z}[x]$, $f_n \neq 0$ primitív polinom. Ha $f\!\left(\frac{p}{q}\right) = 0$, ahol $p, q \in \mathbb{Z}$ és $(p, q) = 1$, akkor

$$p \mid f_0 \quad \text{és} \quad q \mid f_n.$$

*Bizonyítás.* Írjuk fel a gyökfeltételt, és szorozzuk végig $q^n$-nel:

$$0 = f_n\left(\frac{p}{q}\right)^n + f_{n-1}\left(\frac{p}{q}\right)^{n-1} + \dots + f_1\frac{p}{q} + f_0 \quad \Big/ \cdot q^n$$
$$0 = f_np^n + f_{n-1}qp^{n-1} + \dots + f_1q^{n-1}p + f_0q^n.$$

Az utolsó tag kivételével minden tagnak osztója $p$, ezért $p \mid f_0q^n$; mivel $(p, q) = 1$, ebből $p \mid f_0$. Hasonlóan az első tag kivételével minden tagnak osztója $q$, ezért $q \mid f_np^n$, és $(p,q) = 1$ miatt $q \mid f_n$. $\square$

**Megjegyzés.** $f$ primitívsége nem szükséges feltétel, csak praktikus — nem primitív polinomból a tartalom kiemelésével primitívet kapunk, ami ugyanazokkal a gyökökkel rendelkezik.

### Alkalmazás: $\sqrt{2}$ irracionalitása

**Állítás.** $\sqrt{2} \notin \mathbb{Q}$.

*Bizonyítás.* Tekintsük az $x^2 - 2 \in \mathbb{Z}[x]$ polinomot. Ennek $\frac{p}{q}$ alakú gyökeire ($p, q \in \mathbb{Z}$, $(p, q) = 1$) teljesül, hogy $p \mid 2$ és $q \mid 1$, így a lehetséges racionális gyökei $\pm 1$ és $\pm 2$. Egyik sem gyök ($1 - 2 = -1$, $4 - 2 = 2$), tehát $x^2 - 2$-nek nincs racionális gyöke, vagyis $\sqrt 2$ irracionális. $\square$

Az érv általánosan is működik: mivel másod- és harmadfokú polinom test fölött pontosan akkor felbontható, ha van gyöke, a racionális gyökteszt ebben a fokszám-tartományban **teljes irreducibilitási döntést** ad $\mathbb{Q}$ fölött.

### Feladattípusok és módszerek: racionális gyökök és irreducibilitás $\mathbb{Z}[x]$-ben (2020. 11. feladatsor)

**Menet.** (1) Ha az együtthatók közös osztója van (nem primitív), emeljük ki a tartalmat. (2) A gyökjelöltek $\pm\frac pq$, $p\mid f_0$, $q\mid f_n$. (3) A jelölteket Horner-táblával próbáljuk, minden talált gyöknél osztunk, és a hányadossal folytatjuk. (4) Ha a polinom $2$ vagy $3$ fokú, a gyökmentesség irreducibilitást jelent; magasabb foknál az Eisenstein-kritérium ([[concepts/dimatii/schonemann-eisenstein-kriterium]]) vagy másodfokú tényezők keresése kell.

Eredmények (az algoritmussal számolva):

- $40x^4+45x+15=5(8x^4+9x+3)$: nincs racionális gyök (egyik jelölt sem gyök).
- $x^4-2x^3-8x^2+13x-24$: egyetlen racionális gyök $-3$, a hányados $x^3-5x^2+7x-8$ gyökmentes, tehát irreducibilis $\mathbb{Q}$ fölött.
- $x^4+4x^3-2x^2-12x+9=(x-1)^2(x+3)^2$: a gyökök $1$ és $-3$, mindkettő kétszeres.
- $10x^4-13x^3+15x^2-18x-24$: nincs racionális gyök.
- $4x^6-8x^5-3x^4-11x^3+18x^2+28x+8$: racionális többszörös gyökei $2$ és $-\tfrac12$, mindkettő kétszeres; lásd [[concepts/dimatii/gyok-multiplicitasa]].

**Racionális gyök nincs $\Rightarrow$ nem irreducibilis is lehet** negyedik fokon: a gyökteszt csak a lineáris tényezőt zárja ki.

**Tipikus hibák.** A jelöltlistában a főegyüttható osztóit kihagyni (csak egész gyökök keresése); $p$ és $q$ relatív prímségét nem kikötni; a tartalom kiemelése nélkül „irreducibilisnek” nevezni egy nem primitív polinomot $\mathbb{Z}$ fölött (a $40x^4+45x+15$ $\mathbb{Z}$ fölött felbontható $5\cdot(\ldots)$ alakban, $\mathbb{Q}$ fölött irreducibilis).

## Kapocs

- [[concepts/dimatii/irreducibilis-polinom]] — a másod- és harmadfokú eset gyök-kritériuma
- [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]] — a primitivitás fogalma, és a $\mathbb{Z}$–$\mathbb{Q}$ átvezetés
- [[concepts/dimatii/schonemann-eisenstein-kriterium]] — magasabb fokú irreducibilitás igazolásának eszköze
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a gyök és a gyöktényező kapcsolata
- [[concepts/dimatii/gyok-multiplicitasa]] — a többszörös racionális gyökök multiplicitása
