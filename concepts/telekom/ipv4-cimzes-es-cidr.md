---
tags: [concept]
sources: [Laki_Lecture_7b.pdf, Laki_Lecture_8.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# IPv4-címzés, alhálózatok és CIDR

Minden hoszt és router egy 32 bites IP-címmel rendelkezik, amely a **hálózat számát** és a **hoszt számát** kódolja. Évtizedekig osztályos (A–E) címzést használtak; a címek gyors fogyása miatt ma az osztály nélküli **CIDR** az általános, ahol a hálózati részt egy maszk (prefixhossz) jelöli, és a router a **leghosszabb illeszkedő prefix** szerint továbbít.

## Tartalom

### Az IP-cím

- 4 bájton ábrázoljuk, pontokkal elválasztott decimális írásmóddal: pl. `192.168.0.1`.
- A (hálózat, hoszt) kombináció egyedi.

### Osztályos címzés (történeti)

| Osztály | Kezdő bitek | Szerkezet |
|---|---|---|
| A | `0` | 8 bit hálózat (7 hasznos) + 24 bit hoszt |
| B | `10` | 16 bit hálózat + 16 bit hoszt |
| C | `110` | 24 bit hálózat + 8 bit hoszt |
| D | `1110` | többesküldéses (multicast) cím |
| E | `1111` | jövőbeli felhasználásra |

### Speciális címek

| Cím | Jelentés |
|---|---|
| csupa 0 | ez a hoszt |
| 0…0 hálózat + hoszt | egy hoszt ezen a hálózaton |
| csupa 1 | adatszórás a helyi hálózaton |
| hálózat + 1…1 | adatszórás egy távoli hálózaton |
| `01111111` + bármi (127.x.x.x) | visszacsatolás (*loopback*) |

### Alhálózatok (subnet)

Az azonos hálózatban lévő hosztok ugyanazzal a hálózatszámmal rendelkeznek. Egy hálózat belső használatra több részre osztható (pl. egyetemi tanszékek egy központi router körül), de a külvilág számára **egyetlen hálózatként** jelenik meg — ez az **alhálózat**.

- A routernek ismernie kell az **alhálózati maszkot** (*subnet mask*). Kétféle jelölés: IP-cím jellegű (`255.255.252.0`) vagy a fix pozíciók száma (`/22`).
- A routerek táblájában `(hálózat, 0)` és `(saját hálózat, hoszt)` alakú bejegyzések vannak.
- Ha nincs találat, az **alapértelmezett router** felé továbbítják a csomagot.

### CIDR — osztály nélküli tartományközi forgalomirányítás

**Probléma:** az IP-címek gyorsan fogytak (1996-ban kötötték be a 100 000. hálózatot); az osztályok sok címet pazaroltak (különösen a B osztályú címek népszerűsége miatt).

**Megoldás:** CIDR (*Classless Inter-Domain Routing*) — tetszőleges hosszú prefix. Például 2000 cím igénylésekor egy **2048 méretű** (azaz $2^{11}$, `/21`) blokkot adnak ki.

A forgalomirányítás bonyolultabb lesz:
- minden bejegyzés egy 32 bites maszkkal egészül ki: **(IP-cím, alhálózati maszk, kimeneti vonal)**;
- új csomag esetén a célcímből **kimaszkolják** (bitenkénti ÉS) az alhálózati címet, és találat esetén a **leghosszabb illeszkedés** felé továbbítják;
- túl sok bejegyzés keletkezik → **csoportos (aggregált) bejegyzések**.

### Kidolgozott példa: továbbítás

A router táblája:

| Cím/maszk | Következő ugrás |
|---|---|
| 135.46.56.0/22 | 0. interfész |
| 135.46.60.0/23 | 1. interfész |
| 192.53.40.0/23 | 1. router |
| alapértelmezett | 2. router |

Csomag érkezik a **135.46.57.14** címre: `10001011 00101110 00111001 00001110`.

- `/22` maszk (`…11111100 00000000`): az eredmény `10001011 00101110 00111000 00000000` = **135.46.56.0** → illeszkedik az első bejegyzésre.
- `/23` maszk: az eredmény szintén 135.46.56.0, ami **nem** egyezik a 135.46.60.0-val.

Tehát a továbbítás a **0. interfész** felé történik.

### Kidolgozott példa: aggregálás

Csoportosítható-e a 57.6.96.0/21, 57.6.104.0/21, 57.6.112.0/21, 57.6.120.0/21 bejegyzés, ha mindegyik következő ugrása az 1. router? A harmadik bájt binárisan: `01100|000`, `01101|000`, `01110|000`, `01111|000` — az első 19 bit (`…011`) közös, a 20–21. bit minden kombinációja előfordul. Tehát egyetlen **(57.6.96.0/19, 1. router)** bejegyzés helyettesíti mind a négyet.

### Forgalomirányítási tábla a gyakorlatban

Egy hoszt táblája (Network Destination, Netmask, Gateway, Interface, Metric):

| Cél | Maszk | Átjáró | Interfész | Metrika |
|---|---|---|---|---|
| 0.0.0.0 | 0.0.0.0 | 192.168.0.1 | 192.168.0.100 | 10 |
| 127.0.0.0 | 255.0.0.0 | 127.0.0.1 | 127.0.0.1 | 1 |
| 192.168.0.0 | 255.255.255.0 | 192.168.0.100 | 192.168.0.100 | 10 |
| 192.168.0.100 | 255.255.255.255 | 127.0.0.1 | 127.0.0.1 | 10 |
| 192.168.0.255 | 255.255.255.255 | 192.168.0.100 | 192.168.0.100 | 10 |

A `0.0.0.0/0` sor az alapértelmezett átjáró (bármire illeszkedik, de a legrövidebb prefix, így csak végső esetben nyer).

**Vizsgaszempont:** leghosszabb prefix-egyezés kiszámítása bináris maszkolással, bejegyzések aggregálása, blokkméret és prefixhossz átváltása ($2^{32-k}$ cím egy `/k` blokkban), speciális címek.

## Kapocs

- [[concepts/telekom/ipv4-fejlec-es-fragmentacio]] — a címek helye a fejlécben
- [[concepts/telekom/nat]] — a címfogyás gyors javítása
- [[concepts/telekom/ipv6]] — a hosszú távú megoldás
- [[concepts/telekom/hierarchikus-es-adatszoro-routing]] — hierarchikus routing
- [[concepts/telekom/bgp]] — prefixek hirdetése AS-ek között
