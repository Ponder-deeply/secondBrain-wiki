---
tags: [concept, dimatii/polinomok]
sources: [DimatIIEa07.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/irreducibilis-polinom]] — a másod- és harmadfokú eset gyök-kritériuma
- [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]] — a primitivitás fogalma, és a $\mathbb{Z}$–$\mathbb{Q}$ átvezetés
- [[concepts/dimatii/schonemann-eisenstein-kriterium]] — magasabb fokú irreducibilitás igazolásának eszköze
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a gyök és a gyöktényező kapcsolata
