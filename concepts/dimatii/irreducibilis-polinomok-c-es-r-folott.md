---
tags: [concept]
sources: [DimatIIEa07.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy10_Polinomok.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
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

### Farkas-diák megfogalmazása

Az algebra alaptételéből minden $f \in \mathbb{C}[x]$ felírható $f(x) = a_n (x - c_1)^{\alpha_1} \cdots (x - c_k)^{\alpha_k}$ alakban, ahol $c_i \in \mathbb{C}$ páronként különbözők és $\alpha_1 + \ldots + \alpha_k = n = \deg f$; így $\mathbb{C}$ fölött az irreducibilis polinomok pontosan az elsőfokúak. Valós esetben: ha $c \in \mathbb{C} \setminus \mathbb{R}$ gyöke $f \in \mathbb{R}[x]$-nek, akkor $x - c$ és $x - \bar c$ felbonthatatlanok és nem asszociáltak, ezért $g(x) = (x - c)(x - \bar c) \mid f(x)$.

### Feladattípusok és módszerek: felbontás $\mathbb{C}$ és $\mathbb{R}$ fölött (2020. 10. feladatsor)

**Módszer.** $\mathbb{C}$ fölött a felbontás gyöktényezős (elsőfokú tényezők); $\mathbb{R}$ fölött a nem valós gyököket konjugált párokba csoportosítjuk, a páros szorzata valós másodfokú: $(x-c)(x-\overline c)=x^2-2\mathrm{Re}(c)x+|c|^2$.

- **Egy gyök ismert.** $3x^4-5x^3+3x^2+4x-2$ egyik gyöke $1+i$: a valós együtthatók miatt $1-i$ is gyök, szorzatuk $x^2-2x+2$, és $3x^4-5x^3+3x^2+4x-2=(x^2-2x+2)(3x^2+x-1)$ (a szorzással ellenőrizve), a többi gyök $1-i$ és $\tfrac{-1\pm\sqrt{13}}6$.
- **Nevezetes azonosságok.** $x^8-16=(x^4-4)(x^4+4)$, és $x^4+4=(x^2+2x+2)(x^2-2x+2)$ (Sophie Germain-azonosság), így $\mathbb{R}$ fölött $x^8-16=(x-\sqrt2)(x+\sqrt2)(x^2+2)(x^2+2x+2)(x^2-2x+2)$; $\mathbb{C}$ fölött mind a nyolc gyök egy-egy gyöktényezőt ad. Hasonlóan $x^6+27=(x^2+3)(x^4-3x^2+9)$ és $x^4-3x^2+9=(x^2+3)^2-9x^2=(x^2+3x+3)(x^2-3x+3)$, így $\mathbb{R}$ fölött $x^6+27=(x^2+3)(x^2+3x+3)(x^2-3x+3)$.
- **Helyettesítéses alakok.** $x^{2n}-2x^n-3=(x^n-3)(x^n+1)$ ($y=x^n$ másodfokú egyenlet), $x^{2n}+x^n+1$ az $y^2+y+1$ gyökeinek ($\omega,\omega^2$) $n$-edik gyökei.
- **Minimális fokú polinom adott gyökökhöz.** A gyökök konjugáltjait is hozzávesszük: ha $1$ kétszeres, $2$, $3$ és $1+i$ egyszeres gyök, a minimális valós polinom $(x-1)^2(x-2)(x-3)(x^2-2x+2)=x^6-9x^5+33x^4-65x^3+74x^2-46x+12$ (fok $6$); ha $i$ háromszoros és $-1-i$ egyszeres, akkor a konjugáltak ($-i$ háromszoros, $-1+i$ egyszeres) is kellenek: $(x^2+1)^3(x^2+2x+2)$, fok $8$.

**Tipikus hibák.** Valós együtthatós polinomnál a konjugált gyököt kihagyni (így a minimális fok alulbecsült); $\mathbb{R}$ fölött $x^4+4$-et irreducibilisnek venni, mert nincs valós gyöke (másodfokúak szorzata); a konjugált gyök multiplicitását nem másolni.

## Kapocs

- [[concepts/dimatii/irreducibilis-polinom]] — a felbonthatatlanság általános fogalma
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a gyöktényező kiemelése mindkét bizonyításban
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a valós eset bizonyításának eszköze
- [[concepts/dimatii/racionalis-gyokteszt]] — a $\mathbb{Q}$ fölötti eset felderítésének elemi eszköze
