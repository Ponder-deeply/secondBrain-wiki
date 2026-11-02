---
tags: [concept]
sources: [09.kovetkeztetes.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Formulák klózformára (SKNF) hozása

A rezolúció klózhalmazon dolgozik, ezért az axiómákat és a célállítás negáltját skolemizált konjunktív normálformára (SKNF) kell hozni. A kielégíthetőséget az átalakítás megtartja, az ekvivalenciát nem.

## Tartalom

### Lépések

1. Kiküszöböljük az $\leftrightarrow$ és $\to$ jeleket (logikai törvények): $a\to b$ helyett $\neg a\vee b$.
2. Redukáljuk a negációk hatáskörét (De Morgan azonosságok).
3. Standardizáljuk a változókat (kvantoronkénti átnevezés).
4. Egzisztenciális kvantorok kiküszöbölése (skolemizálás): $\forall x_1\dots\forall x_n\exists z\,F(\dots,z,\dots)$ helyett $\forall x_1\dots\forall x_n\,F(\dots,f(x_1,\dots,x_n),\dots)$. Nem ekvivalens átalakítás, de kielégíthetőség-tartó. Kvantor nélkül (n=0) Skolem-konstans.
5. Az univerzális kvantorokat a formula elejére emeljük a sorrend megtartásával (prenex normálforma).
6. A formula többi részét konjunktív normálformára alakítjuk (kommutatív, asszociatív, disztributív törvények).
7. Kialakítjuk a klózokat: a kvantorokat és konjunkciós jeleket elhagyjuk, a változókat klózonként egyedivé nevezzük át.

### Példa (kuruzslók)

- $A_1$: $\exists x\{P(x)\wedge\forall y[D(y)\to T(x,y)]\}$ = $\exists x\{P(x)\wedge\forall y[\neg D(y)\vee T(x,y)]\}$ $\approx$ ($a$ Skolem-konstans) $P(a)\wedge\forall y[\neg D(y)\vee T(a,y)]$; klózok: $P(a)$, $\neg D(y)\vee T(a,y)$.
- $A_2$: $\forall x\{P(x)\to\forall y[Q(y)\to\neg T(x,y)]\}$ = $\forall x\forall u\{\neg P(x)\vee\neg Q(u)\vee\neg T(x,u)\}$ (változó átnevezés); klóz: $\neg P(x)\vee\neg Q(u)\vee\neg T(x,u)$.
- $B$: $\neg\forall x[D(x)\to\neg Q(x)]$ = $\neg\forall x[\neg D(x)\vee\neg Q(x)]$ = $\exists x[D(x)\wedge Q(x)]$ (De Morgan) $\approx D(b)\wedge Q(b)$; klózok: $D(b)$, $Q(b)$.

## Kapocs

- [[concepts/mesint/rezolucio-mint-keresesi-rendszer]] — az átalakítás a rezolúció előfeltétele
- [[concepts/logika/skolem-normalforma]] — Skolem-normálforma elmélete
- [[concepts/logika/prenex-forma]] — a 5. lépés eredménye
- [[concepts/logika/kloz-es-klozhalmaz]] — a 7. lépés célja
