---
tags: [concept]
sources: ["08.evolucio.pdf"]
derivation: source
kind: overview
element: water
updated: 2026-10-12
---

# Evolúciós algoritmus tervezése

Egy evolúciós algoritmus megtervezése öt döntési területből áll: kódolás, rátermettségi függvény, evolúciós operátorok, kezdő populáció és megállási feltétel, valamint stratégiai paraméterek.

## Tartalom

Az [[concepts/mesint/evolucios-algoritmus]] alapváza minden problémára azonos; a feladatspecifikus részeket a tervezés során kell megadni:

1. **Problématér egyedeinek reprezentációja: kódolás** — [[concepts/mesint/evolucios-kodolas]].
2. **Rátermettségi (fitnesz) függvény** — kapcsolatban kell állnia a kódolással és a céllal ([[concepts/mesint/ratermettseg-kiertekelese]]).
3. **Evolúciós operátorok** — [[concepts/mesint/szelekcio]], [[concepts/mesint/rekombinacio-es-keresztezes]], [[concepts/mesint/mutacio]], [[concepts/mesint/visszahelyezes]]; a kódolástól függ, hogy az operátor megőrzi-e a kód-invariánst.
4. **Kezdő populáció és megállási feltétel (cél).**
5. **Stratégiai paraméterek:** a populáció mérete, a mutáció valószínűsége, az utódképzési ráta, a visszahelyezési ráta stb.

### A példák tervezési döntései

| probléma | egyed | reprezentáció | rátermettség |
|---|---|---|---|
| n-királynő (1.) | minden oszlopban egy királynő | oszloponkénti sorpozíciók sorozata | ütésben nem lévő párok száma |
| n-királynő (2.) | minden sorban és oszlopban egy királynő | sorpozíciók permutációja | ütésben nem lévő párok száma |
| SAT | igazságkiértékelés | bitsorozat | igazra értékelt klózok száma |
| gráfszínezés | színezés | színvektor (direkt) vagy csúcssorrend (indirekt) | jó élek / kiszínezett csúcsok száma |
| kő-papír-olló | stratégia | $\{0,1,2\}^{81}$ sorozat | játszmamintán elért pontszám |

A SAT feladat: adott egy $n$ változós KNF-ű Boole-formula (lásd [[concepts/logika/kloz-es-klozhalmaz]]), milyen igazságkiértékelésnél igaz? Pl. $(x_1\vee\neg x_2\vee x_5)\wedge(x_1\vee\neg x_3)\wedge(\neg x_1\vee x_4)\wedge(\neg x_2\vee x_5)$, egy megoldás: $x_1=1, x_2=0, x_3=0, x_4=1, x_5=1$. Az EA-ban szelekcióként rulettkerék, keresztezésként egypontos bitcsere, mutációként bitek átbillentése szerepel; a mintaciklusban a populáció legjobbja 3-ról 4-re (azaz teljes megoldásra) javul.

## Kapocs

- [[concepts/mesint/evolucios-algoritmus]] — az alapalgoritmus, amelyet a tervezés paraméterez
- [[concepts/mesint/grafszinezes]] — a gráfszínezési feladat más keresőkkel
- [[concepts/mesint/n-kiralyno-problema]] — a vezérpélda
