---
tags: [concept, logika/temporalis-logika]
sources: [LTL_CTL.pdf]
derivation: source
updated: 2026-09-08
---

# LTL és CTL összehasonlítása

Az LTL és a CTL egyaránt temporális logika Kripke-struktúrák fölött, de eltérő kielégítési relációjuk ($\models$ út, illetve állapot mellett) miatt egyik sem foglalja magába a másikat: kifejezőerejük nem összemérhető, bonyolultságuk és intuitivitásuk is eltérő.

## Tartalom

### Ekvivalencia LTL és CTL formulák között

Egy $\varphi_{CTL}$ CTL-formula és egy $\varphi_{LTL}$ LTL-formula ekvivalens, ha ugyanazok a Kripke-struktúrák (modellek) elégítik ki őket:

$$\varphi_{CTL} \equiv \varphi_{LTL} \iff \big[(M \models_M \varphi_{CTL}) \Leftrightarrow (M \models_M \varphi_{LTL})\big] \text{ minden } M\text{-re}$$

### Kifejezőerő: az $E$ útkvantor

Bármely CTL-formula, amely az $E$ útkvantort lényegileg használja, **nem fejezhető ki LTL-ben**. Például az $EXp$ ("van olyan út, amelyen a következő állapotban $p$") formulának nincs LTL megfelelője: az LTL formulái mindig az összes útra vonatkoznak (implicit univerzális kvantifikáció a modellkielégítésben, lásd [[concepts/logika/ltl]]), így nem tudnak "létezik egy út" jelentést kifejezni.

### A $G$ kapcsolat

Ha egy $\varphi_{CTL}$ CTL-formula és egy $\varphi_{LTL}$ LTL-formula ekvivalens, akkor:

$$AG\,\varphi_{CTL} \equiv G\,\varphi_{LTL}$$

### Nevezetes nem-ekvivalenciák

**$FXp \equiv XFp \equiv AXAFp \not\equiv AFAXp$**

Az első három kifejezés ekvivalens, de a negyedik, $AFAXp$, nem. Az $AFAXp$ azt mondja: bármely állapotból indulva, minden úton el fogunk érni előbb-utóbb egy olyan állapotot, amelynek **minden** közvetlen rákövetkezője kielégíti $p$-t. Van olyan modell, amely kielégíti $AXAFp$-t, de nem elégíti ki $AFAXp$-t — ez mutatja, hogy a négy formula nem mind ekvivalens egymással.

**$FGp \not\equiv AFAGp$**

Van olyan modell, amely kielégíti $FGp$-t ("valamikor a jövőben $p$ már mindig igaz marad" — egy konkrét úton), de nem elégíti ki $AFAGp$-t ("minden állapotból indulva, minden úton elérünk egy olyan pontot, ahonnan minden rákövetkező kielégíti $p$-t"). Ha van egy állapot, amelyen keresztül ciklikusan visszatérő út fut úgy, hogy azon a cikluson mindig lesz $\neg p$-t kielégítő lehetséges rákövetkező, akkor $AFAGp$ sérül, miközben a cikluson kívüli konkrét út még kielégítheti $FGp$-t.

**$GFp \equiv AGAFp$, de $(GFp \Rightarrow GFq) \not\equiv (AGAFp \Rightarrow AGAFq)$**

Bár $GFp$ és $AGAFp$ önmagukban ekvivalensek, a belőlük képzett implikációk már nem azok. Az LTL formula egyetlen útra vonatkozó implikáció, míg a CTL formula két, egymástól **függetlenül** meghatározott állapothalmazra vonatkozó implikáció — ez a különbség okozza a nem-ekvivalenciát. Van olyan modell, amely kielégíti $AGAFp \Rightarrow AGAFq$-t (mert az előtag, $AGAFp$, nem is teljesül, tehát az implikáció trivialitásból igaz), miközben nem elégíti ki $GFp \Rightarrow GFq$-t (mert van olyan út, amely kielégíti $GFp$-t, de nem elégíti ki $GFq$-t).

Ezek a példák közös tanulsága: a CTL állapot-alapú, útkvantorral kombinált szemantikája és az LTL út-alapú szemantikája még akkor is szétválhat, ha az egyszerű építőelemek (pl. $GFp$ és $AGAFp$) ekvivalensek — összetettebb formulákban ez az ekvivalencia nem öröklődik automatikusan.

### Bonyolultság

Legyen $|\varphi| = n$ a formula mérete, $|M| = m$ a modell mérete.

- **CTL:** $O(mn)$ — lineáris a modell és a formula méretében.
- **LTL:** $O(m \cdot 2^n)$ — exponenciális a formula méretében, és PSPACE-teljes.

### Intuitivitás

A forrás két empirikus megfigyelést idéz a szakirodalomból:

- *"Formal Verification Made Easy"* (IBM Journal of Research and Development, 1997): csak az egyszerű CTL-egyenleteket találták érthetőnek; a nem-triviális egyenletek nehezen érthetők és hibára hajlamosak.
- *"On the Fly Model Checking"* (CAV'98, 1998): a CTL a legtöbb felhasználó számára nehezen használható, és a hardverről való új típusú gondolkodást igényel.

Vagyis a CTL alacsonyabb számítási bonyolultsága nem jár együtt automatikusan könnyebb érthetőséggel — a két szempont (bonyolultságelméleti és kognitív) itt szétválik.

## Kapocs

- [[concepts/logika/ltl]] — a lineáris temporális logika: út-alapú szemantika, PSPACE-teljes döntési probléma
- [[concepts/logika/ctl]] — az elágazó idejű temporális logika: állapot-alapú szemantika, útkvantorokkal, lineáris idejű döntési probléma
- [[concepts/logika/kripke-struktura]] — a közös modell, amelyen mindkét logika értelmezett
- [[concepts/logika/szemantikus-tulajdonsagok]] — rokon fogalom más logikai keretben: ott is a modellek (interpretációk) közötti kielégítés, illetve minden modellre való érvényesség adja az ekvivalencia és a logikai igazság fogalmát
