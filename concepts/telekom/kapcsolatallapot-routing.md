---
tags: [concept]
sources: [Laki_Lecture_7b.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Kapcsolatállapot alapú forgalomirányítás és a Dijkstra-algoritmus

A kapcsolatállapot alapú (*link-state*) routingban minden router megismeri az **egész alhálózat gráfját**: a saját szomszédsági információit elárasztással minden más routernek elküldi, majd a teljes képen **Dijkstra algoritmusával** maga számolja ki a legrövidebb utakat. Motivációja, hogy figyelembe vegye az eltérő sávszélességeket, és hogy a távolságvektor alapú algoritmusok lassan konvergáltak. Két fő implementációja az **OSPF** és az **IS-IS**.

## Tartalom

### Az alapötlet öt lépése

1. **Szomszédok felkutatása** és hálózati címeik meghatározása. Beinduláskor a router minden kimenő vonalán egy speciális `HELLO` csomagot küld; a vonal másik végén lévő router válaszában közli az (egyedi) azonosítóját.
2. **Késleltetés vagy költség mérése** minden szomszédhoz. Legközvetlenebb módja egy speciális `ECHO` csomag, amelyet a másik oldalnak azonnal vissza kell küldenie; a késleltetés a **körbeérési idő felével** becsülhető (javítás: több kísérlet átlaga).
3. **Csomag összeállítása** a megismert információkból — ez a **kapcsolatállapot-hirdetés**, LSA (*Link State Advertisement*). Tartalma: a feladó azonosítója, egy **sorszám**, egy **korérték** és a szomszédok listája, mindegyikhez a felé tapasztalható késleltetéssel. Előállítás periodikusan vagy hibaesemény esetén.
4. **Megbízható szétosztás** az **összes többi** routernek. Elárasztással, de a csomagban lévő sorszám minden küldésnél 1-gyel nő. A routerek számon tartják az összes látott (forrás, sorszám) párt: ha **új** érkezik, minden vonalon továbbküldik, kivéve azt, amelyiken érkezett; a **másodpéldányokat eldobják**; a **kisebb sorszámúakat elavultnak** tekintik, nem küldik tovább.
5. **Legrövidebb utak kiszámítása** minden más routerhez: a teljes LSA-készletből felépíthető az alhálózat teljes gráfja, erre fut a **Dijkstra-algoritmus**, amelynek eredménye a forgalomirányító tábla.

Az elárasztás problémái és megoldásai:

| Probléma | Megoldás |
|---|---|
| A sorszámok egy idő után körbeérnek | 32 bites sorszám |
| Egy router összeomlik (és újraindulva 0-tól számoz) | **kor** bevezetése: a router másodpercenként csökkenti, nullánál eldobja |
| A sorszámmező megsérül | ugyanúgy a korral |

További finomítások: a csomag először tárolóterületre kerül, nem egyből a küldési sorba; nyugtázás.

**Jellemzők:** a routerek számával és a szomszédok átlagos számával arányos tár kell: $O(kn)$, ahol $k$ a szomszédok, $n$ a routerek száma — nagy hálózatnál költséges és memóriaigényes. A hardver- és szoftverhibák komoly gondot okozhatnak, és a hálózat méretével nő a hiba valószínűsége.

### Dijkstra algoritmusa (1959)

Statikus algoritmus; célja két csomópont közötti legrövidebb út meghatározása (valójában egy forrásból az összes csomópontba — **legrövidebb utak fája**).

**Informálisan:** minden csomópontot felcímkézünk a forrástól vett legrövidebb *ismert* távolsággal (kezdetben $\infty$). A címke **ideiglenes** vagy **állandó**; kezdetben minden ideiglenes. Mindig a legkisebb ideiglenes címkéjű csomópont válik állandóvá, és ekkor a szomszédai címkéit javítjuk.

**Pszeudokód** (`Dijkstra(G, s, w)`, kimenet a $T = (V, E')$ legrövidebbút-fa $s$ gyökérrel):

```
E' := ∅; ready[s] := true; ready[v] := false ∀v ≠ s
d[s] := 0; d[v] := ∞ ∀v ≠ s
forall v ∈ Adj[s]: pred[v] := s; d[v] := w(s,v); Q.Insert(v, d[v])
while Q ≠ ∅ do
    v := Q.DeleteMin(); E' := E' ∪ {(pred[v], v)}; ready[v] := true
    forall u ∈ Adj[v] do
        if u ∈ Q and d[v] + w(v,u) < d[u] then        -- javító út
            pred[u] := v; d[u] := d[v] + w(v,u); Q.DecreasePriority(u, d[u])
        else if u ∉ Q and not ready[u] then           -- új út
            pred[u] := v; d[u] := d[v] + w(v,u); Q.Insert(u, d[u])
```

**Kidolgozott példa** (forrás A, cél D). Élek: A–B 2, A–G 6, B–C 7, B–E 2, E–F 2, E–G 1, C–F 3, C–D 3, F–H 2, G–H 4, H–D 2. A címkék (távolság, megelőző):

| Lépés | Állandóvá válik | Prioritási sor $Q$ |
|---|---|---|
| 0 | A (0) | (B,2), (G,6) |
| 1 | B (2, A) | (E,4), (G,6), (C,9) |
| 2 | E (4, B) | (G,5), (F,6), (C,9) — G javult 6→5 |
| 3 | G (5, E) | (F,6), (C,9), (H,9) |
| 4 | F (6, E) | (H,8), (C,9) — H javult 9→8 |
| 5 | H (8, F) | (C,9), (D,10) |
| 6 | C (9, B) | (D,10) |
| 7 | D (10, H) | ∅ |

A legrövidebb A→D út: **A–B–E–F–H–D**, hossza 10.

### OSPF vs. IS-IS

A link-state stratégia két eltérő implementációja.

| | OSPF | IS-IS |
|---|---|---|
| Ki használja | cégek és adatközpontok | internetszolgáltatók |
| Jelleg | több lehetőséget támogat | sokkal tömörebb: kisebb hálózati overhead, több eszközt támogat |
| IP-kötődés | IPv4 felett (az LSA-kat IPv4 felett küldi); IPv6-hoz OSPFv3 kell | nem kötődik az IP-hez, IPv4-gyel és IPv6-tal is működik |
| Felépítés | átfedő **területek** (*area*) köré szerveződik; **Area 0** a hálózat magja | **2 szintű hierarchia**; a 2. szint (Level 2) a gerinchálózat |

### Link state vs. distance vector

| | Link state | Distance vector |
|---|---|---|
| Üzenetkomplexitás | $O(n\cdot E)$ | $O(d\cdot n\cdot k)$ |
| Időkomplexitás | $O(n \log n)$ | $O(n)$ |
| Konvergenciaidő | $O(1)$ | $O(k)$ |
| Robusztusság | a csomópontok hibás **link**költséget hirdethetnek; mindenki a saját tábláját számolja | hibás **út**költséget hirdethetnek; a hibák a DV-táblák megosztása miatt továbbterjednek |

Melyik a jobb? A gyakorlatban attól függ; általában a link state népszerűbb.

**Vizsgaszempont:** a link-state öt lépése; az elárasztás sorszám/kor mechanizmusa; Dijkstra kézi lefuttatása táblázattal szinte biztos feladat; LS vs. DV összevetés.

## Kapocs

- [[concepts/telekom/routing-alapok]] — legrövidebb út alapú forgalomirányítás, nyelőfa
- [[concepts/telekom/tavolsagvektor-routing]] — az elosztott Bellman–Ford alternatíva
- [[concepts/telekom/hierarchikus-es-adatszoro-routing]] — területek, tartományok, AS-ek
