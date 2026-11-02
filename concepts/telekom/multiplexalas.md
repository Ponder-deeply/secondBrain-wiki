---
tags: [concept]
sources: [Laki_Lecture_2.pdf, Laki_Lecture_3.pdf, Laki_Lecture_5.pdf]
derivation: source
kind: comparison
element: air
updated: 2026-09-25
---

# Multiplexálás (statikus csatornahozzáférés)

A multiplexálás lehetővé teszi, hogy több jel egy időben utazzon egy fizikai közegen: a csatornát logikailag elkülönített alcsatornákra bontjuk, és a küldő oldalon egy **multiplexer** helyezi a jeleket a megfelelő alcsatornára. A felosztás **statikus** — előre rögzített, ellentétben a MAC-protokollok dinamikus hozzáférésével.

## Tartalom

### Az öt módszer

**Térbeli multiplexálás — SDM** (*Space-Division Multiplexing*). A legegyszerűbb: vezetékesen minden csatornának külön pont-pont vezeték, vezeték nélkül külön antenna (irány, cella) jut. Példa: cellás mobilhálózatok.

**Frekvenciamultiplexálás — FDM** (*Frequency-Division Multiplexing*). Minden szignálhoz más frekvenciasáv tartozik, a csatornán ezek kombinációja halad. Tipikusan analóg vonalon használják. A szomszédos csatornák közé **védősávot** (*guard band*) hagynak, hogy ne lapolódjanak át (pl. 3 telefonvonal: 300–3100 Hz-es sávok 60–72 kHz közé tolva). Szórt spektrumú változatai:
- **DSSS** (*Direct Sequence Spread Spectrum*) — XOR a szignálon egy véletlen bitsorozattal;
- **FHSS** (*Frequency Hopping Spread Spectrum*) — a frekvenciát pszeudovéletlen számsorozat szerint váltogatják.

**Hullámhossz-multiplexálás — WDM** (*Wavelength-Division Multiplexing*). Az FDM optikai megfelelője: több szál jele eltérő hullámhosszon ($\lambda_1,\dots,\lambda_4$) egy *combiner*-rel egyetlen hosszú szálra kerül, a túloldalon egy *splitter* és hullámhossz-szűrők választják szét.

**Időbeli multiplexálás — TDM** (*Time-Division Multiplexing*). A párhuzamos adatfolyamokat rövid időintervallumokra szegmentálja: minden állomás saját diszkrét **időszeletet** (*slot*) kap, és a szeletek körbe-körbe váltják egymást (`A B C A B C …`). Koordináció vagy merev felosztás kell hozzá; mobil bázisállomásoknál is használják.

**Kódosztásos multiplexálás — CDM / CDMA** (*Code Division Multiple Access*). Minden állomás egyszerre, a teljes sávon ad; a jeleket ortogonális kódok választják szét. Mobilkommunikációban használatos, részletesen: [[concepts/telekom/cdma]].

### Összefoglaló táblázat

| Módszer | Mit oszt fel? | Tipikus alkalmazás |
|---|---|---|
| SDM | teret (vezeték, antenna) | cellás hálózatok |
| FDM | frekvenciatartományt | analóg vonal, kábel-TV, rádió |
| WDM | hullámhosszt (optikai FDM) | optikai gerinchálózat |
| TDM | időt (slotok) | mobil bázisállomás időszeletei |
| CDM | kódteret | 3G mobil (IS-95) |

### Mikor rossz a statikus felosztás?

Ha $N$ állomás kap fix sávot vagy slotot, akkor egy éppen hallgató állomás kapacitása kárba vész, egy aktív pedig csak $1/N$ részt használhat akkor is, ha egyedül forgalmaz. Löketszerű (*bursty*) számítógépes forgalomnál ez pazarló — ezért az adatkapcsolati réteg dinamikus közeghozzáférési protokollokat használ ([[concepts/telekom/kozeghozzaferes-alapjai]]).

**Vizsgaszempont:** a rövidítések (SDM, FDM, WDM, TDM, CDM, DSSS, FHSS) feloldása és egymondatos jellemzése tipikus tesztkérdés.

## Kapocs

- [[concepts/telekom/cdma]] — a kódosztásos hozzáférés algoritmusa és példája
- [[concepts/telekom/modulacio]] — különböző vivők egyidejű használata
- [[concepts/telekom/atviteli-kozegek]] — kábel-TV frekvenciakiosztás mint FDM
- [[concepts/telekom/kozeghozzaferes-alapjai]] — a dinamikus alternatíva
