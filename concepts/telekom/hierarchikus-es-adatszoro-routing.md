---
tags: [concept]
sources: [Laki_Lecture_7b.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# Hierarchikus, adatszóró és többes-küldéses forgalomirányítás

Nagy hálózatban a routerek táblái a mérettel arányosan nőnek, ezért a routereket **tartományokra** osztjuk, és hierarchikusan irányítunk — az Interneten ez az autonóm rendszerek (AS) közötti és azon belüli routing kétszintű rendszere. Külön feladat, ha egy csomagot **mindenkinek** (adatszórás) vagy egy **csoportnak** (többes küldés) kell eljuttatni.

## Tartalom

### A hálózati réteg szerepkörei és szolgálatai

**Fő feladat:** a csomagok továbbítása a forrás és a cél között — ez a legalacsonyabb réteg, amely két *végpont* közötti átvitellel foglalkozik. Ehhez ismernie kell a kommunikációs alhálózat topológiáját (útvonalak meghatározása), és ügyelnie kell, hogy ne terheljen túl bizonyos útvonalakat vagy routereket, miközben mások tétlenek.

A szállítási réteg felé nyújtott szolgálatok vezérelvei:
1. a szolgálat legyen független az alhálózat kialakításától;
2. a szállítási réteg elől el kell takarni az alhálózatok számát, típusát és topológiáját;
3. a hálózati címek egységes számozási rendszert alkossanak, LAN-ok és WAN-ok esetén is.

Két szolgálatfajta:
- **összeköttetés nélküli** (Internet) — **datagram** alhálózat;
- **összeköttetés alapú** (ATM) — **virtuális áramkör** alhálózat.

### Hierarchikus forgalomirányítás

**Motiváció:** a hálózat méretével a routerek táblázatai, és velük a memória-, CPU- és sávszélességigény is arányosan nő. Ötlet: a telefonhálózatokhoz hasonló hierarchia.

**Jellemzők:**
- A routereket **tartományokra** osztjuk. A saját tartományát minden router ismeri, a többiek belső szerkezetéről nincs tudomása (a többi tartományt egyetlen bejegyzés képviseli).
- Nagy hálózatban többszintű hierarchia is kellhet.
- $N$ routerből álló alhálózathoz az optimális szintszám $\ln N$, amely routerenként $e\cdot\ln N$ bejegyzést igényel (Kamoun és Kleinrock, 1979). Példa: $N = 10^6$ esetén $\ln N \approx 13{,}8$ szint és kb. 38 bejegyzés, az egyszintű 1 millió helyett.

### Hierarchikus forgalomirányítás az IP-ben

Az Internet a hálózati réteg szintjén **autonóm rendszerek** (AS, *Autonomous System*) összekapcsolt együttese. Nincs igazi szerkezete, de számos fő **gerinchálózata** van; ezekhez csatlakoznak a területi és regionális hálózatok, azokhoz pedig az egyetemek, vállalatok és internetszolgáltatók LAN-jai. Az Internet protokollja az IP.

A routing kétszintű:
- **AS-ek közötti** (tartományok közötti): **EGP** — *Exterior Gateway Protocols*; ilyen a BGP ([[concepts/telekom/bgp]]);
- **AS-en belüli** (tartományon belüli): **IGP** — *Interior Gateway Protocols*; ilyen a RIP, az OSPF és az IS-IS ([[concepts/telekom/tavolsagvektor-routing]], [[concepts/telekom/kapcsolatallapot-routing]]).

A kommunikáció menete az Interneten:
1. a szállítási réteg viszi az adatfolyamot, és datagramokra tördeli;
2. minden datagram átmegy az Interneten, menet közben esetleg kisebb egységekre darabolva ([[concepts/telekom/ipv4-fejlec-es-fragmentacio]]);
3. a célgép hálózati rétege összeállítja az eredeti datagramot, és átadja a szállítási rétegnek;
4. a célgép szállítási rétege beilleszti a datagramot a vételi folyamat bemeneti adatfolyamába.

### Adatszóró forgalomirányítás (broadcasting)

Egy csomag mindenhová történő egyidejű küldése. Megvalósítások:

1. **Külön csomag** minden rendeltetési helyre — pazarolja a sávszélességet, és lista kell hozzá.
2. **Elárasztás** — kétpontos kommunikációhoz nem megfelelő (sok másodpéldány).
3. **Többcélú forgalomirányítás** (*multidestination routing*) — a csomagban lista van a rendeltetési helyekről; a routerek ez alapján döntenek a vonalakról, minden vonalhoz másolatot készítenek, és beleteszik a megfelelő részlistát.
4. **A forrás routerhez tartozó nyelőfa / feszítőfa használata** — ha minden router ismeri, mely vonalai tartoznak a feszítőfához, azokon továbbítja az adatszóró csomagot, kivéve azon, amelyen érkezett. Hátrány: nem mindig ismert a feszítőfa.
5. **Visszairányú továbbítás** (*reverse path forwarding*) — a router ellenőrzi, hogy a csomag azon a vonalon érkezett-e, amelyen *ő maga* szokott a forráshoz küldeni. Ha igen, nagy eséllyel a legjobb utat követte, és ez az első másolat: kimásolja minden vonalra, kivéve azt, amelyiken érkezett. Ha más vonalon jött, valószínű másodpéldányként **eldobja**. Előnye: nem kell ismerni a feszítőfát.

### Többes-küldéses forgalomirányítás (multicasting)

Egy csomag meghatározott **csoporthoz** történő egyidejű küldése.
- Csoportkezelés kell hozzá: létrehozás, megszüntetés, csatlakozás, leválás (ez **nem** a routing algoritmus része).
- Minden router kiszámít egy, az alhálózat összes többi routerét lefedő feszítőfát.
- Többes-küldéses csomag esetén az első router **levágja** a feszítőfa azon ágait, amelyek nem csoportbeli hoszthoz vezetnek; a csomagot csak a **csonkolt feszítőfa** mentén továbbítják.

**Vizsgaszempont:** a broadcast öt módszere (különösen a reverse path forwarding logikája), a multicast feszítőfa-csonkolás, az IGP/EGP megkülönböztetés és a Kamoun–Kleinrock eredmény.

## Kapocs

- [[concepts/telekom/routing-alapok]] — nyelőfa és optimalitási elv
- [[concepts/telekom/feszitofa-protokoll]] — a feszítőfa fogalma a 2. rétegben
- [[concepts/telekom/bgp]] — AS-ek közötti routing
- [[concepts/telekom/ipv4-cimzes-es-cidr]] — hierarchikus címzés és aggregálás
