---
tags: [concept]
sources: [07.md]
derivation: source
updated: 2026-09-04
---

# Aszimptotikus jelölések ($O$, $\Omega$, $\Theta$)

Az aszimptotikus jelölések $\mathbb{N} \to \mathbb{R}_0^+$ függvények nagyságrendjének összehasonlítására szolgálnak; Edmund Landau-tól származnak.

## Definíció

$$O(g) := \{ f \mid \exists c > 0,\ \exists N \in \mathbb{N},\ \forall n > N : f(n) \le c \cdot g(n) \}$$

Hasonlóan: $f = \Omega(g) \Leftrightarrow g = O(f)$, és $f = \Theta(g) \Leftrightarrow f = O(g)$ és $f = \Omega(g)$.

## Relációs tulajdonságok

Az $O$, $\Omega$, $\Theta$ 2-ágú relációnak tekinthető a függvényuniverzumon:
- **Tranzitív:** $f = O(g),\ g = O(h) \Rightarrow f = O(h)$ (hasonlóan $\Omega$-ra és $\Theta$-ra)
- **Reflexív:** $f = O(f)$
- **$\Theta$ szimmetrikus** és **ekvivalenciareláció** — az ekvivalenciaosztályokat a „legegyszerűbb" tagjukkal szokás jelölni (pl. $1$, $n$, $n^2$, $\log n$, $2^n$)
- **$O$, $\Omega$ fordított szimmetrikus:** $f = O(g) \Leftrightarrow g = \Omega(f)$

## Zártsági tulajdonságok

- **Összeadás:** $f, g = O(h) \Rightarrow f + g = O(h)$ (és $\Omega$, $\Theta$-ra is)
- **Pozitív konstanssal szorzás:** $c > 0,\ f = O(g) \Rightarrow c \cdot f = O(g)$
- **Szekvenciatétel:** $f + g = \Theta(\max\{f, g\})$ — az összeg aszimptotikus nagyságrendjét a domináns tag határozza meg

Részletesen: [[concepts/bvszam/zartsagi-tulajdonsagok]].

## Határértékes karakterizáció

Ha $\lim_{n\to\infty} f(n)/g(n)$ létezik:
- $\to +\infty \Rightarrow f = \Omega(g)$ és $f \neq O(g)$
- $\to c > 0 \Rightarrow f = \Theta(g)$
- $\to 0 \Rightarrow f = O(g)$ és $f \neq \Omega(g)$

## Konkrét összefüggések

- $p(n) = a_k n^k + \cdots + a_0$ ($a_k > 0$) esetén $p(n) = \Theta(n^k)$
- Minden $p(n)$ polinomra és $c > 1$ konstansra: $p(n) = O(c^n)$, de $p(n) \neq \Omega(c^n)$
- $c > d > 1$: $d^n = O(c^n)$, de $d^n \neq \Omega(c^n)$
- $a, b > 1$: $\log_a n = \Theta(\log_b n)$
- $c > 0$: $\log n = O(n^c)$, de $\log n \neq \Omega(n^c)$

## Kapocs

- [[concepts/bvszam/turing-gep]] — időigény mérésére $O$-jelölést alkalmaz
- [[concepts/bvszam/tobb-szalagos-turing-gep]] — a $k$-szalagos TG szimulálásának időköltsége $O(f(n)^2)$
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — a komplexitásosztályok aszimptotikus korlátokkal definiáltak
