---
tags: [concept]
sources: [Rezolúció_II.pdf, Szabo-Ivan-Elsorendu-logika-egyetemi-jegyzet.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Skolem normálforma

A Skolem normálforma (Skolem formula) olyan prenex formula, amelynek prefixumában — az egzisztenciális kvantoroknak megfelelő individuumváltozók függvényszimbólumokkal (Skolem-függvényekkel) való kiváltása után — kizárólag univerzális kvantorok szerepelnek; kielégíthetőség szempontjából ekvivalens az eredeti formulával.

## Tartalom

### Fogalom

A Skolem formula a $\forall x_1, \forall x_2, \dots, \forall x_n A$ alakú [[concepts/logika/prenex-forma|prenex formula]], ahol a prefixumban csak univerzális kvantorok szerepelnek. A diasor ezt eldönthető formulaosztálynak nevezi, ez azonban általában nem igaz: függvényszimbólumok jelenlétében a Skolem formulák kielégíthetősége algoritmikusan eldönthetetlen, csak a kielégíthetetlenség félig eldönthető ([[concepts/logika/herbrand-tetel|Herbrand-tétel]], rezolúció). Eldönthető viszont például a függvényszimbólumot nem tartalmazó $\exists^*\forall^*$ prefixumú formulák osztálya (Bernays–Schönfinkel), amelyek Skolem alakjában csak Skolem-konstansok jelennek meg.

### A Skolem alakra hozás algoritmusa

Tekintsük az első egzisztenciális kvantort a prenex formula prefixumában, legyen ez $\exists x_j$. Ha a formula igaz egy interpretációban, akkor az $x_1, x_2, \dots, x_{j-1}$ változók minden értékkombinációjához létezik legalább egy olyan érték az $x_j$ változónak, amelyre a formula igaz. Ezt a tényt egy új, $j-1$ argumentumú **Skolem-függvénnyel**, $f(x_1, x_2, \dots, x_{j-1}) = x_j$, fejezzük ki: ez a függvény minden $x_1,\dots,x_{j-1}$ változókiértékeléshez hozzárendeli $x_j$ egy megfelelő értékét, és $\exists x_j$ eltűnik a prefixumból. A lépést sorra végrehajtjuk minden egzisztenciális kvantorra, amíg egy sem marad.

Ha egy egzisztenciális kvantor előtt nem áll univerzális kvantor a prefixumban (nincs tőle balra $\forall$), a hozzá tartozó Skolem-függvény $0$ argumentumú — **Skolem-konstans**.

### Példák

**1. példa:** $\forall x \exists y P(x,y)$ Skolem alakja $\forall x P(x, f(x))$ — $f$ egyváltozós Skolem-függvény, mert az $y$-hoz tartozó egzisztenciális kvantor előtt egy univerzális kvantor ($\forall x$) áll.

**2. példa:** a $\exists x \exists y \forall y_1 \forall y_2(\lnot P(x,y) \vee \lnot Q(y_1) \vee P(x,a) \vee (P(y_2,x) \wedge \lnot R(x,y_2)))$ prenex formulában (a [[concepts/logika/prenex-forma|prenex forma]] példájának eredménye) $x$ és $y$ egzisztenciális kvantorai előtt nincs univerzális kvantor, ezért a hozzájuk tartozó Skolem-függvények $0$ argumentumúak (Skolem-konstansok, pl. $q, r$). A Skolem alak:

$$\forall y_1 \forall y_2(\lnot P(q,r) \vee \lnot Q(y_1) \vee P(q,a) \vee (P(y_2,q) \wedge \lnot R(q,y_2)))$$

### Kielégíthetőség-tartás

A Skolemizáció nem ekvivalens átalakítás — az eredeti formula és Skolem alakja nem logikailag ekvivalensek —, csak **kielégíthetőség-tartó**: az eredeti formula pontosan akkor kielégíthető, ha Skolem alakja is az. Ez elegendő ahhoz, hogy a kielégíthetetlenség eldöntésének feladatában a formula helyett a Skolem alakjával dolgozzunk.

### Szerepe a klózhalmazzá alakításban

A Skolem normálforma a köztes lépés a tetszőleges elsőrendű formula [[concepts/logika/elsorendu-kloz|elsőrendű klózok]] konjunkciójává alakításában:

1. tetszőleges formula átírható [[concepts/logika/prenex-forma|prenex alakba]];
2. tetszőleges prenex formula átírható Skolem alakba;
3. tetszőleges Skolem normálforma felírható elsőrendű klózok konjunkciójaként.

### Szabó Iván jegyzete szerint: s-ekvivalencia és zárttá tétel

- A Skolem alak a prenex alakból úgy áll elő, hogy a prefixum kvantorain végigmegyünk, és minden $\exists y$-ra töröljük a $\exists y$ részt, a magban pedig $y$ minden előfordulását $f(x_1,\dots,x_n)$-re cseréljük, ahol $x_1,\dots,x_n$ az $y$ előtt deklarált $\forall$-kötött változók, $f$ pedig *új*, sehol máshol nem szereplő Skolem-függvényjel (formulahalmaznál az egész halmazra nézve új).
- **Példa a prefixumra:** $\forall w\,\exists v\,\exists x\,\forall y\,\exists z$ esetén $v\mapsto g(w)$, $x\mapsto h(w)$ (új jel, $f,g$ már foglalt), $z\mapsto i(w,y)$; a Skolem prefixum $\forall w\,\forall y$.
- Az eredmény *nem ekvivalens* az eredetivel (új függvényjelek jelennek meg), hanem **s-ekvivalens** (satisfiability): az eredeti formula pontosan akkor kielégíthető, ha a Skolem alakja az. Ez formulahalmazra is érvényes, ha minden elemnél teljesen új függvényjeleket vezetünk be.
- Mivel $\Sigma\models F$ gyakran $\Sigma\cup\{\neg F\}$ kielégíthetetlenségével bizonyítható, az s-ekvivalencia elég. A bemenetet még **le is zárjuk**: minden szabad változóelőfordulást új konstansra cserélünk, hogy a formulák zártak legyenek.
- Sorrend: nyilak eltüntetése $\to$ kiigazítás ([[concepts/logika/valtozoiban-tiszta-alak]]) $\to$ prenex alak $\to$ Skolem alak.

## Kapocs

- [[concepts/logika/prenex-forma]] — az előző lépés, amelyből a Skolem alak előáll
- [[concepts/logika/elsorendu-kloz]] — a Skolem normálforma magjából felírt klózok konjunkciója
- [[concepts/logika/herbrand-univerzum]] — a Skolem-függvények és -konstansok szerepe a Herbrand univerzum felépítésében
- [[concepts/logika/term]] — a Skolem-függvény alkalmazásával kapott kifejezések termek
- [[concepts/logika/valtozoiban-tiszta-alak]] — a prenex alakra hozás előfeltétele (kiigazítás)
