---
tags: [concept]
sources: [Laki_Lecture_2.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Digitális vonali kódolások

A vonali kódolás dönti el, hogyan lesz a bitekből feszültségjel alapsávú átvitelnél. A fő probléma a **szinkronizáció**: a vevő órája csak a jelátmenetekből tud igazodni, ezért a hosszú, átmenet nélküli sorozatok (csupa 0 vagy csupa 1) deszinkronizációhoz vezetnek. A kódok ebben, és a sávszélesség-hatékonyságban térnek el.

## Tartalom

### Kiinduló feltételek és a szinkronizáció problémája

Két diszkrét jelszintünk van (magas = 1, alacsony = 0), az átvitel szinkron: egy óra vezérli a mintavételezést. A vevő szempontjából a jel amplitúdója és időbeli kiterjedése számít.

**Deszinkronizáció**: hosszú egyes- vagy nullás sorozat alatt nincs átmenet, a két óra elcsúszik egymáshoz képest, és a vevő kihagy (vagy beszúr) egy bitet. További kérdés: hogyan különböztessük meg a sok nullát attól az állapottól, amikor egyáltalán nincs jel?

Megoldási lehetőségek:

1. **Explicit órajel** — párhuzamos csatornán; rövid átvitelnél alkalmas.
2. **Kritikus időpontok** — pl. egy szimbólum vagy blokk kezdetén szinkronizálunk, közben az órák szabadon futnak (feltéve, hogy rövid ideig együtt maradnak).
3. **Szimbólumkódok, önütemező jel** (*self-clocking*) — a jel maga hordozza a szinkronizációhoz szükséges információt, külön óra nélkül dekódolható.

### A kódok leírása

A digitális kódok három momentumban térnek el: mi történik a jelintervallum **elején**, **közepén** és **végén**. A leírásban ez a hármas zárójelben áll.

| Kód | (eleje, közepe, vége) |
|---|---|
| **NRZ-L** | 1 → magas, 0 → alacsony szint; semmi; semmi |
| **NRZ-M** | 1 → szintváltás, 0 → nincs váltás; semmi; semmi |
| **RZ** | 1 → magas, 0 → alacsony; 1-esnél középen váltás (visszatér nullára); semmi |
| **Biphase-Mark** | mindig váltás; 1-esnél középen váltás; semmi |
| **Biphase-Space** | mindig váltás; 0-snál középen váltás; semmi |
| **Differential Manchester** | 0-snál váltás; mindig váltás középen; semmi |
| **Delay-Modulation** | semmi; 1-esnél váltás; 0-s bit után, ha 0-s bit következik, váltás |
| **Manchester** | semmi; 1 → magasról alacsonyra, 0 → alacsonyról magasra; semmi |

### A három fontos kód részletesen

**NRZ (Non-Return to Zero)**: 1 → magas jel, 0 → alacsony jel. Egyszerű, de hosszú 0- vagy 1-sorozatnál elveszik a szinkron.

**Manchester** (10 Mbps Ethernet, a diákon 10BASE-TX): 1 → átmenet magasról alacsonyra, 0 → alacsonyról magasra, a bitidő közepén. Minden bitben van átmenet, így megoldja az órák elcsúszását. Hátránya: az átviteli kapacitás **felét** használja ki (bitenként két óraciklus kell).

**NRZI (Non-Return to Zero Inverted)**: 1 → átmenet, 0 → a szint változatlan marad. A csupa egyes sorozatot megoldja, a **csupa nullát nem**.

### 4B/5B kódolás NRZI előtt (100 Mbps Ethernet, 100BASE-TX)

Ötlet: minden 4 bites csoportot egy 5 bites kódszóra cserélünk úgy, hogy egyik kódszó elején se legyen egynél több, a végén kettőnél több nulla. Így egymás után fűzve sem lesz háromnál több egymást követő nulla, és az NRZI mindig kap átmenetet.

| 4 bit | 5 bit | 4 bit | 5 bit |
|---|---|---|---|
| 0000 | 11110 | 1000 | 10010 |
| 0001 | 01001 | 1001 | 10011 |
| 0010 | 10100 | 1010 | 10110 |
| 0011 | 10101 | 1011 | 10111 |
| 0100 | 01010 | 1100 | 11010 |
| 0101 | 01011 | 1101 | 11011 |
| 0110 | 01110 | 1110 | 11100 |
| 0111 | 01111 | 1111 | 11101 |

Ára: 5 bitből csak 4 hasznos, **20%-ot veszítünk a hatékonyságból** — de ez jóval kevesebb, mint a Manchester 50%-a. A Gigabit Ethernet ugyanezt az elvet **8B/10B** kódolással valósítja meg.

**Vizsgaszempont:** adott bitsorozat jelalakjának felrajzolása NRZ, NRZI és Manchester kódolással; a kódok önütemező képességének és hatékonyságának összevetése (NRZ 100%, 4B/5B 80%, Manchester 50%).

## Kapocs

- [[concepts/telekom/modulacio]] — szélessávú átvitel: a bitek vivőhullámra ültetése
- [[concepts/telekom/szimbolumok-baud-es-bitrata]] — többszintű szimbólumok
- [[concepts/telekom/ethernet]] — a Manchester és a 4B/5B alkalmazása
