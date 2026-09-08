---
tags: [concept]
sources: [10.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Cook–Levin tétel bizonyítása

A Cook–Levin tétel szerint SAT NP-teljes. A bizonyítás megmutatja, hogy minden $L \in \text{NP}$ visszavezethető SAT-ra polinom időben, a számítás „táblakódolásával".

## Táblakódolás

Legyen $M$ egy $p(n)$ lépésidejű NTG, amely $L$-et ismeri fel. Az $M$ $w$ bemenetű számítása felírható egy $(p(n)+1) \times (2p(n)+3)$ méretű **tableau** (tábla) $T$ segítségével, amelynek minden cellájában egy $\Delta = Q \cup \Gamma \cup \{\#\}$ feletti szimbólum áll.

Változók: $x_{i,j,s}$ — igaz, ha a $T$ tábla $(i,j)$ cellájában $s \in \Delta$ áll.

## A $\varphi_w$ formula részei

$$\varphi_w := \varphi_0 \land \varphi_{start} \land \varphi_{move} \land \varphi_{accept}$$

**$\varphi_0$** — minden cellában pontosan egy szimbólum áll:
$$\varphi_0 := \bigwedge_{i,j} \left( \bigvee_{s \in \Delta} x_{i,j,s} \right) \land \bigwedge_{i,j} \bigwedge_{s \neq t} (\neg x_{i,j,s} \lor \neg x_{i,j,t})$$

**$\varphi_{start}$** — az első sor a $w$ bemenethez tartozó kezdőkonfigurációt kódolja.

**$\varphi_{move}$** — minden egymást követő sorrpár érvényes TG-lépésnek felel meg. Minden $(i,j)$ pozícióra $\psi_{i,j}$ tiltja az „illegális ablakokat" (2×3-as szomszédság):
$$\psi_{i,j} := \bigwedge_{\substack{(b_1,\ldots,b_6) \\ \text{illegális ablak}}} \left( \neg x_{i,j-1,b_1} \lor \neg x_{i,j,b_2} \lor \neg x_{i,j+1,b_3} \lor \neg x_{i+1,j-1,b_4} \lor \neg x_{i+1,j,b_5} \lor \neg x_{i+1,j+1,b_6} \right)$$
Ez KNF alakú — szemben az „összes legális ablak" diszjunkciós változatával.

**$\varphi_{accept}$** — az utolsó sorban van elfogadó állapot:
$$\varphi_{accept} = \bigvee_{j=2}^{2p(n)+2} x_{p(n)+1,\, j,\, q_f}$$

## Méret és visszavezetés

| Rész | Méret |
|------|-------|
| $\varphi_0$ | $O(p^2(n))$ |
| $\varphi_{start}$ | $O(p(n))$ |
| $\varphi_{move}$ | $O(p^2(n))$ |
| $\varphi_{accept}$ | $O(p(n))$ |

$\varphi_w$ összesen $O(p^2(n))$ méretű, tehát polinom időben megkonstruálható.

$$w \in L \iff \varphi_w \text{ kielégíthető} \iff \langle \varphi_w \rangle \in \text{SAT}$$

Mivel ez minden $L \in \text{NP}$-re fennáll: SAT NP-nehéz. Mivel SAT $\in$ NP, SAT NP-teljes.

## Kapocs

- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — NP, NP-teljesség definíciói
- [[concepts/bvszam/ksat-es-3sat]] — SAT $\leq_p$ 3SAT; 3SAT NP-teljes
- [[concepts/bvszam/visszavezetes]] — polinom idejű visszavezetés ($\leq_p$) fogalma
- [[concepts/bvszam/nemdeterminisztikus-turing-gep]] — NTG mint az NP alap modellje
