---
tags: [concept, logika/tablokalkulus]
sources: [Tablókalkulus.pdf]
derivation: source
updated: 2026-09-08
---

# Jelölt formula és a formulák $\alpha$/$\beta$ típusa

A tablókalkulus a formulákat **jelölt** alakban ($TA$, $FA$) kezeli, és minden formulát a logikai összekötőjele szerint $\alpha$- vagy $\beta$-típusúnak minősít; ez a két osztályozás adja meg a **közvetlen tablók** — a kalkulus egyetlen levezetési lépésének — szabályait.

## Tartalom

### Jelölt formula

Vezessük be a nyelvbe a $T$, $F$ szimbólumokat. **Jelölt formulának** nevezzük a $TA$, $FA$ kifejezéseket, ahol $A$ jelöletlen [[concepts/logika/iteletlogikai-formula|ítéletlogikai formula]]. Olvasatuk: $TA$ — „$A$ igaz”, $FA$ — „$A$ hamis”. Egy interpretációban $TA$ igaz, ha $A$ igaz, és hamis, ha $A$ hamis; $FA$ pedig igaz, ha $A$ hamis, és hamis, ha $A$ igaz.

A jelölt alak mellett a kalkulusnak van egy **jelöletlen** változata is, amely közvetlenül a jelöletlen formulákkal, azok igazzá válásának feltételeivel dolgozik — ez a két megközelítés csak jelölésben tér el, tartalmilag ekvivalens (lásd [[concepts/logika/analitikus-tablo]]).

### $\alpha$- és $\beta$-típusú formulák

A kétváltozós logikai műveletek igazságtáblája alapján a $A \wedge B$, $\neg(A \vee B)$, $\neg(A \supset B)$ alakú formulák (illetve jelölt megfelelőik: $TA \wedge B$, $FA \vee B$, $FA \supset B$) egyetlen sorban veszik fel az igaz értéket — igazzá válásuk a két argumentumra **együttesen** megadott feltételtől függ. Ezeket **$\alpha$-típusúnak** (lényegében konjukciós jellegűnek) nevezzük.

Ezzel szemben a $\neg(A \wedge B)$, $A \vee B$, $A \supset B$ alakú formulák (jelölve: $FA \wedge B$, $TA \vee B$, $TA \supset B$) három sorban vesznek fel igaz értéket — igazzá válásuk a két argumentumra **egymástól függetlenül** megadott két feltételtől függ. Ezeket **$\beta$-típusúnak** (lényegében diszjunkciós jellegűnek) nevezzük.

Formálisan: minden $\alpha$-típusú formula átalakítható $\alpha_1 \wedge \alpha_2$ alakúvá, minden $\beta$-típusú $\beta_1 \vee \beta_2$ alakúvá. Az $\alpha_1, \alpha_2$-t az $\alpha$; a $\beta_1, \beta_2$-t a $\beta$ **közvetlen részformáinak** nevezzük — ez nem mindig esik egybe a formula eredeti alakja szerinti közvetlen részformulával. Például $\neg(A \vee B)$ közvetlen részformulája (a [[concepts/logika/formulaszerkezet|szerkezeti]] értelemben) $A \vee B$, de mint $\alpha$-típusú formulának a két közvetlen részformulája $\neg A$ és $\neg B$.

A táblázat az egyes formulaalakokhoz tartozó $\alpha_1, \alpha_2$, illetve $\beta_1, \beta_2$ argumentumokat adja meg:

| $\alpha$ | $\alpha_1$ | $\alpha_2$ | $\beta$ | $\beta_1$ | $\beta_2$ |
|---|---|---|---|---|---|
| $A \wedge B$ | $A$ | $B$ | $\neg(A \wedge B)$ | $\neg A$ | $\neg B$ |
| $\neg(A \vee B)$ | $\neg A$ | $\neg B$ | $A \vee B$ | $A$ | $B$ |
| $\neg(A \supset B)$ | $A$ | $\neg B$ | $A \supset B$ | $\neg A$ | $B$ |

Tehát ha $\alpha_1$ is és $\alpha_2$ is igaz, akkor $\alpha$ igaz — azaz $\{\alpha_1, \alpha_2\} \models_0 \alpha$. Ha $\beta_1$ vagy $\beta_2$ igaz, akkor $\beta$ igaz — azaz $\{\beta_1\} \models_0 \beta$, illetve $\{\beta_2\} \models_0 \beta$.

### Közvetlen tabló

A fenti igazzá válási feltételeket megvalósító szabályokat, amelyek egy formulához (formulatípushoz) hozzárendelik a levezetésben megjelenő új formulát vagy formulapárt, a formula **közvetlen tablójának** nevezzük. Jelöletlen alakban:

- $A \wedge B$ közvetlen tablója: $A$, majd alá $B$ (egy ágon, egymás után).
- $\neg\neg A$ közvetlen tablója: $A$.
- $\neg(A \wedge B)$ közvetlen tablója: elágazás, $\neg A$ a bal, $\neg B$ a jobb ágon.
- $\neg(A \vee B)$ közvetlen tablója: $\neg A$, majd alá $\neg B$.
- $A \vee B$ közvetlen tablója: elágazás, $A$ a bal, $B$ a jobb ágon.
- $\neg(A \supset B)$ közvetlen tablója: $A$, majd alá $\neg B$.
- $A \supset B$ közvetlen tablója: elágazás, $\neg A$ a bal, $B$ a jobb ágon.

Jelölt alakban ugyanez, kiegészítve a negáció szabályával:

| Formula | Közvetlen tabló |
|---|---|
| $T\neg A$ | $FA$ |
| $F\neg A$ | $TA$ |
| $TA \wedge B$ | $TA$, alá $TB$ |
| $FA \wedge B$ | elágazás: $FA$ \| $FB$ |
| $FA \vee B$ | $FA$, alá $FB$ |
| $TA \vee B$ | elágazás: $TA$ \| $TB$ |
| $FA \supset B$ | $TA$, alá $FB$ |
| $TA \supset B$ | elágazás: $FA$ \| $TB$ |

A jelöletlen szabályok a feldolgozott formula igazzá válásának feltételeit adják; a jelölt szabályok a jelöltnek megfelelő igazságértéket biztosító feltételeket. A közvetlen tabló az egyetlen atomi lépés, amelyből az [[concepts/logika/analitikus-tablo|analitikus tabló]] egésze felépül.

## Kapocs

- [[concepts/logika/iteletlogikai-formula]] — a jelöletlen formulák, amelyekre a jelölés épül
- [[concepts/logika/formulaszerkezet]] — a közvetlen részformula szokásos (szerkezeti) fogalma, amelytől az $\alpha$/$\beta$ felbontás eltérhet
- [[concepts/logika/igazsagtabla]] — az $\alpha$/$\beta$ osztályozás alapja: melyik oszlopban hány sorban igaz a művelet
- [[concepts/logika/analitikus-tablo]] — a közvetlen tablóból felépülő teljes kalkulus
