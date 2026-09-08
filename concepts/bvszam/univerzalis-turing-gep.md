---
tags: [concept]
sources: [08.md]
derivation: source
updated: 2026-04-09
---

# Univerzális Turing gép (UTG)

Az univerzális Turing gép ($U$) egy konkrét TG, amely képes szimulálni tetszőleges $M$ Turing gép működését tetszőleges $w$ bemeneten; ez alapozza meg az $L_u \in \text{RE}$ tételt.

## $L_u$ definíciója

$$L_u = \{\langle M, w \rangle \mid w \in L(M)\}$$

ahol $\langle M, w \rangle$ az $M$ TG és a $w$ bemenet kódolása.

## Tétel: $L_u \in \text{RE}$

### Bizonyítás — 4-szalagos UTG

Feltehető, hogy $M$ egyszalagos. $U$ négy szalagot használ:

| Szalag | Tartalom |
|--------|----------|
| 1. (csak olvasható) | $\langle M, w \rangle$ — $M$ leírása és a bemenet |
| 2. | $M$ aktuális szalagtartalma és fejpozíciója |
| 3. | $M$ aktuális állapota |
| 4. | segédszalag |

$U$ működése:
1. Ellenőrzi, hogy a bemenet első része érvényes TG-kódolás-e; ha nem, elutasít.
2. $w$-t a 2. szalagra másolja; $q_0$ kódját a 3. szalagra másolja.
3. **Szimuláció egy lépése:** leolvassa $M$ aktuális szimbólumát (2. szalag) és állapotát (3. szalag); megkeresi a $\delta$-átmenetet az 1. szalagon; előállítja az új tartalmat és állapotot.
4. Ha $M$ elfogadó/elutasító állapotba lép, $U$ is belép saját elfogadó/elutasító állapotába. Különben goto 3.

**Megjegyzés:** Ha $M$ nem áll meg $w$-n, $U$ sem áll meg $\langle M, w \rangle$-n — ezért $U$ csak *felismeri* $L_u$-t, nem *dönti el*.

## Tétel: $L_u \notin \text{R}$

**Bizonyítás (indirekt):** Ha létezne $L_u$-t eldöntő TG, abból megkonstruálható lenne $L_{u\neg}$-t felismerő $M'$; az $M'$ saját kódolásán diagonalizálási paradoxont okoz. Ellentmondás.

## Kapocs

- [[concepts/bvszam/turing-gep]] — DTG definíciója, Church–Turing tézis
- [[concepts/bvszam/tobb-szalagos-turing-gep]] — a 4-szalagos szimuláció alapja
- [[concepts/bvszam/r-re-nyelvek]] — $L_u \in \text{RE} \setminus \text{R}$
- [[concepts/bvszam/visszavezetes]] — $L_u \leq L_h$ visszavezetés
- [[concepts/bvszam/eldonthetetlen-problemak]] — megállási probléma, Rice-tétel
