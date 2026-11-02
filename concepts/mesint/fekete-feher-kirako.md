---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: model
element: fire
updated: 2026-10-12
---

# Fekete-fehér kirakó

Egy $n+m+1$ hosszú sínen $n$ fekete és $m$ fehér lapka és egy üres hely van; a cél, hogy minden fehér a feketék elé kerüljön. Állapottér-modell és két heurisztika (inverziószám, módosított inverziószám).

## Tartalom

### A feladat

Egy lapkát szomszédos üres helyre tolhatunk, vagy a szomszéd felett üres helyre ugrathatunk. Kezdetben a feketék után jönnek a fehérek, majd az üres hely. Kerüljenek a fehérek a feketék elé!

### Állapottér-modell

Ld. [[concepts/mesint/allapotter-modell]].

- **Állapottér**: $AT = rec(v:\{B,W,\_\}^{n+m+1},\ \ddot{u}res:[1..n+m+1])$.
  - **Invariáns**: $n$ darab $B$, $m$ darab $W$, 1 üres hely; $\ddot{u}res$ az üres hely indexe.
- **Műveletek**: $TolBal,\ TolJobb,\ UgrikBal,\ UgrikJobb: AT\to AT$.
  - Például $TolBal$: HA $this.\ddot{u}res\neq 1$ AKKOR $this.v[this.\ddot{u}res-1]\leftrightarrow this.v[this.\ddot{u}res]$; $this.\ddot{u}res := this.\ddot{u}res-1$.
- **Kezdőállapot**: $[B,\dots,B,W,\dots,W,\_]$.
- **Végállapot**: $\forall i,j\in[1..n+m+1],\ i<j:\ \neg(this.v[i]=B\wedge this.v[j]=W)$ — nincs fehér lapka fekete után.

A végállapot nem egyetlen állapot: az üres hely bárhol lehet, ezért több célállapot van.

### Heurisztikák

- **Inverziószám**: $I(this)$ = minimálisan hány csere kell ahhoz, hogy minden fehér minden feketét megelőzzön (a fekete-fehér párok száma, ahol a fekete megelőzi a fehéret).
- **Módosított inverziószám**: $M(this)=2\cdot I(this)-\begin{cases}1 & \text{ha } this\text{-nek része } \_BW \text{ vagy } BW\_\\ 0 & \text{egyébként}\end{cases}$

Az $M$ azért finomabb, mert a kétszeres inverziószámból levon 1-et, ha az utolsó lépésre kész a fehér-fekete cserepár az üres hely mellett (ezt egy lépéssel lehet kihasználni). A kezdőállapotra ($B\,W\,W\,\_$) $I=2$, $M=4$.

### A keresés a példán ($n=1$, $m=2$)

Az ábra a két heurisztikával bejárt állapotgráfot mutatja a kezdőállapotból. Az $I$ szerinti (kék) úton az $I$ értékei $2,2,2,1,1,0$ (platók: két-két egymást követő azonos érték), az $M$ szerinti (lila) úton $M=4,3,2,1,0$ és közben $I=2,1,1,0$: az $M$ **szigorúan** csökken a kezdőállapottól, ezért a hegymászó módszernél ([[concepts/mesint/hegymaszo-modszer]]) jobban eligazít. Több célállapot is elérhető, ezek mind 0 értékűek.

## Kapocs

- [[concepts/mesint/heurisztika]] — a heurisztika fogalma és célja
- [[concepts/mesint/modellfuggo-vezerles]] — a tologatós és Hanoi heurisztikák a modellfüggő vezérléshez
- [[concepts/mesint/allapotter-modell]] — az alkalmazott modell
- [[concepts/mesint/tologato-jatek]] — hasonló, üres helyes tologatós feladat
- [[concepts/mesint/hegymaszo-modszer]] — a heurisztikákat felhasználó keresés
