---
tags: [concept]
sources: [Laki_Lecture_8.pdf, Laki_Lecture_9.pdf]
derivation: source
kind: procedure
element: air
updated: 2026-09-25
---

# A hálózati réteg segédprotokolljai: ICMP, ARP, RARP, DHCP

Az IP önmagában csak továbbít; működéséhez segédprotokollok kellenek. Az **ICMP** a váratlan események (hibák) jelentésére, az **ARP** az IP-cím → MAC-cím leképezésre, a **RARP** (és utódai, a BOOTP és a **DHCP**) a fordított irányra, illetve a hosztok automatikus hálózati konfigurálására szolgál.

## Tartalom

### ICMP — Internet Control Message Protocol

**Feladata:** váratlan események jelentése. Többféle ICMP-üzenetet definiáltak:

| Üzenet | Jelentés | Lehetséges ok / hatás |
|---|---|---|
| **Elérhetetlen cél** | a csomag kézbesítése sikertelen volt | pl. egy nem darabolható (DF) csomag útvonalán egy „kis csomagos hálózat” van |
| **Időtúllépés** | az IP csomag élettartam (TTL) mezője elérte a 0-t | torlódás miatt hurok alakult ki, vagy a számláló túl alacsony volt |
| **Paraméterprobléma** | a fejrészben érvénytelen mezőt észleltünk | egy router vagy a hoszt IP-szoftverének hibája |
| **Forráslefojtás** | lefojtó csomagot küldünk | a fogadó állomásnak lassítania kellett a forgalmazását |
| **Visszhangkérés / -válasz** | egy állomás jelenlétének ellenőrzése | a fogadónak visszhangválaszt kell küldenie (így működik a `ping`) |
| **Átirányítás** | a csomag rosszul irányítottságát jelzik | a router észleli, hogy a csomag nem az optimális úton halad |

Kapcsolat: az „elérhetetlen cél” üzenet a path MTU-felderítés alapja, az „időtúllépés” a TTL-mechanizmusé ([[concepts/telekom/ipv4-fejlec-es-fragmentacio]]).

### ARP — Address Resolution Protocol

**Feladata:** az IP-cím megfeleltetése egy fizikai (MAC-) címnek — a csomagot a helyi hálózaton végül Ethernet-kerettel kell kézbesíteni ([[concepts/telekom/ethernet]]).

**Hozzárendelés:** a küldő **adatszóró** csomagot küld az Ethernetre: „Kié a 192.60.34.12-es IP-cím?”. Minden hoszt ellenőrzi, hogy övé-e a kérdéses cím; ha igen, a saját Ethernet-címével válaszol.

**Lépésenként** (a diák ábrája): (1) A hoszt csomagot küldene a 151.17.35.6-ra; (2) megnézi az ARP-táblázatát — nincs bejegyzés; (3) broadcast: „Who is 151.17.35.6?”; (4) B válaszol: „I am! 151.17.35.6 = 08-00-07-86-0A-DC”; (5) A felveszi B bejegyzését a táblába; (6) elküldi a csomagot.

**Opcionális javítások:**
- a fizikai cím–IP hozzárendelések tárolása (**cache**);
- a leképezések megváltoztathatósága (**időhatály** bevezetése, a táblázat „Age” oszlopa).

**Távoli hálózaton lévő hoszt esetén:**
- a router is válaszoljon az ARP-re a hoszt alhálózatán (**proxy ARP**), vagy
- alapértelmezett Ethernet-cím (a router címe) használata az összes távoli forgalomhoz.

### RARP — Reverse Address Resolution Protocol

**Feladata:** a fizikai cím megfeleltetése egy IP-címnek (pl. lemez nélküli, újonnan induló gépnek).

**Hozzárendelés:** az újonnan indított állomás adatszórással kérdez: „A 48 bites Ethernet-címem 14.04.05.18.01.25. Tudja valaki az IP-címemet?” — a **RARP-szerver** a megfelelő IP-címmel válaszol.

**Javítások:**
- **BOOTP** — UDP csomagokat használ; a hozzárendelési táblázatot manuálisan kell karbantartani (**statikus** címkiosztás).
- **DHCP** — külön kiszolgáló osztja ki a címeket a kérések alapján; a kiszolgáló és a kérő nem kell, hogy ugyanazon a LAN-on legyen, ezért LAN-onként kell egy **DHCP relay agent** (közvetítő) — ez az adatszóró felfedezőcsomagot egyes küldésesként továbbítja a szerverhez (**statikus és dinamikus** címkiosztás).

### DHCP — Dynamic Host Configuration Protocol

Lényegében már az alkalmazási réteghez tartozik, de logikailag ide. Segítségével a hosztok automatikusan jutnak hozzá a kommunikációjukhoz szükséges hálózati azonosítókhoz: IP-cím, hálózati maszk, alapértelmezett átjáró stb. Eredetileg az RFC 1531 definiálta a BOOTP kiterjesztéseként; újabb RFC-k: 1541, 2131 (aktuális).

**Üzenetváltás:**
- **Inicializálás** (nincs cím vagy lejárt a bérlet): `DHCPDISCOVER` (broadcast) → `DHCPOFFER` → `DHCPREQUEST` → `DHCPACK`.
- **Megújítás** (a T1 időzítő lejár): `DHCPREQUEST` → `DHCPACK` (közvetlenül a szervernek).
- **Újrakötés** (a T2 lejár): `DHCPREQUEST` (broadcast) → `DHCPACK`.

**Lehetőségek:**
- IP-cím osztása **MAC-cím alapján**: egyes kliensek MAC-címéhez előre beállított fix IP rendelhető;
- **dinamikus** osztás: a beállított tartományból „érkezési sorrendben” — elég annyi cím, ahány gép egyidejűleg működik;
- további paraméterek: hálózati maszk, alapértelmezett átjáró, névkiszolgáló, domainnév, hálózati rendszerbetöltéshez szerver és fájlnév.

**Címek bérlése:** a szerver a címeket **bérleti időtartamra** (*lease time*) adja; a hosszánál figyelembe veszi a kliens kérését, de a szerver beállításai korlátozzák. A bérlet lejárta előtt meghosszabbítható, és a cím explicit módon vissza is adható.

**Vizsgaszempont:** ARP vs. RARP iránya és működése (broadcast kérés, unicast válasz), a DHCP négylépéses kézfogása (DISCOVER–OFFER–REQUEST–ACK) és a bérlés; ICMP-üzenettípusok és kiváltó okaik.

## Kapocs

- [[concepts/telekom/ipv4-fejlec-es-fragmentacio]] — TTL és DF, amelyekhez ICMP-üzenetek tartoznak
- [[concepts/telekom/ethernet]] — a MAC-címek, amelyekre az ARP leképez
- [[concepts/telekom/ipv4-cimzes-es-cidr]] — a kiosztott IP-címek és maszkok
- [[concepts/telekom/udp]] — a BOOTP és a DHCP szállítója
