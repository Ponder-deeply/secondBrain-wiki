---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Többváltozós integrálhatóság és kritériumai

Az oszcillációs összeg eltűnése jellemzi az integrálhatóságot; elegendő feltétel, hogy a korlátos függvény egy Jordan-nullmértékű halmaztól eltekintve folytonos legyen — de ez a feltétel nem szükséges.

## Tartalom

### Oszcillációs összeg

Legyen $A \in \mathcal{J}_p$, $f : A \to \mathbb{R}$ korlátos, $\mathcal{F} = \{B_1,\dots,B_n\}$ az $A$ egy felosztása. Az $f$-nek az $\mathcal{F}$-hez tartozó **oszcillációs összege**

$$\Omega(f,\mathcal{F}) = \sum_{i=1}^n t_p(B_i)\left(\sup_{B_i} f - \inf_{B_i} f\right) = S(f,\mathcal{F}) - s(f,\mathcal{F}).$$

### Az integrálhatóság átfogalmazásai

- $f$ akkor és csak akkor integrálható, ha minden $\varepsilon > 0$-hoz van olyan $\mathcal{F}$ felosztás, hogy $\Omega(f,\mathcal{F}) < \varepsilon$.
- $f$ akkor és csak akkor integrálható, ha minden végtelenül finomodó $\mathcal{F}_n$ felosztássorozatra $\Omega(f,\mathcal{F}_n) \to 0$.

### Elegendő feltétel: majdnem mindenütt folytonosság

**Tétel.** Legyen $A \in \mathcal{J}_p$, $f : A \to \mathbb{R}$ korlátos. Ha $f$ egy nullmértékű halmaz kivételével folytonos, akkor integrálható.

**Bizonyítás.** Legyen $\varepsilon > 0$ és $M > 0$ felső korlátja $|f|$-nek. Legyen $C = \{x \in A : f \text{ folytonos } x\text{-ben}\}$; a feltétel szerint $t(A) = t(C)$.

- Elég finom kockázásban a $C$ belső kockái $\varepsilon/(4M)$-nél pontosabban kitöltik $C$-t: $b_n(C) > t(A) - \varepsilon/(4M)$. Legyen $K$ ezeknek a kockáknak az uniója; $K$ kompakt, és $t(K) > t(A) - \varepsilon/(4M)$.
- $f$ folytonos $K$-n, tehát a Heine-tétel miatt egyenletesen folytonos; az $\varepsilon/(2t(A))$-hoz vegyük az egyenletes folytonossághoz tartozó $\delta$-t.
- Osszuk $K$-t $\delta$-nál kisebb átmérőjű $R_1,\dots,R_N$ kis kockákra, és legyen $\mathcal{F} = \{A\setminus K, R_1,\dots,R_N\}$.

Ekkor

$$\Omega(f,\mathcal{F}) \leq t(A\setminus K)\cdot 2M + \sum_{i=1}^N t(R_i)\cdot\frac{\varepsilon}{2t(A)} \leq \frac{\varepsilon}{4M}\cdot 2M + t(K)\cdot\frac{\varepsilon}{2t(A)} < \varepsilon. \qquad \square$$

### A megfordítás nem igaz

Legyen $\{q_1, q_2, \dots\}$ a $\mathbb{Q}^p$ egy felsorolása, és

$$f(q_n) = \frac{1}{n}, \qquad f(x) = 0 \ \text{ ha } x \in \mathbb{R}^p \setminus \mathbb{Q}^p.$$

Ez a függvény bármely Jordan-mérhető halmazon integrálható, és az integrálja $0$; a szakadási pontjainak halmaza viszont sűrű, tehát nemhogy nullmértékű nem lenne — Jordan-mérhető sem.

### Kitekintés: a Lebesgue-kritérium

A Jordan-mérték kiterjesztése a **Lebesgue-mérték**. A mértékelmélet kurzuson bebizonyítjuk, hogy bármely $A \in \mathcal{J}_p$ halmaz és korlátos $f : A \to \mathbb{R}$ esetén $f$ akkor és csak akkor Riemann-integrálható, ha egy **Lebesgue-nullmértékű** halmaz kivételével folytonos. A fenti ellenpélda éppen azt mutatja, hogy a Jordan-nullmértékűség ehhez túl erős követelmény.

## Kapocs

- [[concepts/analiii/jordan-mertek-szerinti-integral]] — az alsó és felső integrál, amelyek különbsége az oszcillációs összeg határértéke
- [[concepts/analiii/jordan-nullmerteku-halmazok]] — a kivételes halmazok fogalma, és a folytonos grafikonok nullmértékűsége
- [[concepts/analiii/also-felso-osszegek-kockazassal]] — a végtelenül finomodó sorozatokra vonatkozó kritérium alapja
- [[concepts/analii/integralhato-fuggvenyek]] — az egyváltozós Darboux-kritérium, amelynek ez a szó szerinti általánosítása; ott $\Omega(f,\tau) = \sum (M_i-m_i)(x_i-x_{i-1})$, itt a hosszak helyére Jordan-mértékek lépnek
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — az egyváltozós „folytonos $\Rightarrow$ integrálható" tétel, amelynek ez a nullmértékű kivételhalmazt megengedő erősítése
- [[concepts/analii/riemann-fuggveny]] — az itt szereplő ellenpélda a Riemann-függvény többdimenziós rokona
