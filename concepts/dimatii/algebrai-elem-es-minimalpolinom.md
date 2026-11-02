---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Algebrai elem és minimálpolinom

Egy bővítés eleme algebrai az alaptest fölött, ha gyöke egy nem nulla, az alaptest fölötti polinomnak; ekkor a gyököt eltüntető polinomok ideálját egyetlen főpolinom generálja, a minimálpolinom, ami irreducibilis.

## Tartalom

### Algebrai elem

Legyen $K$ részteste $F$-nek, $\alpha \in F$. Ha $\alpha$ gyöke egy nem nulla $K$ fölötti polinomnak, akkor $\alpha$ **algebrai elem** $K$ fölött. $F$ **algebrai bővítése** $K$-nak, ha $F$ minden eleme algebrai $K$ fölött.

### A minimálpolinom egyértelmű létezése

**Tétel.** Tetszőleges $F[x]$ test fölötti polinomgyűrűben minden $J \neq \langle 0 \rangle$ ideálhoz egyértelműen létezik olyan $g \in F[x]$ főpolinom, amire $J = \langle g \rangle$.

*Bizonyítás.* Egzisztencia: legyen $h$ minimális fokszámú polinom $J$-ben, főegyütthatója $b$; $g = b^{-1}h$ főpolinom. Tetszőleges $f \in J$-re maradékos osztással $f = gq + r$, $\deg r < \deg g = \deg h$; mivel $J$ ideál, $r = f - gq \in J$, és $\deg h$ minimalitása miatt $r = 0$. Minden $f \in J$ többszöröse $g$-nek, így $J = \langle g \rangle$.
Unicitás: ha $J = \langle g' \rangle$ is, akkor $g = c'g'$ és $g' = cg$, tehát $g = c'cg$, $c'c$ az egységelem; $c, c'$ konstansok, és $g, g'$ főpolinomok, így $g = g'$. $\square$

### Minimálpolinom

**Definíció.** Legyen $K$ részteste $F$-nek, $\alpha \in F$ algebrai $K$ fölött. Az az egyértelműen meghatározott $g \in K[x]$ főpolinom, amire
$$J = \{ f \in K[x] \mid f(\alpha) = 0 \} = \langle g \rangle,$$
az $\alpha$ **$K$ feletti minimálpolinomja**. $\deg(g)$ az $\alpha$ **$K$ feletti foka**.

**Tétel (a minimálpolinom tulajdonságai).** Ha $\alpha$ $K$ feletti minimálpolinomja $g$, akkor

1. $g$ irreducibilis $K[x]$-ben;
2. tetszőleges $f \in K[x]$-re $f(\alpha) = 0 \iff g \mid f$;
3. $g$ a legalacsonyabb fokszámú főpolinom $K[x]$-ben, amelynek $\alpha$ gyöke.

*Bizonyítás.* (1) Indirekt: ha $g = h_1h_2$, $1 \le \deg h_i < \deg g$ ($\deg g > 0$, hiszen van gyöke), akkor $0 = g(\alpha) = h_1(\alpha)h_2(\alpha)$, így $h_1$ vagy $h_2$ $J$-beli, azaz $g \mid h_1$ vagy $g \mid h_2$ — ellentmond a kisebb fokoknak. (2) a definícióból. (3) Ha $f(\alpha) = 0$, akkor $f \in J$, azaz $g$ többszöröse, tehát $f = g$ vagy $\deg f > \deg g$. $\square$

## Kapocs

- [[concepts/dimatii/testbovites-es-primresztest]] — a bővítés fogalma, algebrai bővítés
- [[concepts/dimatii/egyszeru-testbovites]] — a minimálpolinom adja a $K(\alpha)$ szerkezetét
- [[concepts/dimatii/irreducibilis-polinom]] — a minimálpolinom irreducibilis
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — az egzisztencia-bizonyítás eszköze
- [[concepts/dimatii/foideal]] — a test fölötti polinomgyűrű főideálgyűrű
