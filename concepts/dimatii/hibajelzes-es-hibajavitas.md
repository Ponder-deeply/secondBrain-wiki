---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf, dm2gy11.pdf, dm2gy12.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Hibajelzés és hibajavítás

A hibakorlátozó kódolás két képessége: észrevenni, hogy az átvitel során hiba történt, illetve helyre is állítani az elküldött kódszót — mindkettőt a kód távolsága szabja meg.

## Tartalom

### Hibajelző kód

Egy kód **$t$-hibajelző**, ha minden olyan esetben jelez, ha az elküldött és a megkapott szó legfeljebb $t$ helyen tér el. Egy kód **pontosan $t$-hibajelző**, ha $t$-hibajelző, de van olyan $t+1$-hiba, amit nem jelez.

Példák: az ISBN 1-hibajelző, a paritásbites kód 1-hibajelző, a kétdimenziós paritásellenőrzés 2-hibajelző.

A hiba javításának módjai:

- **ARQ** (Automatic Retransmission Request) — újraküldés;
- **FEC** (Forward Error Correction) — a vett szóból javítunk, például kétdimenziós paritásellenőrzéssel.

### Minimális távolságú dekódolás és hibajavító kód

**Minimális távolságú dekódolás** esetén egy adott szóhoz azt a kódszót rendeljük, amelyik hozzá a legközelebb van. Több ilyen szó esetén kiválasztunk ezek közül egyet, és az adott szóhoz mindig azt rendeljük.

A dekódolás két részre bontható: a hibajavításnál megpróbáljuk meghatározni, mi volt az elküldött kódszó, majd visszaállítjuk az üzenetet. Mivel az utóbbi egyértelmű, ezért hibajavító kódok dekódolásán legtöbbször csak a hibajavítást értjük.

Egy kód **$t$-hibajavító**, ha minden olyan esetben helyesen javít, amikor egy elküldött szó legfeljebb $t$ helyen változik meg. Egy kód **pontosan $t$-hibajavító**, ha $t$-hibajavító, de van olyan $t+1$ hibával érkező szó, amit helytelenül javít, vagy nem javít.

Ha a kód távolsága $d$, akkor minimális távolságú dekódolással $t < \frac{d}{2}$ esetén $t$-hibajavító.

**Példák.** A $(*)$ kód pontosan 1-hibajavító. Az ismétléses kód: $a \mapsto (a,a,a)$ esetén $d = 3$, 1-hibajavító; $a \mapsto (a,a,a,a,a)$ esetén $d = 5$, 2-hibajavító.

### A távolság és a hibajelző képesség kapcsolata

Tekintsünk egy kódot, aminek a távolsága $d$. Ha egy elküldött kódszó legalább 1, de $d$-nél kevesebb helyen sérül, akkor az így kapott szó biztosan nem kódszó, mivel két kódszó legalább $d$ helyen különbözik. Tehát legfeljebb $d-1$ hiba esetén a kód jelez.

Másrészt a kódban van két olyan kódszó, amelyek távolsága $d$; ha az egyiket küldjük, és ez éppen a másikká változik, akkor $d$ hiba történt, de nem vesszük észre. A kód tehát **pontosan $d-1$-hibajelző**.

### A távolság és a hibajavító képesség kapcsolata

Legyen a kód távolsága $d$, és használjunk minimális távolságú dekódolást.

$t < \frac{d}{2}$ hiba esetén biztosan jól javítunk, hiszen a háromszög-egyenlőtlenség miatt az eredetileg elküldött kódszótól különböző bármely kódszó biztosan $\frac{d}{2}$-nél több helyen tér el a vett szótól.

Másrészt legyenek $u$ és $w$ olyan kódszavak, amelyek távolsága $d$, és legyen $v$ az a szó, amit úgy kapunk $u$-ból, hogy azon $t \ge \frac{d}{2}$ pozícióból, amelyekben eltérnek, a $w$ megfelelő pozíciójában lévő betűt írjuk. Ekkor $v$ az $u$-tól $t$ helyen, míg $w$-től $d - t \le \frac{d}{2} \le t$ helyen különbözik. Ha a kód $t$-hibajavító lenne, akkor $v$-t egyrészt $u$-ra, másrészt $w$-re kellene javítania.

A kód ezáltal **pontosan $\left\lfloor \frac{d-1}{2} \right\rfloor$-hibajavító**.

### Feladattípusok és módszerek: képességek meghatározása (2024. 11–12. sorozat)

**Menet.** Kódolásból kódszavakat sorolunk fel (vagy lineáris kódnál a $\mathbf{H}$ oszlopaiból olvassuk le), $d=\min_{u\neq v}d(u,v)$, majd *hibajelző* képesség $d-1$, *hibajavító* $\lfloor\frac{d-1}2\rfloor$. **MDS**, ha $d=n-k+1$ (azaz $|C|=q^{n-d+1}$, lásd [[concepts/dimatii/singleton-korlat]]).

A 2024. 11. sorozat 2–3–4. feladata (a távolságokat a kódszavak felsorolásával ellenőriztük):

| kód | $n,k$ | $d$ | jelzés | javítás | MDS? |
| --- | --- | --- | --- | --- | --- |
| $(c_1,c_2,c_3,\ c_1+c_2+c_3+1)$ binárisan | 4, (nem lineáris) | 2 | 1 | 0 | $|C|=8=2^{4-2+1}$ igen |
| $(c_1,c_2,c_3,\ c_1,\ c_2+c_3)$ | 5, 3 | 2 | 1 | 0 | nem |
| $(c_1,c_2,c_3,\ c_1,\ 1-c_2c_3)$ | 5 | **1** | 0 | 0 | nem |
| $(c_1,c_2,\ c_1+c_2)$ | 3, 2 | 2 | 1 | 0 | igen |
| $(c_1,c_2,\ c_1+c_2,\ \max\{c_1,c_2\})$ | 4 | 2 | 1 | 0 | nem |
| $(c_1,c_2,c_1+c_2)$, $\mathbb{F}_5$ vagy $\mathbb{F}_7$ fölött | 3, 2 | 2 | 1 | 0 | igen |
| $(c_1,c_2,c_1+c_2,c_1c_2)$, $\mathbb{F}_7$ | 4, 2 | 2 | 1 | 0 | nem ($d<3$) |
| $(c_1,c_2,c_3,c_1+c_2,c_1+c_3)$, $\mathbb{F}_3$ | 5, 3 | 2 | 1 | 0 | nem |
| $(c_1,c_2,c_3,c_1+c_2,c_1+c_3,c_2+c_3)$, $\mathbb{F}_3$ | 6, 3 | 3 | 2 | 1 | nem ($d<4$) |
| $(c_1,c_2,c_3,\ \sum c_i,\ c_1+2c_2+3c_3)$ mod 5 | 5, 3 | 3 | 2 | 1 | igen |
| ugyanez mod 4 | 5 | 2 | 1 | 0 | — (a $\mathbb{Z}_4$ nem test) |

Az $1-c_2c_3$-as kód $d=1$: a $(0,0,0)$ és $(0,0,1)$ kódszavak csak a harmadik koordinátában térnek el — az utolsó komponens a $c_2c_3$ szorzat miatt nem lineáris, és az információt nem védi. A $\mathbb{Z}_4$-es változatban a $2\cdot2=0$ nullosztó miatt két különböző üzenet kódolása kevés helyen térhet el, ezért a távolság csökken.

**Gömbszámlálás.** A $(c_1,c_2,c_3,\ c_1+c_2,\ c_1+c_3,\ c_2+c_3)$ bináris kód ($n=6$, $d=3$): minden kódszó $1$ sugarú gömbje $1+6=7$ szót fed, a nyolc gömb páronként diszjunkt (mert $d=3$), így $8\cdot7=56$ szót fedünk $2^6=64$-ből; a **maradék $8$ szó** minden kódszótól legalább $2$ távolságra van. A lap „$\mathbb{F}_2^5$” jelölése valószínűleg elírás: a $6$ hosszú kódhoz $\mathbb{F}_2^6$ tartozik, és ebben $8$ ilyen szó van (felsorolással ellenőrizve).

**Tipikus hibák.** $t=d/2$-t hibajavításnak venni ($d=4$-nél $1$ hibát javítunk, nem kettőt); $d=1$-nél a „jelzés $d-1=0$” elfelejtése; a kódolást lineárisnak hinni, ha egy komponens szorzat, $\max$ vagy konstans tagot tartalmaz.

## Kapocs

- [[concepts/dimatii/hamming-tavolsag]] — a $d$ mennyiség, amely mindkét képességet meghatározza
- [[concepts/dimatii/hibakorlatozo-kodolas-peldai]] — ISBN, paritásbit, kétdimenziós paritásellenőrzés
- [[concepts/dimatii/hamming-korlat]] — a $t$-hibajavító kódok méretének felső korlátja
- [[concepts/dimatii/szindroma-dekodolas]] — lineáris kódnál a minimális távolságú dekódolás hatékony megvalósítása
