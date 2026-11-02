---
tags: [concept]
sources: [Laki_Lecture_7b.pdf, Laki_Lecture_8.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# IPv4 fejléc és fragmentáció

Az IP datagram fejléce (legalább 20 bájt, 32 bites szavakba rendezve) tartalmazza a továbbításhoz szükséges összes információt: címeket, élettartamot, protokollazonosítót és a **darabolás** mezőit. Mivel minden hálózatnak saját MTU-ja van, a routereknek a túl nagy csomagot szét kell vágniuk, a célállomásnak pedig össze kell raknia — ez a **fragmentáció**.

## Tartalom

### A fejléc mezői

| Szó | Mezők |
|---|---|
| 1. | verzió (4 bit) · IHL / HLen (4) · szolgálat típusa / TOS (8) · teljes hossz (16) |
| 2. | azonosítás (16) · jelzőbitek: DF, MF · darabeltolás / offset |
| 3. | élettartam / TTL (8) · protokoll (8) · fejrész ellenőrző összege (16) |
| 4. | forrás címe (32) |
| 5. | cél címe (32) |
| … | opciók (változó; általában nincs) |

- **verzió** — melyik IP-verzió (jelenleg a 4 és 6 közötti átmenet zajlik).
- **IHL** — a fejléc hossza **32 bites szavakban**; legkisebb értéke **5** (azaz 20 bájt).
- **szolgálat típusa** — szolgálati osztály (3 bites precedencia, 3 jelzőbit: D, T, R).
- **teljes hossz** — fejléc és adatrész együttes hossza **bájtokban**.
- **azonosítás** — egy datagram minden darabja ugyanazt az értéket hordozza.
- **DF** — „ne darabold” (*don't fragment*) jelzés a routereknek.
- **MF** — „több darab” (*more fragments*): minden darabban be kell állítani, **kivéve az utolsót**.
- **darabeltolás** — a darab helye a datagramon belül (a diákon: elemi darabméret 8 bájt; a példák bájtban adják meg).
- **élettartam (TTL)** — elvileg másodpercenként kellene csökkenteni, a gyakorlatban **minden ugrásnál eggyel** csökkentik; nullánál a csomagot eldobják (ICMP időtúllépés — [[concepts/telekom/arp-dhcp-icmp]]).
- **protokoll** — a szállítási réteg protokolljának azonosítója (TCP, UDP…).
- **ellenőrző összeg** — csak a **fejrészre**; a routereken belüli rossz memóriaszavak okozta hibák ellen; **minden ugrásnál újra kell számolni** (hiszen a TTL változik).
- **forrás és cél címe** — IP-címek ([[concepts/telekom/ipv4-cimzes-es-cidr]]).
- **opciók** — a következő verzió bővíthetősége miatt hagyták benne; eredetileg 5 opció volt; a routerek általában figyelmen kívül hagyják.

### Miért kell fragmentáció?

Minden hálózatnak saját **MTU**-ja (*Maximum Transmission Unit*, a maximális csomagméret) van; a DARPA/Internet alapelv szerint a hálózatok heterogének lehetnek, és egy útvonal minimális MTU-ja nem ismert előre. Az IP megoldása: **vágjuk szét a csomagot, amikor az MTU csökken**, és **a fogadó állomásnál** állítsuk helyre.

Az Internet jellemzői ebből a szempontból: elosztott és heterogén (minden hálózat maga választ MTU-t); kapcsolat nélküli datagram-protokoll (minden darab tartalmazza a továbbításhoz szükséges összes információt, és a darabok függetlenül, akár különböző úton érkeznek); *best effort* (a routerek és a fogadó is eldobhat darabokat, a küldő értesítése nem kötelező); a legtöbb feladat a végpontra hárul.

### Kidolgozott példa

Útvonal: MTU 4000 → MTU 2000 → MTU 1500. Az eredeti datagram: 20 bájt fejléc + 3800 bájt adat (hossz 3820, MF = 0).

**Első router (MTU 2000):**
- 1. darab: hossz 2000 (20 + **1980**), MF = 1, offset = 0;
- 2. darab: hossz 1840 (20 + **1820**), MF = 0, offset = 1980. ($1980 + 1820 = 3800$.)

**Második router (MTU 1500):** mindkét darabot tovább kell vágni.
- az 1980 bájtos részből: hossz 1500 (20 + 1480), MF = 1, offset 0; és hossz 520 (20 + 500), MF = 1, offset 1480;
- az 1820 bájtos részből: hossz 1500 (20 + 1480), MF = 1, offset 1980; és hossz 360 (20 + 340), **MF = 0**, offset 3460.

Figyeljük meg: a „közbülső” darabok MF-je 1 marad, csak az eredetileg utolsó darab legutolsó része kap MF = 0-t.

### Helyreállítás a célállomáson

Az MF = 0 darabból kiszámítható a teljes adatmennyiség:
$$\text{hossz} - \text{fejléchossz} + \text{offset} = 360 - 20 + 3460 = 3800.$$

Kihívások: **nem sorrendben** érkező darabok, **duplikátumok**, **hiányzó** darabok — memóriakezelési szempontból „rémálom”.

### Fragmentáció a valóságban

A fragmentáció **költséges** (memória és CPU a visszaállításhoz), ezért ha lehet, kerülni kell.
- **MTU-felderítő protokoll** (*path MTU discovery*): a küldő a *don't fragment* bittel küld, és addig csökkenti a csomagméretet, amíg egy meg nem érkezik; egy router *can't fragment* hibaüzenete közvetlenül tartalmazhatja az adott hálózat MTU-ját.
- Darabokat kezelő router: gyors, specializált hardver, dedikált erőforrás.

Az IPv6 routerek már egyáltalán nem darabolnak ([[concepts/telekom/ipv6]]).

**Vizsgaszempont:** adott MTU-sorozatra a darabok hosszának, MF-jének és offsetjének kiszámítása — klasszikus számolási feladat; a fejlécmezők jelentése (különösen IHL, TTL, protokoll, checksum).

## Kapocs

- [[concepts/telekom/ipv4-cimzes-es-cidr]] — a forrás- és célcím szerkezete
- [[concepts/telekom/ipv6]] — egyszerűsített fejléc, fragmentáció nélkül
- [[concepts/telekom/csma-cd]] — az Ethernet 1500 bájtos MTU-ja
- [[concepts/telekom/arp-dhcp-icmp]] — ICMP hibaüzenetek (időtúllépés, elérhetetlen cél)
