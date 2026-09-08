---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Jordan-nullmértékű halmazok

Egy halmaz Jordan-nullmértékű, ha külső mértéke $0$; ezek a halmazok mindig mérhetők, és a $k(\partial A) = 0$ kritérium révén ők döntik el, hogy egy halmaz Jordan-mérhető-e.

## Tartalom

### Definíció

$A \subset \mathbb{R}^p$ **(Jordan-)nullmértékű**, ha $k(A) = 0$.

Mivel $0 \leq b(A) \leq k(A) = 0$, minden nullmértékű halmaz automatikusan mérhető, és $t(A) = 0$.

### Alaptulajdonságok

- Nullmértékű halmaz minden részhalmaza is nullmértékű (a külső mérték monoton).
- Véges sok nullmértékű halmaz uniója is nullmértékű (a külső mérték szubadditív).
- Minden nullmértékű halmaz mérhető.

Hangsúlyozandó, hogy csak **véges** unióról van szó: a Jordan-mértéknél nincs megszámlálható additivitás, ez a Lebesgue-mérték felé mutató lényeges különbség.

### Mérhetőségi kritérium

$A \subset \mathbb{R}^p$ akkor és csak akkor Jordan-mérhető, ha $\partial A$ nullmértékű, azaz $k(\partial A) = 0$. Ez a $k(A) = b(A) + k(\partial A)$ azonosságból következik, lásd [[concepts/analiii/kulso-belso-mertek-tulajdonsagai]].

### Folytonos függvény grafikonja nullmértékű

**Lemma.** Legyen $K \subset \mathbb{R}^p$ kompakt és $f : K \to \mathbb{R}$ folytonos. Ekkor

$$\operatorname{graph} f = \{(x_1,\dots,x_p, f(x_1,\dots,x_p)) : (x_1,\dots,x_p) \in K\}$$

nullmértékű a $(p+1)$-dimenziós Jordan-mérték szerint.

**Bizonyítás.** $K$ belefér egy nagy, egész koordinátájú $R$ téglába. A Heine-tétel miatt $f$ egyenletesen folytonos; adott $\varepsilon > 0$-hoz legyen $\delta$ az egyenletes folytonossághoz tartozó szám. Ha $n > \sqrt{p}/\delta$, akkor az $1/n$ élű kiskockák átmérője kisebb $\delta$-nál. $R$-et felkockázva minden kis kocka fölött a grafikon belefér egy legfeljebb $\varepsilon$ magas hasábba, ezért

$$k(\operatorname{graph} f) \leq t(R) \cdot \varepsilon.$$

Ez minden $\varepsilon > 0$-ra igaz, tehát $k(\operatorname{graph} f) = 0$. $\square$

### Következmények

- Minden síklap nullmértékű.
- Minden poliéder mérhető (határa véges sok síklap).
- A gömb mérhető (határa két folytonos függvény grafikonja).
- Minden korlátos konvex halmaz mérhető (bizonyítás nélkül, LTS2).

## Kapocs

- [[concepts/analiii/kulso-belso-mertek-tulajdonsagai]] — innen jön a $k(A) = b(A) + k(\partial A)$ azonosság, amelyre a mérhetőségi kritérium épül
- [[concepts/analiii/jordan-merheto-halmazok-gyuruje]] — a mérhető halmazok zártsága unióra, metszetre, különbségre a határok nullmértékűségén múlik
- [[concepts/analiii/tobbvaltozos-integralhatosag]] — ha egy korlátos függvény nullmértékű halmaztól eltekintve folytonos, akkor integrálható
- [[concepts/analii/egyenletes-folytonossag]] — a grafikonlemma bizonyításának motorja a Heine-tétel; itt ugyanaz az egyváltozós tétel dolgozik kompakt $K \subset \mathbb{R}^p$ halmazon
