---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Elsőrendű logika

Az elsőrendű logika az ítéletkalkulus kiterjesztése: paraméteres állításokat (predikátumokat) és kvantorokat enged meg, így az állítások igazságértéke egy interpretáció struktúrájától függ.

## Tartalom

### Az elsőrendű nyelv szimbólumai

Egy $\mathcal{L}$ **elsőrendű nyelv** szimbólumhalmaza a következő részekből áll:

- **predikátumszimbólumok** $Pred$, **függvényszimbólumok** $Func$ és **konstansszimbólumok** $Const$ véges halmazai;
- az **egyedváltozók** $Ind = \{x_1, x_2, \ldots\}$ megszámlálhatóan végtelen halmaza;
- a **műveleti jelek** $\{\neg, \land, \lor, \to\}$ halmaza;
- az **univerzális kvantor** ($\forall$) és az **egzisztenciális kvantor** ($\exists$);
- a $($, $)$ és $,$ jelek.

Minden $s \in Const \cup Pred \cup Func$ szimbólumhoz tartozik egy nemnegatív egész **aritás** $ar(s)$; a konstansszimbólumok aritása mindig $0$.

### Termek és formulák

A **termek** $Term$ halmaza a legszűkebb halmaz, amelyre:

- $Ind \cup Const \subseteq Term$,
- ha $f \in Func$ és $t_1, \ldots, t_{ar(f)} \in Term$, akkor $f(t_1, \ldots, t_{ar(f)}) \in Term$.

Az **atomi formulák** $AForm$ halmaza: ha $p \in Pred$ és $t_1, \ldots, t_{ar(p)} \in Term$, akkor $p(t_1, \ldots, t_{ar(p)}) \in AForm$.

A **formulák** $Form$ halmaza a legszűkebb halmaz, amelyre:

- $AForm \subseteq Form$,
- ha $\varphi \in Form$, akkor $\neg\varphi \in Form$,
- ha $\varphi_1, \varphi_2 \in Form$, akkor $(\varphi_1 \circ \varphi_2) \in Form$ ($\circ \in \{\land, \lor, \to\}$),
- ha $x \in Ind$ és $\varphi \in Form$, akkor $\exists x\varphi \in Form$ és $\forall x\varphi \in Form$.

A $\psi$ a $\varphi$ **részformulája**, ha $\psi$ előfordul $\varphi$ rekurzív előállítása során.

### Interpretáció

Az $\mathcal{L}$ nyelv egy **interpretációja** egy $I = \langle U, I_{Pred}, I_{Func}, I_{Const} \rangle$ struktúra, ahol:

- $U$ tetszőleges nemüres halmaz (az **univerzum**);
- $I_{Pred}$ minden $p \in Pred$-hez egy $ar(p)$ változós $U$-feletti $p^I$ relációt rendel;
- $I_{Func}$ minden $f \in Func$-hoz egy $f^I : U^{ar(f)} \to U$ függvényt rendel;
- $I_{Const}$ minden $a \in Const$-hoz egy $a^I \in U$ elemet rendel.

### Változókiértékelés és érték

Egy $\kappa : Ind \to U$ függvény **változókiértékelés**. A $\kappa$ egy **$x$-variánsa** olyan $\kappa'$ változókiértékelés, amely legfeljebb $x$ értékében tér el $\kappa$-tól.

Egy $t \in Term$ értéke $I$ és $\kappa$ mellett $|t|^{I,\kappa}$:

- $|a|^{I,\kappa} = a^I$ konstansra, $|x|^{I,\kappa} = \kappa(x)$ egyedváltozóra,
- $|f(t_1, \ldots, t_n)|^{I,\kappa} = f^I(|t_1|^{I,\kappa}, \ldots, |t_n|^{I,\kappa})$.

Egy $\varphi \in Form$ értéke $|\varphi|^{I,\kappa}$ ($igaz$ vagy $hamis$):

- atomi $p(t_1, \ldots, t_n)$ esetén $igaz \iff (|t_1|^{I,\kappa}, \ldots, |t_n|^{I,\kappa}) \in p^I$,
- $\neg$ és a kétváltozós műveletek esetén az ítéletkalkulusban látott módon,
- $|\exists x\psi|^{I,\kappa} = igaz \iff$ van olyan $x$-variánsa $\kappa'$ a $\kappa$-nak, hogy $|\psi|^{I,\kappa'} = igaz$,
- $|\forall x\psi|^{I,\kappa} = igaz \iff$ minden $\kappa'$ $x$-variánsra $|\psi|^{I,\kappa'} = igaz$.

A kielégíthetőség, érvényesség és logikai következmény fogalma az ítéletkalkulusban látott módon definiálható.

### Kötött és szabad változó, zárt formula

Tekintsük $x \in Ind$ egy előfordulását $\varphi$-ben. Az előfordulás **kötött**, ha $\varphi$ egy $\exists x\psi$ vagy $\forall x\psi$ alakú részformulájában szerepel; egyébként **szabad**. Ha $\varphi$-ben minden egyedváltozó minden előfordulása kötött, akkor $\varphi$ **zárt formula** vagy **mondat**, egyébként **nyitott**.

Ha $\varphi$ zárt, akkor $|\varphi|^{I,\kappa}$ értéke független $\kappa$-tól, így helyette $|\varphi|^I$-t írunk.

## Kapocs

- [[concepts/bvszam/itelet-kalkulus]] — az elemi (paraméter nélküli) logika
- [[concepts/bvszam/halmaz-relacio-alapfogalmak]] — relációk, az interpretáció építőkövei
