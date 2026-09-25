---
tags: [concept, logika/rezolucio-iteletlogika]
sources: [Rezolúció_I.pdf]
derivation: source
updated: 2026-09-08
---

# Horn klóz és Horn logika

A Horn klózok — legfeljebb egy nem negált literált tartalmazó klózok — kitüntetett szerepet játszanak a rezolúciós kalkulusban: bennük a különben nem teljes lineáris input- és egységrezolúciós stratégia is teljessé válik.

## Tartalom

### Definíciók

**Horn klóz:** egy klózt Horn klóznak nevezünk, ha legfeljebb egy literálja nem negált.

**Horn logika:** az összes, csak Horn klózokat tartalmazó KNF alakú formulák halmaza.

**Példa:** $S = \{B \vee \neg C,\ A \vee \neg C,\ \neg A \vee \neg B,\ \neg A \vee C,\ C\}$ Horn klózok halmaza.

### Teljességi tétel

**Tétel:** a lineáris input- és az egységrezolúciós stratégia teljes a Horn logikában — noha [[concepts/logika/rezolucios-kalkulus|általános klózhalmazokon]] egyik sem az.

**Példa** (mindkét stratégia levezeti az üres klózt ugyanabból az $S$-ből):

Lineáris input rezolúció: $1.\ B\vee\neg C\ [\in S]$; $2.\ \neg A\vee\neg B\ [\in S]$; $3.\ \neg A\vee\neg C\ [\mathrm{rez}(1,2)]$; $4.\ A\vee\neg C\ [\in S]$; $5.\ \neg C\ [\mathrm{rez}(3,4)]$; $6.\ C\ [\in S]$; $7.\ \square\ [\mathrm{rez}(5,6)]$.

Egységrezolúció: $1.\ B\vee\neg C\ [\in S]$; $2.\ C\ [\in S]$; $3.\ B\ [\mathrm{rez}(1,2)]$; $4.\ \neg A\vee\neg B\ [\in S]$; $5.\ \neg A\ [\mathrm{rez}(3,4)]$; $6.\ A\vee\neg C\ [\in S]$; $7.\ \neg C\ [\mathrm{rez}(5,6)]$; $8.\ \square\ [\mathrm{rez}(2,7)]$.

### Egységklózok szerepe

**Tétel:** ha az üres klóz levezethető lineáris input rezolúcióval egy $K$ klózhalmazból, akkor $K$-ban van legalább egy egységklóz.

*Bizonyítás vázlata:* az üres klózt mint rezolvenst egy centrális egységklózból és egy klózhalmazbeli klózból kapjuk; ez utóbbi ekkor csak egységklóz lehet.

**Tétel:** kielégíthetetlen Horn klózhalmazban van legalább egy egységklóz.

### Teljes levezetési fa

A **teljes levezetési fa** egy adott klózzal kezdődő összes lineáris levezetést megadja. Például $S = \{X\vee Z,\ \neg X\vee Z,\ \neg Y\vee\neg Z,\ \neg X\vee Y,\ \neg Z\}$ esetén a teljes levezetési fa minden ága egy-egy lehetséges lineáris levezetést ír le $X \vee Z$-ből kiindulva, több ágon eljutva az üres klózig.

### Kapcsolódás a bonyolultsághoz (HORNSAT)

Az itt tárgyalt tételek a Horn logika **levezetéselméleti** tulajdonságairól szólnak (a lineáris input- és egységrezolúció teljessége). A Horn-formulák kielégíthetőségének **bonyolultságelméleti** vizsgálatát — hogy a HORNSAT probléma polinom időben eldönthető, tehát P-beli — lásd [[concepts/bvszam/hornsat]].

## Kapocs

- [[concepts/logika/rezolucios-kalkulus]] — a lineáris input- és egységrezolúciós stratégia általános (nem csak Horn-beli) tulajdonságai
- [[concepts/logika/kloz-es-klozhalmaz]] — klóz, klózhalmaz, üres klóz fogalma
- [[concepts/bvszam/hornsat]] — a HORNSAT probléma P-beli eldönthetősége, mohó egységpropagációval
