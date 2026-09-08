---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Eldönthetetlenség az elsőrendű logikában

Az ítéletkalkulustól eltérően az elsőrendű logikában a formulák érvényessége, kielégíthetősége és kielégíthetetlensége algoritmikusan nem dönthető el; egyedül a kielégíthetetlenség (illetve érvényesség) ismerhető fel.

## Az érvényesség eldönthetetlen

Legyen
$$\textsc{ValidityPred} = \{\langle \varphi \rangle \mid \varphi \text{ érvényes elsőrendű logikai formula}\}.$$

### 2.32. tétel: $\textsc{ValidityPred} \notin \mathrm{R}$

A bizonyítás megmutatja, hogy $\mathrm{PMP} \leq \textsc{ValidityPred}$. Adott $D = \{[\tfrac{u_1}{v_1}], \ldots, [\tfrac{u_k}{v_k}]\}$ dominókészlethez (a $\Sigma = \{a_1, \ldots, a_n\}$ ábécé felett) olyan $\varphi_D$ formulát konstruálunk, amely pontosan akkor érvényes, ha $D$-nek van megoldása.

Az elsőrendű nyelv: egy kétváltozós $p$ predikátum, $n$ darab egyváltozós $f_{a_1}, \ldots, f_{a_n}$ függvényjel (egy-egy ábécébetűt fűz hozzá), és egy $c$ konstans. Legyen $\varphi_D = (\varphi_1 \wedge \varphi_2) \to \varphi_3$, ahol

- $\varphi_1 = p(f_{u_1}(c), f_{v_1}(c)) \wedge \ldots \wedge p(f_{u_k}(c), f_{v_k}(c))$ — az egyes dominók,
- $\varphi_2 = \forall x \forall y\, \big(p(x,y) \to (p(f_{u_1}(x), f_{v_1}(y)) \wedge \ldots \wedge p(f_{u_k}(x), f_{v_k}(y)))\big)$ — dominó hozzáfűzése,
- $\varphi_3 = \exists z\, p(z, z)$ — a felső és alsó szó megegyezik.

(Itt $f_{a_{i_1} \ldots a_{i_m}}(t)$ az $f_{a_{i_1}}(\ldots(f_{a_{i_m}}(t))\ldots)$ term rövidítése.)

Az a kulcsinterpretáció, amelyben $f_{a_i}^I(u) = a_i u$ és $p^I(u,v)$ pontosan akkor igaz, ha $u, v$ egy közös prefix-megoldás (dominósorozat) felső, illetve alsó szava, mutatja: $\varphi_D$ érvényes $\iff$ $D$-nek van megoldása. Mivel $\mathrm{PMP} \notin \mathrm{R}$, ezért $\textsc{ValidityPred} \notin \mathrm{R}$.

## 2.33. következmény: kielégíthetőség és következmény

Legyen $F$ elsőrendű formulák tetszőleges halmaza, $\varphi$ egy formula. Az alábbi kérdések **mind eldönthetetlenek**:

1. Kielégíthetetlen-e $\varphi$?
2. Kielégíthető-e $\varphi$?
3. Teljesül-e $F \models \varphi$?

## RE-besorolás

- A **kielégíthetetlenség** (és vele az érvényesség) eldöntése **RE-beli**: van olyan algoritmus — pl. az elsőrendű logika **rezolúciós algoritmusa** —, ami pontosan a kielégíthetetlen formulákon áll meg $igen$ válasszal.
- A **kielégíthetőség** eldöntése **nincs is RE-ben**: mivel a kielégíthetőség és a kielégíthetetlenség egymás komplementerei, és RE nem zárt komplementerre, a kielégíthetetlenség RE-belisége kizárja, hogy a kielégíthetőség is RE-beli legyen.

## Kapocs

- [[concepts/bvszam/post-megfelelkezesi-problema]] — a visszavezetés forrása
- [[concepts/bvszam/visszavezetes]] — many-one visszavezetés
- [[concepts/bvszam/r-re-nyelvek]] — R, RE, és komplementerre való zártság
- [[concepts/bvszam/eldonthetetlen-problemak]] — további eldönthetetlen problémák
