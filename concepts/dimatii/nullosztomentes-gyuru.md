---
tags: [concept]
sources: [DimatIIEa04.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Nullosztómentes gyűrű és karakterisztika

Olyan gyűrű, amelyben két nemnulla elem szorzata sosem nulla; ilyenkor a nemnulla elemek additív rendje közös, és ez a közös érték a gyűrű karakterisztikája.

## Tartalom

### Definíció

Ha egy $(R; \oplus, \otimes)$ gyűrűben $\forall r, s \in R$, $r \ne 0$, $s \ne 0$ esetén $r \otimes s \ne 0$, akkor $R$ **nullosztómentes gyűrű**. Ezzel egyenértékűen: $r \otimes s = 0 \Rightarrow r = 0$ vagy $s = 0$.

### Példa nem nullosztómentes gyűrűre

$(\mathbb{R}^{2 \times 2}; +, \cdot)$:

$$\begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} \cdot \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} = \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix},$$

vagyis két nemnulla mátrix szorzata a nullmátrix.

### Állítás

Nullosztómentes gyűrűben a nemnulla elemek **additív rendje megegyezik**, és ez a közös rend vagy egy $p$ prímszám, vagy végtelen.

### Karakterisztika

Ha az előző állításban szereplő közös rend $p$, akkor azt mondjuk, hogy a gyűrű **karakterisztikája** $p$ (jelölés: $\mathrm{char}(R) = p$); ha a közös rend végtelen, akkor a gyűrű karakterisztikája $\mathrm{char}(R) = 0$.

### Kapcsolódó eredmény

Minden test nullosztómentes. Legyen ugyanis $(F; \oplus, \otimes)$ test $0$ nullelemmel és $1$ egységelemmel. Indirekt tegyük fel, hogy léteznek $a, b \in F$ nemnulla elemek, amikre $a \otimes b = 0$. Ekkor

$$b = 1 \otimes b = a^{-1} \otimes a \otimes b = a^{-1} \otimes 0 = 0,$$

ami ellentmondás. $\square$

### A karakterisztika-tétel bizonyítása

Legyen $R$ legalább kételemű, nullosztómentes gyűrű.

1. Tegyük fel, hogy van $a \in R^*$ véges $|a| = n_a$ renddel, azaz $n_a a = 0$. Tetszőleges $b \in R^*$-ra $n_a(ab) = (n_a a)b = 0b = 0$, másrészt $n_a(ab) = a(n_a b)$. A nullosztómentesség miatt $n_a b = 0$, így $|b| \le |a| = n_a$. Hasonlóan $|b| \ge |a|$, tehát $|b| = |a| = n_a$.
2. Ha nincs véges rendű elem, minden nemnulla elem rendje végtelen.
3. A közös rend nem lehet $1$: $0 = 1\cdot a = a$ lenne, $a = 0$ ellentmondás.
4. A közös $n$ nem lehet összetett: $n = kl$, $1 < k, l < n$ esetén $na = l(ka) = 0$. Ha $ka \neq 0$, akkor $|ka| = n$ és $|ka| \le l < n$ — ellentmondás; ha $ka = 0$, akkor $|a| \le k < n$ — ellentmondás. Marad: a közös rend prím vagy végtelen. $\square$

### Nullosztók és regularitás

Az $R$ gyűrűben $a$ baloldali, $b$ jobboldali nullosztó, ha $a \neq 0$, $b \neq 0$, $ab = 0$. A szorzás pontosan akkor reguláris (egyszerűsíthető), ha $R$ nullosztómentes (bizonyítás: [[concepts/dimatii/gyuru]]). Nem nullosztómentes gyűrű, amelynek karakterisztikája mégis 2: [[concepts/dimatii/boole-gyuru]].

### Feladattípusok és módszerek: nullosztók $\mathbb{Z}_m$-ben (gyakorlati feladatsor, 2020 ősz, 6. sor)

$\mathbb{Z}_m$-ben a nemnulla $a$ pontosan akkor nullosztó, ha $\mathrm{lnko}(a,m)>1$; a többi nemnulla elem egység. **$\mathbb{Z}_{12}$ nullosztói:** $2,3,4,6,8,9,10$ (az egységek $1,5,7,11$). Tanúk: $2\cdot6=0$, $3\cdot4=0$, $8\cdot3=24\equiv0$, $9\cdot4=36\equiv0$, $10\cdot6=60\equiv0$. Lásd [[concepts/dimatii/invertalhatosag-zm-ben]].

## Kapocs

- [[concepts/dimatii/gyuru]] — az alapfogalom, amelyet a nullosztómentesség szűkít
- [[concepts/dimatii/integritasi-tartomany]] — kommutatív, nullosztómentes gyűrű
- [[concepts/dimatii/test]] — minden test nullosztómentes
- [[concepts/dimatii/polinomgyuru]] — nullosztómentes $R$ fölött $R[x]$ is nullosztómentes
