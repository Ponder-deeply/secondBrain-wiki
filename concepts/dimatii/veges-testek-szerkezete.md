---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Véges testek szerkezete

A véges test elemszáma prímhatvány, minden eleme gyöke $x^q - x$-nek, a $q$ elemű test az $x^q-x$ felbontási teste, ezért egyértelmű; résztesteit az exponens osztói adják, multiplikatív csoportja ciklikus.

## Tartalom

### Az elemszám

**Tétel.** Tetszőleges $F$ véges test esetén $|F| = p^n$, ahol $\mathbb{F}_p$ az $F$ prímteste és $[F : \mathbb{F}_p] = n$.

*Bizonyítás.* Ha $F = \mathbb{F}_p$, akkor $|F| = p^1$. Különben van $K$ résztest, amelyre $[F:K] = n$, azaz $F$ $n$-dimenziós vektortér $K$ felett az $\{a_1,\dots,a_n\}$ bázissal. Minden elem $a_1k_1 + \dots + a_nk_n$ alakú, és minden $k_i$ helyébe $|K|$ különböző érték írható, így $|F| = |K|^n$. Speciálisan a prímtest az $F$ legszűkebb résztestét adja, ezért $|F| = |\mathbb{F}_p|^n = p^n$.

### $a^q = a$

**Tétel.** $q$ elemű $F$ testben minden $a \in F$-re $a^q = a$.

*Bizonyítás.* $a = 0$ és $a = 1$ triviális. A nem nulla elemek $q-1$ elemű csoportot alkotnak; ha $n = |a| > 1$, a [[concepts/dimatii/mellekosztaly-es-lagrange-tetel]] (Lagrange-tétel) szerint $n \mid |F^*| = q-1$, $q-1 = ns$, így $a^{q-1} = (a^n)^s = 1^s = 1$, tehát $a^q = a$.

### $x^q - x$ felbontási teste

**Tétel.** Legyen $F$ $q$ elemű test, $K$ résztestje. Ekkor $F$ az $f = x^q - x \in K[x]$ polinom $K$ feletti felbontási teste, és

$$x^q - x = \prod_{a \in F}(x - a).$$

*Bizonyítás.* Az előző tétel miatt $F$ minden eleme gyöke $f$-nek; $\deg f = q$, így legfeljebb $q$ gyöke van, tehát pontosan $F$ elemei a gyökök. Nincs szűkebb test, ami $f$ összes gyökét tartalmazná.

### Létezés

**Tétel.** Minden $p$ prím és $n \ge 1$ esetén van $p^n$ elemű véges test.

*Bizonyítás.* Legyen $q = p^n$, $f = x^q - x \in \mathbb{F}_p[x]$, és $F$ az $f$ felbontási teste $\mathbb{F}_p$ felett. $f$-nek nincs többszörös gyöke: $f' = qx^{q-1} - 1 = -1$ ($q \equiv 0 \bmod p$), így $(f, f') = 1$ (lásd [[concepts/dimatii/gyok-multiplicitasa]], [[concepts/dimatii/polinom-algebrai-derivaltja]]). Legyen $S = \{a \in F : a^q - a = 0\}$. Ekkor:

1. $S$-nek $q$ eleme van ($f$ gyökei);
2. $0, 1 \in S$;
3. $a, b \in S$ esetén $(a-b)^q = a^q - b^q = a - b$ ([[concepts/dimatii/frobenius-egyenloseg]]), így $a - b \in S$;
4. $a, b \ne 0$ esetén $(ab^{-1})^q = a^qb^{-q} = ab^{-1}$, így $ab^{-1} \in S$.

Tehát $S$ test, és tartalmazza $f$ összes gyökét; $F$ a legszűkebb ilyen, így $F = S$, és $|F| = q$.

### Egyértelműség

**Tétel.** Tetszőleges $q = p^n$ elemű véges test izomorf az $f = x^q - x$ polinom $\mathbb{F}_p$ feletti felbontási testével.

*Bizonyítás.* Az elemszámtétel szerint $F$ karakterisztikája $p$ és $F : \mathbb{F}_p$; az előző tétel szerint $F$ az $f$ felbontási teste; a [[concepts/dimatii/felbontasi-test]] egyértelműsége adja az állítást. Ezért beszélünk *a* $q$ elemű testről, $\mathbb{F}_q$.

### Résztestek

**Tétel.** $\mathbb{F}_q$ ($q = p^n$) minden résztestje $p^m$ elemű, ahol $m \mid n$, és minden $m \mid n$-hez egyértelműen létezik $p^m$ elemű résztest.

**Példa.** $\mathbb{F}_{2^{30}}$ résztestei: $\mathbb{F}_{2^6}, \mathbb{F}_{2^{10}}, \mathbb{F}_{2^{15}}$ alatt $\mathbb{F}_{2^2}, \mathbb{F}_{2^3}, \mathbb{F}_{2^5}$, legalul $\mathbb{F}_2$; a tartalmazás az osztóság rendezését követi.

### Multiplikatív csoport

**Tétel.** Tetszőleges $\mathbb{F}_q$ véges test $\mathbb{F}_q^*$ multiplikatív csoportja ciklikus ([[concepts/dimatii/ciklikus-csoport]]). Generáló elemét az $\mathbb{F}_q$ **primitív elemének** nevezzük (vö. [[concepts/dimatii/primitiv-gyok]]).

**Tétel (bővítőelem létezése).** Ha $\mathbb{F}_r$ az $\mathbb{F}_q$ véges bővítése, akkor $\mathbb{F}_r$ egyszerű bővítése $\mathbb{F}_q$-nak, és $\mathbb{F}_r$ minden primitív eleme megfelelő bővítőelem.

**Következmény.** Minden $\mathbb{F}_q$-hoz és $n$ pozitív egészhez létezik $n$-edfokú irreducibilis polinom $\mathbb{F}_q[x]$-ben: ha $\mathbb{F}_r = \mathbb{F}_q(\alpha)$, akkor $\alpha$ minimálpolinomja ilyen. (A diák ezt a kérdést — mindig van-e $n$-edfokú irreducibilis $\mathbb{F}_p$ felett — a létezéstétel előtt nyitva hagyja; a kérdésre ez a következmény felel igennel.)

## Kapocs

- [[concepts/dimatii/veges-testek]] — a faktorgyűrűs konstrukció ($\mathbb{F}_p[x]/\langle f \rangle$)
- [[concepts/dimatii/felbontasi-test]] — az egyértelműség eszköze
- [[concepts/dimatii/frobenius-egyenloseg]] — $(a-b)^q = a^q - b^q$
- [[concepts/dimatii/ciklikus-csoport]] — $\mathbb{F}_q^*$ ciklikus
- [[concepts/dimatii/primitiv-gyok]] — a prímtest esete
- [[concepts/dimatii/mellekosztaly-es-lagrange-tetel]] — $a^q = a$ bizonyítása
- [[concepts/dimatii/algebrai-elem-es-minimalpolinom]] — az irreducibilis polinom mint minimálpolinom
