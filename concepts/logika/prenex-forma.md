---
tags: [concept]
sources: [Rezolúció_II.pdf]
derivation: source
updated: 2026-09-08
---

# Prenex forma

A prenex forma olyan elsőrendű formula, amelyben az összes kvantor a formula elején, egyetlen kvantormentes törzs előtt áll; minden elsőrendű formula átírható vele ekvivalens prenex formává.

## Tartalom

### Fogalom

Legyen $Q$ tetszőleges kvantor. A $Q_1x_1 Q_2x_2 \dots Q_nx_n B$ alakú formula **prenex forma**, ahol

- $Q_1x_1 Q_2x_2 \dots Q_nx_n$ a **prefixum**,
- $B$ a formula **magja** (törzse), amely **kvantormentes** [[concepts/logika/elsorendu-formula|formula]].

Ha a prenex formula magja KNF-ben vagy DNF-ben van, a formula **normálforma**: prenex konjunktív, illetve prenex diszjunktív formula.

### Átalakítási szabályok

**Általános De Morgan szabályok:**

$$\lnot \forall x A \sim \exists x \lnot A \qquad \lnot \exists x A \sim \forall x \lnot A$$

**Kvantorkiemelési szabályok** — $A[x]$ jelöli, hogy $A$-ban $x$ szabadon fordulhat elő, $B$ pedig $x$-et nem tartalmazza:

1. $\forall x A[x] \wedge B \sim \forall x (A[x] \wedge B)$, ill. $\forall x A[x] \vee B \sim \forall x (A[x] \vee B)$
2. $\exists x A[x] \wedge B \sim \exists x (A[x] \wedge B)$, ill. $\exists x A[x] \vee B \sim \exists x (A[x] \vee B)$
3. $\forall x A[x] \wedge \forall x B[x] \sim \forall x (A[x] \wedge B[x])$ — de $\vee$-re **nem** igaz
4. $\exists x A[x] \vee \exists x B[x] \sim \exists x (A[x] \vee B[x])$ — de $\wedge$-re **nem** igaz
5. $Q_1 x A[x] \wedge Q_2 x B[x] \sim Q_1 x Q_2 z (A[x] \wedge B[x/z])$
6. $Q_1 x A[x] \vee Q_2 x B[x] \sim Q_1 x Q_2 z (A[x] \vee B[x/z])$

Az 5–6. szabály azonos nevű kvantorral kezdődő, de eltérő kötött változójú részformulák egyesítésekor kell: a második részformula kötött változóját át kell nevezni ($x/z$), különben a kiemelés nem érvényes ekvivalencia.

### A prenex formába való átírás algoritmusa

1. A logikai összekötőjelek átírása $\lnot, \wedge, \vee$ segítségével (a $\supset$ eltüntetése: $A \supset B \sim \lnot A \vee B$).
2. A De Morgan szabályok alkalmazása, amíg minden $\lnot$ hatásköre atomi formula nem lesz.
3. A kvantorkiemelési szabályok alkalmazása, amíg minden kvantor a formula elejére nem kerül, és a törzs kvantormentessé nem válik.

### Példa

A $\forall x(\forall y P(x,y) \wedge \exists y \lnot(Q(y) \supset P(x,a))) \supset \lnot \forall x \exists y (P(y,x) \supset R(x,y))$ formula átírása:

**1. lépés** (a $\supset$ eltüntetése):
$$\lnot(\forall x(\forall y P(x,y) \wedge \exists y \lnot(\lnot Q(y) \vee P(x,a)))) \vee \lnot \forall x \exists y(\lnot P(y,x) \vee R(x,y))$$

**2. lépés** (De Morgan szabályok, ismételve amíg a negáció atomi formulára szorul):
$$\exists x(\exists y \lnot P(x,y) \vee \forall y(\lnot Q(y) \vee P(x,a))) \vee \exists x \forall y (P(y,x) \wedge \lnot R(x,y))$$

**3. lépés** (kvantorkiemelés): a két diszjunkciós tag $\exists x$ kvantora azonos nevű, ezért az 5. szabály szerint az egyik ág kötött $y$ változóit át kell nevezni ($y \mapsto y_1$, illetve $y \mapsto y_2$), mielőtt kiemelhetők:

$$\exists x \exists y \forall y_1 \forall y_2\big(\lnot P(x,y) \vee (\lnot Q(y_1) \vee P(x,a)) \vee (P(y_2,x) \wedge \lnot R(x,y_2))\big)$$

Ez már prenex formula; a magja DNF alakú.

### Kapcsolat a klózhalmazzá alakítással

A prenex forma az első lépés a formula elsőrendű klózok konjunkciójává alakításához: a prenex formából [[concepts/logika/skolem-normalforma|Skolem normálforma]] állítható elő, amiből viszont [[concepts/logika/elsorendu-kloz|elsőrendű klózok]] konjunkciója írható fel.

## Kapocs

- [[concepts/logika/elsorendu-formula]] — a kvantormentesség és a kvantorok fogalma, amire a prenex forma épül
- [[concepts/logika/szabad-es-kotott-valtozo]] — a kvantorkiemelésnél szükséges változóátnevezés háttere
- [[concepts/logika/skolem-normalforma]] — a prenex formából Skolem-formulává alakítás következő lépése
- [[concepts/logika/elsorendu-kloz]] — a klózhalmazzá alakítás célformája
