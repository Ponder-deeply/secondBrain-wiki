---
tags: [concept]
sources: ["09.kovetkeztetes.pdf"]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Előre haladó szabályalapú következtetés

A tényekből indul, előrefelé láncolással jut a célliterálokig; a reprezentáció célja, hogy a hátrafelé láncolásnál literált literállal kelljen összevetni.

## Tartalom

### Reprezentáció

ÉS/VAGY formájú (ÉVF) kifejezések: literálok, valamint $A\wedge B$, $A\vee B$ alakú formulák, ahol $A$ és $B$ is ÉVF kifejezés.

- **Tény**: univerzálisan kötött, tetszőleges ÉVF kifejezés.
- **Szabályok**: $L\to W$ alakú, univerzálisan kötött kifejezések, ahol $L$ egy literál, $W$ pedig ÉVF kifejezés.
- **Cél**: $L_1\vee\dots\vee L_n$ alakú, egzisztenciálisan kötött kifejezés, ahol $L_1,\dots,L_n$ literálok.

### Működés

A tény ÉVF szerkezete ÉS/VAGY gráfot határoz meg: egy $\wedge$-csomópontnál elég az egyik részből levezetni a célt, egy $\vee$-csomópontnál mindkét részből le kell vezetni. A levezetés a tényből szabály-illesztésekkel halad, a levezetett literálokat célliterálokkal illesztjük.

**Példa.** Tény: $(A\vee\neg B)\wedge C$. Szabályok: $A\to D\wedge E$, $\neg B\to D\vee\neg H$. Cél: $D\vee G\vee\neg H$.

- $(A\vee\neg B)\wedge C$-ből elég az $A\vee\neg B$ rész;
- $A\vee\neg B$-ből mindkét ágból le kell vezetni a célt: $A$ és $\neg B$;
- $A$ a szabállyal $D\wedge E$-t ad, $D$ illeszkedik a $D$ célliterálra;
- $\neg B$ a szabállyal $D\vee\neg H$-t ad, $D$ és $\neg H$ is célliterálra illeszkedik.

A bizonyítást a tényből célliterálokba vezető hiperút szimbolizálja ([[concepts/mesint/hiperut]]).

## Kapocs

- [[concepts/mesint/szabalyalapu-kovetkeztetes]] — az általános keret, tények és szabályok
- [[concepts/mesint/visszafele-halado-szabalyalapu-kovetkeztetes]] — a tükörképe, a célból indul
- [[concepts/mesint/es-vagy-grafok]] — az ÉS/VAGY gráf és a hiperút
