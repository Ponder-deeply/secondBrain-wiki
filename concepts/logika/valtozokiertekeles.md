---
tags: [concept, logika/elsorendu-logika-szemantika]
sources: [Elsőrendű_logika_szemantika.pdf]
derivation: source
updated: 2026-09-08
---

# Változókiértékelés

A változókiértékelés egy $\kappa : V \to U$ leképezés, amely a nyelv individuumváltozóihoz az interpretáció univerzumának elemeit rendeli; az interpretáció mellett ez a szemantika második, elmaradhatatlan komponense.

## Tartalom

### Definíció

Legyen $V$ a nyelv individuumváltozóinak halmaza, $U$ pedig egy $I$ interpretáció univerzuma. Egy **változókiértékelés** egy $\kappa : V \to U$ leképezés. A $\kappa$ egy $x$ változóhoz rendelt értékét $\kappa(x)$-szel jelöljük; ez az $U$-beli elem lesz az $x$ term $I,\kappa$ melletti helyettesítési értéke, $|x|^{I,\kappa}$.

Az interpretáció önmagában nem elég a nyelv kifejezéseinek kiértékeléséhez: egy $I$ megadja, mihez rendelődnek a nyelv logikán kívüli szimbólumai (predikátumok, függvények, konstansok — lásd [[concepts/logika/elsorendu-interpretacio]]), de a **szabad individuumváltozók** értékét nem rögzíti. Erre szolgál $\kappa$: egy formula vagy term helyettesítési értéke csak az $\langle I, \kappa\rangle$ pár együttes megadásával határozható meg.

### Variáns

Legyen $x$ egy változó. A $\kappa^*$ változókiértékelés a $\kappa$ **$x$ szerinti variánsa**, ha minden $x$-től különböző $y$ változóra $\kappa^*(y) = \kappa(y)$ — azaz $\kappa^*$ legfeljebb $x$ értékében térhet el $\kappa$-tól. Ezt a jelölésben $\kappa[x \mapsto u]$-val is írjuk, ahol $u \in U$ az $x$-hez rendelt új érték.

A variáns fogalma a kvantorok szemantikájának alapja: egy $\exists x A$, illetve $\forall x A$ formula helyettesítési értékét éppen $\kappa$ $x$ szerinti variánsain keresztül definiáljuk — lásd [[concepts/logika/szemantikus-tulajdonsagok]] és a term/formula szemantika egzisztenciális, illetve univerzális esete [[concepts/logika/term-szemantika]] oldalon.

**Példa.** Ha $U = \{a, b, c\}$ és $\kappa$ a $y$ változóhoz rendre az $a$, $b$, $c$ értékeket veszi fel, akkor a $\forall x P(x, y)$ formula $|{\cdot}|^{I,\kappa}$ helyettesítési értéke minden egyes $\kappa$-variánsra külön kiszámítandó — ez adja a formula **értéktábláját** (lásd [[concepts/logika/szemantikus-tulajdonsagok]]).

## Kapocs

- [[concepts/logika/elsorendu-interpretacio]] — az interpretáció, amely mellé $\kappa$ társul
- [[concepts/logika/term-szemantika]] — ahol $\kappa$ először szerepet kap: $|x|^{I,\kappa} = \kappa(x)$
- [[concepts/logika/szemantikus-tulajdonsagok]] — a kvantorok szemantikája $\kappa$-variánsokkal
- [[concepts/logika/elsorendu-szemantikus-fa]] — az interpretációk (és implicit a kiértékelések) szisztematikus előállítása
