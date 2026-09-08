---
tags: [concept]
sources: [10.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# kSAT és 3SAT

A $k$SAT problémák a SAT speciális esetei, ahol minden klózban pontosan $k$ literál szerepel. 3SAT NP-teljes; 2SAT viszont P-beli.

## Definíciók

Legyen $k \geq 1$. Ekkor
$$k\text{SAT} = \{ \langle \varphi \rangle \mid \langle \varphi \rangle \in \text{SAT},\ \varphi \text{ minden tagjában pontosan } k \text{ literál van} \}.$$

A 3SAT-ot tartalmazó klózok átalakíthatóak 3KNF alakra úgy, hogy minden tag pontosan három literált tartalmaz; az új segédváltozók ($x, y, x_1, \ldots$) korábban nem használt ítéletváltozók.

## Polinom idejű visszavezetés tranzitivitása

**Állítás:** $L_1 \leq_p L_2,\ L_2 \leq_p L_3 \Rightarrow L_1 \leq_p L_3$.

**Bizonyítás:** Ha $f$ ($p_1(n)$ idejű) visszavezet $L_1$-et $L_2$-re, és $g$ ($p_2(n)$ idejű) visszavezet $L_2$-t $L_3$-ba, akkor $g \circ f$ visszavezet $L_1$-et $L_3$-ba. Mivel $|f(w)| \leq n + p_1(n)$, a kompozíció időigénye $p_2(n + p_1(n))$ — ez polinom.

## Tétel: 3SAT NP-teljes

**Bizonyítás:**
- 3SAT $\in$ NP: tanúellenőrzés mint SAT-nál.
- SAT $\leq_p$ 3SAT: az alábbi klóz-felosztó transzformáció:

| Eredeti klóz | 3KNF megfelelő |
|---|---|
| $l$ (1 literál) | $l \lor x \lor y,\ l \lor x \lor \neg y,\ l \lor \neg x \lor y,\ l \lor \neg x \lor \neg y$ |
| $l_1 \lor l_2$ | $l_1 \lor l_2 \lor x,\ l_1 \lor l_2 \lor \neg x$ |
| $l_1 \lor l_2 \lor l_3$ | $l_1 \lor l_2 \lor l_3$ (változatlan) |
| $l_1 \lor l_2 \lor l_3 \lor l_4$ | $l_1 \lor l_2 \lor x,\ \neg x \lor l_3 \lor l_4$ |
| $l_1 \lor \cdots \lor l_n\ (n \geq 5)$ | $l_1 \lor l_2 \lor x_1,\ \neg x_1 \lor l_3 \lor x_2,\ \ldots,\ \neg x_{n-3} \lor l_{n-1} \lor l_n$ |

Az $x, y, x_1, \ldots, x_{n-3}$ új segédváltozók. A transzformáció kielégíthetőséget megőriz: ha $l$ kielégíti $\varphi$-t, az új segédváltozókhoz megadható alkalmas értékadás; fordítva, a segédváltozók értéke eltüntethető.

## NP-teljes problémák terjesztése

**Tétel:** Ha $L$ NP-teljes, $L \leq_p L'$ és $L' \in \text{NP}$, akkor $L'$ NP-teljes.

Ez a tranzitivitással együtt lehetővé teszi NP-teljesség bizonyítását ismert NP-teljes problémákból való visszavezetéssel.

## Kapocs

- [[concepts/bvszam/cook-levin-bizonyitas]] — SAT NP-teljes volta (Cook–Levin)
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — NP, NP-teljesség, NP-nehézség definíciói
- [[concepts/bvszam/2sat]] — 2SAT $\in$ P, implikációs gráf
- [[concepts/bvszam/visszavezetes]] — polinom idejű visszavezetés ($\leq_p$)
