---
tags: [concept]
sources: [Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, dimat2gyak02mo.pdf]
references: [Lehman–Leighton–Meyer, Mathematics for Computer Science, 9.2.1 és 9.13. feladat]
derivation: source
kind: theorem
element: water
updated: 2026-10-22
---

# Az euklideszi algoritmus helyessége invariánssal és lépésszáma

Az euklideszi algoritmus állapotgépként is leírható, amelynek az lnko invariáns; két lépésenként felezi az első koordinátát, ezért logaritmikus a lépésszáma, és a legrosszabb eset a Fibonacci-számokon áll elő.

## Tartalom

### Az algoritmus mint állapotgép

Az állapotok az $(x, y)$ nemnegatív egész párok, a kezdőállapot $(a, b)$, az egyetlen átmenet
$$(x, y) \to (y,\ x \bmod y), \qquad y > 0.$$

**Invariáns.** $(x, y) = (a, b)$, azaz az lnko nem változik, mert $(x,y) = (y, x \bmod y)$ ([[concepts/dimatii/euklideszi-algoritmus]], rekurzív alak). Kezdetben igaz. Ha az algoritmus megáll, $y = 0$, és az invariáns szerint $x = (x, 0) = (a,b)$: **részleges helyesség**. A megállást a szigorúan csökkenő $y$ garantálja.

Az invariáns-módszer a bővített változatra is működik: a $(x, y, s, t, u, v)$ állapotgépben az $sa + tb = y$ és $ua + vb = x$ is invariáns, ez adja a lineáris kombinációt ([[concepts/dimatii/bovitett-euklideszi-algoritmus]]).

### Gyors: logaritmikus lépésszám

**Lemma.** $0 < y \le x$ esetén $x \bmod y \le x/2$.

*Bizonyítás.* Ha $y \le x/2$, akkor a maradék kisebb $y$-nál, tehát kisebb $x/2$-nél. Ha $y > x/2$, akkor $x \bmod y = x - y < x/2$. $\square$

Két átmenet után az első koordináta $x$-ről legfeljebb $x/2$-re csökken. Az első koordináta $a$-ról indul, és végül $(a,b)$-vel egyenlő, így az algoritmus legfeljebb
$$1 + 2\log_2 a$$
átmenet után megáll. A lépésszám tehát a bemenet *hosszával* (számjegyeinek számával) arányos, nem a számok értékével: ezért használható kriptográfiai méretű számokra ([[concepts/dimatii/rsa]]).

### Legrosszabb eset: Fibonacci-számok

**Tétel (Lamé).** Azok a legkisebb $a \ge b > 0$ egészek, amelyekre az algoritmus pontosan $n$ átmenetet tesz $(a,b)$-ből indulva, az $F_{n+1}$ és $F_n$ Fibonacci-számok ($F_0 = 0$, $F_1 = 1$).

Indukcióval: az $(F_{n+1}, F_n)$ egy lépés után $(F_n, F_{n+1} \bmod F_n) = (F_n, F_{n-1})$, mert $F_{n+1} = 1\cdot F_n + F_{n-1}$, és minden hányados $1$. Az algoritmus akkor lassú, ha mindegyik hányados $1$.

Mivel $F_n \ge \varphi^{n-2}$ az $\varphi = (1+\sqrt5)/2$ aranymetszéssel, a lépésszám legfeljebb $\log_\varphi a$ nagyságrendű, valamivel kisebb a $2\log_2 a$ korlátnál.

**Egy futás.** $(168, 219)$: a hányadosok $0, 1, 3, 3, 2, 2$, az lnko $3$, az lkkt $168 \cdot 219/3 = 12264$. Néhány további eredmény: $(90,111) = 3$ és $[90,111] = 3330$; $(756, 795) = 3$ és $[756,795] = 200340$; $(1440, 1587) = 3$ és $[1440,1587] = 761760$; $(3048,4611) = 3$ és $[3048,4611] = 4684776$.

### Bináris lnko

A bináris lnko-algoritmus csak $2$-vel osztást és kivonást használ: ha mindkét szám páros, $(x,y,e) \to (x/2,y/2,2e)$; ha csak az egyik, azt felezi; különben a nagyobból kivonja a kisebbet. Ugyanúgy invariánssal igazolható (az $e \cdot (x,y) = (a,b)$ invariáns), és legfeljebb $1 + 3(\log a + \log b)$ lépés kell neki. Hardverben gyorsabb lehet az osztásnál.

## Kapocs

- [[concepts/dimatii/euklideszi-algoritmus]] — az algoritmus és az állapotgép átmenete
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az invariáns kiterjesztése a lineáris kombinációra
- [[concepts/dimatii/lnko-azonossagok-es-fibonacci]] — a Fibonacci-számok relatív prímsége
- [[concepts/dimatii/maradekos-osztas]] — az átmenet maradéka
- [[concepts/dimatii/rsa]] — miért gyors a kulcsgenerálás nagy számokra is
