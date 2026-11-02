---
tags: [concept]
sources: [Laki_Lecture_1.pdf]
derivation: source
kind: definition
element: air
updated: 2026-09-25
---

# Hálózati alapfogalmak

A tárgy első előadásának szótára: mi a hoszt, a médium, a kétféle késleltetés és a kétféle sávszélesség, és hogyan osztályozzuk a hálózatokat kiterjedésük és felépítésük szerint. A gyakorlati beugró tesztek pontosan ilyen definíciókat kérdeznek.

## Tartalom

### Szereplők és közeg

- **Hálózati hoszt** (*host*): olyan eszköz, amely egy számítógépes hálózattal összeköttetésben áll. Információt oszthat meg, szolgáltatást és alkalmazásokat nyújthat a hálózat többi csomópontjának.
- **Átviteli csatorna / médium / fizikai közeg**: az a közeg, amelyen a kommunikáció a hosztok között folyik — koaxiális kábel, levegő, optikai kábel stb. (részletesen: [[concepts/telekom/atviteli-kozegek]]).

### Kétféle késleltetés

A két fogalmat a vizsgán rendszeresen összecserélik, ezért érdemes pontosan megjegyezni:

| Fogalom | Jelölés | Jelentés | Mitől függ |
|---|---|---|---|
| **Propagációs késés** (*propagation delay*) | $d_{prop}$ vagy $d$ | az idő, amíg a jel a küldőtől **megérkezik** a címzetthez | távolság és terjedési sebesség |
| **Átviteli késleltetés** (*transmission delay*) | $d_T$ | az idő, amíg egy csomag **összes bitje felkerül** a csatornára | csomagméret és sávszélesség |

Az átviteli késleltetés egy $L$ bites csomagra és $B$ bit/s sávszélességre $d_T = L/B$; a propagációs késés $s$ távolságra és $v$ terjedési sebességre $d_{prop} = s/v$ (rézben és üvegszálban $v \approx \tfrac{2}{3}c$, lásd [[concepts/telekom/atviteli-kozegek]]).

### Kétféle sávszélesség

- **Jel sávszélesség**: jelfeldolgozásban az egymást követő frekvenciák legnagyobb és legkisebb eleme közötti különbség; **Hertzben** mérik. Ez korlátozza, hogy hány harmonikus jut át a csatornán ([[concepts/telekom/fourier-analizis-es-savkorlat]]).
- **Hálózati sávszélesség**: az adatátvitelhez elérhető vagy felhasznált kommunikációs erőforrás mértéke, **bit/s**-ban.

A mértékegységeknél két szabvány él egymás mellett:

| SI (decimális) | IEC (bináris) |
|---|---|
| 1 KB/s $= 8\cdot 10^3$ bit/s (kilobájt) | 1 KiB/s $= 8\cdot 2^{10}$ bit/s (kibibájt) |
| 1 MB/s $= 8\cdot 10^6$ bit/s | 1 MiB/s $= 8\cdot 2^{20}$ bit/s |
| 1 GB/s $= 8\cdot 10^9$ bit/s | 1 GiB/s $= 8\cdot 2^{30}$ bit/s |
| … TB, PB, EB ($10^{12}, 10^{15}, 10^{18}$) | … TiB, PiB, EiB ($2^{40}, 2^{50}, 2^{60}$) |

A hálózati sebességeknél az SI prefixum a szokásos.

### Kapcsolási elv

- **Csomagkapcsolt hálózat** (pl. Internet): az adatot csomagokra bontjuk, a különböző forgalmak csomagjai közösen, összekeverve használják a vonalat.
- **Áramkörkapcsolt hálózat** (pl. vezetékes telefon): a kommunikáció idejére dedikált út épül ki a kapcsolóközpontokon át.

### Osztályozás kiterjedés szerint (Tanenbaum)

| Processzorok távolsága | Terület | Hálózattípus |
|---|---|---|
| 1 m | négyzetméter | PAN — *Personal Area Network* |
| 10 m – 1 km | szoba, épület, kampusz | LAN — *Local Area Network* |
| 10 km | város | MAN — *Metropolitan Area Network* |
| 100 – 1000 km | ország, kontinens | WAN — *Wide Area Network* |
| 10 000 km | bolygó | Internet |

### Példa topológiák

- **Sín-topológia** (LAN): minden állomás egy közös kábelre csatlakozik.
- **Gyűrű-topológia** (LAN): az állomások zárt körben kapcsolódnak.
- **TV-kábel alapú hálózat** (MAN): fejállomásból induló fa, a házak koaxiális ágakra csatlakoznak.
- **WAN**: LAN-okat köt össze egy routerekből álló **alhálózattal**; a csomagokat a routerek egyenként továbbítják, és minden router maga dönti el, melyik szomszédnak küldi tovább.

### Mi az Internet?

„Hálózatok hálózata”: világra kiterjedő nyitott WAN. Jellemzői: rendszerfüggetlen, nincs központi felügyelete, építőelemei a LAN-ok, globális, és olyan szolgáltatásokat nyújt, mint a World Wide Web, az e-mail vagy a fájlátvitel. Tervezési elveit lásd: [[concepts/telekom/internet-tortenete-es-tervezesi-elvei]].

## Kapocs

- [[concepts/telekom/internet-tortenete-es-tervezesi-elvei]] — az Internet mint „hálózatok hálózata” kialakulása
- [[concepts/telekom/retegzett-halozati-architektura]] — hogyan szervezzük a hálózati funkciókat
- [[concepts/telekom/atviteli-kozegek]] — a médium fajtái és jellemzői
- [[concepts/telekom/megall-es-var-protokoll]] — a propagációs és átviteli késleltetés a csatornakihasználtság képletében
