---
tags: [concept]
sources: ["09.kovetkeztetes.pdf"]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Visszafelé haladó szabályalapú következtetés

A célból indul, hátrafelé láncolással részcélokra bontja, amíg tényliterálokat nem kap; a válasz a hiperút változó-helyettesítéseiből olvasható ki.

## Tartalom

### Reprezentáció

ÉVF kifejezések: literálok, valamint $A\wedge B$, $A\vee B$ alakú formulák, ahol $A$, $B$ is ÉVF kifejezés.

- **Tény**: $L_1\wedge\dots\wedge L_n$ alakú, univerzálisan kötött kifejezés, ahol $L_i$ literálok.
- **Szabályok**: $W\to L$ alakú, univerzálisan kötött kifejezések, ahol $L$ literál, $W$ ÉVF kifejezés.
- **Cél**: egzisztenciálisan kötött, tetszőleges ÉVF kifejezés.

Az alak célja, hogy a hátrafelé láncolásnál literált literállal kelljen összevetni.

### Példa 1

Tény: $A\wedge C\wedge\neg D$. Szabályok: $A\vee\neg B\to U$, $A\wedge\neg D\to V$. Cél: $U\wedge(V\vee\neg W)$.

- a célnál mindkét részt igazolni kell: $U$ és $V\vee\neg W$;
- $U$: szabály-illesztéssel $A\vee\neg B$, elég az $A$, ami tényliterálra illeszkedik;
- $V\vee\neg W$: elég az egyik rész; $V$ szabállyal $A\wedge\neg D$-re vezet, mindkettő tényliterál.

A bizonyítást a célból tényliterálokba vezető hiperút szimbolizálja.

### Példa 2: kutya-macska pár

Tények: $K(Fifi)\wedge K(Gyilkos)\wedge Cs(Fifi)\wedge Ny(Cili)$ ($K$ kutya, $Cs$ csóvál, $Ny$ nyávog). Szabályok:

- $\forall x\,(Ny(x)\to M(x))$ (a nyávogó állatok macskák);
- $\forall x\,(K(x)\wedge Cs(x)\to B(x))$ (a farkát csóváló kutya barátságos);
- $\forall x\forall y\,(K(x)\wedge B(x)\wedge M(y)\to\neg F(y,x))$ (a macskák nem félnek a barátságos kutyáktól).

Cél: $\exists x\exists y\,(M(x)\wedge\neg F(x,y)\wedge K(y))$ — válaszadáshoz: van-e keresett kutya-macska pár.

A célt három részre bontjuk ($M(x)$, $\neg F(x,y)$, $K(y)$), a szabályok változóit átnevezve ($x_1,x_2,x_3$). $M(x)$ az $Ny(x)$-re, majd $\{x|Cili\}$ helyettesítéssel $Ny(Cili)$-re vezet; $\neg F(x,y)$ a harmadik szabállyal $K(y)\wedge B(y)\wedge M(x)$-re, ahol $B(y)$ tovább $K(y)\wedge Cs(y)$-re; $K(y)$ tényei $\{y|Fifi\}$ vagy $\{y|Gyilkos\}$. Csak az $y=Fifi$ ág ellentmondásmentes ($Cs(Fifi)$ miatt).

A bizonyítás az a hiperút, amely a célból tényliterálokba vezet, és ellentmondásmentes változó-helyettesítései vannak. A válasz a helyettesítésekből olvasható ki: $\{x|Cili,\ y|Fifi\}$.

## Kapocs

- [[concepts/mesint/szabalyalapu-kovetkeztetes]] — az általános keret és a keresőrendszer-nézet
- [[concepts/mesint/elore-halado-szabalyalapu-kovetkeztetes]] — az ellenkező irány
- [[concepts/mesint/visszafele-halado-keresesi-modell]] — a visszafelé haladó keresés modellje
- [[concepts/mesint/hiperut]] — a bizonyítást szimbolizáló hiperút
- [[concepts/mesint/valaszadas-rezolucioval]] — válaszadás rezolúcióval, összevetésül
