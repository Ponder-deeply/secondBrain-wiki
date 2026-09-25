---
tags: [concept, dimatii/polinomok]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/polinomok-maradekos-osztasa]] — az algoritmus elemi lépése
- [[concepts/dimatii/test]] — a feltétel, ami minden nem-nulla polinommal való osztást megenged
- [[concepts/dimatii/veges-testek]] — az inverz kiszámítása $\mathbb{Z}_p[x]/(f)$-ben ezzel az algoritmussal történik
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az egész számokra vonatkozó megfelelője
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a kitüntetett közös osztó fogalma $\mathbb{Z}$-ben
- [[concepts/dimatii/euklideszi-algoritmus]] — az egész számokra vonatkozó eredeti eljárás
