---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Hiperút és megoldás-gráf

Az ÉS/VAGY gráf $n \to M$ hiperútja egy olyan véges részgráf, amely az $n$ csúcsból az $M$ csúcssorozatba vezet; a megoldás-gráf a startcsúcsból a célcsúcsok sorozatába vezető hiperút.

## Tartalom

### Definíció

Egy ÉS/VAGY gráf $n \to M$ hiperútja ($n \in N$, $M \in N^+$) egy véges részgráf, amelyben

- $M$ csúcsaiból nem indul hiperél,
- $M$-en kívüli csúcsokból pontosan egy hiperél indul,
- a hiperút minden csúcsa elérhető az $n$ csúcsból egy közönséges irányított úton.

A **megoldás-gráf** egy $s \to M$ hiperút, ahol $s$ a startcsúcs, $M$ pedig célcsúcsok sorozata. A diát illusztráló példában az $a$ csúcsból a $\langle d, e \rangle$ sorozatba vezető hiperút haladási irányai egyértelműek.

### A hiperút bejárása

Az $n \to M$ hiperút **bejárását** a hiperéleinek adott sorrendű felsorolásával kapjuk, amit a hiperút csúcsaiból képzett csúcssorozatok felsorolásával is megadhatunk:

- az első sorozat $\langle n \rangle$;
- a $C$ sorozatot a $C^{k \leftarrow K}$ sorozat követi, ha van az $n \to M$ hiperútban $(k, K)$ hiperél, és $k \in C$, de $k \notin M$. A $C^{k \leftarrow K}$ úgy adódik, hogy $C$-ben a $k$ helyére mindenhol $K$-t írunk.

Egy hiperutat ezért többféleképpen is felfoghatunk közönséges irányított útként, mert több bejárása is lehet. Példa ($n \to \langle a, b \rangle$, $a \to \langle c, d \rangle$, $b \to a$ hiperélekkel):

- $\langle n \rangle \to \langle a, b \rangle \to \langle a, a \rangle \to \langle c, d, c, d \rangle$
- $\langle n \rangle \to \langle a, b \rangle \to \langle c, d, b \rangle \to \langle c, d, a \rangle \to \langle c, d, c, d \rangle$

## Kapocs

- [[concepts/mesint/es-vagy-grafok]] — az ÉS/VAGY gráf, amelyben a hiperút értelmezett
- [[concepts/mesint/graf-fogalmak]] — közönséges irányított út és gráffogalmak
- [[concepts/mesint/utkereses-es-vagy-grafban]] — a hiperút bejárásai adják a megfeleltetett $\delta$-gráfot
- [[concepts/mesint/graf-reprezentacio]] — a megoldás a reprezentációs gráfban
- [[concepts/mesint/problema-redukcios-modell]] — modell, ahol a megoldás-gráf megoldja a problémát
