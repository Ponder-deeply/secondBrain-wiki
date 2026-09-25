---
tags: [concept, logika/elsorendu-logika-szemantika]
sources: [Elsőrendű_logika_szemantika.pdf]
derivation: source
updated: 2026-09-08
---

# Elsőrendű szemantikus tulajdonságok

Egy elsőrendű formula (vagy formulahalmaz) szemantikus tulajdonságai — kielégíthetőség, logikai igazság (tautológia), kielégíthetetlenség és szemantikus következmény — mind a formula $I,\kappa$ melletti helyettesítési értékére épülnek; ezek szemantikai úton való eldöntése azért reménytelen, mert az összes lehetséges interpretáló struktúrára szükség volna.

## Tartalom

### A formula helyettesítési értéke

A term szemantikájára ([[concepts/logika/term-szemantika]]) épülve, egy $A$ formula $I,\kappa$ melletti $|A|^{I,\kappa}$ helyettesítési értéke szerkezeti rekurzióval:

- **Atomi formula.** $|P(t_1,\dots,t_n)|^{I,\kappa} = i$, ha $\big(|t_1|^{I,\kappa},\dots,|t_n|^{I,\kappa}\big) \in P^I$, ahol $P^I$ a $P$ predikátum igazhalmaza az interpretációban.
- **Kvantált formula.** $|\exists x A|^{I,\kappa} = i$, ha $|A|^{I,\kappa^*} = i$ legalább egy $\kappa^*$ $x$ szerinti variánsára ([[concepts/logika/valtozokiertekeles]]). $|\forall x A|^{I,\kappa} = i$, ha $|A|^{I,\kappa^*} = i$ $\kappa$ **minden** $x$ szerinti $\kappa^*$ variánsára.
- Az összetett (logikai összekötőjelekkel épített) formulák értéke az ítéletlogikából ismert módon, a prímkomponensek értékéből adódik.

**Kielégítés.** Az $L$ egy $I$ interpretációja a $\kappa$ változókiértékelés mellett **kielégíti** az $A$ formulát ($I,\kappa \models A$), ha $|A|^{I,\kappa} = i$. Ha $A$ mondat (zárt formula, nincs szabad változója) és $I \models A$, akkor az $I$ által megadott $S$ struktúra **modellje** $A$-nak: $S \models A$. Egy $F = \{F_1,\dots,F_n\}$ zárt formulahalmazt egy $I$ **kielégít** ($I \models F$), ha minden $F_k$-ra $|F_k|^I = i$.

### Az értéktábla

Egy elsőrendű formula **prímformulái** az atomi formulák (paraméteres állítások az interpretációban) és a kvantált formulák (állítások, ha zártak); **prímkomponensei** azok a prímformulák, amelyekből a formula a logikai összekötőjelekkel felépül. Az elsőrendű formula **értéktáblájában** az első sorba a szabad individuumváltozók, a prímkomponensek, majd a formula kerül; a változók alá a lehetséges kiértékeléseket, a prímformulák alá a megfelelő helyettesítési értékeket, a formula alá a belőlük számított értéket írjuk. (Az ítéletlogikai igazságtáblától éppen abban különbözik, hogy a prímformulák — mivel paraméteres állítások — csak a változók kiértékelése *után* válnak konkrét igazságértékű állításokká.)

### Kielégíthetőség

Egy $G$ formula **kielégíthető**, ha $L$-hez van legalább egy $I$ interpretáció és $\kappa$ változókiértékelés, amelyre $I,\kappa \models G$. Egy zárt $F$ formulahalmaz **kielégíthető**, ha $L$-nek van legalább egy $I$ interpretációja, amelyre $I \models F$.

### Logikai igazság és tautológia

Egy $G$ formula **logikailag igaz** (logikai törvény), jelölés $\models G$, ha $G$ igaz minden lehetséges $I$ interpretációra és minden $\kappa$ változókiértékelésre — vagyis minden lehetséges interpretáló struktúrában.

Egy $G$ formula **tautológia**, ha az értéktáblájában a prímkomponensekhez rendelhető *összes* lehetséges igazságérték-hozzárendelés esetén a formula helyettesítési értéke $i$. A tautológia szigorúan szűkebb fogalom, mint a logikai igazság: minden tautológia logikailag igaz, de nem minden logikailag igaz formula tautológia.

**Példa.** $\forall x P(x) \land \forall x Q(x) \supset \forall x P(x)$ prímkomponens-alakja $p \land q \supset p$, ami tautológia. Ezzel szemben $\forall x(P(x) \land Q(x)) \supset \forall x P(x)$ prímkomponens-alakja $r \supset p$, ami *nem* tautológia — pedig mindkét formula logikailag igaz. Tétel: ha $\models_0 G$ (azaz $G$ ítéletlogikai értelemben tautológia), akkor $\models G$; a fordítottja nem áll.

### Kielégíthetetlenség

Egy $G$ formula (illetve $F$ formulahalmaz) **kielégíthetetlen**, ha $L$-hez nincs olyan $I$ interpretáció, hogy $I \models G$ (illetve $I \models F$). Más szóval: $G$ kielégíthetetlen, ha minden interpretációban, az értéktábla minden sorában $G$ helyettesítési értéke $h$; $F$ kielégíthetetlen, ha a közös értéktábla minden sorában van $F$-nek legalább egy $h$ értékű eleme.

### Szemantikus következmény

A $G$ formula **logikai (szemantikus) következménye** az $F$ formulahalmaznak ($F \models G$), ha minden olyan $I$ interpretációra, amelyre $I \models F$, $I \models G$ is fennáll — azaz az $F, G$ közös értéktáblájának minden olyan sorában, ahol $F$ minden eleme igaz, $G$ is igaz.

Kapcsolódó tételek:

- $F \models G$ pontosan akkor, ha $F \cup \{\lnot G\}$ kielégíthetetlen.
- Ha $G$ bármely $F$ feltételhalmaznak következménye, akkor $G$ logikailag igaz.
- Dedukciós tétel: $\{F_1,\dots,F_n\} \models G \iff \{F_1,\dots,F_{n-1}\} \models F_n \supset G$; ismételt alkalmazásával $\{F_1,\dots,F_n\}\models G \iff\ \models F_1 \supset (F_2 \supset(\dots \supset(F_n\supset G)\dots))$.
- $G$ a **legszűkebb következménye** $F$-nek, ha minden interpretáló struktúrában a közös értéktáblának pontosan azokban a soraiban igaz, ahol $F_1,\dots,F_n$ mindegyike igaz.
- Az $A$ és $B$ formulák **logikailag ekvivalensek**, ha $\{A\}\models B$ és $\{B\}\models A$.

### Miért reménytelen a szemantikai eldöntés

Mind a kielégíthetőség/kielégíthetetlenség, mind a logikai igazság/tautológia, mind a szemantikus következmény vizsgálata elméletileg megoldható lenne az *összes* interpretáló struktúrában felvett közös értéktábla alapján. Csakhogy egy adott $U$ univerzum felett, $M = |U|$ mellett, az $(r_1,\dots,r_n; s_1,\dots,s_k)$ szignatúrájú lehetséges struktúrák száma
$$\Big(\prod_{j=1}^n 2^{M^{r_j}}\Big)\cdot \prod_{t=1}^k M^{M^{s_t}}$$
(lásd [[concepts/logika/elsorendu-interpretacio]]); már az alsó becslés — csak a relációk száma — is kontinuum számosságú, ha $U$ megszámlálhatóan végtelen. Ez algoritmikusan kezelhetetlen: a teljes kipróbálás nem járható út.

Gödel bebizonyította, hogy **a szemantikus eldöntésprobléma algoritmikusan nem oldható meg** — nincs univerzális eldöntési algoritmus sem a kielégíthetetlenségre, sem a logikai igazságra. Ez motiválja két további irányt: eldönthető formulaosztályok keresését, illetve — a jelentősebb út — a logika **szintaktikai** felépítését és arra kalkulusok (tabló, rezolúció) kidolgozását, amelyek a szemantikai kiértékelést megkerülik. Az interpretációk szisztematikus, véges eszközökkel való bejárására ad módszert az [[concepts/logika/elsorendu-szemantikus-fa]].

## Kapocs

- [[concepts/logika/term-szemantika]] — a formula szemantikájának alapja: a benne szereplő termek értéke
- [[concepts/logika/valtozokiertekeles]] — a kvantorok szemantikájában használt $\kappa$-variánsok
- [[concepts/logika/elsorendu-interpretacio]] — a lehetséges interpretációk száma, ami a szemantikai eldöntést kezelhetetlenné teszi
- [[concepts/logika/elsorendu-szemantikus-fa]] — az interpretációk szisztematikus, fás előállítása
- [[concepts/logika/iteletlogikai-formula]] — az ítéletlogikai tautológia-fogalom, amelyhez a fenti definíció mérhető
- [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg]] — a szemantikus eldönthetetlenség tömör összefoglalása
