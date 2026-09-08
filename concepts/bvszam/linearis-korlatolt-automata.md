---
tags: [concept]
sources: [10.md]
derivation: source
updated: 2026-04-09
---

# Lineárisan korlátolt automata (LKA)

Az LKA a veremautomata és a Turing gép közötti eszköz: TG-hez hasonlóan működik, de munkaterülete az input hosszával arányosan korlátolt.

## Definíció

Az LKA egy nemdeterminisztikus Turing gép, amelynek:
- szalagja véges: a bemenet bal és jobb végét speciális jelekkel ($\$_L$, $\$_R$) határolják,
- a fej nem léphet ki ezen határjeleken túl (a munkaterület $\leq |w|$ cella),
- elfogadás: a szokásos TG-elfogadó állapottal.

## $\mathcal{L}_1$ és LKA kapcsolata

**Tétel:** $\mathcal{L}_1 =$ LKA által felismert nyelvek osztálya.

(Bizonyítás: $\mathcal{L}_1 \to \text{LKA}$: minden 1-típusú grammatikához megadható LKA a levezetés nemdeterminisztikus szimulációjával. $\text{LKA} \to \mathcal{L}_1$: LKA konfigurációit kódoló grammatikából 1-típusú grammatika.)

## Eldönthetőség

Minden LKA $L(A)$ nyelve eldönthető ($L(A) \in \text{R}$), mivel az összes lehetséges konfiguráció száma véges és felülről becsülhető $m(u) = |Q| \cdot |u| \cdot |\Gamma|^{|u|}$-val.

Ez nem ellentmondás a nondeterminizmussal — az LKA elfogadási problémája dönthetővé válik, mert a keresési tér véges és felsorolható.

## Helye a hierarchiában

$$\mathcal{L}_2 \subsetneq \mathcal{L}_1 \subsetneq \text{R} \subsetneq \text{RE} = \mathcal{L}_0$$

## Kapocs

- [[concepts/bvszam/l0-re-ekvivalencia]] — részletes összefoglaló + diagonalizáció
- [[concepts/bvszam/kornyezetfuggo-nyelvek]] — $\mathcal{L}_1$ grammatikák
- [[concepts/bvszam/turing-gep]] — TG, amelynek LKA korlátozottabb változata
