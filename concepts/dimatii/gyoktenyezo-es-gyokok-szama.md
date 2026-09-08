---
tags: [concept]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf]
derivation: source
updated: 2026-09-08
---

# Gyöktényező és a gyökök száma

A maradékos osztás tételének következményei: minden gyökhöz tartozó gyöktényező kiemelhető, ezért egységelemes integritási tartomány fölött egy nem-nulla polinomnak legfeljebb annyi gyöke van, mint amennyi a foka.

## Tartalom

### Gyöktényező

**Definíció.** Ha $c \in R$ az $f \in R[x]$ polinom gyöke, akkor $(x - c) \in R[x]$ a $c$-hez tartozó **gyöktényező**.

**Következmény (gyöktényező leválasztása).** Legyen $R$ egységelemes integritási tartomány. Ha $0 \neq f \in R[x]$ és $c \in R$ gyöke $f$-nek, akkor létezik olyan $q \in R[x]$, amire $f(x) = (x-c)q(x)$.

*Bizonyítás.* Osszuk el maradékosan $f$-et $(x-c)$-vel — ez megtehető, mert $(x-c)$ főegyütthatója $1$, ami egység:

$$f(x) = q(x)(x-c) + r(x).$$

Mivel $\deg(r) < \deg(x-c) = 1$, ezért $r$ konstans polinom. Helyettesítsünk $c$-t:

$$0 = f(c) = q(c)(c-c) + r(c) = r(c),$$

amiből $r = 0$. $\square$

### A gyökök száma

**Következmény.** Az $R$ egységelemes integritási tartomány fölötti $f \neq 0$ polinomnak legfeljebb $\deg(f)$ gyöke van.

*Bizonyítás.* $f$ foka szerinti teljes indukció. $\deg(f) = 0$-ra az állítás igaz (a nem-nulla konstansnak nincs gyöke). Legyen $\deg(f) > 0$. Ha $f(c) = 0$, akkor $f(x) = (x-c)g(x)$, ahol $\deg(g) + 1 = \deg(f)$. Ha $d$ gyöke $f$-nek, akkor

$$0 = f(d) = (d-c)g(d),$$

és mivel $R$ nullosztómentes, ezért $d - c = 0$ (azaz $d = c$), vagy $g(d) = 0$ (azaz $d$ gyöke $g$-nek). Innen az indukciós feltevés adja az állítást. $\square$

**Az egységelemes integritási tartomány feltétel nem elhagyható.** Egy tetszőleges gyűrűben lehetnek nullosztók, és akkor az állítás hamis. Például $\mathbb{Z}_6$ fölött

$$(x-2)(x-3) \equiv x^2 + x \equiv (x - 0)(x + 1) \pmod 6,$$

vagyis egy másodfokú polinomnak négy gyöke van: $0, 2, 3, 5$.

### Polinomot meghatározó helyettesítési értékek

**Következmény.** Ha $R$ egységelemes integritási tartomány, és két, legfeljebb $n$-ed fokú $R[x]$-beli polinomnak $n+1$ különböző helyen ugyanaz a helyettesítési értéke, akkor a két polinom egyenlő.

*Bizonyítás.* A két polinom különbsége legfeljebb $n$-ed fokú, és $n+1$ gyöke van, ezért csak a nullpolinom lehet. $\square$

**Következmény.** Ha $R$ **végtelen** egységelemes integritási tartomány, akkor két különböző $R[x]$-beli polinomhoz nem tartozik ugyanaz a polinomfüggvény — ellenkező esetben a különbségüknek végtelen sok gyöke lenne.

## Kapocs

- [[concepts/dimatii/polinomok-maradekos-osztasa]] — az itteni állítások mind ennek következményei
- [[concepts/dimatii/helyettesitesi-ertek-es-polinomfuggveny]] — a polinom és a polinomfüggvény viszonya itt dől el
- [[concepts/dimatii/gyok-multiplicitasa]] — a gyöktényező magasabb hatványainak vizsgálata
- [[concepts/dimatii/lagrange-interpolacio]] — az egyértelműséget kimondó következmény párja a létezésről
