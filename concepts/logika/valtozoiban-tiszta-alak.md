---
tags: [concept]
sources: [Elsőrendű_logika_alapjai.pdf, Szabo-Ivan-Elsorendu-logika-egyetemi-jegyzet.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Változóiban tiszta (kiigazított) alak

Egy elsőrendű formula változóiban tiszta, ha egyetlen változó sem fordul elő egyszerre szabadon és kötötten, és két különböző kvantor nem köti ugyanazt a változót. A kötött változók átnevezésével bármely formula ekvivalens tiszta alakra hozható.

## Tartalom

### Definíció

A gyakorlat szerint egy formula **változóiban tiszta**, ha minden változója vagy csak szabad, vagy csak *egyetlen* kvantor által kötött. Szabó Iván jegyzete ugyanezt **kiigazított** formulának nevezi: (1) különböző kvantorok különböző változókat kötnek le, és (2) nincs olyan változó, amely kötötten és szabadon is előfordul. (A [[concepts/logika/szabad-es-kotott-valtozo]] szerinti „vegyes” változó éppen a (2) megsértése.)

**Nem tiszta**: $\exists x\,p(x,y) \wedge \forall x\,q(f(x),x) \wedge \exists y\,p(y,f(y))$ — $x$-et két kvantor köti, $y$ kötött és szabad is. Az egyik hiba is elég lenne.

**Tiszta, ekvivalens alak** (a kvantorok változóinak indexelt átnevezésével): $\exists x_1\,p(x_1,y) \wedge \forall x_2\,q(f(x_2),x_2) \wedge \exists y_1\,p(y_1,f(y_1))$.

### Az átnevezés szabálya

Egy kvantor által kötött változót a kvantor hatáskörében *minden* kötött előfordulásával együtt, **új** változóra szabad átnevezni:

- $\forall x\,P(x) = \forall y\,P(y)$
- $\forall x(P(x) \wedge Q(x)) = \forall y(P(y) \wedge Q(y))$
- $\forall x(P(x) \wedge Q(y)) \neq \forall y(P(y) \wedge Q(y))$ — a szabad $y$ „bekötődne” (változófogás)
- $\forall x(P(x) \wedge Q(y)) = \forall z(P(z) \wedge Q(y))$ — jó, mert $z$ új

Szabály: az új név nem szerepelhet a hatókörben szabadon, és nem lehet más kvantor által kötött név sem.

### Példák a gyakorlatról

- $\forall x\,P(x) \supset \forall x\,Q(x)$ $\to$ $\forall x\,P(x) \supset \forall y\,Q(y)$
- $\forall x\,P(x) \wedge \exists x\,Q(x) \wedge P(x)$ $\to$ $\forall y\,P(y) \wedge \exists z\,Q(z) \wedge P(x)$ (a szabad $x$ marad)
- $\forall x\,P(x) \wedge Q(x)$ $\to$ $\forall y\,P(y) \wedge Q(x)$

### Sorrend a normálformákhoz

Szabó jegyzete szerint a normálformára hozás sorrendje: **először a nyilak eltüntetése** ($F \to G \equiv \neg F \vee G$; $F \leftrightarrow G \equiv (\neg F \vee G) \wedge (F \vee \neg G)$), **utána a kiigazítás**. Fordított sorrendben a $\leftrightarrow$ átírása megkettőzi a benne levő kvantort, és újra két egyforma nevű kötött változó keletkezik. A kiigazított formulán érvényes a nyolc kvantorkiemelési ekvivalencia (pl. $(\exists x F) \vee G \equiv \exists x(F \vee G)$, mert $G$-ben nem szerepel $x$), ezért a [[concepts/logika/prenex-forma]] algoritmusának ez az előfeltétele. A prenex alak után jön a [[concepts/logika/skolem-normalforma]].

## Kapocs

- [[concepts/logika/szabad-es-kotott-valtozo]] — szabad, kötött, vegyes változó; a „vegyes” az, amit a tiszta alak kizár
- [[concepts/logika/prenex-forma]] — a kvantorkiemelés előfeltétele a tiszta alak
- [[concepts/logika/skolem-normalforma]] — a prenex alakból képzett Skolem alak
- [[concepts/logika/helyettesitesi-algoritmus]] — a változófogás elkerülése behelyettesítéskor ugyanezzel az átnevezéssel történik
