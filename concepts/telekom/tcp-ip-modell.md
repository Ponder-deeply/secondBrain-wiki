---
tags: [concept]
sources: [Laki_Lecture_1.pdf, Laki_Lecture_2.pdf]
derivation: source
kind: comparison
element: air
updated: 2026-09-25
---

# TCP/IP modell és a hibrid modell

A TCP/IP modell (RFC 1122) az Internet négyrétegű modellje: 1982 márciusában az amerikai katonai hálózatok standardja lett, 1985-től kereskedelmi célra is népszerűsítették (*Interop*). A tankönyvek (Tanenbaum, Stallings, Kurose, Forouzan) ennek ötrétegű, **hibrid** változatát használják — a tárgy is ezt követi.

## Tartalom

### A négy réteg alulról felfelé

1. **Kapcsolati réteg** (*host-to-network* / *link layer*) — nem specifikált, a helyi hálózattól (LAN) függ. Példák: ARPANET, SATNET, Ethernet, LAN.
2. **Internet réteg** (*internet* / *network layer*) — speciális csomagformátum, útvonal-meghatározás (*routing*) és csomagtovábbítás (*packet forwarding*). Protokollja: **IP**.
3. **Szállítói réteg** (*transport layer*):
   - **TCP** (*Transmission Control Protocol*): megbízható, kétirányú bájtfolyam-átviteli szolgáltatás; szegmentálás, folyamfelügyelet, multiplexálás. Részletesen: [[concepts/telekom/tcp]].
   - **UDP** (*User Datagram Protocol*): nem megbízható átviteli szolgáltatás, nincs folyamfelügyelet. Részletesen: [[concepts/telekom/udp]].
4. **Alkalmazási réteg** (*application layer*) — szolgáltatások: Telnet, FTP, SMTP, HTTP, NNTP, DNS, SSH stb.

A modell jobb oldala szerint a felső három réteg **protokollokat**, a legalsó **hálózatokat** jelent.

### A három modell összevetése

| OSI (7) | Hibrid (5) — a tárgyban ezt használjuk | TCP/IP (4) |
|---|---|---|
| Alkalmazási, Megjelenítési, Ülés | Alkalmazási | Alkalmazási |
| Szállítói | Szállítói | Szállítói |
| Hálózati | Hálózati | Hálózati (Internet) |
| Adatkapcsolati | Adatkapcsolati | Kapcsolati (*Link*) |
| Fizikai | Fizikai | ↑ (a Link részeként) |

Vagyis a hibrid modell az OSI felső három rétegét összevonja (mint a TCP/IP), az alsó kettőt viszont külön kezeli (mint az OSI). Ennek oka didaktikai: a fizikai réteg (jelek, kódolás) és az adatkapcsolati réteg (keretezés, hibajavítás, közeghozzáférés) egészen más problémákat old meg.

### A félév tananyaga a hibrid modell mentén

1. Referenciamodellek
2. Fizikai réteg
3. Adatkapcsolati réteg — (a) LLC alréteg, (b) MAC alréteg
4. Hálózati réteg
5. Socket programozási alapok
6. Szállítói réteg
7. Alkalmazási réteg
8. Kitekintés — SDN, OpenFlow, P4, 5G

**Vizsgaszempont:** a TCP és UDP jellemzése (megbízható bájtfolyam vs. nem megbízható datagram) és a rétegek egymásnak való megfeleltetése a három modell között tipikus tesztkérdés.

## Kapocs

- [[concepts/telekom/osi-referenciamodell]] — a hétrétegű modell rétegenkénti leírása
- [[concepts/telekom/retegzett-halozati-architektura]] — beburkolás, homokóra-modell
- [[concepts/telekom/internet-tortenete-es-tervezesi-elvei]] — a TCP/IP történeti háttere
