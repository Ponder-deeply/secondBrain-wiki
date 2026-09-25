---
tags: [concept, logika/tablokalkulus]
sources: [Tablókalkulus.pdf]
derivation: source
updated: 2026-09-08
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

**Tétel (teljesség).** Ha $C$ kielégíthetetlen, akkor $C$ (bármely) $T$ tablója zárt.

*Bizonyítás.* Tegyük fel indirekt, hogy $C$ kielégíthetetlen, de $T$-nek van nyitott ága. Egy ilyen ágon szereplő formulahalmaz **lefelé zárt**: ha rajta szerepel egy $\alpha$-formula, akkor $\alpha_1$ és $\alpha_2$ is szerepel rajta; ha egy $\beta$-formula, akkor $\beta_1$ és $\beta_2$ közül legalább az egyik. Egy ilyen szerkezetű, komplemens párt nem tartalmazó halmaz [[concepts/logika/hintikka-halmaz|Hintikka halmaz]], ami a Hintikka lemma szerint kielégíthető — tehát az ág minden formulája, így $C$ is, kielégíthető. Ez ellentmond a feltevésnek. $\blacksquare$

A helyesség és a teljesség együtt azt adja, hogy **a tablókalkulus a kielégíthetetlenség eldöntésének helyes és teljes szintaktikus módszere**: $C$ kielégíthetetlen pontosan akkor, ha van tablócáfolata. Mivel a kielégíthetőség/tautológia kérdése (lásd fent) mindig kielégíthetetlenségi kérdésre vezethető vissza, a tabló ezáltal mindkettőt eldönti — véges formula esetén véges lépésben.

### Formulahalmaz tablója

Egy véges $\{F_1, \dots, F_n\}$ formulahalmaz tablójának gyökerében az $F_1 F_2 \dots F_n$ sorozat áll, és a tablót a szokásos módon, formulánként építjük tovább. Végtelen formulahalmaz tablóját ugyanígy, a formulák egy rögzített sorrendje szerint állítjuk elő.

## Kapocs

- [[concepts/logika/jelolt-formula-es-formulatipusok]] — a közvetlen tabló szabályai, amelyekből az analitikus tabló felépül
- [[concepts/logika/hintikka-halmaz]] — a teljesség bizonyításának kulcsfogalma: a nyitott ágon előálló formulahalmaz
- [[concepts/logika/szemantikus-tulajdonsagok]] — a kielégíthetőség, kielégíthetetlenség és tautológia fogalma, amelyre a tabló épül
- [[concepts/logika/elsorendu-tablo]] — a kalkulus kiterjesztése az elsőrendű logikára
- [[concepts/bvszam/itelet-kalkulus]] — az ítéletlogika szintaxisa, amelyen a tabló dolgozik
