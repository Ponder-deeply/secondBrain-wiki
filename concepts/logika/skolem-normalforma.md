---
tags: [concept]
sources: [Rezolúció_II.pdf]
derivation: source
updated: 2026-09-08
---

# Skolem normálforma

A Skolem normálforma (Skolem formula) olyan prenex formula, amelynek prefixumában — az egzisztenciális kvantoroknak megfelelő individuumváltozók függvényszimbólumokkal (Skolem-függvényekkel) való kiváltása után — kizárólag univerzális kvantorok szerepelnek; eldönthető formulaosztály, és kielégíthetőség szempontjából ekvivalens az eredeti formulával.

## Tartalom

### Fogalom

A Skolem formula a $\forall x_1, \forall x_2, \dots, \forall x_n A$ alakú [[concepts/logika/prenex-forma|prenex formula]], ahol a prefixumban csak univerzális kvantorok szerepelnek. Ez eldönthető formulaosztály (a rá vonatkozó kielégíthetőségi eldöntésprobléma algoritmikusan eldönthető).

### A Skolem alakra hozás algoritmusa

Tekintsük az első egzisztenciális kvantort a prenex formula prefixumában, legyen ez $\exists x_j$. Ha a formula igaz egy interpretációban, akkor az $x_1, x_2, \dots, x_{j-1}$ változók minden értékkombinációjához létezik legalább egy olyan érték az $x_j$ változónak, amelyre a formula igaz. Ezt a tényt egy új, $j-1$ argumentumú **Skolem-függvénnyel**, $f(x_1, x_2, \dots, x_{j-1}) = x_j$, fejezzük ki: ez a függvény minden $x_1,\dots,x_{j-1}$ változókiértékeléshez hozzárendeli $x_j$ egy megfelelő értékét, és $\exists x_j$ eltűnik a prefixumból. A lépést sorra végrehajtjuk minden egzisztenciális kvantorra, amíg egy sem marad.

Ha egy egzisztenciális kvantor előtt nem áll univerzális kvantor a prefixumban (nincs tőle balra $\forall$), a hozzá tartozó Skolem-függvény $0$ argumentumú — **Skolem-konstans**.

### Példák

**1. példa:** $\forall x \exists y P(x,y)$ Skolem alakja $\forall x P(x, f(x))$ — $f$ egyváltozós Skolem-függvény, mert az $y$-hoz tartozó egzisztenciális kvantor előtt egy univerzális kvantor ($\forall x$) áll.

**2. példa:** a $\exists x \exists y \forall y_1 \forall y_2(\lnot P(x,y) \vee Q(y_1) \vee P(x,a) \vee P(x,y_2) \wedge \lnot R(x,y_2))$ prenex formulában $x$ és $y$ egzisztenciális kvantorai előtt nincs univerzális kvantor, ezért a hozzájuk tartozó Skolem-függvények $0$ argumentumúak (Skolem-konstansok, pl. $q, r$). A Skolem alak:

$$\forall y_1 \forall y_2(\lnot P(q,r) \vee \lnot Q(y_1) \vee P(q,a) \vee P(q,y_2) \wedge \lnot R(q,y_2))$$

### Kielégíthetőség-tartás

A Skolemizáció nem ekvivalens átalakítás — az eredeti formula és Skolem alakja nem logikailag ekvivalensek —, csak **kielégíthetőség-tartó**: az eredeti formula pontosan akkor kielégíthető, ha Skolem alakja is az. Ez elegendő ahhoz, hogy a kielégíthetetlenség eldöntésének feladatában a formula helyett a Skolem alakjával dolgozzunk.

### Szerepe a klózhalmazzá alakításban

A Skolem normálforma a köztes lépés a tetszőleges elsőrendű formula [[concepts/logika/elsorendu-kloz|elsőrendű klózok]] konjunkciójává alakításában:

1. tetszőleges formula átírható [[concepts/logika/prenex-forma|prenex alakba]];
2. tetszőleges prenex formula átírható Skolem alakba;
3. tetszőleges Skolem normálforma felírható elsőrendű klózok konjunkciójaként.

## Kapocs

- [[concepts/logika/prenex-forma]] — az előző lépés, amelyből a Skolem alak előáll
- [[concepts/logika/elsorendu-kloz]] — a Skolem normálforma magjából felírt klózok konjunkciója
- [[concepts/logika/herbrand-univerzum]] — a Skolem-függvények és -konstansok szerepe a Herbrand univerzum felépítésében
- [[concepts/logika/term]] — a Skolem-függvény alkalmazásával kapott kifejezések termek
