---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Probléma-redukciós modell

A probléma-redukció az állapottér-modell műveleteihez redukciós operátorokat rendel, amelyek állapothalmazokat képeznek állapothalmazokra, így a keresés a célhalmazból a kezdőhalmaz felé haladhat akkor is, ha a műveleteknek nincs inverze.

## Tartalom

**Modell.** Adott a probléma valamilyen állapottér-modellje: állapottér $AT$, invariáns $Inv: AT\to\mathbb{L}$. Az állapottér-modell minden $M: AT\to AT$ műveletéhez generálunk egy $R_M: 2^{AT}\to 2^{AT}$ leképezést (**redukciós operátor**), amely egy $B$ állapothalmazhoz azt az $A$ állapothalmazt rendeli, amelynek bármelyik állapotából az $M$ művelet a $B$ valamelyik állapotába vezet:

- $\mathcal{D}_{R_M} = \{B\in 2^{AT} \mid B\ne\emptyset\}$
- $\forall B\in\mathcal{D}_{R_M}: R_M(B) = \{a\in AT \mid Inv(a)\ \text{és}\ M(a)\in B\}$

A redukció tehát azt kérdezi: mely állapotokból lehet egy adott művelettel egy adott állapothalmazba eljutni?

- **Célhalmaz:** csupa (de nem feltétlenül az összes) célállapotból áll.
- **Kezdőhalmaz:** legalább egy kezdőállapotot tartalmaz.

**Feladat és megoldás.** Olyan redukciós operátor-sorozatot keresünk, amely a célhalmazból a kezdőhalmazba vezet. A megoldás az ezen operátorokat generáló műveletek *fordított sorrendben kiolvasott* sorozata.

**Gráfmodell.** Irányított gráf: a csúcsok állapothalmazok, az élek a redukálások, a célcsúcs a célhalmaz, a startcsúcsok a kezdőhalmazok; a feladat a célcsúcsból egy startcsúcsba vezető út keresése.

**A kancsóprobléma redukciós operátora.** Az $R_{Tölt(i,j)}: 2^{AT}\to 2^{AT}$, ahol $i,j\in Keys$, $i\ne j$:

$$R_{Tölt(i,j)}(B) = \{a\in AT \mid \sum a[k]=5 \wedge \forall k: a[k]\le k \wedge \min(a[i],\ j-a[j])>0 \wedge \forall b\in B: b[i]=a[i]-\min(a[i],\ j-a[j]) \wedge b[j]=a[j]+\min(a[i],\ j-a[j]) \wedge b[k]=a[k]\ (k\ne i,j)\}$$

Az első sorok az állapottér-modell invariánsa, a $\min(\dots)>0$ a művelet előfeltétele, a többi a művelet hatása ($a$ az input, $b$ az új állapot).

**A kancsóprobléma redukciós gráfja** (részlet). A keresés a célhalmazból indul: $[a,b,1]=\{[4,0,1],[3,1,1],[2,2,1],[1,3,1]\}$. Egy $Tölt(i,j)$ redukcióval olyan halmazt kapunk, amelynek elemeiből egy lépéssel a fenti halmazba jutunk; az állapotok helyett halmazaikkal dolgozunk (az áthúzott elemek az invariánst vagy az előfeltételt sértő, illetve már szereplő állapotok). A cél olyan halmaz megtalálása, amely a kezdőállapotot, $[5,0,0]$-t tartalmazza: pl. $[x,0,y]=\{[4,0,1],[5,0,0]\}$ vagy $[x,y,0]$, amelyben a $[5,0,0]$ szerepel.

## Kapocs

- [[concepts/mesint/visszafele-halado-keresesi-modell]] — a redukció a visszafelé keresés feltételeinek sérülésekor használatos.
- [[concepts/mesint/kancso-problema]] — a redukció motiváló és kidolgozott példája.
- [[concepts/mesint/allapotter-modell]] — a redukció kiindulópontja.
- [[concepts/mesint/problema-dekompozicios-modell]] — a problémamegoldás másik, ÉS/VAGY gráfos modellje.
- [[concepts/mesint/graf-reprezentacio]] — a gráf-reprezentáció általános keretében.
