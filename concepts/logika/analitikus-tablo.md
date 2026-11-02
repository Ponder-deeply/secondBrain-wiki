---
tags: [concept]
sources: [Tablókalkulus.pdf, Tablokalkulus_1_2_rész.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Analitikus tabló (ítéletlogika)

Az analitikus tabló egy $C$ ítéletlogikai formula kielégíthetetlenségének igazolására szolgáló **szintaktikus kalkulus**: a formulát fokozatosan, a [[concepts/logika/jelolt-formula-es-formulatipusok|közvetlen tablók]] szabályai szerint bontja szét egy bináris fává, amíg minden ág lezár vagy tovább már nem bontható.

## Tartalom

### Motiváció

Egy $Q$ formuláról el kell dönteni, hogy kielégíthetetlen-e (a), vagy hogy tautológia-e (b). Mindkét kérdés visszavezethető ugyanarra a vizsgálatra: az (a) esetben magával $\varphi(Q)^{[i]}$-vel, a (b) esetben a tagadással, $\varphi(\neg Q)^{[i]}$-vel dolgozva keressük, hogy a kapott feltételek kielégíthetetlenek-e. (A kielégíthetőség és a tautológia fogalmára lásd [[concepts/logika/szemantikus-tulajdonsagok]].)

### Jelöletlen analitikus tabló

Egy $C$ ítéletlogikai formula **analitikus tablója** egy olyan bináris fa, amelynek csúcsai jelöletlen ítéletlogikai formulák. A fa gyökere a $C$ formula. Tegyük fel, hogy $C$-nek egy $T$ tablója adott, és legyen $D$ a $T$ egy levélcsúcsa. Ekkor a $T$ tabló **közvetlen kiterjesztése** a következők egyike lehet:

- **(A)** Ha van még nem „feldolgozott” $\alpha$-formula a gyökértől $D$-be vezető úton, akkor $D$-hez az út folytatásaként hozzákapcsoljuk az $\alpha$ formula közvetlen tablója szerint nyert $\alpha_1$, majd $\alpha_2$ formulákat mint új csúcsokat.
- **(B)** Ha van még nem feldolgozott $\beta$-formula a gyökértől $D$-be vezető úton, akkor $D$-ben a tabló elágazik: a bal oldali rákövetkező csúcsba $\beta$ közvetlen tablójából $\beta_1$, a jobb oldaliba $\beta_2$ kerül.

### Jelölt analitikus tabló

A jelölt változatban a csúcsok jelölt formulák, a gyökér a $C$ formula. A közvetlen kiterjesztés:

- **(A)** $TA \wedge B$, $FA \vee B$, $FA \supset B$ alakú, még nem feldolgozott formulára: a megfelelő közvetlen tablóból nyert jelölt formulákat az út folytatásaként fűzzük $D$-hez.
- **(B)** $FA \wedge B$, $TA \vee B$, $TA \supset B$ alakú formulára: a tabló elágazik $D$-ben, a közvetlen tabló két formulája a bal, illetve a jobb ágra kerül.
- **(C)** $T\neg A$, $F\neg A$ alakú formulára: a közvetlen tabló szerinti egyetlen jelölt formulát fűzzük az út folytatásaként $D$-hez.

### Zárt ág, zárt tabló, tablócáfolat

A tabló egy **ága zárt**, ha megjelenik rajta egy már nem tovább bontható (feldolgozhatatlan, azaz literál szintű) formula és annak negáltja is — jelölt alakban egy komplemens pár. Egy **tabló zárt**, ha minden ága zárt. A tablókalkulus megállási feltétele a tabló lezárása: ha a $C$ formula tablója zárt, akkor azt mondjuk, hogy $C$-nek van **tablócáfolata**.

**Példa.** A $(X \vee (Y \wedge Z)) \supset (X \vee Y) \wedge (X \vee Z)$ formula tagadásának tablója minden ágon lezár (két literál és annak negáltja jelenik meg), tehát a tagadás kielégíthetetlen, azaz az eredeti formula tautológia.

### Helyesség

**Tétel (helyesség).** Ha egy $C$ formulának van tablócáfolata (tablója zárt), akkor $C$ kielégíthetetlen.

*Bizonyítás.* Ha $C$ kielégíthető, akkor a közvetlen tablójában — $\alpha$-formula esetén mindkét, $\beta$-formula esetén legalább az egyik komponens — igaz marad az eredeti formulát kielégítő interpretációban. Ezért $C$ tablójának lesz legalább egy olyan ága, amelyen csupa kielégíthető formula szerepel (**igaz ág**: nincs rajta komplemens pár). Tegyük fel indirekt, hogy $C$ tablója zárt, de $C$ kielégíthető: ekkor kellene lennie legalább egy igaz ágnak — ellentmondás, hiszen egy zárt tablóban minden ág zárt. $\blacksquare$

### Teljesség

**Tétel (teljesség).** Ha $C$ kielégíthetetlen, akkor $C$ (bármely) befejezett (teljes) $T$ tablója zárt.

*Bizonyítás.* Tegyük fel indirekt, hogy $C$ kielégíthetetlen, de $T$-nek van nyitott ága. Mivel $T$ befejezett, egy ilyen ágon szereplő formulahalmaz **lefelé zárt**: ha rajta szerepel egy $\alpha$-formula, akkor $\alpha_1$ és $\alpha_2$ is szerepel rajta; ha egy $\beta$-formula, akkor $\beta_1$ és $\beta_2$ közül legalább az egyik. Egy ilyen szerkezetű, komplemens párt nem tartalmazó halmaz [[concepts/logika/hintikka-halmaz|Hintikka halmaz]], ami a Hintikka lemma szerint kielégíthető — tehát az ág minden formulája, így $C$ is, kielégíthető. Ez ellentmond a feltevésnek. $\blacksquare$

A helyesség és a teljesség együtt azt adja, hogy **a tablókalkulus a kielégíthetetlenség eldöntésének helyes és teljes szintaktikus módszere**: $C$ kielégíthetetlen pontosan akkor, ha van tablócáfolata. Mivel a kielégíthetőség/tautológia kérdése (lásd fent) mindig kielégíthetetlenségi kérdésre vezethető vissza, a tabló ezáltal mindkettőt eldönti — véges formula esetén véges lépésben.

### Formulahalmaz tablója

Egy véges $\{F_1, \dots, F_n\}$ formulahalmaz tablójának gyökerében az $F_1 F_2 \dots F_n$ sorozat áll, és a tablót a szokásos módon, formulánként építjük tovább. Végtelen formulahalmaz tablóját ugyanígy, a formulák egy rögzített sorrendje szerint állítjuk elő.

### Gyakorló feladatok (ítéletlogika)

A gyakorlati diasor (2020/21) négy feladata ugyanazt az eldöntési kérdést járja körül jelölt és jelöletlen tablóval. A bontási szabály: előbb az $\alpha$-formulák, utána a $\beta$-formulák; a lezárt ágat $\otimes$ jelöli.

**1. Helyes-e $\{(X\supset Y)\wedge(X\supset Z),\ X\} \models_0 Y\wedge Z$?** A dedukciós tétellel tautológia-kérdéssé alakítjuk: $((X\supset Y)\wedge(X\supset Z)) \supset (X\supset(Y\wedge Z))$ tautológia-e, azaz van-e tablócáfolata a formulának? Jelölt tabló: a gyökér $F\,(\dots)$; az $\alpha$-bontás után $T\,((X\supset Y)\wedge(X\supset Z))$ és $F\,(X\supset(Y\wedge Z))$, majd $T(X\supset Y)$, $T(X\supset Z)$, $TX$, $F(Y\wedge Z)$. A $T(X\supset Y)$ ágazik: $FX\ \otimes$ ($TX$-szel) | $TY$. A $TY$ ágon $F(Y\wedge Z)$ ágazik: $FY\ \otimes$ | $FZ$. Az $FZ$ ágon $T(X\supset Z)$ ágazik: $FX\ \otimes$ | $TZ\ \otimes$. Minden ág zárt, így a negált formula kielégíthetetlen, a formula tautológia, a következmény teljesül.

**2. Tautológia-e $(\neg X\vee\neg Y)\supset\neg(X\wedge Y)$?** Jelölt tabló: $F(\dots)$ $\to$ $T(\neg X\vee\neg Y)$, $F\neg(X\wedge Y)$ $\to$ $T(X\wedge Y)$ $\to$ $TX$, $TY$; a $T(\neg X\vee\neg Y)$ ágazik $T\neg X$ | $T\neg Y$ $\to$ $FX\ \otimes$ | $FY\ \otimes$. Zárt: tautológia.

**3. Ugyanez jelöletlen tablóval.** A gyökér a negált formula, $\neg((\neg X\vee\neg Y)\supset\neg(X\wedge Y))$; $\alpha$: $\neg X\vee\neg Y$ és $\neg\neg(X\wedge Y)$ $\to$ $X\wedge Y$ $\to$ $X$, $Y$; az ágazás $\neg X\ \otimes$ | $\neg Y\ \otimes$. Zárt tabló.

**4. Helyes-e $\{X\vee(Y\wedge Z)\} \models_0 (X\vee Y)\wedge(X\vee Z)$?** Visszakövetkeztetéssel: kielégíthetetlen-e $\{X\vee(Y\wedge Z),\ \neg((X\vee Y)\wedge(X\vee Z))\}$ (egyetlen konjunkcióként a gyökérben)? A $X\vee(Y\wedge Z)$ ágazik: $X$ | $Y\wedge Z$. Mindkét ágon a $\neg((X\vee Y)\wedge(X\vee Z))$ ágazik $\neg(X\vee Y)$ | $\neg(X\vee Z)$. A bal ágon $\neg(X\vee Y)\to\neg X,\neg Y$ ellentmond $X$-nek, a $\neg(X\vee Z)\to\neg X$ szintén. A jobb ágon $Y,Z$ áll, így $\neg(X\vee Y)\to\neg Y$ és $\neg(X\vee Z)\to\neg Z$ ellentmond. Minden ág zárt: a következmény teljesül.

A feladatok két bevett átfogalmazást mutatnak: **dedukciós tétel** (a következményből tautológia-kérdés, a gyökérben $F$-fel jelölt implikációlánc) és **visszakövetkeztetés** (a premisszák és a konklúzió negáltja együtt kielégíthetetlen-e).

## Kapocs

- [[concepts/logika/jelolt-formula-es-formulatipusok]] — a közvetlen tabló szabályai, amelyekből az analitikus tabló felépül
- [[concepts/logika/hintikka-halmaz]] — a teljesség bizonyításának kulcsfogalma: a nyitott ágon előálló formulahalmaz
- [[concepts/logika/szemantikus-tulajdonsagok]] — a kielégíthetőség, kielégíthetetlenség és tautológia fogalma, amelyre a tabló épül
- [[concepts/logika/elsorendu-tablo]] — a kalkulus kiterjesztése az elsőrendű logikára
- [[concepts/bvszam/itelet-kalkulus]] — az ítéletlogika szintaxisa, amelyen a tabló dolgozik
- [[concepts/logika/iteletlogikai-formalizalas]] — a dedukciós tételes és visszakövetkeztetéses átfogalmazás igazságtáblás megfelelője
