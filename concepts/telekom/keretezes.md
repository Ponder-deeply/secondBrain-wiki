---
tags: [concept]
sources: [Laki_Lecture_3.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Keretezés (framing)

Az adatkapcsolati réteg a fizikai réteg bitfolyamát **keretekre** tördeli, hogy a vevő tudja, hol kezdődik és végződik egy adatblokk (csak így olvashatók a fejlécek), és hogy keretenként ellenőrző összeget számolhasson. Mivel megbízható időzítésre nem nagyon van lehetőség, a keret határait magában az adatfolyamban kell jelezni: karakterszámlálással, bájt- vagy bitbeszúrással, vagy fix keretmérettel (óra alapon).

## Tartalom

### Az adatkapcsolati réteg feladatai röviden

- Adatblokkok (**keretek**) küldése közös médiumra kötött eszközök között; a fizikai közeghez való hozzáférés szabályozása.
- Kihívások: hogyan **keretezzük** az adatot, hogyan ismerjük fel a **hibát** ([[concepts/telekom/hibakezeles-alapjai]]), hogyan vezéreljük a **közeghozzáférést** (MAC), hogyan kerüljük el vagy oldjuk fel az **ütközéseket** ([[concepts/telekom/kozeghozzaferes-alapjai]]).
- Szolgálati interfész a hálózati rétegnek. A diák három szolgálattípust sorolnak fel: nyugtázatlan (a diákon „összeköttetés alapú”; a Tanenbaum-féle felosztásban összeköttetés nélküli), nyugtázott összeköttetés nélküli, és nyugtázott összeköttetés alapú (3 fázis: felépítés, adatátvitel, bontás).
- Átviteli hibák kezelése; adatforgalom szabályozása (a vevő elárasztásának elkerülése — [[concepts/telekom/megall-es-var-protokoll]]).

A keretezés fajtái: **bájt alapú**, **bit alapú** és **óra alapú** protokollok.

### 1. Karakterszámlálás (bájt alapú)

A keret fejlécének egy mezője megadja a keretben lévő karakterek számát; a vevő ebből tudja, hol a keret vége.

Probléma: **nagyon érzékeny a hibára**. Ha a hossz-mező meghibásodik (pl. 5 helyett 7 érkezik), a vevő rossz helyen keresi a következő keret elejét, és onnantól minden keretet félreért — a szinkron nem áll helyre.

### 2. Bájtbeszúrás (byte stuffing)

Egy speciális **FLAG** (jelölő) bájt jelzi a keret elejét és végét (korábban két külön bájtot használtak az elejére és a végére).

- Ha a FLAG az adatban is előfordul, elé egy **ESC** (escape) bájtot szúrunk.
- Ha az ESC is szerepel az adatban, elé is egy újabb ESC-t szúrunk.
- Pontosan úgy, mint a C stringekben a `\"` és `\\`.

Példa: a keretezendő adat `H E L L O [SPACE] [ESC]`, a keretezett adat `[FLAG] H E L L O [SPACE] [ESC] [ESC] [FLAG]`.

Pont-pont protokollok használják: modem, DSL, cellás hálózat.

### 3. Bitbeszúrás (bit stuffing)

Minden keret ugyanazzal a speciális bitmintával kezdődik és végződik — HDLC (*High-level Data Link Control*) esetén `01111110`.

- **Küldő:** az adatban előforduló minden `11111` részsorozat után egy `0` bitet szúr be.
- **Fogadó**, ha `11111`-et lát:
  - `111110` → eltávolítja a 0-t (beszúrás eredménye volt);
  - `111111` → még egy bitet olvas: `1111110` → keret vége; `1111111` → hiba (a küldő ilyet nem állíthat elő), a keretet eldobja.

Példa: az átvitelre szánt `0110111111111111111110010` a beszúrás után `011011111`**0**`11111`**0**`11111`**0**`10010` — minden öt egymást követő egyes után egy 0 kerül be. A vevő a beszúrt biteket eltávolítva visszakapja az eredetit.

Hátránya: legrosszabb esetben (csupa egyes) **20% teljesítménycsökkenés** (5 bitenként 1 extra). Nyitott kérdés: mi történik, ha a záró bitminta sérül?

### 4. Óra alapú keretezés: SONET

*Synchronous Optical Network* — nagyon gyors optikai átvitel, STS-$n$ szintekkel (STS-1: 51,84 Mbps, STS-768: 36,7 Gbps).

- Az STS-1 keretek **rögzített méretűek**: $9 \times 90 = 810$ bájt (9 sor, 90 oszlop; az első oszlopok az *overhead*, a többi a *payload*).
- A keret elején speciális kezdőmintázat áll; 810 bájt fogadása után a vevő újabb kezdőmintát keres.
- A bitek NRZ kódolással mennek; a payloadot egy speciális (127 bites) mintával keverik meg (*scrambling*), hogy elkerüljék a hosszú 0- és 1-sorozatokat ([[concepts/telekom/digitalis-vonali-kodolasok]]).

**Vizsgaszempont:** bájt- és bitbeszúrás elvégzése konkrét adaton (és visszafejtése), a karakterszámlálás hibaérzékenységének magyarázata.

## Kapocs

- [[concepts/telekom/hibakezeles-alapjai]] — a keretenkénti ellenőrzőösszeg
- [[concepts/telekom/digitalis-vonali-kodolasok]] — a bitek szintjén a fizikai réteg dönt
- [[concepts/telekom/osi-referenciamodell]] — az adatkapcsolati réteg helye a modellben
