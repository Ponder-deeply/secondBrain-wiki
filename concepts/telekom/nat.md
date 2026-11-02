---
tags: [concept]
sources: [Laki_Lecture_7b.pdf, Laki_Lecture_8.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# NAT — hálózati címfordítás

A NAT (*Network Address Translation*) **gyors javítás az IP-címek elfogyásának problémájára**: egy cég vagy háztartás kifelé egyetlen (vagy kevés) nyilvános IP-címet kap, belül pedig privát címtartományt használ. A határon álló **NAT box** a kimenő csomagokban lecseréli a forráscímet, és a válaszokat a **portszám** segítségével juttatja vissza a megfelelő belső géphez.

## Tartalom

### Alapelvek

- Az internetforgalomhoz minden cég egy vagy legalábbis kevés IP-címet kap.
- A vállalaton belül minden számítógép egyedi (privát) IP-címet használ a belső forgalomirányításra.
- A vállalaton kívülre menő csomagokban **címfordítást** végzünk.
- A belső hálózatban három privát IP-címtartományt használunk:

| Tartomány | Lehetséges hosztok |
|---|---|
| 10.0.0.0/8 | 16 777 216 ($2^{24}$) |
| 172.16.0.0/12 | 1 048 576 ($2^{20}$) |
| 192.168.0.0/16 | 65 536 ($2^{16}$) |

(A diák a 172.16.0.0/12-re 1 084 576-ot írnak, de $2^{20} = 1\,048\,576$.)

- A címfordítást a **NAT box** végzi.

### Hogyan fogadja a választ?

A kimenő csomag forráscíme a NAT box nyilvános címe lesz — de honnan tudja a NAT box, hogy a visszaérkező válasz melyik belső géphez tartozik?

- A **port** mezőket használja, amelyek mind a TCP, mind az UDP fejlécben megvannak ([[concepts/telekom/udp]], [[concepts/telekom/tcp]]).
- Kimenő csomagnál egy **mutatót** (egy fordítási táblabeli indexet) tárol le, és ezt írja be a **forrásport** mezőbe. A NAT boxnak egy **65 536 bejegyzésből** álló fordítási táblázatot kell kezelnie.
- A fordítási táblázat bejegyzése tartalmazza az **eredeti (belső) IP-címet és forrásportot**.
- Visszaérkező csomagnál a célport alapján kikeresi a bejegyzést, és visszaírja a belső címet és portot.

Példa: a 10.0.0.1 belső gép csomagja a NAT boxon át 192.60.42.12 forráscímmel megy ki; a forrásport egy táblabejegyzés (pl. 4.) indexe lesz.

### Ellenérvek

- **Sérti az IP architekturális modelljét** (minden IP-cím egyetlen gépet azonosít világszerte).
- **Összeköttetés-alapú hálózatot képez** (a NAT box állapotot tart, összeomlásakor minden kapcsolat elvész).
- **Sérti a rétegmodell alapelveit** — a hálózati rétegbeli eszköz a szállítói réteg fejlécéhez nyúl.
- **Kötöttség a TCP és UDP fejléchez** (más szállítói protokollal nem működik).
- **A szöveg törzsében is lehet IP-cím** (egyes alkalmazások az adatban küldik a címüket, amit a NAT nem fordít).
- **Szűkös porttartomány** (legfeljebb 65 536 egyidejű leképezés).

A rétegzés szempontjából a NAT a „végpont–végpont elérhetőség megtörése” példája ([[concepts/telekom/retegzett-halozati-architektura]]). A hosszú távú megoldás a nagyobb címtér, az IPv6 ([[concepts/telekom/ipv6]]).

**Vizsgaszempont:** a NAT működése a portmezővel, a három privát tartomány és az ellenérvek felsorolása.

## Kapocs

- [[concepts/telekom/ipv4-cimzes-es-cidr]] — a címfogyás háttere
- [[concepts/telekom/ipv6]] — a címfogyás végleges megoldása
- [[concepts/telekom/tcp]] — a portszámok helye a szegmensben
- [[concepts/telekom/retegzett-halozati-architektura]] — a rétegelvek megsértése
