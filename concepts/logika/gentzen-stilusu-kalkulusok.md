---
tags: [concept]
sources: ["Természetes levezetés.pdf"]
derivation: source
updated: 2026-09-08
---

# Gentzen stílusú kalkulusok

A szintaktikus eldöntésprobléma megoldására szolgáló kalkuluscsalád gyűjtőneve: olyan szabályrendszerek, amelyek egy szekvencia (feltételhalmaz és konklúzió) megalapozhatóságát egyszerűbb szekvenciák megalapozhatóságára vezetik vissza.

## Tartalom

### A szintaktikus eldöntésprobléma

A bizonyításelmélet **általános eldöntésproblémája** ítéletlogikában és elsőrendű logikában: létezik-e $\{F_1, F_2, \dots\}$-ből $G$-nek tetszőleges (nem feltétlenül véges) [[concepts/logika/bizonyitaselmeleti-levezetes]]e. A **gyönge eldöntésprobléma** szűkebb kérdés: bizonyítható-e ($\vdash_0$-val, üres feltételhalmazból) egy tetszőleges $Q$ ítéletlogikai vagy elsőrendű formula.

Bizonyításelméleti levezetés konstrukciójára nincs algoritmus — ellentétben a szemantikus eldöntésproblémával (igazságtábla), amely véges eljárás. Ez indokolja, hogy több, egymástól eltérő szerkezetű **kalkulust** dolgoztak ki a szintaktikus eldöntésprobléma kezelésére.

### Előre- és visszakövetkeztetés

**Előrekövetkeztetés**: a levezetést a premisszáktól (axiómák, feltételek) a konklúzió felé építjük — ez az általános eldöntésprobléma megoldási iránya, ahogy a [[concepts/logika/bizonyitaselmeleti-levezetes]]-ben definiált formulasorozat is épül: axiómából vagy premisszából, modus ponensszel, lépésről lépésre a célformula felé.

**Visszakövetkeztetés**: a bizonyítandó (gyönge eldöntésproblémabeli) formulából kiindulva vezetjük vissza a kérdést egyre egyszerűbb szerkezetű részkérdésekre, amíg egy megállási feltételig (pl. az azonosság törvényéig) el nem jutunk. A Gentzen stílusú kalkulusok jellemzően ezt az irányt (is) támogatják: egy szabály a vonal alatti (összetettebb) szekvencia megalapozhatóságát a vonal feletti (egyszerűbb) szekvenciák megalapozhatóságára vezeti vissza.

### A család tagjai

Két Gentzen stílusú kalkulust tárgyal a jegyzet:

- **Természetes technika** — lásd [[concepts/logika/termeszetes-levezetes]].
- **Gentzen szekvent módszer** — a szekvenskalkulus, amely a szekvencia mindkét oldalán (a feltételhalmaz és a konklúzió oldalán is) megenged több formulát.

Mindkettő ugyanarra a szintaktikus eldöntésproblémára ad választ, más-más szabályrendszerrel; közös vonásuk, hogy a szabályaik strukturális felépítése garantálja a helyességet (lásd [[concepts/logika/termeszetes-levezetes]] a természetes technika helyesség- és teljességfogalmáról).

### Kapcsolat a logikai programozással

A **logikai programozás** alapja lehet bármely helyes, de nem feltétlenül teljes szintaktikus tételbizonyító eljárás: a probléma feltételeit és a várt következményt a logika nyelvén adjuk meg, majd egy Gentzen stílusú (vagy más) kalkulussal dolgozzuk fel — a kérdés ugyanaz, mint a szintaktikus eldöntésprobléma: levezethető-e a következmény a feltételekből.

## Kapocs

- [[concepts/logika/termeszetes-levezetes]] — a család egyik konkrét tagja, a jegyzetben részletesen tárgyalt kalkulus
- [[concepts/logika/bizonyitaselmeleti-levezetes]] — a levezetés és a szintaktikus következmény ($\vdash_0$) fogalma, amelyre az eldöntésprobléma épül
- [[concepts/logika/dedukcios-tetel]] — a dedukciós tétel, amelyet a természetes technika szabályainak bizonyítása felhasznál
- [[concepts/logika/axiomasemak-iteletkalkulus]] — az ítéletkalkulus axiómasémái, amelyekre az előrekövetkeztetéses levezetés épül
- [[concepts/bvszam/itelet-kalkulus]] — az ítéletkalkulus rokon, tömörebb tárgyalása
