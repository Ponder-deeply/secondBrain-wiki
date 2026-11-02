---
tags: [concept]
sources: [Laki_Lecture_6.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# Bridge-ek és switch-ek: címtanulás és továbbítás

A bridge (híd) több IEEE 802 LAN-t kapcsol össze a **2. rétegben**; az Ethernet switch az eredeti bridge továbbfejlesztett, speciális esete. Három funkciója van: **keretek továbbítása**, **MAC-címek tanulása** és a hurkok kezelése a **feszítőfa algoritmussal**. A switch-ekkel a LAN-ok jól skálázhatók — de az egész Internetet nem lehet így összekötni.

## Tartalom

### Honnan indulunk?

Az Ethernet eredetileg adatszóró technológia volt (koax kábel T-csatlakozókkal, lezárókkal, repeaterrel; majd hubok). Előnye: egyszerű, olcsó és „buta” hardver. Hátránya: **nem skálázható** — több állomás = több ütközés = káosz.

### LAN-ok összekapcsolása bridge-dzsel

- A bridge-ek **lekorlátozzák az ütközési tartományok méretét**: minden porton külön ütközési tartomány van, ezzel jelentősen nő a skálázhatóság.
- Hátrány: a bridge sokkal komplexebb eszköz, mint a hub. A hub fizikai rétegbeli, a bridge adatkapcsolati; memóriapufferek, csomagfeldolgozó hardver és továbbító táblák kellenek.

**Célok:** az ütközési tartományok csökkentése és **teljes átlátszóság** — plug-and-play, önmagát konfiguráló; nem kell hardver- vagy szoftverváltoztatás a hosztokon és hubokon; nem lehet hatással a meglévő LAN-műveletekre.

### Keret-továbbító tábla

Minden bridge karbantart egy **továbbító táblát** (*forwarding table*), soronként: MAC-cím, port, kor. Példa:

| MAC-cím | Port | Kor |
|---|---|---|
| 00:00:00:00:00:AA | 1 | 1 perc |
| 00:00:00:00:00:BB | 2 | 7 perc |
| 00:00:00:00:00:CC | 3 | 2 mp |
| 00:00:00:00:00:DD | 1 | 3 perc |

Továbbításkor a bridge a keret **cél** MAC-címét keresi a táblában: ha megtalálja, csak arra a portra küldi; ha nem, **elárasztja** (*flooding*) — minden más portra kiküldi.

### Címek tanulása

Kézi beállítás is lehetséges, de időigényes, hibaforrás, és nem alkalmazkodik a változásokhoz (új hosztok belépnek, régiek távoznak). Ehelyett a bridge **megtanulja a címeket**: a különböző portokon beérkező keretek **forrás**címét feljegyzi a beérkezési porttal együtt — ebből épül a tábla. A régi bejegyzéseket (kor alapján) törli, így a mozgó hosztokat is követi.

Példa: AA a port 1-en, BB (hubon át) a port 2-n küld keretet → a tábla `AA → 1`, `BB → 2` bejegyzéseket kap, 0 perces korral.

### A hurkok problémája

Ha két bridge redundánsan köt össze két LAN-t, egy ismeretlen célú keret (pl. `Src=AA, Dest=DD`) elárasztással körbe-körbe jár, **a végtelenségig**, és a bridge-ek táblái is folyton átíródnak. Megoldás: a hurkokat logikailag el kell távolítani a topológiából, a kábelek kihúzása nélkül — ezt végzi az IEEE 802.1 feszítőfa algoritmusa ([[concepts/telekom/feszitofa-protokoll]]).

### Bridge vs. switch

A bridge-ek növelik a LAN-ok kapacitását (kevesebb elküldendő csomag kell a sikeres átvitelhez) és kezelik a hurkokat. A **switch a bridge speciális esete**:
- minden port **egyetlen hoszthoz** kapcsolódik (kliens terminál vagy másik switch);
- **full-duplex** linkek;
- egyszerűsített hardver: **nincs szükség CSMA/CD-re** (nincs ütközés);
- különböző sebességű portok is lehetségesek.

### Miért nem lehet az egész Internet egy switch-tartomány?

A switch-ek tudnak MAC-cím alapú útválasztást, automatikusan megtanulják az új állomásokhoz vezető utakat, és feloldják a hurkokat. Mégis **nem**, mert:
- **nem hatékony** — ismeretlen állomások megtalálásához elárasztás kell;
- **gyenge teljesítmény** — a feszítőfa nem foglalkozik terheléselosztással, *hot spot*-ok alakulnak ki;
- **nagyon gyenge skálázhatóság** — minden switch-nek az Internet összes MAC-címét ismernie kellene a továbbító táblájában (a MAC-címek laposak, nem aggregálhatók).

Ezt a problémát a hálózati réteg, az **IP** oldja meg hierarchikus címzéssel ([[concepts/telekom/ipv4-cimzes-es-cidr]]).

**Vizsgaszempont:** a címtanulás és a továbbítás (ismert cél / ismeretlen cél → elárasztás) algoritmusa; hub vs. bridge vs. switch; miért nem skálázódik a 2. réteg.

## Kapocs

- [[concepts/telekom/feszitofa-protokoll]] — hurokmentesítés 802.1 szerint
- [[concepts/telekom/ethernet]] — a LAN, amelyet a switch-ek összekötnek
- [[concepts/telekom/csma-cd]] — amire a switch-elt hálózatban már nincs szükség
- [[concepts/telekom/routing-alapok]] — a 3. rétegbeli megoldás
