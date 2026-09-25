---
tags: [concept, logika/iteletlogika-szemantika]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Következtetésforma

A következtetésforma egy premisszahalmazból és egy konklúzióból álló pár; akkor helyes, ha a premisszák együttes teljesülése minden esetben maga után vonja a konklúzió igazságát.

## Tartalom

### Definíció

**Gondolkodásforma (következtetésforma):** egy $\mathcal{F} = \{A_1, A_2, \dots, A_n\}$ állításhalmazból és egy $A$ állításból álló $(\mathcal{F}, A)$ pár. Az $\mathcal{F}$ elemei a **premisszák**, az $A$ a **konklúzió**.

**Helyes következtetésforma:** az $(\mathcal{F}, A)$ pár akkor helyes, ha létezik olyan eset, amelyben az $\mathcal{F}$ állításhalmaz minden állítása igaz, és **minden ilyen esetben** az $A$ állítás is igaz.

A definíció két külön feltételt köt ki. Az első (a premisszák együtt kielégíthetők) zárja ki azt a degenerált esetet, amikor a premisszahalmaz maga ellentmondásos, és így üresen bármit „maga után vonna”. A második a tényleges következményfeltétel.

Az „eset” fogalmát az ítéletlogikában az [[concepts/logika/iteletlogikai-interpretacio]] teszi pontossá: egy eset egy interpretáció, a premisszák igaz volta pedig a formula helyettesítési értéke az adott interpretációban.

### Példa: az áruházi betörés

A tantárgy visszatérő példája egy nyomozási jegyzőkönyv, amelynek premisszái:

1. Ha férfi a tettes, akkor kistermetű.
2. Ha kistermetű, akkor az ablakon mászott be.
3. A tettes férfi, vagy legalábbis férfiruhát hordott.
4. Ha férfiruhát hordott, és a szemtanú vallomása hiteles, akkor az ablakon mászott be.
5. Senki sem mászott be az ablakon.

A nyomozók sejtése — a konklúzió — az, hogy a tettes nem férfi. A kérdés, hogy ez a következtetésforma helyes-e, természetes nyelven nehezen dönthető el; ezért formalizáljuk az állításokat az [[concepts/logika/iteletlogikai-formula]] szintaxisa szerint, és a helyességet szemantikai eszközökkel — [[concepts/logika/igazsagtabla]] vagy szemantikus következményfogalom — vizsgáljuk.

### Miért kell hozzá formális nyelv

A következtetésforma helyessége nem a premisszák tartalmán, hanem a **formáján** múlik. Ezért a logika előbb egy leíró nyelvet épít fel — ábécé, szintaxis, szemantika hármasából ([[concepts/logika/iteletlogika-abece]], [[concepts/logika/iteletlogikai-formula]]) —, és csak ezután definiálja a következményfogalmat ezen a nyelven.

Az ítéletlogika azokat az állításokat kezeli, amelyek egyetlen egyedről mondanak valamit („A 2 egy páros szám”); a csoportokról szóló állítások („Minden nyúl rágcsáló”) az elsőrendű logika tárgyai.

## Kapocs

- [[concepts/logika/iteletlogikai-formula]] — a nyelv, amelyben a premisszákat és a konklúziót felírjuk
- [[concepts/logika/iteletlogikai-interpretacio]] — az „eset” pontos fogalma
- [[concepts/logika/igazsagtabla]] — a helyesség kimerítő ellenőrzésének eszköze
- [[concepts/bvszam/itelet-kalkulus]] — ugyanez a következményfogalom tömörebb, $F \models \varphi$ jelöléssel
