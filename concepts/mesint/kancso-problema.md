---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: model
element: fire
updated: 2026-10-12
---

# Kancsók problémája

Három kancsóban összesen 5 liter bor van; töltögetéssel kell elérni, hogy a 2 literes kancsóban pontosan 1 liter legyen. Az állapottér-modell jól mutatja, hogy a műveletnek nem mindig van inverze.

## Tartalom

**Feladat.** Kezdetben az 5 literes kancsó tele van, a 3 és 2 literes üres. Töltögetéssel érjük el, hogy a 2 literesbe pontosan 1 liter bor kerüljön.

**Állapottér-modell.**

- Állapottér: $AT = \mathrm{map}(key{:}Keys, value{:}\mathbb{N})$, ahol $Keys=\{5,3,2\}$ (a kancsó mérete a kulcs, a benne levő bor mennyisége az érték).
- Invariáns: $\sum_{i\in Keys} this[i] = 5$ és $\forall i\in Keys: this[i] \le i$.
- Kezdőállapot: $[5,0,0]$, azaz $this[5]=5$, $this[3]=0$, $this[2]=0$.
- Célállapot: $[x,y,1]$, azaz $this[2]=1$. Célállapotok: $[4,0,1]$, $[3,1,1]$, $[2,2,1]$, $[1,3,1]$.
- Művelet: $Tölt(i,j): AT\to AT$.
  - HA $i,j\in Keys$ és $i\ne j$ és $\min(this[i],\ j-this[j])>0$,
  - AKKOR $this[i] := this[i]-\min(this[i],\ j-this[j])$, $this[j] := this[j]+\min(this[i],\ j-this[j])$.
  - Vagyis az $i$-edikből annyit öntünk a $j$-edikbe, amennyi belefér, illetve amennyi van.

**Állapot-gráf és a visszafelé keresés problémája.** Az állapot-gráfban az $5\,0\,0$ a start, a célok az $1\,3\,1$, $2\,2\,1$, $3\,1\,1$, $4\,0\,1$ állapotok. Két gond adódik:

- Melyik célból induljunk? Van olyan célcsúcs, amely a startból nem érhető el.
- Nem fordítható meg minden célból startba vezető út, mert nem minden lépésnek van inverze (a $Tölt$ művelet nem invertálható: a töltés után nem tudjuk, honnan mennyi került át).

Ezért a visszafelé haladó keresés feltételei nem teljesülnek, és **problémaredukciót** használunk: [[concepts/mesint/problema-redukcios-modell]], ahol a keresés a célállapotok halmazától indul, és állapothalmazokkal dolgozunk.

## Kapocs

- [[concepts/mesint/allapotter-modell]] — a kancsóprobléma állapottér-modellje.
- [[concepts/mesint/visszafele-halado-keresesi-modell]] — a feltételeket a $Tölt$ művelet megsérti.
- [[concepts/mesint/problema-redukcios-modell]] — a kancsóprobléma redukciós gráfja és operátora.
- [[concepts/mesint/hanoi-tornyai]] — másik állapottér-modellezett példa.
