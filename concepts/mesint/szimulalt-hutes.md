---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Szimulált hűtés

A hegymászó módszertől csak vezérlési stratégiájában tér el: az új csúcsot véletlenszerűen választja a gyerekek közül, és rosszabb értéket is elfogadhat egy hőmérséklettől függő valószínűséggel.

## Tartalom

### Elfogadási szabály

Az aktuális csúcs ($akt$) gyermekei közül véletlenszerűen választ új csúcsot ($új$), és akkor fogadja el aktuálisnak, ha függvényértéke viszonylag jó (az $f$ minimalizálandó):

- ha $f(új)\le f(akt)$, elfogadja;
- ha $f(új) > f(akt)$, az elfogadás valószínűsége fordítottan arányos az $|f(akt)-f(új)|$ különbséggel: elfogadja, ha

$$e^{\frac{f(akt)-f(új)}{T}} > \mathrm{random}[0,1].$$

### Hűtési ütemterv

Az elfogadás valószínűségét a kitevő $T$ együtthatójával szabályozzuk. Egy $(T_k, L_k)$, $k=1,2,\dots$ ütemtervet készítünk: $L_1$ lépésen keresztül $T_1$, majd $L_2$ lépésen keresztül $T_2$ stb. Ha $T_1, T_2,\dots$ szigorúan monoton csökken, akkor egy ugyanannyival rosszabb függvényértékű új csúcsot kezdetben nagyobb valószínűséggel fogad el a keresés, mint később.

Számpélda ($f(új)=120$, $f(akt)=107$, így a kitevő számlálója $-13$):

| $T$ | $e^{-13/T}$ |
|---|---|
| $10^{10}$ | 0,9999… |
| 50 | 0,77 |
| 20 | 0,52 |
| 10 | 0,2725 |
| 5 | 0,0743 |
| 1 | 0,000002 |

### Algoritmus

```
1. akt := start ; k := 1 ; i := 1
2. while not (akt ∈ T or f(akt) régóta nem változik) loop
3.     if i > L_k then k := k+1 ; i := 1
4.     új := select(Γ(akt) − π(akt))
5.     if f(új) ≤ f(akt) or
6.        (f(új) > f(akt) and e^{(f(akt)−f(új))/T_k} > rand[0,1])
7.     then akt := új
8.     i := i+1
9. endloop
10. return akt
```

A `select` esetei: $\Gamma(akt)=\emptyset$ esetén nem talált megoldást; ha $\Gamma(akt)=\{\pi(akt)\}$, akkor $új := \pi(akt)$; különben $új := select(\Gamma(akt)-\pi(akt))$.

## Kapocs

- [[concepts/mesint/hegymaszo-modszer]] — az alapmódszer, amelynek stratégiáját véletlenítjük
- [[concepts/mesint/tabu-kereses]] — memóriával kezelt alternatíva
- [[concepts/mesint/vezerlesi-strategiak]] — nem módosítható stratégia
