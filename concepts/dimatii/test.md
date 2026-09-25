---
tags: [concept, dimatii/algebrai-strukturak]
sources: [DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/gyuru]] — az alapstruktúra
- [[concepts/dimatii/csoport]] — a nemnulla elemek multiplikatív csoportja
- [[concepts/dimatii/nullosztomentes-gyuru]] — minden test ilyen
- [[concepts/dimatii/integritasi-tartomany]] — a testnél tágabb kommutatív keret
- [[concepts/dimatii/polinomgyuru]] — test fölötti polinomgyűrű a polinomelmélet szokásos színtere
