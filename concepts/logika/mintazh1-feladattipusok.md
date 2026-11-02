---
tags: [concept]
sources: [MintaZH1.pdf]
derivation: inferred
kind: overview
element: fire
updated: 2026-10-19
---

# ZH1 mintazh: feladattípusok és megoldásvázlatok

A kanonikus ZH1 mintazh (`MintaZH1.pdf`) feladatonkénti térképe, a megoldás vázlatával és a lefedő fogalomlapokkal. A gyakorlati rész a valódi ZH-ban csaknem ugyanez; a rövid kérdések és a 3. feladat csak a típust jelzik.

## Tartalom

Maximum: rövid kérdések 12 pont, kifejtős rész 40 pont. A mintazh **nem azonos** a Tóth Gabriella-féle 2019-es mintával (`Toth-Gabriella-Logika-mintazh-2019.pdf`), amely más szerkezetű, nem kanonikus forrás.

### 1. Rövid kérdések (12 pont, elméleti jelleg)

A valódi ZH hasonló stílusú kérdéseket tesz fel, de másokat is; a mintakérdések nem a teljes halmaz.

- **1.1** $F_1,\dots,F_n \models_0 B$ esetén melyik állítás nem teljesül? **Válasz: a)** „ha a közös igazságtábla egy sorában $B$ igaz, akkor mindegyik $F_i$ igaz” — hamis, mert $B$ igaz lehet úgy is, hogy valamelyik $F_i$ hamis. A b), c), d) teljesül: b) a kontrapozíció, c) és d) megengedett sorok (a következményfogalom csak az „összes $F_i$ igaz és $B$ hamis” sort zárja ki). Lásd [[concepts/logika/szemantikus-kovetkezmeny]], [[concepts/logika/kovetkeztetesforma]].
- **1.2** Mi igazolja tablókalkulusban, hogy $A$ kielégíthetetlen? Biztosan jó: *a $TA$-hoz készített tabló minden ágán szerepel egy ítéletváltozó és negáltja* (minden ág ellentmondásos, a tabló zárt). A $TA$ tablójában ellentmondásos ág hiánya éppen ellenkezőleg a kielégíthetőséget jelzi; az $FA$ tablójának lezárása $A$ *tautológia* voltát mutatja, nem a kielégíthetetlenségét. Az „$FA$ tautológia” állítás félreérthető (jelölt formula nem tautológia, csak $\neg A$-ra olvasva jelentene kielégíthetetlenséget): a megoldásnál ezt külön ki kell mondani. Lásd [[concepts/logika/analitikus-tablo]], [[concepts/logika/jelolt-formula-es-formulatipusok]].
- **1.3** Elsőrendű formula prímkomponensei és az értéktábla első sora: $\neg\exists xP(x) \wedge \forall x(P(x)\vee Q(x,\bar a)) \supset P(z)$. Precedencia: $((\neg\exists xP(x)) \wedge \forall x(\dots)) \supset P(z)$. Prímkomponensek: $\exists xP(x)$, $\forall x(P(x)\vee Q(x,\bar a))$, $P(z)$. Az értéktábla **első sora a fejléc** ([[concepts/logika/szemantikus-tulajdonsagok]]): $z \mid \exists xP(x) \mid \forall x(P(x)\vee Q(x,\bar a)) \mid P(z) \mid$ formula. Lásd [[concepts/logika/elsorendu-formula]], [[concepts/logika/szemantikus-tulajdonsagok]].

### 2.1 Igazságtábla, formalizálás és következmény (8 pont)

Jelölések: $A$: eszek fagyit, $B$: odakint meleg van, $C$: elmegyek a boltba (azonos állítás azonos változó).

1. „Csak akkor eszek fagyit, amikor meleg van": $A \supset B$
2. „Ha elmegyek a boltba, akkor eszek egy fagyit": $C \supset A$
3. „Meleg van, de nem megyek a boltba": $B \wedge \neg C$
4. $K$: $\neg A$

A közös, teljesen kitöltött igazságtábla (8 sor, oszlopok: $A,B,C$, a négy formula) alapján a premisszák együtt igazak az $A=B=1,C=0$ és az $A=0,B=1,C=0$ sorban. Az első sorban $K=\neg A$ hamis, tehát **$K$ nem szemantikus következménye** az első háromnak. Lásd [[concepts/logika/igazsagtabla]], [[concepts/logika/iteletlogikai-formula]], [[concepts/logika/kovetkeztetesforma]].

### 2.2.1 Tablókalkulus, ítéletlogika (8 pont)

$\{\neg(X\vee\neg Y),\ (Y\supset Z)\} \models \neg X\vee Z$. Tabló a premisszákból és a $F(\neg X \vee Z)$ jelölésből: $F(X\vee\neg Y)$ szétesik $FX$-re és $F\neg Y$-ra, azaz $TY$; $F(\neg X\vee Z)$ adja: $TX$ és $FZ$. $TX$ és $FX$ ellentmond, az ág zárt, tehát **a következmény teljesül**. (A $Y \supset Z$ ágai itt már nem szükségesek.) Lásd [[concepts/logika/analitikus-tablo]].

### 2.2.2 Tablókalkulus, elsőrendű (8 pont)

$\{R(\bar c)\wedge P(\bar c,\bar b),\ \forall y(R(y)\supset Q(y)),\ \forall x\forall y(P(x,y)\supset Q(x))\} \models R(\bar b)\vee\exists yP(\bar a,y)\supset\exists xQ(x)$ (a $\bar a,\bar b,\bar c$ paraméterek). A konklúzió implikáció: $T(R(\bar b)\vee\exists yP(\bar a,y))$ és $F\exists xQ(x)$. A $\gamma$-szabállyal a $\forall y(R(y)\supset Q(y))$-ból $\bar c$-re: $R(\bar c)\supset Q(\bar c)$; mivel $TR(\bar c)$ már szerepel, adódik $TQ(\bar c)$. Az $F\exists xQ(x)$ ($\gamma$-típus) $\bar c$-re példányosítva $FQ(\bar c)$: ellentmondás, az ág zárt. **A következmény teljesül.** Lásd [[concepts/logika/elsorendu-tablo]].

### 2.3 Elsőrendű értéktábla (8 pont)

Interpretáció: $U=\{1,2,3,4\}$; $P(x)$: $x$ páratlan; $Q(x,y)$: $x>y$; $f(x)$: $x$ rákövetkezője, $f(4)=1$; $g(x)=(x \bmod 2)+1$; $\bar d=1$. Formula: $Q(z,\bar d)\supset\forall x(Q(z,x)\wedge P(g(x)))\supset\neg\forall y\exists xQ(f(x),g(y))$.

- Prímkomponensek: $Q(z,\bar d)$; $\forall x(Q(z,x)\wedge P(g(x)))$; $\forall y\exists xQ(f(x),g(y))$. Szabad változó: $z$, tehát 4 sor ($z=1,\dots,4$).
- $Q(z,1)$ értéke: $h,i,i,i$ ($z>1$). A második prímkomponens $h$ minden sorban, mert $g(1)=2$ páros, $P(g(1))$ hamis. A harmadik $i$ minden sorban ($g(y)\in\{1,2\}$, és $f(1)=2>1$, $f(2)=3>2$).
- Az implikáció **jobbra köt** ([[concepts/logika/zarojelelhagyas]]): $Q(z,\bar d)\supset(\forall\dots\supset\neg\forall\dots)$. Az $h\supset\dots$ belső rész igaz, így a formula **mind a 4 sorban igaz**.
- b) Az értéktábla alapján a formula ebben az interpretációban minden kiértékelésre igaz, tehát **kielégíthető**, és $I$ modellje a lezárásának; viszont *logikai igazságról* egy interpretáció nem dönt, így azt nem mondhatjuk ki. Lásd [[concepts/logika/elsorendu-interpretacio]], [[concepts/logika/valtozokiertekeles]], [[concepts/logika/szemantikus-tulajdonsagok]].

### 3. Wason-feladat (8 pont, csak a típust jelzi)

Lásd [[concepts/logika/wason-kivalasztasi-feladat]]: $A,1,4,B,8$ kártyák, „páros $\Rightarrow$ magánhangzó”; megfordítandó: $4$, $B$, $8$. A valódi ZH-ban a konkrét példány más lesz, a gondolatmenet ugyanaz (az implikáció ellenpéldájának keresése).

## Kapocs

- [[subjects/logika]] — a hub ZH1 szakasza
- [[concepts/logika/wason-kivalasztasi-feladat]] — a 3. feladat részletesen
- [[concepts/logika/szemantikus-kovetkezmeny]] — 1.1, 2.1
- [[concepts/logika/analitikus-tablo]] — 1.2, 2.2.1
- [[concepts/logika/elsorendu-tablo]] — 2.2.2
- [[concepts/logika/szemantikus-tulajdonsagok]] — 1.3, 2.3
