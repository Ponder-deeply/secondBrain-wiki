---
tags: [concept]
sources: [Laki_Lecture_6.pdf, Laki_Lecture_7a.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Távolságvektor alapú forgalomirányítás (elosztott Bellman–Ford)

A távolságvektor alapú (*distance vector*) routingban minden router egy táblázatot tart karban, amelyben minden célhoz szerepel a legrövidebb ismert távolság és az a vonal (következő ugrás), amelyen a célhoz el lehet jutni. A táblázatokat **csak a szomszédoktól** kapott információk alapján frissítik. Ez az ARPANET eredeti algoritmusa, **RIP** (*Routing Information Protocol*) néven is használták. Gyenge pontja a **végtelenig számolás** problémája.

## Tartalom

### Környezet és működés

- Minden csomópont csak a **közvetlen szomszédaival** kommunikálhat.
- **Aszinkron** működés.
- Minden állomásnak van saját **távolságvektora** (cél → költség, következő ugrás), amelyet periodikusan elküld a szomszédoknak.
- A kapott vektorok alapján minden csomópont új táblázatot állít elő.
- Kezdetben csak a közvetlen szomszédokról van információ (a többi cél költsége $\infty$); végül kitöltött vektort kapunk.

### Az algoritmus (A csomópont szemszögéből)

**Inicializálás:** minden $V$ szomszédra $D(A,V) = c(A,V)$, minden más célra $D(A,V) = \infty$.

**Ciklus** — várakozás linkköltség-változásra vagy frissítő üzenetre:
- ha a $c(A,V)$ linkköltség $d$-vel változik: minden $Y$ célra, amely $V$-n át érhető el, $D(A,Y) \mathrel{+}= d$;
- ha $V$-től $D(V,Y)$ frissítés jön: minden $Y$ célra
  - ha $Y$-t eddig is $V$-n át értük el: $D(A,Y) = D(A,V) + D(V,Y)$;
  - különben: $D(A,Y) = \min\big(D(A,Y),\ D(A,V) + D(V,Y)\big)$;
- ha valamely $Y$-ra új minimum adódott, $D(A,Y)$-t elküldi minden szomszédnak.

Ez a Bellman–Ford-egyenlet elosztott változata: $D(A,Y) = \min_V \{c(A,V) + D(V,Y)\}$.

### Kidolgozott példa

Topológia: A–B 2, A–C 7, B–C 1, B–D 3, C–D 1.

Kezdetben A táblája: B 2 (B), C 7 (C), D $\infty$.

1. iteráció, B vektora alapján: $D(A,C) = \min(7,\ 2 + 1) = 3$ (B-n át); $D(A,D) = \min(\infty,\ 2 + 3) = 5$ (B-n át). Közben B is megtanulja, hogy D-t C-n át 2-vel éri el.

3. iteráció végére A táblája: B 2, C 3, D 4 — mind B-n át. Ezután semmi nem változik, az algoritmus **leáll — amíg valami meg nem változik**.

### „A jó hír gyorsan terjed”

Háromszög: A–B, B–C 1, A–C 50. Ha az A–B link költsége 4-ről 1-re csökken, B azonnal frissít (A: 1), elküldi C-nek, C frissít (A: 2 B-n át), és az algoritmus két lépésben leáll.

### Végtelenig számolás (count to infinity)

**„A rossz hír lassan terjed”.** Lánc: A–B–C. Ha az A–B link megszakad, B törli az A-hoz vezető útját — de C még azt hirdeti, hogy A-t 2 költséggel eléri (B-n át!). B nem tudja, hogy C útja rajta át vezet, ezért felveszi: A 3, C-n át. Erre C: A 4, B-n át; majd B: A 5 … és így tovább a végtelenségig. Kör alakult ki.

Ugyanez súlyozott esetben: a háromszögben az A–B link 4-ről 60-ra nő. B tudja, hogy $D(C,A) = 5$, de nem tudja, hogy ez az út $C \to B \to A$, ezért $D(B,A) = 6$ (C-n át); C erre 7-re, B 8-ra lép … amíg lassan el nem éri az A–C közvetlen 50-es útját.

**Probléma összefoglalva:** a jó hír gyorsan, a rossz hír lassan terjed; ciklusok keletkezhetnek.

### Megoldás: split horizon with poisoned reverse

*„Osztott horizont mérgezett visszajelzéssel”* (RFC 1058): a router **negatív információt** küld vissza arról a szomszédjának, amit tőle „tanult”.

Ha C B-n keresztül irányítja az A-ba menő forgalmat, akkor C B-nek $D(C,A) = \infty$ távolságot küld — így B nem fogja C-n keresztül irányítani az A-ba menő forgalmat. A példában az A–B link 60-ra nő: B beírja az A 60-at; C, látva, hogy B-n át már drága, átáll a közvetlen 50-es linkre; majd B megtanulja, hogy C-n át 51 — gyors konvergencia.


**Vizsgaszempont:** DV-tábla kitöltése néhány iteráción át egy kis gráfra; a count-to-infinity forgatókönyv elmagyarázása és a poisoned reverse működése.

## Kapocs

- [[concepts/telekom/routing-alapok]] — optimalitási elv, legrövidebb út
- [[concepts/telekom/kapcsolatallapot-routing]] — globális topológiatudású alternatíva
- [[concepts/telekom/bgp]] — útvonalvektor: a DV kiterjesztése a teljes úttal
