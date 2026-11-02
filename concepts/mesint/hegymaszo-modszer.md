---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-12
---

# Hegymászó módszer

A lokális keresések alapalgoritmusa: a keresés csak az aktuális csúcsot és annak szülőjét tárolja, és mindig az aktuális csúcs legjobb gyerekére lép.

## Tartalom

### Lokális keresés

A **lokális keresés** olyan [[concepts/mesint/kereso-rendszer]], amely a reprezentációs gráf egy kis részét tárolja a globális munkaterületén. Kezdetben csak a startcsúcsot ismeri; leáll, ha a célcsúcs megjelenik a látókörében, vagy valamilyen okból nem tud tovább keresni. Az eltárolt részgráf csúcsait a részgráf szűk környezetéből vett „jobb" csúcsokra cseréli (keresési szabály). A „jobbság" eldöntéséhez a vezérlési stratégia egy **kiértékelő függvényt** (cél-, rátermettségi-, heurisztikus függvény) használ, amely annál jobb értéket ad, minél közelebb esik a csúcs a célhoz.

### A módszer

- **Globális munkaterület:** az aktuális csúcs ($akt$) és szülője ($\pi(akt)$, a megelőző aktuális csúcs). Kezdetben $akt$ = startcsúcs.
- **Terminál**, ha $akt$ célcsúcs vagy zsákutca.
- **Keresési szabály:** $akt$-t egy gyerekére ($\Gamma(akt)$ elemére) cseréli.
- **Vezérlési stratégia:** mindig az $akt$ legjobb – lehetőleg nem a szülőcsúcsként nyilvántartott – gyerekére lép.

Változat: nem engedi meg, hogy az aktuális csúcsot rosszabb értékű csúcsra cseréljük (ilyenkor a keresés inkább leáll).

### Algoritmus

```
1. akt := start
2. while akt ∉ T loop
3.     akt := arg opt_f(Γ(akt) − π(akt))
4. endloop
5. return akt
```

A $\Gamma(akt)-\pi(akt)$ kiválasztás esetei:

- $\Gamma(akt)=\emptyset$: nem talált megoldást;
- $\Gamma(akt)=\{\pi(akt)\}$: $akt := \pi(akt)$ (visszalépés a szülőre);
- különben $akt := \arg\mathrm{opt}_f(\Gamma(akt)-\pi(akt))$.

A bejárt út megadásához az $akt$ egymás után felvett értékeit is össze kell gyűjteni.

A deck Hanoi tornyai példán szemlélteti a módszert a [[concepts/mesint/hanoi-tornyai]] állapotgráfján: a számok az állapotok kiértékelő értékei, és két különböző startból indulva eltérő utak adódnak.

### Értékelés

- **Előny:** könnyű implementálni.
- **Hátrányok:**
  - csak erős heurisztika esetén sikeres: különben „eltéved" (nem talál megoldást), sőt zsákutcába „beragad". Segíthet:
    - véletlenül választott startcsúcsból újra- és újraindítás (*random restart local search*);
    - $k$ aktuális csúcs legjobb $k$ gyerekére lépés (*local beam search*);
    - a mohó stratégia gyengítése és véletlenítése ([[concepts/mesint/szimulalt-hutes]], *simulated annealing*).
  - lokális optimum körül vagy ekvidisztans felületen (azonos értékű szomszédos csúcsok között) található körön végtelen működésbe eshet. Segíthet a memória növelése: [[concepts/mesint/tabu-kereses]].

## Kapocs

- [[concepts/mesint/kereso-rendszer]] — a keretrendszer, amelynek példánya
- [[concepts/mesint/tabu-kereses]] — memóriával bővített változat
- [[concepts/mesint/szimulalt-hutes]] — véletlenített vezérlésű változat
- [[concepts/mesint/vezerlesi-strategiak]] — nem módosítható általános stratégia
- [[concepts/mesint/heurisztika]] — a kiértékelő függvény forrása
- [[concepts/mesint/hanoi-tornyai]] — szemléltető példa
