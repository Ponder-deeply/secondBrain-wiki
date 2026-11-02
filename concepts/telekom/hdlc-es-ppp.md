---
tags: [concept]
sources: [Laki_Lecture_4.pdf]
derivation: source
kind: comparison
element: air
updated: 2026-09-25
---

# HDLC és PPP — adatkapcsolati protokollok a gyakorlatban

A HDLC bitorientált, bitbeszúrást és 3 bites csúszóablakot használó protokollcsalád; a PPP bájt alapú, pont-pont kapcsolatra (pl. betárcsázós internet) készült utóda. Mindkettő a `01111110` jelzőbájttal határolja a kereteit és CRC-vel védi őket; a tárgyalt elméleti eszközök (keretezés, CRC, csúszóablak) itt állnak össze egy valódi protokollá.

## Tartalom

### HDLC — High-level Data Link Control

**Történet:** először az IBM mainframe világában használták **SDLC** néven; ANSI változata az **ADCCP**, ISO változata a **HDLC**; később a CCITT a **LAP** és **LAPB** protokolljához adoptálta. Közös elvek: bitorientáltság (bitbeszúrás, [[concepts/telekom/keretezes]]), apróbb eltérésekkel.

**Keretfelépítés:**

| Jelző | Cím | Vezérlés | Adat | Ellenőrző összeg | Jelző |
|---|---|---|---|---|---|
| `01111110` (8 bit) | 8 bit | 8 bit | > 0 bit | 16 bit | `01111110` (8 bit) |

- **Cím**: több vonallal rendelkező termináloknál van jelentősége; pont-pont kapcsolatnál parancsok és válaszok megkülönböztetésére.
- **Vezérlés**: sorszámozás, nyugtázás és egyéb feladatok.
- **Adat**: tetszőleges hosszú.
- **Ellenőrző összeg**: CRC a **CRC-CCITT** generátorpolinommal ([[concepts/telekom/crc]]).

**Sorszámozás:** **3 bites csúszóablak** ([[concepts/telekom/csuszoablak-protokollok]]).

**Három kerettípus:**
1. **Információs** keret (adat).
2. **Felügyelő** keret:
   - 0. típus — nyugtakeret (`RECEIVE READY`);
   - 1. típus — negatív nyugta (`REJECT`);
   - 2. típus — vételre nem kész (`RECEIVE NOT READY`), amely a következőig minden keretet nyugtáz;
   - 3. típus — szelektív elutasítás (`SELECTIVE REJECT`), egy adott keret újraküldésére szólít fel.
3. **Számozatlan** keret (5 bites típusmező) — vezérlő parancsok:
   - `DISC` — a kapcsolat bontásának bejelentése;
   - `SNRM` — visszacsatlakozó állomás bejelenti jelenlétét (aszinkron);
   - `SABM` — alaphelyzetbe állítja a vonalat (egyenrangúság);
   - `SABME`, `SNRME` — kiterjesztett keretformátum (7 bites sorszám) engedélyezése;
   - `FRMR` — keretelutasítás illegális keretek jelzésére.

A `REJECT` a go-back-N, a `SELECTIVE REJECT` a szelektív ismétlés NAK-jának felel meg.

### PPP — Point-to-Point Protocol

RFC 1661, 1662, 1663. Három dolgot biztosít:

1. **Keretezési módszert** egyértelmű kerethatárokkal.
2. **Kapcsolatvezérlő protokollt (LCP)** a vonalak felélesztésére, tesztelésére, az opciók egyeztetésére és a vonalak elengedésére (szinkron/aszinkron áramkörök, bájt/bit alapú kódolás).
3. **NCP**-t: a hálózati rétegbeli opciók megbeszélését az alkalmazott hálózati protokolltól függetlenül — minden támogatott hálózati réteghez külön NCP.

Kapcsolatfelvétel PC és ISP között: (1) felhívás, fizikai kapcsolat; (2–3) LCP csomagok és válaszok — a PPP paraméterei egyeztetve; (4–5) NCP csomagok és válaszok — az internetkapcsolat kiépült.

**Keretszerkezet** (bájtokban):

| Jelző | Cím | Vezérlő | Protokoll | Adatmező | Ellenőrző összeg | Jelző |
|---|---|---|---|---|---|---|
| 1: `01111110` | 1: `11111111` | 1: `00000011` | 1 vagy 2 | változó | 2 vagy 4 | 1: `01111110` |

- **Bájt alapú** keretszerkezet (bájtbeszúrással), a legkisebb adategység a bájt.
- Alapértelmezésben **nem biztosít megbízható átvitelt**.
- A vezérlő mező alapértéke számozatlan keretet jelez.
- A protokoll mező kódja LCP, NCP, IP, IPX, AppleTalk stb.: a **0-val kezdődő** kódok hálózati protokollokat (IP, XNS), az **1-gyel kezdődők** egyeztetést igénylő protokollokat (LCP, NCP) jelölnek.

### Ethernet keret (előzetes)

Az IEEE 802.3 keret: preambulum (7 bájt), keretkezdő határoló (1), cél MAC (6), forrás MAC (6), opcionális 802.1Q tag (4), EtherType vagy hossz (2), payload (42/46–1500), FCS — 32 bites CRC (4), majd 12 bájt keretköz. Részletesen: [[concepts/telekom/ethernet]].

**Vizsgaszempont:** a HDLC kerettípusai és felügyelő kereteinek jelentése; a PPP három komponense (keretezés, LCP, NCP); a két protokoll összevetése (bit- vs. bájtorientált, megbízható vs. alapból nem).

## Kapocs

- [[concepts/telekom/keretezes]] — bit- és bájtbeszúrás
- [[concepts/telekom/crc]] — a keretek ellenőrző összege
- [[concepts/telekom/csuszoablak-protokollok]] — a HDLC sorszámozása
- [[concepts/telekom/ethernet]] — a LAN-ok keretformátuma
