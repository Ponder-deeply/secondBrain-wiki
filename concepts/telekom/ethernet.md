---
tags: [concept]
sources: [Laki_Lecture_2.pdf, Laki_Lecture_4.pdf, Laki_Lecture_5.pdf, Laki_Lecture_6.pdf]
derivation: source
kind: definition
element: air
updated: 2026-09-25
---

# Ethernet (IEEE 802.3)

Az Ethernet a LAN-ok uralkodó adatkapcsolati technológiája. Eredetileg **adatszóró**, közös közegű hálózat volt CSMA/CD közeghozzáféréssel; ma switchekkel összekötött, full-duplex pont-pont linkekből áll. Ez a lap összegyűjti, amit a tárgy különböző előadásai az Ethernetről mondanak: keretformátum, kódolás, keretméret-korlátok és a topológia fejlődése.

## Tartalom

### Keretformátum (802.3)

| Mező | Méret (bájt) | Szerep |
|---|---|---|
| Preambulum | 7 | |
| Keretkezdő határoló (SFD) | 1 | |
| Cél MAC-cím | 6 | MAC (fizikai) cím |
| Forrás MAC-cím | 6 | |
| 802.1Q tag (opcionális) | 4 | |
| EtherType vagy hossz | 2 | a hasznos teher protokollja vagy hossza |
| Payload | 42/46 – 1500 | a beburkolt IP datagram |
| FCS | 4 | 32 bites CRC ([[concepts/telekom/crc]]) |
| Keretköz | 12 | szünet a következő keretig |

A beburkolás rendjében az Ethernet-keret az IP datagramot hordozza ([[concepts/telekom/retegzett-halozati-architektura]]); a MAC-címet az IP-címből az ARP határozza meg ([[concepts/telekom/arp-dhcp-icmp]]).

### Vonali kódolás sebességenként

- **10 Mbps**: **Manchester**-kódolás — minden bitben van átmenet, önütemező, de a kapacitás felét elhasználja.
- **100 Mbps (100BASE-TX)**: **4B/5B** + NRZI — 20% veszteség.
- **Gigabit Ethernet**: **8B/10B**.

Részletesen: [[concepts/telekom/digitalis-vonali-kodolasok]].

### Keretméret-korlátok

- **Minimális keret: 64 bájt.** A CSMA/CD-nek látnia kell az ütközést, mielőtt a küldő befejezi a keretet: $T_f \ge 2T_{pg}$. 10 Mbps-on és $2\cdot10^8$ m/s jelsebességgel ez legfeljebb 5120 m-es kiterjedést enged; 1 Gbps-on ugyanez a keretméret csak 51 m-t ([[concepts/telekom/csma-cd]]).
- **Maximális keret (MTU): 1500 bájt** payload. Nagyobb keretnél a hibák javítása drága (túl sok adatot kell újraküldeni); kisebbnél sok a fejléc-overhead és a feldolgozási idő. Adatközpontokban **jumbo keretek**: 9000 bájt. Az IP ehhez igazodva darabol ([[concepts/telekom/ipv4-fejlec-es-fragmentacio]]).

### A topológia fejlődése

1. **10Base2** — koaxiális kábel, T-csatlakozók és lezárók (*terminator*); minden állomás egyetlen közös kábelen: sín-topológia, egy ütközési tartomány.
2. **10BaseT, 100BaseT** („T” = sodrott érpár) — csillag **hubbal**. A hub és a repeater **1. rétegbeli** eszköz: a bitjeleket minden portra továbbítja, így továbbra is egyetlen ütközési tartomány van. Előny: egyszerű, olcsó, „buta” hardver; hátrány: nem skálázható — több állomás, több ütközés.
3. **Bridge-ek és switchek** — 2. rétegbeli eszközök, portonként külön ütközési tartomány, MAC-címtanulás és feszítőfa ([[concepts/telekom/bridge-es-switch]], [[concepts/telekom/feszitofa-protokoll]]). A switch minden portján egyetlen hoszt van full-duplex linken, így **nincs szükség CSMA/CD-re**.

### Közeghozzáférés

A klasszikus, adatszóró Ethernet MAC-protokollja a **CSMA/CD** bináris exponenciális hátralékkal: ütközés után $k \in [0, 2^n-1]$ rést vár, $n \le 10$, 16 sikertelen próba után eldobja a keretet ([[concepts/telekom/csma-cd]], [[concepts/telekom/csma]]).

**Vizsgaszempont:** a keret mezői és méretei; miért 64 és 1500 bájt a két határ; hub vs. switch; melyik sebességhez melyik vonali kód tartozik.

## Kapocs

- [[concepts/telekom/csma-cd]] — a közeghozzáférés és a minimális keretméret
- [[concepts/telekom/bridge-es-switch]] — a switchelt Ethernet
- [[concepts/telekom/hdlc-es-ppp]] — másik keretformátum, összevetésre
- [[concepts/telekom/kozeghozzaferes-alapjai]] — a MAC-probléma általában
