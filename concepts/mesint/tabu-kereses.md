---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-12
---

# Tabu keresés

A hegymászó módszer memóriával bővített változata: a legutóbb érintett csúcsokat egy Tabu halmazban tartja, és oda nem lép vissza, így a rövid köröket elkerüli.

## Tartalom

### A módszer

- **Globális munkaterület:** az aktuális csúcs ($akt$), a keresés során utoljára érintett néhány csúcs ($Tabu$, sor adatszerkezet) és az eddigi legjobb csúcs ($opt$). Kezdetben $akt$ és $opt$ a startcsúcs, $Tabu$ üres.
- **Terminál**, ha $opt$ célcsúcs, vagy régóta nem változik, illetve $akt$ zsákutca.
- **Keresési szabály:** az aktuális csúcsot a legjobb gyerekére cseréli, aktualizálja a $Tabu$ halmazt (a lecserélt aktuális csúcsot elhelyezi benne), és ha $akt$ jobb, mint $opt$, akkor $opt$ új értéke $akt$ lesz.
- **Vezérlési stratégia:** mindig az $akt$ legjobb – de a $Tabu$ halmazban nem tárolt – gyerekére lép.

### Algoritmus

```
1. akt, opt, Tabu := start, start, ∅
2. while not (opt ∈ T or opt régóta nem változik) loop
3.     akt := arg opt_f(Γ(akt) − Tabu)
4.     Tabu := Módosít(akt, Tabu)
5.     if f(akt) jobb, mint f(opt) then opt := akt
6. endloop
7. return akt
```

A 3. sor esetei: $\Gamma(akt)=\emptyset$ esetén nem talált megoldást; ha $\Gamma(akt)\subseteq Tabu$, akkor $akt := \arg\mathrm{opt}_f(\Gamma(akt))$ (a tabu felülbírálható); különben $akt := \arg\mathrm{opt}_f(\Gamma(akt)-Tabu)$.

### Értékelés

- **Előny:** a tabu méreténél rövidebb köröket észleli, ez segíthet a lokális optimum, illetve az ekvidisztans felület körüli körök leküzdésében.
- **Hátrányok:** a $Tabu$ méretét kísérletezéssel kell belőni; zsákutcába futva a nem módosítható stratégia miatt beragad.

## Kapocs

- [[concepts/mesint/hegymaszo-modszer]] — az alapmódszer, amelyet bővít
- [[concepts/mesint/szimulalt-hutes]] — másik kiút a lokális optimumból
- [[concepts/mesint/kereso-rendszer]] — keretrendszer
- [[concepts/mesint/hanoi-tornyai]] — a deck példafeladata
