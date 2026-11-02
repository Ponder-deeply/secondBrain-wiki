---
tags: [concept]
sources: [Laki_Lecture_3.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-09-25
---

# Hamming-távolság és Hamming-korlát a hibakezelésben

Két kódszó Hamming-távolsága azon bitpozíciók száma, ahol eltérnek; egy kód Hamming-távolsága a legkisebb páronkénti távolság. Ez az egyetlen szám dönti el, hány bithibát tud a kód felismerni ($d+1$ szabály) és javítani ($2d+1$ szabály). A Hamming-korlát pedig felső becslést ad arra, hány kódszó fér el adott hossz és távolság mellett.

## Tartalom

### Definíciók

Legyen a keret $m$ üzenetbitből és $r$ ellenőrző bitből álló, $n = m + r$ hosszú kódszó.

- **Két kódszó Hamming-távolsága** $d(x,y)$: azon bitpozíciók száma, amelyeken $x$ és $y$ különböző bitet tartalmaz (azaz $x \oplus y$ egyeseinek száma).
- **Egy kód Hamming-távolsága**: ha $S$ egyenlő hosszú bitszavak halmaza,
  $$d(S) := \min_{x,y\in S,\; x\neq y} d(x,y).$$
- A Hamming-távolság **metrika** (teljesül a háromszög-egyenlőtlenség is).

**Példa:** $S = \{0000000000,\ 0000011111,\ 1111100000,\ 1111111111\}$. A páronkénti távolságok 5, 5, 5, 5, 10, 10, így $d(S) = 5$.

### Mit tud egy adott távolságú kód?

- $d(S) = 1$: nincs hibafelismerés — egy legális kódszóból egyetlen bit megváltoztatásával legális kódszó állhat elő.
- $d(S) = 2$: ha a vett $u$ szóhoz van olyan $x$ kódszó, hogy $d(u,x) = 1$, hiba történt. Mivel $2 = d(u,v) \le d(u,x) + d(x,v)$, egy bithiba **felismerhető, de nem javítható** (a sérült szó két kódszótól is 1 távolságra lehet).

Általánosan:

| Cél | Szükséges kódtávolság |
|---|---|
| $d$ bithiba **felismerése** | legalább $d + 1$ |
| $d$ bithiba **javítása** | legalább $2d + 1$ |

Szemlélet: felismeréshez az $x$ kódszó körüli $d$ sugarú gömbben nem lehet másik kódszó ($d_{min} > d$). Javításhoz a kódszavak $d$ sugarú „territóriumai” diszjunktak kell legyenek ($d_{min} > 2d$), így a sérült szót a legközelebbi kódszóra javíthatjuk. Az előző példa ($d(S)=5$) tehát 4 hibát ismer fel, vagy 2-t javít.

### Kódráta és kódtávolság

Egy $S \subseteq \{0,1\}^n$ kód

- **rátája**: $R_S = \dfrac{\log_2 |S|}{n}$ — a hatékonyságot jellemzi (hány hasznos bit jut egy küldött bitre);
- **távolsága**: $\delta_S = \dfrac{d(S)}{n}$ — a hibakezelési lehetőségeket jellemzi.

A jó kódoknak a rátája és a távolsága is nagy. Az előző példában $R_S = \log_2 4/10 = 0{,}2$, $\delta_S = 5/10 = 0{,}5$.

### Hamming-korlát bináris kódkönyvre

**Tétel.** Minden $C \subseteq \{0,1\}^n$ kódra, ahol $d(C) = k \in \mathbb{N}_+$:
$$|C| \sum_{i=0}^{\lfloor (k-1)/2 \rfloor} \binom{n}{i} \le 2^n.$$

**Bizonyítás.**
1. Egy $x \in C$ kódszótól pontosan $i$ távolságra $\binom{n}{i}$ bitszó van (kiválasztjuk, melyik $i$ bitet fordítjuk át).
2. Tehát legfeljebb $\lfloor (k-1)/2 \rfloor$ távolságra $\sum_{i=0}^{\lfloor (k-1)/2\rfloor}\binom{n}{i}$ bitszó van.
3. Egy tetszőleges $x \in \{0,1\}^n$ bitszóhoz legfeljebb egy olyan $u \in C$ kódszó létezik, amelyre $d(x,u) \le \frac{k-1}{2}$. Indirekt: ha $u_1 \ne u_2$ is ilyen lenne, akkor a háromszög-egyenlőtlenségből $d(u_1,u_2) \le d(u_1,x) + d(x,u_2) \le \frac{k-1}{2} + \frac{k-1}{2} = k-1 < k$, ellentmondás.
4. A kódszavak $\frac{k-1}{2}$ sugarú környezetei tehát páronként diszjunktak, uniójuk legfeljebb az összes $2^n$ bitszó. Ebből az egyenlőtlenség. $\square$

Értelmezés: minél nagyobb távolságot (javítóképességet) akarunk, annál nagyobb „gömb” jut egy kódszóra, és annál kevesebb kódszó fér el — a ráta és a távolság egymás rovására nő.

**Vizsgaszempont:** $d(S)$ kiszámítása adott kódra; a $d+1$ / $2d+1$ szabály alkalmazása; a Hamming-korlát kimondása és a diszjunkt gömbökre épülő bizonyítás.

## Kapocs

- [[concepts/telekom/hibakezeles-alapjai]] — redundancia, kódszó, paritás
- [[concepts/telekom/hamming-kod-keretekben]] — egy konkrét, 1 hibát javító kód
- [[concepts/telekom/crc]] — detektáló kód a gyakorlatban
- [[concepts/dimatii/hamming-tavolsag]] — a metrika a Diszkrét matematika II. kódelméleti tárgyalásában
