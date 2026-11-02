---
tags: [concept]
sources: [DimatIIEa04.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Test és ferdetest

Olyan egységelemes gyűrű, amelyben a nemnulla elemek a szorzásra csoportot alkotnak — vagyis az osztás is elvégezhető; ha a szorzás kommutatív is, testről beszélünk.

## Tartalom

### Ferdetest

Az $(R; \oplus, \otimes)$ egységelemes gyűrű **ferdetest**, ha $(R \setminus \{0\}; \otimes)$ csoport.

### Test

A kommutatív ferdetestet — azaz amiben nemcsak az összeadás, hanem a szorzás is kommutatív — **testnek** nevezzük.

### Példák

- $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$ a szokásos műveletekkel testek.
- $\mathbb{Z}_p$ a szokásos műveletekkel test, ha $p$ prím.
- A kvaterniók (lásd lineáris algebra) nem kommutatív ferdetestet alkotnak.

### Állítás

Minden test nullosztómentes.

**Bizonyítás.** Legyen $(F; \oplus, \otimes)$ test $0$ nullelemmel és $1$ egységelemmel. Indirekt tegyük fel, hogy léteznek $a, b \in F$ nemnulla elemek, amikre $a \otimes b = 0$. Ekkor

$$b = 1 \otimes b = a^{-1} \otimes a \otimes b = a^{-1} \otimes 0 = 0,$$

ami ellentmondás. $\square$

### Elhelyezés a hierarchiában

gyűrű $\supset$ egységelemes gyűrű $\supset$ ferdetest $\supset$ test; a kommutatív ágon gyűrű $\supset$ integritási tartomány $\supset$ test. A $\mathbb{Z}_p$ test volta közvetlenül abból következik, hogy prím modulus mellett minden nemnulla maradékosztálynak van multiplikatív inverze.

### Definíció a Farkas-diák szerint

Az $R$ gyűrű **test**, ha kommutatív, és $(R^*, \cdot)$ csoport. Testben nincs nullosztó, és minden véges integritási tartomány test.

### Feladattípusok és módszerek: test-e? (gyakorlati feladatsor, 2020 ősz, 6. sor)

- **$\mathbb{Z}_m$:** mindig gyűrű; test pontosan akkor, ha $m$ prím (lásd [[concepts/dimatii/invertalhatosag-zm-ben]]). $\mathbb{Z}_5$ szorzótáblájából az inverzek: $1\leftrightarrow1$, $2\leftrightarrow3$, $4\leftrightarrow4$.
- **Páros maradékosztályok $\mathbb{Z}_{2m}$-ben:** $2m=10$ esetén $\{\bar0,\bar2,\bar4,\bar6,\bar8\}$ test, egységeleme $\bar6$ ($6\cdot6=36\equiv6$, $6\cdot2=12\equiv2$), $\mathbb{Z}_5$-tel izomorf. $2m=20$ esetén zárt a két műveletre, de nincs egységeleme (nincs olyan páros $e$, hogy $e\cdot a\equiv a$ minden páros $a$-ra), ezért nem test.
- **Véges integritási tartomány** (legalább két elemmel) **test:** ha $a\neq0$, az $x\mapsto ax$ leképezés injektív (nullosztómentesség miatt $ax=ay \Rightarrow a(x-y)=0 \Rightarrow x=y$), véges halmazon tehát szürjektív is, így $ax=1$ megoldható. Lásd [[concepts/dimatii/integritasi-tartomany]].
- **Kéttagú-páros testek:** $\mathbb{Z}_2\times\mathbb{Z}_2$ a $(x,y)(x',y')=(xx'+yy',\ xy'+x'y+yy')$ szorzással, illetve $\mathbb{Z}_3\times\mathbb{Z}_3$ az $(xx'-yy',\ xy'+x'y)$ szorzással testet ad (4, illetve 9 elemű test; a másodikban az $y$ szerepe az $i$ a $\mathbb{Z}_3[x]/(x^2+1)$-ben, lásd [[concepts/dimatii/veges-testek]]).
- **$\mathbb{Q}+\alpha\mathbb{Q}$ ($\alpha^2=-r\alpha-s$, $\alpha\notin\mathbb{Q}$):** zárt a szorzásra az $\alpha^2$ képlete miatt; nemnulla $a+b\alpha$ inverzét a konjugálttal kapjuk: $\alpha' = -r-\alpha$ mellett $(a+b\alpha)(a+b\alpha') = a^2-rab+sb^2 \neq 0$ (különben $-a/b$ racionális gyöke volna $t^2+rt+s$-nek, és $\alpha$ is racionális volna), és $a+b\alpha' \in \mathbb{Q}+\alpha\mathbb{Q}$.
- **Négyelemű egységelemes gyűrűk** izomorfia erejéig négy van: $\mathbb{Z}_4$, $\mathbb{Z}_2\times\mathbb{Z}_2$, a 4 elemű test és $\mathbb{Z}_2[x]/(x^2)$; közülük csak a test nullosztómentes.

## Kapocs

- [[concepts/dimatii/gyuru]] — az alapstruktúra
- [[concepts/dimatii/csoport]] — a nemnulla elemek multiplikatív csoportja
- [[concepts/dimatii/nullosztomentes-gyuru]] — minden test ilyen
- [[concepts/dimatii/integritasi-tartomany]] — a testnél tágabb kommutatív keret
- [[concepts/dimatii/polinomgyuru]] — test fölötti polinomgyűrű a polinomelmélet szokásos színtere
