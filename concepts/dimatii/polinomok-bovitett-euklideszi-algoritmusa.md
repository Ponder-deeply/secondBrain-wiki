---
tags: [concept]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf, dm2gy06_Polinomok.pdf, dm2gy07.pdf, dm2gy08.pdf, dm2gy09_Polinomok.pdf, dm2gy11_Polinomok.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Polinomok bővített euklideszi algoritmusa

Test fölötti polinomgyűrűben tetszőleges nem-nulla polinommal lehet maradékosan osztani, ezért működik a bővített euklideszi algoritmus: két polinom kitüntetett közös osztója mellé megadja annak lineáris kombinációs előállítását is.

## Tartalom

### Oszthatóság és kitüntetett közös osztó

**Definíció.** Azt mondjuk, hogy $f, g \in R[x]$ esetén $f$ **osztója** $g$-nek ($g$ **többszöröse** $f$-nek), ha létezik $h \in R[x]$, amire $g = f\cdot h$.

**Definíció.** Az $f, g \in R[x]$ polinomok **kitüntetett közös osztója** (legnagyobb közös osztója) az a $d \in R[x]$ polinom, amelyre $d \mid f$, $d \mid g$, és tetszőleges $c \in R[x]$ esetén $(c \mid f \wedge c \mid g) \Rightarrow c \mid d$.

Test fölötti polinomgyűrűben tetszőleges nem-nulla polinommal tudunk maradékosan osztani (testben minden nem-nulla elem egység), ezért működik a bővített euklideszi algoritmus. Ez $f, g \in R[x]$ esetén ($R$ test) meghatározza $f$ és $g$ kitüntetett közös osztóját, a $d \in R[x]$ polinomot, továbbá olyan $u, v \in R[x]$ polinomokat, amelyekre $d = u\cdot f + v\cdot g$.

### Az algoritmus

Legyen $R$ test, $f, g \in R[x]$. Ha $g = 0$, akkor $(f, g) = f = 1\cdot f + 0\cdot g$. Különben végezzük el a következő maradékos osztásokat:

$$f = q_1g + r_1,\quad g = q_2r_1 + r_2,\quad r_1 = q_3r_2 + r_3,\ \dots$$
$$r_{n-2} = q_nr_{n-1} + r_n,\qquad r_{n-1} = q_{n+1}r_n.$$

Ekkor $d = r_n$ jó lesz kitüntetett közös osztónak. Az

$$u_{-1} = 1,\ u_0 = 0,\qquad v_{-1} = 0,\ v_0 = 1$$

kezdőértékekkel, továbbá az

$$u_k = u_{k-2} - q_k\cdot u_{k-1}, \qquad v_k = v_{k-2} - q_k\cdot v_{k-1}$$

rekurziókkal megkapható $u = u_n$ és $v = v_n$, amelyekre $d = u\cdot f + v\cdot g$.

### A helyesség bizonyítása

A maradékok foka szigorúan monoton csökkenő természetes szám sorozat, ezért az eljárás véges sok lépésben véget ér.

*A lineáris kombináció.* Indukcióval belátjuk, hogy az $r_{-1} = f$ és $r_0 = g$ jelöléssel $r_k = u_k\cdot f + v_k\cdot g$ teljesül minden $-1 \le k \le n$ esetén. $k = -1$-re $f = 1\cdot f + 0\cdot g$, $k = 0$-ra $g = 0\cdot f + 1\cdot g$. Mivel $r_{k+1} = r_{k-1} - q_{k+1}r_k$,

$$r_{k+1} = (u_{k-1} - q_{k+1}u_k)f + (v_{k-1} - q_{k+1}v_k)g = u_{k+1}f + v_{k+1}g.$$

*Közös osztó.* $r_n \mid r_{n-1}$ nyilvánvaló, és $k = 1$-re $r_{n-2} = q_nr_{n-1} + r_n$ miatt $r_n \mid r_{n-2}$; indukcióval $r_n \mid r_{n-k}$ minden $0 \le k \le n+1$ esetén, így $r_n \mid r_0 = g$ és $r_n \mid r_{-1} = f$.

*Kitüntetettség.* $r_n = u_nf + v_ng$ miatt $f$ és $g$ minden közös osztója osztója $r_n$-nek. $\square$

### Feladattípusok és módszerek (2020. 9. és 11. feladatsor)

A feladatsorokhoz nincs megoldás; az alábbi válaszokat a módszerrel újraszámoltuk.

**1. Legnagyobb közös osztó $\mathbb{Q}[x]$-ben.** Euklideszi algoritmus polinomokra: osztunk maradékosan, a maradék lesz az új osztó, az utolsó nem nulla maradékot főegyütthatójával osztva normáljuk (a kitüntetett közös osztó csak asszociáltság erejéig egyértelmű, a főpolinomot szokás megadni). Eredmények: $(x^4+x^3-3x^2-4x-1,\ x^3+x^2-x-1) = x+1$; $(x^5+x^4-x^3-2x-1,\ 3x^4+2x^3+x^2+2x-2) = x^2+1$; $(7x^4-28x^3+7,\ 11x^3-33x^2+11) = 1$ (relatív prímek).

**2. A test számít.** Ugyanaz a polinompár más testben más lnko-t adhat. $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$ fölött az lnko ugyanaz (a maradékos osztás együtthatói $\mathbb{Q}$-ban maradnak), de $\mathbb{Z}_3$ fölött más lehet: az $x^4+x^3-3x^2-4x-1$ és $x^3+x^2-x-1$ lnko-ja $\mathbb{Q}$ fölött $x+1$, $\mathbb{Z}_3$ fölött $x^2+2 = (x+1)(x+2)$; a $7x^4-28x^3+7$ és $11x^3-33x^2+11$ lnko-ja $\mathbb{Q}$ fölött $1$, $\mathbb{Z}_3$ fölött $x+1$. A „van-e közös gyökük” kérdés az lnko gyökeit kérdezi: közös gyök pontosan akkor van, ha az lnko nem konstans. $\mathbb{Z}$ fölött az lnko csak a $\mathbb{Z}[x]$ Gauss-gyűrű szerint értelmezett (a tartalmak lnko-ja is beleszámít), nem euklideszi algoritmussal számolható közvetlenül.

**3. Megoldható-e $fu+gv=h$?** A bővített euklideszi algoritmus $d = (f,g) = uf+vg$-t ad. Az egyenlet pontosan akkor megoldható, ha $d \mid h$. Ha $d=1$ (relatív prímek), minden $h$-ra megoldható: például $(3x^3-2x^2+x+2)\,x + (x^2-x+1)(-3x^2-x+1) = 1$ ($\mathbb{R}[x]$-ben, $u = x$, $v=-3x^2-x+1$), és a $(x^4-x^3-4x^2+4x+1)u+(x^2-x+1)v = x$ egyenletnek is van megoldása, mert az lnko konstans (a megoldást $x$-szel szorozzuk). $\mathbb{Z}_2[x]$-ben $(x^5+x^2+1,\ x^4+x^2+x)=1$, így a $=1$ egyenlet megoldható; viszont $(x^4+1,\ x^3+x^2+x+1) = (x+1)^3 = x^3+x^2+x+1$, és erre nem osztható az $x^3+x+1$ jobb oldal ($x^3+x+1 = (x^3+x^2+x+1) + x^2$, a maradék $x^2 \neq 0$), tehát az egyenletnek nincs megoldása.

**4. Szimultán polinomkongruencia: legkisebb fokú $h$, amelyre $h \equiv u \pmod f$, $h \equiv v \pmod g$.** A kínai maradéktétel polinomos változata: megoldható pontosan akkor, ha $(f,g) \mid (u-v)$; ha $(f,g) = 1$, a megoldás egyértelmű modulo $fg$, és a bővített euklideszi algoritmus $sf+tg=1$ együtthatóival $h = utg + vsf \bmod fg$. Példa: $f=x^3+1$, $g = x^3+x^2-2$, $u=-x^2$, $v=x^2-2x+2$ $\mathbb{Q}$ fölött: $(f,g)=1$, a megoldás $h = x^5$ (ellenőrzés: $x^5 = x^2\cdot x^3 \equiv -x^2 \pmod{x^3+1}$, és $x^5 \equiv x^2-2x+2 \pmod g$). Ha $f=(x-1)^2$, $g=(x-1)(x^2-2x-2)$, akkor $(f,g)=x-1$, és $u-v = -x^2-1$ helyettesítési értéke $x=1$-ben $-2 \neq 0$, tehát **nincs megoldás**; $\mathbb{Z}_2$ fölött $f=g=x^3+x^2+1$ esetén $u-v=x^2$ nem osztható $f$-fel, szintén nincs megoldás.

**5. Hatványkülönbségek lnko-ja: $(x^m-1,\ x^n-1) = x^{(m,n)}-1$, $(x^m+1,\ x^n+1) = x^{(m,n)}+1$,** ha $\frac{m}{(m,n)}$ és $\frac{n}{(m,n)}$ is páratlan, különben $1$. Az indok az egész számos $(a^m-1,a^n-1)=a^{(m,n)}-1$ eset euklideszi lépéseinek polinomos megfelelője, lásd [[concepts/dimatii/lnko-hatvanykifejezesekre]]. Például $(x^5+1,\ x^{15}-1) = 1$, mert egy közös gyökre $\zeta^5=-1$ lenne, így $\zeta^{15}=-1\ne 1$; a sorozat 10. feladatában $(x-1)^3(x+2)^2(x-3)(x-4)$ és $(x-1)^5(x+2)(x+5)$ lnko-ja gyöktényezős alakból $(x-1)^3(x+2)$: a legkisebb kitevők.

**6. Nagyobb gyakorló sorok (2024. 7–8. alkalom).** Lnko-k: $\mathbb{Q}$ fölött $(x^8-3x^5+x^4-2x^3+2x^2-x+2,\ x^6-x^4-3x^3+x+2) = x^3-1$; $(x^5+x^4-4x^3-2x^2+4x,\ x^7-x^6-2x^5+x^3+4x^2-2x) = x^3-2x$; $\mathbb{Z}_2$ fölött $(x^9+x^7+x^5+x^3+x^2,\ x^7+x^4+x^3+x^2) = x^2$ és $(x^{11}+x^{10}+x^8+x^4+x+1,\ x^9+x^3+x^2+1) = x^3+x^2+x+1$; $\mathbb{Z}_3$ fölött $(x^9+x^8+2x^6+x^5+2x^3+2x,\ x^7+x^6+x^5+2x^4+2x^3+2x^2+2x+1) = x^2+2$ és $(x^9+2x^6+x^5+x^4+2x^3+x^2+2x+2,\ x^7+2x^3) = x^2+2$. Az $uf+vg=1$ egyenlet (relatív prím párokra), a bővített algoritmussal: $\mathbb{Q}$ fölött $f=x^5+x^2-1$, $g=x^3-x$: $u = x^2+x-1$, $v=-x^4-x^3-2x-1$; $\mathbb{Z}_2$ fölött $f=x^7+x^6+x^5+x^3+x^2+x+1$, $g=x^5+x^4+x^2+1$: $u=x^4$, $v=x^6+x^4+x^2+1$; $\mathbb{Z}_2$ fölött $f=x^6+x^5+x^4+x^3+x^2+x+1$, $g=x^5+x^2$: $u=x^4+x+1$, $v=x^5+x^4+x^3+x^2$; $\mathbb{Z}_3$ fölött $f=2x^5+2x^4+1$, $g=x^4+2x^2+x$: $u=2x^3+x+1$, $v=2x^4+2x^3+2x+2$; $\mathbb{Z}_5$ fölött $f=3x^5+x^4+2x^3+x^2+1$, $g=2x^4+x^2+2x$: $u=4x^3+2x+1$, $v=4x^4+3x^3+x^2+4$ (mindegyik behelyettesítéssel ellenőrizve). A megoldás nem egyértelmű: $(u+gt,\ v-ft)$ is jó minden $t$-re; a fenti az algoritmus kimenete, amelynek foka $\deg u<\deg g$, $\deg v<\deg f$.

**Példa „adj példát” típusra** (08. alkalom 3–4.): ha $f$-nek és $g$-nek is gyöke $3$ és $5$, akkor $(x-3)(x-5)\mid (f,g)$; ilyen $f=(x-3)(x-5)$, $g=\tfrac1{15}(x-3)(x-5)$, mert $g(0)=1$. $\mathbb{Z}_7$ fölött (4a): $f=(x-1)(x-2)$, $g=5(x-1)(x-2)$, mert $g(6)=5\cdot 20=100\equiv 2$.

**Tipikus hibák.** A maradékos osztásban az osztó főegyütthatójával nem osztani (nem főpolinom osztója esetén); az utolsó *nulla* maradékot olvasni ki az utolsó *nem nulla* helyett; $\mathbb{Z}_p$ fölött az együtthatókat nem redukálni minden lépésben; a $v$-t nem szorozni a jobb oldallal, ha $fu+gv=h$ és $d\neq 1$.

## Kapocs

- [[concepts/dimatii/polinomok-maradekos-osztasa]] — az algoritmus elemi lépése
- [[concepts/dimatii/test]] — a feltétel, ami minden nem-nulla polinommal való osztást megenged
- [[concepts/dimatii/veges-testek]] — az inverz kiszámítása $\mathbb{Z}_p[x]/(f)$-ben ezzel az algoritmussal történik
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az egész számokra vonatkozó megfelelője
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a kitüntetett közös osztó fogalma $\mathbb{Z}$-ben
- [[concepts/dimatii/euklideszi-algoritmus]] — az egész számokra vonatkozó eredeti eljárás
