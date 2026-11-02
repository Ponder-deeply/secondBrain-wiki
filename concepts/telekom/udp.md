---
tags: [concept]
sources: [Laki_Lecture_9.pdf]
derivation: source
kind: comparison
element: air
updated: 2026-09-25
---

# UDP és a szállítói réteg demultiplexálása

A szállítói réteg alapfeladata az **adatfolyamok demultiplexálása**: egy hoszton sok alkalmazás fut egyszerre, és az IP csak a géphez juttatja el a csomagot. Ezt a **portszámok** oldják meg. A legegyszerűbb szállítói protokoll, az **UDP** (*User Datagram Protocol*) szinte csak ennyit tesz hozzá az IP-hez: 8 bájtos fejléc, portok és egy kontrollösszeg — kapcsolat, megbízhatóság és sorrend garancia nélkül.

## Tartalom

### A szállítói réteg feladatai

- **Feladat:** adatfolyamok demultiplexálása.
- **További lehetséges feladatok:** hosszú élettartamú kapcsolatok; megbízható, sorrendhelyes csomagleszállítás; hibadetektálás; folyam- és torlódásvezérlés.
- **Kihívások:** torlódások detektálása és kezelése; egyensúly a fairség és a csatornakihasználás között.

A szállítói réteg a **legalacsonyabb szintű végpont–végpont protokoll**: fejléceit csak a forrás és a cél végpont olvassa; a routerek számára a szállítói fejléc csak szállítandó adat (*payload*) ([[concepts/telekom/retegzett-halozati-architektura]]).

### Multiplexálás

Datagram hálózatban nincs áramkörkapcsolás és nincs kapcsolat; a kliensek számos alkalmazást futtathatnak egyidőben — kinek szállítsuk le a csomagot? Az IP fejléc „protokoll” mezője csak **8 bit = 256** konkurens folyamot tudna megkülönböztetni — ez nem elég. A demultiplexálás a **szállítói réteg feladata**.

A szerveralkalmazások számos klienssel kommunikálnak; minden alkalmazás egyedi portot kap, és mind ugyanazt a hálózatot használják. A végpontokat (egy kommunikációt) az ötös azonosítja:

$$\langle \text{src\_ip},\ \text{src\_port},\ \text{dest\_ip},\ \text{dest\_port},\ \text{proto}\rangle,$$

ahol `proto` UDP vagy TCP.

### Az UDP fejléc

| 0–15 bit | 16–31 bit |
|---|---|
| Forrás port | Cél port |
| Adat hossz | Kontrollösszeg |

- **8 bájtos** fejléc.
- Egyszerű, **kapcsolatnélküli** átvitel — C socketeknél `SOCK_DGRAM`.
- A **portszámok** teszik lehetővé a demultiplexálást: 16 bit = 65 535 lehetséges port; a 0. port nem engedélyezett.
- **Kontrollösszeg** hibadetektáláshoz: felismeri a hibás csomagokat, de **nem** detektálja az elveszett, duplikált és helytelen sorrendben érkező csomagokat — UDP esetén ezekre nincs garancia.

### Mire jó az UDP?

- A TCP után vezették be — mert **nem minden alkalmazásnak megfelelő a TCP** (pl. a késleltetés fontosabb, mint a teljes megbízhatóság).
- UDP felett **egyedi protokollok** valósíthatók meg: maguk dönthetnek a megbízhatóságról, a sorrendről, a folyam- és torlódásvezérlésről.
- Példák: **RTMP**, valós idejű médiastreamelés (hang, videó), a **Facebook adatközponti protokollja**. A hálózati réteg segédprotokolljai közül a BOOTP és a DHCP is UDP-t használ ([[concepts/telekom/arp-dhcp-icmp]]), az alkalmazási rétegben pedig a DNS ([[concepts/telekom/dns]]).

### UDP vs. TCP röviden

| | UDP | TCP |
|---|---|---|
| Kapcsolat | nincs | kapcsolatalapú (3-utas kézfogás) |
| Megbízhatóság, sorrend | nincs garancia | megbízható, sorrendhelyes bájtfolyam |
| Folyam- és torlódásvezérlés | nincs | van |
| Fejléc | 8 bájt | 20 bájt + opciók |
| Socket típus | `SOCK_DGRAM` | `SOCK_STREAM` |

**Vizsgaszempont:** a demultiplexálás ötöse; az UDP fejléc 4 mezője és mérete; mit detektál és mit nem a kontrollösszeg; mikor jobb az UDP a TCP-nél.

## Kapocs

- [[concepts/telekom/tcp]] — a megbízható szállítói protokoll
- [[concepts/telekom/nat]] — a portmezőket a NAT is kihasználja
- [[concepts/telekom/dns]] — tipikus UDP-alapú alkalmazási protokoll
- [[concepts/telekom/tcp-ip-modell]] — a szállítói réteg helye
