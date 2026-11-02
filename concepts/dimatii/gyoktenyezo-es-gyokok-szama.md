---
tags: [concept]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy08_Polinomok.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
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

### A gyökök száma függ $R$-től (Farkas-diák)

Az $f(x) = x^2 + 1$ gyökei: $\mathbb{Z}[x]$, $\mathbb{Q}[x]$, $\mathbb{R}[x]$ fölött nincs; $\mathbb{C}[x]$ fölött kettő ($i$ és $-i$); $\mathbb{Z}_2[x]$ fölött egy ($1$); $\mathbb{Z}_3[x]$ fölött nincs; $\mathbb{Z}_5[x]$ fölött kettő ($2$ és $3$). A felső korlát ($\le \deg f$) mindegyik esetben teljesül.

### Feladattípusok és módszerek: gyökök száma véges gyűrűben (gyakorlati feladatsor, 8. hét)

**Példa a korlát csődjére:** az $x^2+4x+3\in\mathbb{Z}_8[x]$ polinom összes gyökének meghatározásához mind a $8$ elemet be kell helyettesíteni: az értékek $x=0,\dots,7$ esetén $3,0,7,0,3,0,7,0$, így a gyökök $1,3,5,7$ — **négy gyök egy másodfokú polinomnak**. A „legfeljebb $\deg f$ gyök” tétel $\mathbb{Z}_8$-ban nem érvényes, mert a gyűrű nem integritási tartomány ($x^2+4x+3=(x+1)(x+3)$, és $2\cdot4=0$). Szabály: nullosztós gyűrűben a gyöktényezős felbontásból nem következik, hogy minden gyököt megtaláltunk, ezért kimerítő behelyettesítés kell.

## Kapocs

- [[concepts/dimatii/polinomok-maradekos-osztasa]] — az itteni állítások mind ennek következményei
- [[concepts/dimatii/helyettesitesi-ertek-es-polinomfuggveny]] — a polinom és a polinomfüggvény viszonya itt dől el
- [[concepts/dimatii/gyok-multiplicitasa]] — a gyöktényező magasabb hatványainak vizsgálata
- [[concepts/dimatii/lagrange-interpolacio]] — az egyértelműséget kimondó következmény párja a létezésről
- [[concepts/dimatii/nemlinearis-kongruencia]] — ugyanez a jelenség kongruenciák megoldásánál
