---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/hamming-tavolsag]] — a $d$ mennyiség, amely mindkét képességet meghatározza
- [[concepts/dimatii/hibakorlatozo-kodolas-peldai]] — ISBN, paritásbit, kétdimenziós paritásellenőrzés
- [[concepts/dimatii/hamming-korlat]] — a $t$-hibajavító kódok méretének felső korlátja
- [[concepts/dimatii/szindroma-dekodolas]] — lineáris kódnál a minimális távolságú dekódolás hatékony megvalósítása
