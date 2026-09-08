---
tags: [concept]
sources: [DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/gyuru]] — az alapfogalom, amelyet a nullosztómentesség szűkít
- [[concepts/dimatii/integritasi-tartomany]] — kommutatív, nullosztómentes gyűrű
- [[concepts/dimatii/test]] — minden test nullosztómentes
- [[concepts/dimatii/polinomgyuru]] — nullosztómentes $R$ fölött $R[x]$ is nullosztómentes
