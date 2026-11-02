---
tags: [concept]
sources: [Laki_Lecture_8.pdf]
derivation: source
kind: definition
element: air
updated: 2026-09-25
---

# IPv6

Az IPv4 $2^{32}$ címe kevesebb, mint egy cím emberenként, és a világ egy részén már nincs kiosztható blokk. Az 1998-ban bevezetett IPv6 **128 bites címekkel** oldja meg a problémát, és közben egyszerűsíti a fejlécet: nincs benne ellenőrző összeg, és a routerek nem darabolnak. Bevezetése mégis lassú, mert az IP a protokollverem „dereka” — cseréje az egész Internet frissítését jelenti.

## Tartalom

### A címfogyás

- $2^{32} = 4\,294\,967\,296$ lehetséges cím — kevesebb, mint egy emberenként.
- Az IANA az utolsó /8 blokkot **2011-ben** osztotta ki. A regionális regisztrátorok (RIR) utolsó blokkjai: APNIC (Ázsia/Csendes-óceán) 2011. április 19., RIPE (Európa/Közel-Kelet) 2012. szeptember 14., ARIN és LACNIC 2015 (előrejelzés), AFRINIC 2022 (előrejelzés).

### Címformátum

- **128 bites** címek; kb. $4{,}8\cdot10^{28}$ cím/ember.
- 16 bites értékek **8 csoportban**, kettősponttal elválasztva, hexadecimálisan.
- Minden csoport **vezető nullái** elhagyhatók.
- **Csupa nulla csoportok** (egy összefüggő sorozatuk) elhagyhatók, helyükre `::` kerül.

Példa:
```
2001:0db8:0000:0000:0000:ff00:0042:8329
2001:db8:0:0:0:ff00:42:8329
2001:db8::ff00:42:8329
```

A localhost IPv4-ben `127.0.0.1`, IPv6-ban **`::1`**.

### Fejléc

Az IPv6 fejléc az IPv4 kétszerese: **320 bit** (40 bájt) vs. 160 bit (20 bájt), de fix hosszú és egyszerűbb. Mezői: Version, DSCP/ECN (ld. IPv4 TOS), **Flow Label**, Datagram Length, **Next Header** (ld. IPv4 Protocol mező), **Hop Limit** (ld. IPv4 TTL), forrás- és célcím (128–128 bit).

**Hiányzó mezők az IPv4-hez képest:**
- **fejléc hossza** — beépült a Next Header mechanizmusba (kiegészítő fejlécek láncolata);
- **checksum** — korábban sem igazán használták;
- **Identifier, Flags, Offset** — az IPv6 **routerek nem támogatják a fragmentációt**; az állomások MTU-felderítést alkalmaznak ([[concepts/telekom/ipv4-fejlec-es-fragmentacio]]).

Háttér: az Internet-használat súlypontjai megváltoztak — a mai hálózatok sokkal homogénebbek, mint kezdetben gondolták, a routing költsége és bonyolultsága viszont domináns.

### Teljesítménynövekmény

- Nincsenek ellenőrizendő kontrollösszegek.
- Nem kell a fragmentációt kezelni a routerekben.
- Egyszerű routingtábla-szerkezet: a címtér nagy, **nincs szükség CIDR-re** (de aggregáció kell); a szabványos alhálózatméret **$2^{64}$ cím**.
- Egyszerű autokonfiguráció: *Neighbor Discovery Protocol*.

### További lehetőségek

- **Forrás-routing** — az állomás meghatározhatja az útvonalat, amelyen a csomagjait továbbítani szeretné.
- **Mobil IP** — az állomások magukkal vihetik IP-címüket más hálózatokba (forrás-routinggal irányítva).
- **Privacy kiterjesztések** — véletlenszerűen generált állomásazonosítók; megnehezítik egy IP-cím adott állomáshoz kapcsolását.
- **Jumbogramok** — 4 GB-os datagramok.

### Bevezetési nehézségek

Az IP a protokollverem homokórájának dereka ([[concepts/telekom/retegzett-halozati-architektura]]): az IPv6 bevezetése **minden router és minden hoszt** frissítését jelentené, és új segédprotokollokat: ICMPv6, DHCPv6, DNSv6. A Google forgalmának 2013-ban 0,94%-a, 2015-ben 2,5%-a volt IPv6 feletti (2016 végére kb. 12–15%).

A végpontok ma többnyire támogatják (Windows, OSX, iOS, Android, access pointok); a **probléma az Internet magja**: egy csak IPv4-es mag nem routolja az IPv6 forgalmat.

**Átmeneti megoldás — tunnelek:** az IPv6 csomagokat IPv4 csomagokba csomagoljuk, és így továbbítjuk az IPv4 hálózaton. Implementációk: **6to4**, **IPv6 Rapid Deployment (6rd)**, **Teredo** stb.

**Vizsgaszempont:** IPv6 cím rövidítése és kiterjesztése; mely IPv4 fejlécmezők tűntek el és miért; az átmenet problémája és a tunnelezés.

## Kapocs

- [[concepts/telekom/ipv4-fejlec-es-fragmentacio]] — a lecserélt fejléc és a darabolás
- [[concepts/telekom/ipv4-cimzes-es-cidr]] — a címfogyás háttere
- [[concepts/telekom/nat]] — a rövid távú alternatíva
- [[concepts/telekom/vpn-es-ipsec]] — IP-az-IP-ben beágyazás, hasonló alagút-elv
