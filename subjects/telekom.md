---
tags: [subject]
sources: [Laki_Lecture_1.pdf, Laki_Lecture_2.pdf, Laki_Lecture_3.pdf, Laki_Lecture_4.pdf, Laki_Lecture_5.pdf, Laki_Lecture_6.pdf, Laki_Lecture_7a.pdf, Laki_Lecture_7b.pdf, Laki_Lecture_8.pdf, Laki_Lecture_9.pdf, Laki_Lecture_10.pdf, Laki_Lecture_12_new.pdf, _telekom.md]
derivation: source
math: 15
updated: 2026-10-21
---

# Telekommunikációs hálózatok

Számítógépes hálózatok alulról felfelé, a hibrid ötrétegű modell mentén: fizikai réteg (jelek, kódolás, multiplexálás), adatkapcsolati réteg (keretezés, hibakezelés, csúszóablak, közeghozzáférés, switchek), hálózati réteg (routing, IP, címzés, BGP), szállítói réteg (UDP, TCP, torlódásvezérlés) és alkalmazási réteg (DNS, HTTP, CDN, P2P). Előadó: Laki Sándor; a diák Ács Zoltán (ELTE), D. Choffnes és P. Gill anyagaira épülnek.

## A tárgy célja

Megérteni, hogyan jut el egy bit, egy keret, egy csomag és egy bájtfolyam a küldőtől a címzettig, és melyik réteg milyen problémát old meg útközben. A vezérfonal a rétegzés: minden réteg csak az alatta lévő szolgáltatására épít ([[concepts/telekom/retegzett-halozati-architektura]]).

Órarend és oktatók: _telekom. Vizsga- vagy zárthelyi-követelményt sem a jegyzet, sem a diák nem tartalmaznak; ha előkerül, ide kell felvenni.

## Fogalomlapok

### 1. előadás — Alapfogalmak, történet, referenciamodellek

- [[concepts/telekom/halozati-alapfogalmak]] — hoszt, médium, propagációs és átviteli késés, kétféle sávszélesség, PAN/LAN/MAN/WAN
- [[concepts/telekom/internet-tortenete-es-tervezesi-elvei]] — ARPANET, Kahn négy alapelve, best effort
- [[concepts/telekom/retegzett-halozati-architektura]] — szolgáltatás–interfész–protokoll, beburkolás, homokóra-modell
- [[concepts/telekom/osi-referenciamodell]] — a hét réteg feladatai és példái
- [[concepts/telekom/tcp-ip-modell]] — a négyrétegű TCP/IP és a tárgyban használt hibrid ötrétegű modell

### 2. előadás — Fizikai réteg

- [[concepts/telekom/fourier-analizis-es-savkorlat]] — harmonikusok, a „b” karakter példája, csillapítás decibelben
- [[concepts/telekom/szimbolumok-baud-es-bitrata]] — bitráta = baud · log₂M
- [[concepts/telekom/atviteli-kozegek]] — réz, koax, üvegszál, spektrum, $\lambda f = c$, GEO/MEO/LEO műholdak
- [[concepts/telekom/digitalis-vonali-kodolasok]] — NRZ, NRZI, Manchester, 4B/5B, a szinkronizáció problémája
- [[concepts/telekom/modulacio]] — alapsáv és szélessáv, ASK/FSK/PSK, QPSK, QAM-16
- [[concepts/telekom/multiplexalas]] — SDM, FDM, WDM, TDM, CDM

### 3. előadás — CDMA, keretezés, hibadetektálás

- [[concepts/telekom/cdma]] — chipsorozatok, ortogonalitás, Walsh-mátrix, dekódolási példa
- [[concepts/telekom/keretezes]] — karakterszámlálás, bájt- és bitbeszúrás, SONET
- [[concepts/telekom/hibakezeles-alapjai]] — bithiba, burst, FEC vs. ARQ, redundancia, paritás
- [[concepts/telekom/hamming-tavolsag-es-korlat]] — $d+1$ és $2d+1$ szabály, kódráta, Hamming-korlát bizonyítással
- [[concepts/telekom/hamming-kod-keretekben]] — ellenőrző bitek kettőhatvány pozíción, kódolás és javítás

### 4. előadás — CRC és adatkapcsolati protokollok

- [[concepts/telekom/crc]] — mod 2 polinomosztás, kidolgozott példa, felismerhető hibák
- [[concepts/telekom/megall-es-var-protokoll]] — forgalomszabályozás, utópia → megáll-és-vár → ABP, kihasználtság
- [[concepts/telekom/csuszoablak-protokollok]] — pipelining, go-back-N, szelektív ismétlés
- [[concepts/telekom/hdlc-es-ppp]] — HDLC kerettípusai, PPP (LCP, NCP)
- [[concepts/telekom/ethernet]] — a 802.3 keret, kódolások, 64/1500 bájt, hubtól a switchig (több előadás anyaga)

### 5. előadás — Közeghozzáférés (MAC)

- [[concepts/telekom/kozeghozzaferes-alapjai]] — a csatornakiosztás osztályai és modellje, $S$ és $G$
- [[concepts/telekom/aloha]] — $S = Ge^{-2G}$ és $S = Ge^{-G}$ levezetése
- [[concepts/telekom/csma]] — 1-perzisztens, nem-perzisztens, $p$-perzisztens
- [[concepts/telekom/csma-cd]] — ütközésdetektálás, bináris exponenciális hátralék, minimális keret és kábelhossz

### 6. előadás — Ütközésmentes protokollok, LAN-ok összekapcsolása, routing

- [[concepts/telekom/versenymentes-protokollok]] — bittérkép, bináris visszaszámlálás, adaptív fabejárás
- [[concepts/telekom/bridge-es-switch]] — címtanulás, továbbítás, elárasztás, a 2. réteg korlátai
- [[concepts/telekom/feszitofa-protokoll]] — 802.1 STP, BPDU, gyökérválasztás
- [[concepts/telekom/routing-alapok]] — optimalitási elv, nyelőfa, adaptív és statikus algoritmusok
- [[concepts/telekom/tavolsagvektor-routing]] — elosztott Bellman–Ford, végtelenig számolás, poisoned reverse

### 7. előadás (7a, 7b) — Link-state, hierarchikus routing

- [[concepts/telekom/kapcsolatallapot-routing]] — HELLO/ECHO/LSA, elárasztás, Dijkstra kidolgozva, OSPF vs. IS-IS
- [[concepts/telekom/hierarchikus-es-adatszoro-routing]] — tartományok, IGP/EGP, broadcast és multicast routing

### 8. előadás — Az IP és segédprotokolljai

- [[concepts/telekom/ipv4-fejlec-es-fragmentacio]] — fejlécmezők, MTU, darabolási példa
- [[concepts/telekom/ipv4-cimzes-es-cidr]] — osztályok, alhálózat, CIDR, leghosszabb prefix, aggregálás
- [[concepts/telekom/nat]] — privát tartományok, portalapú címfordítás, ellenérvek
- [[concepts/telekom/ipv6]] — 128 bites címek, egyszerűsített fejléc, tunnelek
- [[concepts/telekom/bgp]] — AS-ek, útvonalvektor, politikák, eBGP/iBGP
- [[concepts/telekom/arp-dhcp-icmp]] — ICMP üzenetek, ARP, RARP, BOOTP, DHCP

### 9. előadás — VPN, szállítói réteg 1

- [[concepts/telekom/vpn-es-ipsec]] — alagutak, IP-az-IP-ben, IPsec alagút mód
- [[concepts/telekom/udp]] — demultiplexálás portokkal, 8 bájtos fejléc
- [[concepts/telekom/tcp]] — kézfogás, sorszámok, meghirdetett ablak, Nagle, RTO és Karn

### 10. előadás — Szállítói réteg 2

- [[concepts/telekom/tcp-torlodasvezerles]] — cwnd, slow start, AIMD, Tahoe, Reno, CUBIC, a TCP problémái
- [[concepts/telekom/aktiv-sorkezeles-es-dctcp]] — drop-tail, RED, ECN, DCTCP

### 12–13. előadás — Alkalmazási réteg

- [[concepts/telekom/dns]] — névhierarchia, szervertípusok, iteratív feloldás, rekordok, DNSSEC
- [[concepts/telekom/http-es-web]] — kapcsolattípusok, üzenetek, sütik, caching, proxy
- [[concepts/telekom/cdn-es-p2p]] — terheléselosztás, CDN, DNS-átirányítás, anycast, BitTorrent

## Vizsgafelkészülés — számolós feladattípusok

Minden lap végén „Vizsgaszempont” bekezdés áll. A kézzel számolandó feladattípusok és lapjaik:

- baud ↔ bitráta, $\lambda f = c$, decibel — [[concepts/telekom/szimbolumok-baud-es-bitrata]], [[concepts/telekom/atviteli-kozegek]], [[concepts/telekom/fourier-analizis-es-savkorlat]]
- jelalak NRZ/NRZI/Manchester kódolással — [[concepts/telekom/digitalis-vonali-kodolasok]]
- CDMA dekódolás — [[concepts/telekom/cdma]]
- bájt- és bitbeszúrás — [[concepts/telekom/keretezes]]
- Hamming-távolság, Hamming-kódszó és hibajavítás — [[concepts/telekom/hamming-tavolsag-es-korlat]], [[concepts/telekom/hamming-kod-keretekben]]
- CRC-maradék — [[concepts/telekom/crc]]
- csatornakihasználtság, ablakméret — [[concepts/telekom/megall-es-var-protokoll]], [[concepts/telekom/csuszoablak-protokollok]]
- ALOHA optimum levezetése — [[concepts/telekom/aloha]]
- minimális keretméret, maximális kábelhossz — [[concepts/telekom/csma-cd]]
- bináris visszaszámlálás, fabejárás — [[concepts/telekom/versenymentes-protokollok]]
- feszítőfa — [[concepts/telekom/feszitofa-protokoll]]
- távolságvektor-táblák, Dijkstra — [[concepts/telekom/tavolsagvektor-routing]], [[concepts/telekom/kapcsolatallapot-routing]]
- IP-fragmentáció — [[concepts/telekom/ipv4-fejlec-es-fragmentacio]]
- leghosszabb prefix, aggregálás — [[concepts/telekom/ipv4-cimzes-es-cidr]]
- cwnd lefutása — [[concepts/telekom/tcp-torlodasvezerles]]
- HTTP válaszidő — [[concepts/telekom/http-es-web]]

## Hiányzó anyagrészek

- A tanmenet ([[concepts/telekom/tcp-ip-modell]]) szerinti **socketprogramozás** nincs a forrásdiák között (a 11. előadás diasora hiányzik).
- A **kitekintés** (SDN, OpenFlow, P4, 5G) szintén csak a tanmenetben szerepel.
- A vezeték nélküli LAN-ok (802.11, CSMA/CA) egyik ingestelt diasorban sem szerepelnek.
