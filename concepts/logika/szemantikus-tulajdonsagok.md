---
tags: [concept]
sources: [Elsőrendű_logika_szemantika.pdf, Elsőrendű_logika_alapjai.pdf, Szabo-Ivan-Elsorendu-logika-egyetemi-jegyzet.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
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

Church és Turing (1936) bebizonyította — a diasor ezt tévesen Gödelnek tulajdonítja —, hogy **a szemantikus eldöntésprobléma algoritmikusan nem oldható meg** — nincs univerzális eldöntési algoritmus sem a kielégíthetetlenségre, sem a logikai igazságra. Ez motiválja két további irányt: eldönthető formulaosztályok keresését, illetve — a jelentősebb út — a logika **szintaktikai** felépítését és arra kalkulusok (tabló, rezolúció) kidolgozását, amelyek a szemantikai kiértékelést megkerülik. Az interpretációk szisztematikus, véges eszközökkel való bejárására ad módszert az [[concepts/logika/elsorendu-szemantikus-fa]].

### Gyakorló értéktáblák

Az értéktábla felépítése: szabad változók (változókiértékelés) | prímkomponensek | formula, egyetlen interpretációban. A prímkomponensek a legkisebb részek, amelyekhez „helyes” igazságérték rendelhető: atomi vagy kvantált formulák (pl. $\forall x(P(x)\wedge Q(x,y))\supset\forall yQ(z,y)\supset P(\bar a)\vee Q(w)$ prímkomponensei: $\forall x(P(x)\wedge Q(x,y))$, $\forall yQ(z,y)$, $P(\bar a)$, $Q(w)$). Véges univerzumon $\forall$ konjunkció, $\exists$ diszjunkció: $U=\{0,1,2\}$, $|P|=\{0,2\}$ esetén $|\forall xP(x)|=i\wedge h\wedge i=h$, $|\exists xP(x)|=i\vee h\vee i=i$.

**1. feladat.** $\forall x\exists yP(x,y)\wedge Q(\bar a)\vee P(\bar a,z)$; $U=\{0,1\}$, $P(x,y)$: $x<y$, $Q(x)$: $x=0$, $\bar a=0$. Az egyetlen szabad változó $z$, két sor. $\forall x\exists yP(x,y)$ hamis (az $x=1$-hez nincs nagyobb $y$), $Q(\bar a)$ igaz, $P(\bar a,z)$: $z=0$-ra $h$, $z=1$-re $i$. Eredmény ($1\wedge2\vee3$): $z=0$: $h$; $z=1$: $i$. Leolvasható: kielégíthető (ebben az interpretációban van igaz sor), nem kielégíthetetlen, nem logikai törvény.

**2. feladat.** $\exists z\exists y(P(z,y)\wedge Q(f(\bar a)))\supset\forall vP(v,\bar a)\wedge P(f(x),\bar b)$; $U=\{1,2,3\}$, $P$: $x=y$, $Q$: páros, $\bar a=1$, $\bar b=3$, $f$: rákövetkező (a $3$ rákövetkezője az $1$). Szabad változó: $x$ (3 sor). $\exists z\exists y(\dots)$ igaz ($f(\bar a)=2$ páros, $z=y$ választható); $\forall vP(v,\bar a)$ hamis ($v=2$-re $h$); így a hátsó konjunkció minden sorban hamis, a teljes formula (igaz $\supset$ hamis) **mindhárom sorban hamis**. Következmény: ebben az interpretációban sehol sem igaz; kielégíthetetlen is lehet, de egy másik interpretációban lehet igaz sor; nem logikai törvény.

**3. feladat.** $\exists w\forall yP(f(w,y),\bar a)\supset Q(z)\supset P(z,x)\vee P(v,\bar a)$ (az implikáció jobbra köt); $U=\{0,1\}$, $P$: $\geq$, $Q(x)$: $x\geq0$, $\bar a=0$, $f$: összeadás. Szabad változók: $z,x,v$ (8 sor). Mivel $P(v,\bar a)$ ($v\geq0$) mindig igaz, a diszjunkció, így a teljes formula **minden sorban igaz** (a $P(z,x)$ a $z=0,x=1$ sorokban hamis, de ez nem számít). Kielégíthető, nem kielégíthetetlen; hogy logikai törvény-e, az a többi interpretációtól függ.

### Tautológia és logikai törvény – ellenőrző példák

Minden tautológia logikai törvény, de fordítva nem. Tautológiát a prímkomponensekre (mint ítéletváltozókra) felírt igazságtáblából olvasunk le:

- $\forall xP(x)\wedge\forall xR(x)\supset\forall xP(x)$ — $A\wedge B\supset A$: tautológia, tehát logikai törvény.
- $\forall x(P(x)\wedge R(x))\supset\forall xP(x)$ — $A\supset B$: nem tautológia (a második sor $h$), mégis logikai törvény.

A diasor végén négy gyakorlófeladat áll (megoldás nincs mellette; a fenti módszerrel):

1. $P(x,y)\vee\neg Q(x)\supset\exists xQ(x)\vee(\exists xQ(x)\supset P(x,y)\vee\neg Q(x))$ — tautológia: $D=P(x,y)\vee\neg Q(x)$, $C=\exists xQ(x)$ mellett $D\supset(C\vee(C\supset D))$, ami $D$ igaz volta esetén a belső implikáció miatt, hamis $D$ esetén pedig az előtag miatt igaz.
2. $P(x,y)\supset\neg Q(x)\wedge Q(x)\supset P(x,y)$ — jobbra kötés: $P\supset((\neg Q\wedge Q)\supset P)$; a belső előtag mindig hamis, tehát tautológia.
3. $(\exists yP(a,y)\supset\neg\forall xQ(x))\vee\exists zP(a,z)$ — **nem tautológia** (a két egzisztenciális formula különböző prímkomponens, $A$ és $C$; a $(A\supset\neg B)\vee C$ hamis, ha $A=i$, $B=i$, $C=h$), viszont **logikai törvény**, mert $\exists yP(a,y)$ és $\exists zP(a,z)$ egyenértékű.
4. $(\exists yP(a,y)\supset\neg\forall xQ(x))\vee\exists yP(a,y)$ — ugyanaz a prímkomponens kétszer: $(A\supset\neg B)\vee A$ tautológia.

(A diasorban a feladatok megoldása nem szerepel; a fenti megoldások a bemutatott módszer alkalmazásai.)

### Szemantikus következmény modellhalmazokkal

Szabó Iván jegyzete a következményt modellhalmazokkal írja: $\Sigma\models\Gamma$ azt jelenti, hogy $\mathrm{Mod}(\Sigma)\subseteq\mathrm{Mod}(\Gamma)$ (ami modellje $\Sigma$-nak, az modellje $\Gamma$-nak is). $\Sigma\models\perp$ pontosan akkor, ha $\Sigma$ kielégíthetetlen, mert $\mathrm{Mod}(\perp)=\emptyset$, és $\emptyset$ részhalmaza csak az üres halmaz lehet.

## Kapocs

- [[concepts/logika/term-szemantika]] — a formula szemantikájának alapja: a benne szereplő termek értéke
- [[concepts/logika/valtozokiertekeles]] — a kvantorok szemantikájában használt $\kappa$-variánsok
- [[concepts/logika/elsorendu-interpretacio]] — a lehetséges interpretációk száma, ami a szemantikai eldöntést kezelhetetlenné teszi
- [[concepts/logika/elsorendu-szemantikus-fa]] — az interpretációk szisztematikus, fás előállítása
- [[concepts/logika/iteletlogikai-formula]] — az ítéletlogikai tautológia-fogalom, amelyhez a fenti definíció mérhető
- [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg]] — a szemantikus eldönthetetlenség tömör összefoglalása
- [[concepts/logika/elsorendu-formalizalas]] — a gyakorló formulák forrása: mondatok formalizálása
- [[concepts/logika/helyettesitesi-algoritmus]] — a helyettesítési lemma: a kvantor-kiértékelés szintaktikus megfelelője
