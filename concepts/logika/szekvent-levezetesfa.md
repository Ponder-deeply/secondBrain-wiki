---
tags: [concept, logika/gentzen-stilusu-kalkulusok]
sources: [Szekventkalkulus.pdf]
derivation: source
updated: 2026-09-08
---

# Szekvent levezetésfa és bizonyíthatóság

A **levezetésfa** egy adott szekventkalkulusban ($K$-kalkulusban) rekurzívan felépülő fastruktúra, amelynek gyökere a bizonyítandó szekvent; egy szekvent akkor **bizonyítható**, ha van ilyen levezetésfája.

## Tartalom

### A $K$-kalkulusbeli levezetésfa definíciója

Legyen $K$ a G- vagy a C-kalkulus egyike ([[concepts/logika/szekventkalkulus]]). A $K$-kalkulusbeli levezetésfát és a **levezetésfa magasságát** a következő szerkezeti (rekurzív) definíció adja meg:

1. A $K$-kalkulus minden axiómaszekventje egy levezetésfa; ez a szekvent a levezetésfa gyökere, magassága 1.
2. Ha $D$ egy $m$ magasságú $K$-kalkulusbeli levezetésfa, amelynek gyökere valamely $K$-kalkulusbeli (egy premisszájú) levezetési szabályban épp a vonal feletti szekvent, akkor a szabállyal a vonal alatti $S$ szekventet előállítva, a $D$-ből és $S$-ből kapott fa is $K$-kalkulusbeli levezetésfa, amelynek gyökere $S$, magassága $m+1$.
3. Ha $D_1$ és $D_2$ rendre $m_1$ és $m_2$ magasságú levezetésfák, amelyek gyökerei egy (két premisszájú) levezetési szabályban a vonal feletti két szekvent, akkor a szabállyal a vonal alatti $S$ szekventet előállítva, a $D_1$-ből, $D_2$-ből és $S$-ből kapott fa is levezetésfa, gyökere $S$, magassága $\max(m_1, m_2) + 1$.
4. Minden levezetésfa az 1–3. szabályok véges sokszori alkalmazásával áll elő.

A definíció szerkezete megegyezik az [[concepts/logika/iteletlogikai-formula]] lapon látott szerkezeti rekurzióéval: alaplépés (axiómaszekvent, magasság 1) és rekurzív lépés (egy vagy két korábbi fából egy szabály alkalmazásával új fa), lezárva a "véges sokszori alkalmazás" feltétellel.

### Szekvent bizonyíthatósága

Egy $S$ szekvent a $K$-kalkulusban **bizonyítható**, ha van olyan $K$-kalkulusbeli levezetésfa, amelynek $S$ a gyökere. Jelölése: $\vdash_K S$.

**Fontos:** ugyanaz a szekvent az egyik kalkulusban bizonyítható lehet, a másikban nem — pontosabban nem *ugyanazzal* a fával, hiszen a két kalkulus axiómasémája és szabályai eltérnek (lásd a példát alább). A [[concepts/logika/szekventkalkulus]] lapon tárgyalt ekvivalenciatétel szerint azonban ami az egyikben bizonyítható, az a másikban is bizonyítható — csak esetleg más fával.

### Példa: levezetésfa a C-kalkulusban

A C-kalkulusban az alábbi fa 3 magasságú levezetésfa, gyökere a $\to A \supset (B \supset A)$ szekvent:

$$
\dfrac{\dfrac{A, B \to A}{A \to B \supset A}\ (\to\supset)}{\to A \supset (B \supset A)}\ (\to\supset)
$$

(Az egyes lépések mellett zárójelben szerepel az alkalmazott levezetési szabály neve.) A fa gyökere felől nézve tehát az $A, B \to A$ axiómaszekventből két $(\to \supset)$ szabály-alkalmazással jutunk el a végkonklúzióig.

Ugyanez a fa a **G-kalkulusban nem levezetésfa**, mert $A, B \to A$ a G-kalkulusban nem axiómaszekvent — a G-kalkulus axiómasémája $X \to X$ alakú (csak egyetlen, mindkét oldalon azonos formulát enged meg kísérő nélkül), a C-kalkulusé pedig $X, \Gamma \to \Delta, X$ (tetszőleges kísérő formulahalmazzal). Ez a definíciós különbség az oka annak, hogy ugyanazon szekvent bizonyítására a két kalkulusban általában más alakú fát kell építeni.

### Példa: levezetésfa a G-kalkulusban

Az $A \wedge B \to B \wedge A$ szekvent a G-kalkulusban az alábbi (3 magasságú) levezetésfával bizonyítható:

$$
\dfrac{\dfrac{B \to B}{A \wedge B \to B}\ (\wedge\to) \qquad \dfrac{A \to A}{A \wedge B \to A}\ (\wedge\to)}{A \wedge B \to B \wedge A}\ (\to\wedge)
$$

A fa két axiómaszekventből ($B \to B$ és $A \to A$) indul, két $(\wedge \to)$ lépéssel köztes szekventeket állít elő, amelyeket egy $(\to \wedge)$ lépés egyesít a végkonklúzióban — ez a 3. definíciós szabály (két premisszájú szabály) esete: a fa magassága $\max(2, 2) + 1 = 3$.

## Kapocs

- [[concepts/logika/szekventkalkulus]] — a G- és C-kalkulus szabályrendszerei, amelyekre a levezetésfa épül
- [[concepts/logika/szekvent]] — a szekvent szintaxisa és szemantikája
- [[concepts/bvszam/itelet-kalkulus]] — az ítéletkalkulus, amelynek axiómasémás bizonyítás-fogalmához a szekventkalkulus helyessége és teljessége köti a szekvent bizonyíthatóságát
</content>
