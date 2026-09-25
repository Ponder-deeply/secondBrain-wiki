---
tags: [concept, logika/tablokalkulus]
sources: [Tablókalkulus.pdf]
derivation: source
updated: 2026-09-08
---

# Elsőrendű analitikus tabló

Az [[concepts/logika/analitikus-tablo|ítéletlogikai tabló]] elsőrendű kiterjesztése: az $\alpha$/$\beta$ szabályok mellett két új szabály jelenik meg a kvantorokra ($\gamma$, $\delta$ típus), és a kalkulus — helyesen és teljesen — a kielégíthetetlenség eldöntésére szolgál, term nélküli, paraméteres elsőrendű nyelven.

## Tartalom

### Termek nélküli elsőrendű nyelv

Az elsőrendű klasszikus tablószabályok biztosítanák, hogy egy kvantált formula magjába az interpretáló struktúra univerzumának megfelelő eleme kerüljön be, az $x \| t$ (tetszőleges term szerinti), illetve $x \| y$ (kritikus változó szerinti) helyettesítéssel. A tárgyalás egyszerűsítése végett a tabló elmélete az univerzumelemeket **term nélkül**, közvetlenül kezeli: az elsőrendű nyelv ábécéje

- logikán kívüli részben: tetszőleges aritású predikátumszimbólumok (minden argumentumszámhoz megszámlálhatóan végtelen sok) és az indivíduum **paraméterek** megszámlálható sorozata;
- logikai részben: indivíduum változók, egyenlőség predikátumszimbólum, logikai összekötőjelek, kvantorok.

**Term:** minden indivíduum változó és indivíduum paraméter. **Formula:** (1) ha $P$ $n$-változós predikátumszimbólum és $t_1,\dots,t_n$ termek, akkor $P(t_1,\dots,t_n)$ atomi formula; (2) ha $A, B$ formulák, akkor $\neg A$ és $(A \circ B)$ ($\circ \in \{\wedge,\vee,\supset\}$) is; (3) ha $A$ formula, akkor $\forall xA$ és $\exists xA$ is formulák. A paramétert nem tartalmazó formulákat **tiszta formulának** nevezzük — a tabló mindig egy tiszta (zárt) formulából indul.

### Univerzális és egzisztenciális típusú formulák

Az $\alpha$/$\beta$ típus mellett (lásd [[concepts/logika/jelolt-formula-es-formulatipusok]]) elsőrendben két új formulatípus jelenik meg:

- **$\gamma$-típus (univerzális):** $\forall xA$ és $\neg\exists xA$.
- **$\delta$-típus (egzisztenciális):** $\exists xA$ és $\neg\forall xA$.

A $\gamma$ és $\delta$ formulák magjába egy $a$ indivíduum paraméter behelyettesítését $\gamma(a)$, illetve $\delta(a)$ jelöli.

### Közvetlen tablók elsőrendben

Jelöletlen alakban, a $\gamma$/$\delta$ szabályok:

| Típus | Formula | Közvetlen tabló |
|---|---|---|
| $\gamma$ (C) | $\forall xA$ / $\neg\exists xA$ | $A(x\|a)$ / $\neg A(x\|a)$ — $a$ **tetszőleges** term (paraméter) |
| $\delta$ (D) | $\exists xA$ / $\neg\forall xA$ | $A(x\|a)$ / $\neg A(x\|a)$ — $a$ **kritikus** paraméter (megkötéssel) |

Jelölt alakban:

| Formula | Közvetlen tabló |
|---|---|
| $T\forall xA$ / $F\exists xA$ | $TA(x\|a)$ / $FA(x\|a)$ |
| $T\exists xA$ / $F\forall xA$ | $TA(x\|a)$ (megkötéssel) / $FA(x\|a)$ |

A **megkötés** azt fejezi ki, hogy a $\delta$-szabály (D) alkalmazásakor választott $a$ paraméter nem fordulhat elő a gyökértől az adott csúcsig már feldolgozott egyetlen formulában sem — ez a **kritikus paraméter**. A $\gamma$-szabály (C) ezzel szemben tetszőleges (akár már felhasznált) $a$ paraméterre alkalmazható, és — mivel $\forall xA$ minden elemre igaz kell legyen — újra is alkalmazható ugyanarra a $\gamma$-formulára más paraméterrel.

### Az elsőrendű analitikus tabló definíciója

Egy $C$ elsőrendű **tiszta** formula analitikus tablója egy olyan bináris fa, amelynek csúcsai jelöletlen elsőrendű formulák, gyökere a $C$ formula. Ha $T$ egy tabló és $D$ a $T$ egy levélcsúcsa, a $T$ **közvetlen kiterjesztése** a következők egyike:

- **(A)** Ha van fel nem dolgozott $\alpha$-formula a gyökértől $D$-ig vezető úton: $D$-hez az út folytatásaként hozzáfűzzük az $\alpha_1$, majd $\alpha_2$ formulákat.
- **(B)** Ha van fel nem dolgozott $\beta$-formula: $D$-ben a tabló elágazik, a bal ágra $\beta_1$, a jobb ágra $\beta_2$ kerül.
- **(C)** Ha van $\gamma$-formula a gyökértől $D$-ig vezető úton: $D$-hez az út folytatásaként hozzáfűzzük a $\gamma(a)$ formulát, ahol $a$ tetszőleges paraméterszimbólum. (Egy $\gamma$-formula így többször is „feldolgozható”, más-más $a$-val.)
- **(D)** Ha van fel nem dolgozott $\delta$-formula a gyökértől $D$-ig vezető úton: $D$-hez hozzáfűzzük a $\delta(a)$ formulát, ahol $a$ a gyökértől $D$-ig vezető úton még elő nem forduló, azaz **kritikus** paraméterszimbólum.

Zárt ág, zárt tabló és tablócáfolat fogalma megegyezik az ítéletlogikai esettel ([[concepts/logika/analitikus-tablo]]).

**Példa.** A $(\forall xA \supset B) \supset \exists x(A \supset B)$ zárt formula (ahol $x \notin Par(B)$) tagadásának tablója az $\alpha$/$\beta$/$\gamma$/$\delta$ szabályok alkalmazásával minden ágon lezár — a formula tehát logikailag igaz.

### Helyesség

**Tétel.** Ha egy elsőrendű $G$ formula tablója zárt, akkor $G$ kielégíthetetlen.

*Bizonyítás* (indirekt). Tegyük fel, hogy $G$ tablója zárt, de $G$ kielégíthető egy $\sigma_0$ interpretációban. Ekkor kell lennie a tablónak legalább egy nyitott, kielégíthető ágának: az $\alpha$/$\beta$ szabályokra ez már belátott ([[concepts/logika/analitikus-tablo]]); a **C** szabályra, ha a kiterjesztés egy $\gamma$ formulából jött, akkor $\gamma$ igaz volt a kielégítő interpretációban, tehát $\gamma(a)$ is igaz marad benne; a **D** szabályra, ha a kiterjesztés egy $\delta$ formulából jött, akkor $\delta$ igaz volt, és mivel $a$ a $\delta(a)$-ban új paraméter, $\delta(a)$ is igaz marad. Tehát $G$ tablójának lenne nyitott ága, azaz $G$ tablója nem lehetne zárt — ellentmondás. $\blacksquare$

### Elsőrendű Hintikka halmaz és a teljesség

A teljesség bizonyításához szükséges az **elsőrendű Hintikka halmaz** fogalma és a rá vonatkozó Hintikka lemma — ezeket lásd [[concepts/logika/hintikka-halmaz]].

**Tétel (teljesség).** Ha az elsőrendű $G$ formula kielégíthetetlen, akkor $G$ tablója zárt.

*Bizonyítás* (indirekt). Tegyük fel, hogy $G$ kielégíthetetlen, de $G$ tablójának van nyitott ága. Egy nyitott ágon előálló formulahalmaz elsőrendű Hintikka halmaz, ami a Hintikka lemma szerint kielégíthető, és $G$ is eleme ennek a halmaznak — tehát $G$ kielégíthető. Ez ellentmond a feltevésnek. $\blacksquare$

A helyesség és teljesség együtt: az elsőrendű $G$ formula pontosan akkor kielégíthetetlen, ha tablója zárt — a tabló itt is helyes és teljes eldöntési módszer a kielégíthetetlenségre (bár, az elsőrendű logika algoritmikus eldönthetetlensége miatt, nem feltétlenül *terminál* minden kielégíthető formulán, lásd [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg]]).

### Szisztematikus tabló

$G$ **szisztematikus tablójának** nevezzük azt a tablóépítési stratégiát, amely biztosítja, hogy minden teljes nyitott ágon Hintikka halmaz álljon elő (a kritikus paraméterek $U$ halmaza felett): az **A**, **B**, **D** szabályokat hajtjuk végre, amíg lehet, majd a **C** szabályt, ahol a $\gamma(a)$ mellett magát a $\gamma$ formulát is visszahelyezzük az ág végére (hogy később, más paraméterrel, újra feldolgozható legyen).

A tabló **befejezett szisztematikus tabló**, ha nyitott ága vagy végtelen, vagy véges, de további kiterjesztés már nem lehetséges (minden nem atomi formula fel van dolgozva).

### Löwenheim-tétel

**Tétel (Löwenheim).** Ha $G$ egyáltalán kielégíthető, akkor kielégíthető legfeljebb megszámlálható univerzumon.

*Bizonyítás.* Legyen $T$ a $G$ befejezett szisztematikus tablója. Mivel $G$ kielégíthető, $T$-nek van nyitott ága. Egy nyitott ágon véges sok vagy megszámlálhatóan végtelen kritikus paraméter fordul elő (hiszen minden **D**-lépés legfeljebb egy új paramétert vezet be). A kapott formulahalmaz Hintikka halmaz, tehát $G$ ezen (legfeljebb megszámlálható) paraméterhalmaz — mint univerzum — felett is kielégíthető. $\blacksquare$

### Kompaktsági tétel

**Tétel.** Ha egy megszámlálható $S$ formulahalmaz minden véges részhalmaza kielégíthető, akkor $S$ is kielégíthető.

*Bizonyítás.* Rendezzük $S$ elemeit egy $A_1, A_2, \dots$ sorozatba. Állítsuk elő $A_1$ teljes tablóját — ez nem zárt, mert $A_1$ kielégíthető. Ezután minden nyitott ághoz kapcsoljuk $A_2$ tablóját: mivel $\{A_1, A_2\}$ kielégíthető, marad legalább egy nyitott ág. Ezt folytatva $A_3, A_4, \dots$ tablóival, minden lépésben a feltétel (minden véges részhalmaz kielégíthető) miatt marad nyitott ág. Az így kapott végtelen fa **végesen elágazó** (minden csúcsból legfeljebb két él indul), ezért König lemmája szerint van legalább egy végtelen nyitott ága, $\Theta$. $\Theta$ tartalmazza minden $A_i$-t, és a rajta szereplő formulák halmaza Hintikka halmaz, amely $S$-t is tartalmazza. A Hintikka halmaz kielégíthető, tehát $S$ is kielégíthető. $\blacksquare$

*Megjegyzés.* A tétel megfordítása triviálisan igaz (ha $S$ kielégíthető, minden véges részhalmaza is az), és a tétel megszámlálhatónál nagyobb számosságú formulahalmazra is érvényben marad.

## Kapocs

- [[concepts/logika/jelolt-formula-es-formulatipusok]] — az $\alpha$/$\beta$ típus és a közvetlen tabló alapfogalma
- [[concepts/logika/analitikus-tablo]] — az ítéletlogikai tabló, amelynek ez a fejezet a kiterjesztése
- [[concepts/logika/hintikka-halmaz]] — az elsőrendű Hintikka halmaz és lemma, a teljesség kulcsa
- [[concepts/logika/elsorendu-szemantikus-fa]] — a véges univerzum feletti interpretációk fás felsorolása, amelyre a tabló gondolata épül
- [[concepts/logika/szemantikus-tulajdonsagok]] — a kielégíthetőség és kielégíthetetlenség fogalma
- [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg]] — az elsőrendű logika algoritmikus eldönthetetlensége, ami a tabló esetleges nemterminálását indokolja
