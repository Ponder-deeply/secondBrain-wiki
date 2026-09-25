---
tags: [concept, dimatii/polinomok]
sources: [DimatIIEa07.pdf]
derivation: source
updated: 2026-09-08
---

# Irreducibilis polinomok $\mathbb{C}$ és $\mathbb{R}$ fölött

Az algebra alaptételére támaszkodva a komplex számtest fölött pontosan az elsőfokú polinomok felbonthatatlanok, a valós számtest fölött pedig az elsőfokúak és a gyöktelen másodfokúak.

## Tartalom

### $\mathbb{C}$ fölött

**Tétel.** $f \in \mathbb{C}[x]$ pontosan akkor felbonthatatlan, ha $\deg(f) = 1$.

*Bizonyítás.* ($\Leftarrow$) Mivel $\mathbb{C}$ a szokásos műveletekkel test, ezért a test fölötti elsőfokú polinomok felbonthatatlanok — lásd [[concepts/dimatii/irreducibilis-polinom]].

($\Rightarrow$) Indirekt tegyük fel, hogy $\deg(f) \neq 1$. Ha $\deg(f) < 1$, akkor $f = 0$ vagy $f$ egység, tehát nem felbonthatatlan, ellentmondásra jutottunk. Ha $\deg(f) > 1$, akkor az **algebra alaptétele** értelmében van gyöke $f$-nek. A gyöktényezőt kiemelve $f(x) = (x-c)g(x)$ alakot kapunk, ahol $\deg(g) \ge 1$, vagyis egy nemtriviális szorzat-előállítást; így $f$ nem felbonthatatlan — ismét ellentmondás. $\square$

Az algebra alaptételét itt felhasználtuk, de nem bizonyítottuk.

### $\mathbb{R}$ fölött

**Tétel.** $f \in \mathbb{R}[x]$ pontosan akkor felbonthatatlan, ha

- $\deg(f) = 1$, **vagy**
- $\deg(f) = 2$, és $f$-nek nincs valós gyöke.

*Bizonyítás.* ($\Leftarrow$) Ha $\deg(f) = 1$, az állítás a test fölötti elsőfokú polinomokról szóló állításból következik. Ha $\deg(f) = 2$ és $f$-nek nincs gyöke, akkor a másod- és harmadfokú polinomokra vonatkozó ekvivalencia adja, hogy $f$ felbonthatatlan.

($\Rightarrow$) Ha $f$ felbonthatatlan, akkor $\deg(f) \ge 1$; és ha $\deg(f) = 2$, akkor nem lehet gyöke. Marad annak igazolása, hogy **nem lehet kettőnél magasabb fokú $\mathbb{R}$ fölötti irreducibilis polinom.** Tegyük fel, hogy $\deg(f) \ge 3$. Az algebra alaptétele értelmében $f$-nek mint $\mathbb{C}$ fölötti polinomnak van $c \in \mathbb{C}$ gyöke.

- Ha $c \in \mathbb{R}$, akkor a gyöktényező kiemelésével $f$ nemtriviális felbontását kapjuk.
- Legyen most $c \in \mathbb{C}\setminus\mathbb{R}$ gyöke $f$-nek, és tekintsük a
  $$g(x) = (x - c)(x - \overline{c}) = x^2 - 2\operatorname{Re}(c)x + |c|^2 \in \mathbb{R}[x]$$
  polinomot. Osszuk el maradékosan $f$-et $g$-vel: léteznek $q, r \in \mathbb{R}[x]$, hogy $f = qg + r$. Itt $r = 0$, mert $\deg(r) < 2$, és $r$-nek gyöke $c \in \mathbb{C}\setminus\mathbb{R}$. Tehát $f = qg$, ami nemtriviális felbontás — ellentmondás. $\square$

### Konjugált gyökpárok

**Megjegyzés.** Ha $f \in \mathbb{R}[x]$-nek $c \in \mathbb{C}$ gyöke, akkor $\overline{c}$ is gyöke, hiszen a valós együtthatók konjugálása önmagukba visz:

$$f(\overline{c}) = \sum_{j=0}^{\deg(f)} f_j(\overline{c})^j = \sum_{j=0}^{\deg(f)} \overline{f_j}\cdot\overline{c^j} = \overline{\left(\sum_{j=0}^{\deg(f)} f_jc^j\right)} = \overline{f(c)} = \overline{0} = 0.$$

Ez az észrevétel adja, hogy a $g(x) = (x-c)(x-\overline{c})$ tényező valós együtthatós.

## Kapocs

- [[concepts/dimatii/irreducibilis-polinom]] — a felbonthatatlanság általános fogalma
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a gyöktényező kiemelése mindkét bizonyításban
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a valós eset bizonyításának eszköze
- [[concepts/dimatii/racionalis-gyokteszt]] — a $\mathbb{Q}$ fölötti eset felderítésének elemi eszköze
