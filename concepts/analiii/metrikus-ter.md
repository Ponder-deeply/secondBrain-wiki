---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.1–1.2. pont"]
derivation: source
updated: 2026-09-07
---

# Metrikus tér

A metrikus tér az a minimális struktúra, amelyben a „távolság" fogalma értelmes: egy nemüres ponthalmaz és egy három axiómának eleget tevő távolságfüggvény. Az Analízis III. topológiai apparátusa — konvergencia, nyíltság, teljesség, kompaktság — ezen az egyetlen definíción nyugszik.

## Tartalom

### Definíció

**Metrikus tér:** a $(M, d)$ pár, ahol

- $M \neq \emptyset$ a pontok halmaza (*a tér*),
- $d : M \times M \to [0, \infty)$ a *metrika* (távolság), amelyre

1. $\forall x, y \in M:\ d(x,y) \geq 0$, és $d(x,y) = 0 \iff x = y$;
2. $\forall x, y \in M:\ d(x,y) = d(y,x)$ (szimmetria);
3. $\forall x, y, z \in M:\ d(x,y) + d(y,z) \geq d(x,z)$ (háromszög-egyenlőtlenség).

### Példák

- **Diszkrét metrika.** Tetszőleges $M$-en $d(x,y) = 1$ ha $x \neq y$, és $0$ ha $x = y$.
- **Euklideszi távolság.** $M = \mathbb{R}^p$, $d(x,y) = |y - x| = \sqrt{\sum_{i=1}^p |y_i - x_i|^2}$.
- **Taxi-metrika.** $M = \mathbb{R}^p$, $d(x,y) = \sum_{i=1}^p |y_i - x_i|$.
- **Maximum-metrika.** $M = \mathbb{R}^p$, $d(x,y) = \max_{1 \leq i \leq p} |y_i - x_i|$.
- **Függvénytér.** $M = C[a,b]$, a folytonos $[a,b] \to \mathbb{R}$ függvények vektortere, $d(f,g) = \max_{x \in [a,b]} |g(x) - f(x)|$.

Ugyanazon az $M$ halmazon több, egymástól lényegesen különböző metrika is élhet, és a konvergencia is, a topológia is függhet a választástól — a $C[0,1]$ tér az $L^1$ és az $L^\infty$ metrikával erre a szokásos ellenpélda (lásd [[concepts/analiii/ekvivalens-normak]]).

## Kapocs

- [[concepts/analiii/normalt-vektorter]] — a $d(x,y) = \|y-x\|$ képlet minden normából metrikát csinál
- [[concepts/analiii/konvergencia-metrikus-terben]] — a metrika első alkalmazása: gömbök és limesz
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — mikor „nincs lyuk" a térben
- [[concepts/analiii/kompakt-halmazok]] — kompaktság tetszőleges metrikus térben
- [[concepts/analiii/felmetrikus-ter]] — mi marad, ha a $\rho(x,y)=0 \Rightarrow x=y$ axiómát elejtjük
- [[concepts/analiii/metrikabol-uj-metrika]] — metrika transzformálása és leszűkítése
- [[concepts/analiii/metrikus-terek-szorzata]] — a szorzatmetrika; a $(\mathbb{K}^n,\rho_p)$ terek mint szorzatok
- [[concepts/analiii/ekvivalens-metrikak]] — mikor cserélhető fel két metrika büntetlenül
- [[concepts/analiii/topologikus-ter]] — a metrika elhagyása: csak a nyílt halmazok rendszere marad
