---
tags: [concept]
sources: [Laki_Lecture_12_new.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# DNS — Domain Name System

Az emberek neveket jegyeznek meg (`www.northeastern.edu`), a gépek IP-címekkel dolgoznak (`129.10.117.100`). A DNS a kettő közötti leképezést végző **elosztott, hierarchikus adatbázis**: a névtér egy fa, amely zónákra bomlik, minden zónának saját felügyeleti (authoritatív) szervere van, a lekérdezés pedig a gyökértől lefelé haladva — ma iteratívan — jut el a válaszig. Kényelmes eszköz, de a bizalom forrása is, ezért támadások célpontja.

## Tartalom

### Nevek és címek

- **Címek** (pl. 129.10.117.100) — a számítógépek által használt címkék a gépek azonosítására; a **hálózat szerkezetét** tükrözik.
- **Nevek** (pl. www.northeastern.edu) — ember számára értelmes címkék; a **szervezeti struktúrát** tükrözik.

### Előzmény: hosts.txt

A DNS előtt minden név–IP leképezés egy `hosts.txt`-ben volt (ma is: `/etc/hosts` Linuxon, `C:\Windows\System32\drivers\etc\hosts` Windowson). Központosított, manuális rendszer: a változásokat e-mailben kellett beküldeni az SRI-nek (Stanford Research Institute), a gépek periodikusan FTP-vel letöltötték; „flat” (sík) névtér, hierarchia nélkül. Szétesett, mert **nem skálázható**, nehéz volt a nevek **egyediségét** biztosítani (MIT: Massachusetts vagy Melbourne?), és sok gépnek elavult volt a fájlja.

### A DNS általában

- **Elosztott** adatbázis, nem központosított.
- Egyszerű **kliens–szerver** architektúra: **UDP 53-as port** (vannak TCP implementációk is); rövid kérések, rövid válaszok.
- **Hierarchikus névtér**: `.com → google.com → mail.google.com`.

### Névhierarchia és adminisztráció

- A gyökér (*Root*) alatt a legfelső szint a **TLD-k** (*Top Level Domains*): net, edu, com, gov, mil, org, uk, fr stb. Maximális famélység: 128.
- Minden doménnév egy részfa: `.edu → neu.edu → ccs.neu.edu → www.ccs.neu.edu`. Nincsenek névütközések (neu.com ≠ neu.edu).
- A fa **zónákra** bomlik; minden zóna rendelkezik egy felügyeleti szervvel, amely a hierarchia egy részéért felelős (a gyökér: ICANN; a com/net/edu/gov: Verisign; a `*.neu.edu`: NEU; a `*.ccs.neu.edu`: CCIS).
- **TLD-k** (ICANN, 1998): 22+ általános — klasszikus (.com, .edu, .gov, .mil, .org, .net) és későbbi (.aero, .museum, .xxx); ~250 **országkód** TLD (két betű, pl. .au, .hu; 2010-től nemzetközi karakterekkel is); némelyik elüzletiesedett (.tv — Tuvalu), „domain hack”-ek (instagr.am, goo.gl).

### Szerverek

- **Egy DNS szerver** a hierarchia egy részét felügyeli (nem kell minden nevet tárolnia), tárolja a zónájához tartozó hosztok és domének rekordjait (másolatok lehetnek a robusztusság miatt), és **ismeri a root szerverek címét**.
- **Root name serverek**: a Root Zone fájlért felelősek (lista a TLD-kről és felügyelőikről, ~272 KB; pl. `com. 172800 IN NS a.gtld-servers.net.`). Az ICANN adminisztrálja; **13 root szerver**, A–M címkékkel (pl. `i.root-servers.net`); ebből 6 **anycastolt** (globálisan sok replika). A gyakorlatban a rendszerek lokálisan cache-elik az információjukat.
- **Lokális névszerverek**: minden ISP/cégnek van egy alapértelmezett névszervere, gyakran a **DHCP** konfigurálja fel ([[concepts/telekom/arp-dhcp-icmp]]); a lekérdezések itt kezdődnek, az eredményt gyakran cache-elik.
- **Authoritatív névszerverek**: az adott hoszt név→IP leképezését tárolják (pl. a `neu.edu` felügyelője tudja, hogy `www.neu.edu = 155.33.17.68`).

### Névfeloldás

Minden hoszt ismer egy lokális DNS szervert, és minden kérést annak küld. Ha az tud válaszolni (mert ő a felügyelő, vagy van cache-elt rekordja), kész. Különben végigmegy a hierarchián **felülről lefelé** a keresett név felügyeleti szerveréig; a cache alapján lépések átugorhatók (pl. cache-elt root fájl esetén egyből az „edu” szerverhez).

| | **Rekurzív** lekérdezés | **Iteratív** lekérdezés |
|---|---|---|
| Működés | a kérdezett névszerver végzi el a teljes feloldást, és a válasszal tér vissza | a névszerver a választ vagy legalább a következő kérdezendő szerver adatait adja vissza („nem tudom, de ez a szerver talán igen”) |
| Előny | a szerver kihelyezheti a kliens terhelését; egy klienscsoport felett cache-elhet | a szervernek válasz után nincs dolga a kéréssel; könnyű nagy terhelésű szervert építeni |
| Hátrány | terhet rak a kérdezett szerverre (pl. root); a válasz továbbításához véletlen ID kell a lekérdezésben | |

**Napjainkban a DNS iteratív módon működik** (a lokális szerver kérdezi sorban a root, com, ns1.google.com szervereket).

**Cache vs. frissesség:** egy új domén kb. **72 óra** alatt válik elérhetővé (*DNS propagáció*), mert a zónafájlok **1–72 óráig** élnek a cache-ekben — addig a lokális szerver a régi, cache-elt zónafájl alapján azt feleli: „a név nem létezik”.

### Erőforrásrekordok (Resource Records)

A lekérdezés két mezője: **name** és **type**. A válasz rekordja négy mezőből áll: **(name, value, type, TTL)**; egy válaszban több rekord is lehet. A name és a value jelentése a típustól függ:

| Típus | Name | Value | Megjegyzés |
|---|---|---|---|
| **A** / **AAAA** | doménnév | IP-cím | A = IPv4, AAAA = IPv6 |
| **NS** | (rész)domén | a hozzá tartozó DNS szerver | „menj és küldd a kérésed ehhez a szerverhez” |
| **CNAME** | doménnév | kanonikus név | alias nevekhez; a CDN-ek is használják |
| **MX** | e-mailben szereplő doménnév | a mailszerver kanonikus neve | |
| **PTR** | IP-cím | doménnév | fordított lekérdezés; külön hierarchia (`in-addr.arpa`, `ip6.arpa`); nincs garancia, hogy minden IP-re működik |

### A DNS mint indirekció

Egy gép IP-címének cseréje triviális (csak a rekordot kell átírni); egy gépnek sok alias neve lehet; egy névhez sok IP tartozhat (**terheléselosztás**); a válasz függhet a földrajzi helytől és az ISP-től — erre épülnek a CDN-ek ([[concepts/telekom/cdn-es-p2p]]).

### Biztonság

A DNS a **bizalom forrása** a weben (a felhasználó azt várja, hogy a begépelt bank-cím a bankjához vigye).

- **DoS**: a szerverek túlterhelése. A 2002. októberi masszív DDoS a root szerverek ellen szinte észrevétlen maradt, mert a root zónák mindenhol cache-elve vannak; célzottabb támadás (lokális vagy authoritatív szerver ellen) hatékonyabb lenne.
- **DNS hijacking** (eltérítés): OS/böngésző fertőzése (a trójai átírja a `/etc/hosts`-ot), man-in-the-middle, válaszhamisítás (*spoofing*: a kérések lehallgatása, a válaszok megversenyeztetése).
- **DNS cache poisoning**: a támadó hamis bejegyzést juttat egy rekurzív/lokális szerver cache-ébe (pl. egy saját doménre vonatkozó kérdésre adott válasz *Authority*/*Additional* szekciójában nem releváns NS és A rekordokat is küld); a TTL lejártáig az adott szerver minden kliense hamis választ kap — sokkal rosszabb, mint a spoofing, mert **egy teljes ISP-t érinthet**.
- **Megoldás: DNSSEC** — a kritikus rekordokat kriptográfiai aláírással látják el, a feloldó ellenőrzi. Új rekordtípusok: **DNSKEY** (a zóna publikus kulcsa), **RRSIG** (a válasz aláírása), **DS** (kulcsok a delegációhoz), **NSEC/NSEC3** (a létezés hitelesített tagadása). A **Trust Anchor** a publikus kulcsok gyökere (a kliens konfigurációjában); a biztonság követi a DNS hierarchiát: $K_{ROOT}$ ellenőrzi $K_{EDU}$-t, az a $K_{UW.EDU}$-t, az pedig az IP-címet. Első változat 1997, újraírva 2005; root szerverek 2010 júliusától, .com/.net 2011 januárjától.
- **A DNSSEC nem old meg mindent**: a DNS továbbra is sebezhető **reflexiós/amplifikációs** támadásokkal. Mivel a DNS UDP-t használ (nincs kézfogás), hamisított forráscímű (az áldozat címe) kis kérésre nagy válasz (zónafájl, DNSSEC rekordok) megy az áldozatnak; a gyenge láncszem a **nyílt feloldók** (*open resolvers*). 2012-es eset: 65 Gbps DDoS.

**Vizsgaszempont:** rekurzív vs. iteratív lekérdezés; a rekordtípusok (A, AAAA, NS, CNAME, MX, PTR) name/value jelentése; a névszervertípusok; miért tart 72 óráig a propagáció; cache poisoning és a DNSSEC bizalmi lánca.

## Kapocs

- [[concepts/telekom/udp]] — a DNS szállítója (53-as port), és ezért sebezhető reflexióval
- [[concepts/telekom/cdn-es-p2p]] — DNS-alapú átirányítás a CDN-ekben
- [[concepts/telekom/http-es-web]] — a webes kérések első lépése a névfeloldás
- [[concepts/kript/hash-fuggveny]] — kriptográfiai alapok az aláírásokhoz
