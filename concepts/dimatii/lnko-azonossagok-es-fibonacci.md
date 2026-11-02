---
tags: [concept]
sources: [dimat2gyak02mo.pdf, Dimat2mintaZH1.pdf, dm2gy06.pdf, dm2gy09_Polinomok.pdf, dm2gy11_Polinomok.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-22
---

# Lnko-azonosságok, Mersenne-számok és Fibonacci-számok

Néhány lnko-azonosság az euklideszi algoritmus egy lépését teszi láthatóvá, és ezekkel kitevős alakú számok (például $2^m - 1$) legnagyobb közös osztója pár sorban meghatározható.

## Tartalom

### Az azonosságok

Egész $a, b, c$ esetén:

1. $(ca, cb) = c\,(a,b)$ ($c > 0$);
2. $(a, b) = (a - b, b)$, általánosabban $(a,b) = (a - kb, b)$;
3. $(c, b) = 1 \Rightarrow (ac, b) = (a, b)$.

A kettes pont az euklideszi algoritmus egy lépése ([[concepts/dimatii/euklideszi-algoritmus]]), az első és a harmadik a [[concepts/dimatii/legnagyobb-kozos-oszto]] tulajdonságai.

**Előjelek.** $(a+1, b+1) = (a - b, b + 1)$ (kivonás), ezzel szemben $(a - 1, b + 1) = (a + b, b + 1)$; az utóbbi helyett gyakran kényelmesebb $(a-1, b+1) = (a-1, a+b)$.

**ZH-minta.** $(11^4 + 1,\ 11^6 + 1)$: $11^6 + 1 - 11^2(11^4 + 1) = 1 - 121 = -120$, így $(11^4+1, 11^6+1) = (14642, 120)$, és $14642 = 120 \cdot 122 + 2$, tehát az lnko $(120, 2) = 2$.

### Mersenne-típusú számok

**Tétel.** $(2^m - 1,\ 2^n - 1) = 2^{(m,n)} - 1$.

Az $m \ge n$ lépés: $2^m - 1 - 2^{m-n}(2^n - 1) = 2^{m-n} - 1$, és $2^{m-n} - 1$ a kivonásos lépés. A kitevők így pontosan az euklideszi algoritmust futják le.

- $(2^{13} - 1, 2^8 - 1)$: $(13, 8) = 1$, az lnko $2^1 - 1 = 1$. Lépésenként: $(2^{13} - 2^8,\ 2^8 - 1) = (2^8(2^5 - 1),\ 2^8 - 1) = (2^5 - 1,\ 2^8 - 1) = \dots = (2^2 - 1, 2^3 - 1) = (3,7) = 1$, felhasználva a 3. azonosságot.
- $(2^{15} - 1, 2^9 - 1)$: $(15, 9) = 3$, az lnko $2^3 - 1 = 7$.
- $(3^{13} - 1, 3^8 - 1) = 3^1 - 1 = 2$ és $(3^{15} - 1, 3^9 - 1) = 3^3 - 1 = 26$ (ugyanez az érv tetszőleges alapra).

### Polinomok: $x^m \pm 1$

Ugyanez polinomokra, $\mathbb{Q}[x]$-ben: $(x^m - 1,\ x^n - 1) = x^{(m,n)} - 1$. Az $x^m + 1$ és $x^n + 1$ lnko-ja $x^d + 1$, ha $d = (m,n)$ és $m/d$, $n/d$ is páratlan, különben $1$. Vegyes példa: $(x^5 + 1,\ x^{15} - 1)$. Modulo $x^5 + 1$ az $x^5 \equiv -1$, így $x^{15} - 1 = (x^5)^3 - 1 \equiv -2$, azaz a maradék nemnulla konstans, és az lnko $1$. A polinomok euklideszi algoritmusát lásd [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]].

### Fibonacci-számok

$F_1 = F_2 = 1$, $F_{n+2} = F_{n+1} + F_n$.

**Tétel.** $(F_{n+1}, F_n) = 1$.

*Bizonyítás indukcióval.* $(F_2, F_1) = (1,1) = 1$. Ha $(F_{n+1}, F_n) = 1$, akkor $(F_{n+2}, F_{n+1}) = (F_{n+1} + F_n, F_{n+1}) = (F_n, F_{n+1}) = 1$. $\square$

Következmények:

- $(F_{n+2}, F_n) = (F_{n+1} + F_n, F_n) = (F_{n+1}, F_n) = 1$.
- $(F_{n+3}, F_n) = (2F_{n+1} + F_n, F_n) = (2F_{n+1}, F_n) = (2, F_n)$ a 3. azonosság miatt. Ez $2$, ha $F_n$ páros, különben $1$. $F_n$ pontosan akkor páros, ha $3 \mid n$ ($F_3 = 2$, és a paritás $1,1,0$ szerint ismétlődik).

**Bézout-együtthatók.** Az $F_n x + F_{n-1} y = 1$ egyenletre a Cassini-azonosságból $F_n F_{n-2} - F_{n-1}^2 = (-1)^{n-1}$, így egy megoldás $x = (-1)^{n-1}F_{n-2}$, $y = (-1)^n F_{n-1}$ (ellenőrzés $n = 5$: $5 \cdot 2 + 3 \cdot (-3) = 1$). Az összes megoldás ehhez az $F_{n-1}k, -F_n k$ párokat hozzáadva adódik, lásd [[concepts/dimatii/bovitett-euklideszi-algoritmus]].

## Kapocs

- [[concepts/dimatii/euklideszi-algoritmus]] — az azonosságok az algoritmus egy lépésének következményei
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — az lnko alaptulajdonságai
- [[concepts/dimatii/euklideszi-algoritmus-lepesszama]] — a Fibonacci-számok a legrosszabb eset
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a lineáris kombináció előállítása
- [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]] — az $x^m - 1$ típusú lnko polinomokra
