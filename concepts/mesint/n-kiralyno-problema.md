---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: model
element: fire
updated: 2026-10-12
---

# $n$-királynő probléma

Az $n$ királynőt kell úgy elhelyezni egy $n\times n$-es táblán, hogy ne üssék egymást. A példa azt mutatja, hogy ugyanahhoz a feladathoz egyre kisebb problématerű [[concepts/mesint/allapotter-modell]] adható: három modellváltozat.

## Tartalom

### 1. modell: királynők áthelyezése

- **Állapottér**: $AT = \{\text{♛}, \_\}^{n\times n}$, kétdimenziós tömb. Invariáns: egy állapot (tábla) pontosan $n$ királynőt tartalmaz.
- **Művelet**: `Áthelyez(x,y,u,v)`: HA $1\le x,y,u,v\le n$ és `this[x,y]`=♛ és `this[u,v]`=`_`, AKKOR `this[x,y] ↔ this[u,v]` (csere).
- A célállapot nem ismert, egy feltétel (nincs ütés) ellenőrzésével dönthető el.
- Állapot-gráf: csúcsok száma $\binom{n^2}{n}$, ki-fok $n(n^2-n)$, mindenféle hosszú kör van; adott csúcsból induló, oda-vissza lépések nélküli $k$ hosszú utak száma $(n(n^2-n))^k$. A problématér óriási.

### A problématér csökkentése

- Bővítsük az állapotteret az $n$-nél kevesebb királynőt tartalmazó állásokkal, és használjunk új műveletet: királynő-felhelyezést (kezdő állás az üres tábla).
- A műveletek előfeltételének szigorításával csökken az állapot-gráf átlagos ki-foka: sorról sorra haladva csak egy-egy királynőt helyezzünk fel, és ütést tartalmazó állásra ne tegyünk királynőt.

### 2. modell: soronkénti felhelyezés

- **Invariáns**: az első néhány sor egy-egy királynőt tartalmaz.
- **Művelet**: `Helyez(oszlop)`: HA $1\le oszlop\le n$ és a `this`-beli soron következő üres sor $\le n$ és nincs ütés a `this`-ben, AKKOR `this[következő üres sor, oszlop] := ♛`.
- Állapot-gráf fa: csúcsok száma $<(n^{n+1}-1)/(n-1)$, ki-fok $n$, ágak száma $<n^n$.

### Művelet hatékonysága

A művelet számítási bonyolultsága csökkenthető, ha
- az állapotokat extra információval egészítjük ki (a soron következő üres sor sorszáma tárolható a tábla mellett, nem kell kiszámolni, csak eggyel növelni);
- az invariáns szigorításával szűkítjük az állapotteret: nem engedünk ütést létrehozni a táblán, ezért megjelöljük az ütés alatt álló üres mezőket. Egy mező státusza: szabad, ütés alatt álló vagy foglalt.

### 3. modell: ütés alatt álló mezők jelölése

- **Állapottér**: $AT = rec(t:\{\text{♛},\times,\_\}^{n\times n},\ köv\_sor:\mathbb N)$.
- **Invariáns**: $köv\_sor\le n+1$; az első $köv\_sor-1$ sor egy-egy királynőt tartalmaz; a királynők nem ütik egymást. Jelölés: $\times$ = királynő által ütött üres mező, $\_$ = szabad üres mező.
- **Művelet** `Helyez(oszlop)`: HA $1\le oszlop\le n$ és $this.köv\_sor\le n$ és `this.t[this.köv_sor, oszlop]`=`_`, AKKOR a mezőre ♛ kerül, a lejjebbi sorokban az oszlop és a két átló mezői $\times$-szel jelölődnek, $köv\_sor := köv\_sor+1$.
- Az előfeltétel számításigénye konstans, a hatásé lineáris.
- **Kezdőállapot**: üres mátrix, $köv\_sor=1$. **Célállapot**: $köv\_sor>n$ — a célfeltétel nagyon egyszerű lett.
- A gráf szintén fa; a zsákutcák (nem teljes elhelyezések) is szerepelnek benne.

## Kapocs

- [[concepts/mesint/allapotter-modell]] — az általános modell
- [[concepts/mesint/allapotter-vs-problemater]] — itt a válasz célállapot, mégis a műveletsorozatok között keresünk
- [[concepts/mesint/hanoi-tornyai]] — másik mintapélda
- [[concepts/mesint/tologato-jatek]] — harmadik mintapélda
