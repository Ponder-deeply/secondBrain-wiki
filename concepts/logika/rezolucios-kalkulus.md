---
tags: [concept, logika/rezolucio-iteletlogika]
sources: [Rezolúció_I.pdf]
references: [Tk. 227-238. o.]
derivation: source
updated: 2026-09-08
---

# Rezolúciós kalkulus (ítéletlogika)

A rezolúciós kalkulus egyetlen levezetési szabályra — a rezolvensképzésre — épülő, helyes és teljes eljárás egy klózhalmaz kielégíthetetlenségének eldöntésére: a kalkulus akkor és csak akkor tudja levezetni az üres klózt, ha a klózhalmaz kielégíthetetlen.

## Tartalom

### Egyszerűsítési szabály és motiváció

Ha $X$ ítéletváltozó és $C$ egy $X$-et nem tartalmazó klóz, akkor
$$(X \vee C) \wedge (\neg X \vee C) \sim_0 C.$$
Speciális esetként $(X) \wedge (\neg X) \sim_0 \square$ — azonosan hamis. A rezolvensképzés szabálya ennek az azonosságnak az általánosítása tetszőleges klózpárra.

### Rezolvens

Legyenek $C_1, C_2$ olyan klózok, amelyek pontosan egy **komplemens literálpárt** tartalmaznak: $C_1 = C_1' \vee L_1$ és $C_2 = C_2' \vee L_2$, ahol $L_1 = \neg L_2$. Ekkor létezik a rezolvensük:
$$\mathrm{res}(C_1, C_2) = C = C_1' \vee C_2'.$$

**Tétel** (Tk. 227-228. o.): $\{C_1, C_2\} \models_0 C$ — a rezolvensképzés helyes következtetésforma, azaz a rezolúciós kalkulus levezetési szabálya.

### Rezolúciós levezetés

Egy $S$ klózhalmazból való **rezolúciós levezetés** egy véges $k_1, k_2, \dots, k_m$ ($m \ge 1$) klózsorozat, ahol minden $j = 1, \dots, m$-re
1. vagy $k_j \in S$,
2. vagy van olyan $1 \le s, t < j$, hogy $k_j$ a $(k_s, k_t)$ klózpár rezolvense.

A levezetés célja (megállási feltétele) az **üres klóz** ($\square$) levezetése. Ha $S$-ből levezethető $\square$, ezt **rezolúciós cáfolatnak** nevezzük. Az $S$ klózhalmazból való rezolúciós levezetés maga **döntési eljárás**: eldöntésproblémája, hogy levezethető-e $S$-ből az üres klóz.

### Helyesség és teljesség

**A rezolúciós kalkulus helyes** (Tk. 230. o.):

- (6.3.12) Lemma: legyen $S$ tetszőleges klózhalmaz és $k_1, \dots, k_n$ rezolúciós levezetés $S$-ből. Ekkor minden $k_j$ ($j = 1,\dots,n$) szemantikus következménye $S$-nek.
- (6.3.13) Tétel: ha $S$-ből levezethető az üres klóz, akkor $S$ kielégíthetetlen.

Mindkettő indukcióval igazolható.

**A rezolúciós kalkulus teljes** (Tk. 230. o.):

- (6.3.14) Tétel: ha az $S$ véges klózhalmaz kielégíthetetlen, akkor $S$-ből levezethető az üres klóz.

Bizonyítás (Tk. 231-233. o.): tetszőleges zárt [[concepts/logika/iteletlogikai-szemantikus-fa|ítéletlogikai szemantikus fa]] esetén előállítunk egy rezolúciós cáfolatot.

**A teljesség bizonyításának algoritmusa:**

1. $j := 0$, $S_j := S$, $LIST := \emptyset$.
2. Állítsuk elő $S_j$ szemantikus fáját; $n_j :=$ a fa szintjeinek száma. Ha $n_j = 0$, levezettük az üres klózt — a levezetés $LIST$-ből kiolvasható.
3. Egyébként válasszunk ki a fa egy levezető csúcsát. A csúcsot tartalmazó két ágra illesztett klózok legyenek $k_j'$ és $k_j''$, rezolvensük $k_j$. Tegyük $LIST$ végére $k_j', k_j'', k_j$-t.
4. $S_{j+1} := S_j \cup \{k_j\}$, $j := j+1$; folytassuk a 2. lépéssel.

Ez az algoritmus a zárt szemantikus fa minden levezető csúcsát egy-egy rezolvensképzési lépéssé alakítja, amíg a fa el nem "fogy" — ekkor az üres klóz levezetve.

### Levezetési fa

A **levezetési fa** egy adott rezolúciós levezetés szerkezetét mutatja: olyan gráf, amelynek csúcsaiban klózok vannak, és két csúcsból akkor vezet él egy harmadikba, ha a harmadik a két csúcsbeli klóz rezolvense (Tk. 235-236. o.).

*Példa:* $S_1 = \{X \vee Z,\ \neg X \vee Z,\ X \vee \neg Z,\ \neg X \vee \neg Z\}$ esetén az $1.\ X\vee Z\ [\in S_1]$, $2.\ \neg X \vee Z\ [\in S_1]$, $3.\ Z\ [1,2\text{ rez.}]$, $4.\ X \vee \neg Z\ [\in S_1]$, $5.\ \neg X \vee \neg Z\ [\in S_1]$, $6.\ \neg Z\ [4,5\text{ rez.}]$, $7.\ \square\ [3,6\text{ rez.}]$ levezetés az üres klózt vezeti le.

### Levezetési stratégiák

- **Lineáris rezolúciós levezetés:** $k_1, l_1, k_2, l_2, \dots, k_{m-1}, l_{m-1}, k_m$ klózsorozat, ahol $k_1, l_1 \in S$, és $i = 2,\dots,m$ esetén $k_i$ a $k_{i-1}, l_{i-1}$ rezolvense, ahol $l_{i-1} \in S$ vagy egy korábban megkapott **centrális klóz** (valamely $k_s, l_s$, $s<i$, rezolvense). A $k_i$ klózokat centrális klózoknak, az $l_i$ klózokat mellékklózoknak nevezzük.
- **Lineáris inputrezolúciós levezetés:** mint a lineáris rezolúció, azzal a megszorítással, hogy minden $l_i \in S$ (a mellékklózok mindig az eredeti klózhalmazból származnak, sosem korábbi centrális klózok).
- **Egységrezolúciós stratégia:** rezolvens csak akkor képezhető, ha a két klóz közül legalább az egyik egységklóz.

**Tulajdonságaik** (Tk. 236-238. o.): a lineáris rezolúció helyes és teljes; a lineáris input- és az egységrezolúció helyes, de **nem** teljes — kivéve a [[concepts/logika/horn-kloz-es-horn-logika|Horn logikát]], ahol mindkettő teljes. További, az előadásban nem tárgyalt stratégiák: Tk. 281-300. o.

## Kapocs

- [[concepts/logika/kloz-es-klozhalmaz]] — a rezolvensképzés tárgyai: klóz, klózhalmaz, üres klóz
- [[concepts/logika/iteletlogikai-szemantikus-fa]] — a teljesség bizonyításának háttéreszköze
- [[concepts/logika/horn-kloz-es-horn-logika]] — a Horn logikában a lineáris input- és egységrezolúció is teljes
- [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]] — a helyesség/teljesség fogalmának bizonyításelméleti háttere
- [[concepts/logika/elsorendu-rezolucio]] — a rezolúciós elv elsőrendű logikára való kiterjesztése (unifikációval)
