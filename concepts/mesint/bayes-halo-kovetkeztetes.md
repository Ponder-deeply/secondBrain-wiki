---
tags: [concept]
sources: [10.bizonytalansag.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Következtetés Bayes-hálókban

A Bayes-hálóbeli következtetés célja egy feltételes valószínűség kiszámítása a Bayes-módszerrel; egyszeresen kötött hálóra lineáris idejű, többszörösen kötött hálóra csak redukáló módszerekkel (összevonás, vágóhalmaz-feltételezés, sztochasztikus szimuláció) kezelhető.

## Tartalom

### Az alapfeladat és eszközei

Egy feltételes valószínűség kiszámítása az alábbi eszközökkel történik: [[concepts/mesint/bayes-tetel]], normalizálás, felbontás teljes eseményrendszerre, láncszabály, feltételes függetlenség. Egy feltételes valószínűségre rekurzív algoritmus készíthető, amelynek számításigénye erősen függ a háló bonyolultságától.

- **Egyszeresen kötött háló** (az irányítást figyelmen kívül hagyva fa-gráf: két csúcs között nincs alternatív irányítatlan út): van **lineáris futási idejű** algoritmus.
- **Többszörösen kötött háló**: különféle redukáló módszerek alkalmazhatók.

### Számolási példa: $p(B \mid Sz)$

A betörés–riasztás–szomszéd hálóban ([[concepts/mesint/bayes-halo-tervezese]]) a szomszéd telefonált; mi a betörés valószínűsége?

$$p(B \mid Sz) = \frac{p(Sz \mid B)\,p(B)}{p(Sz)} = \alpha \cdot p(Sz \mid B)\, p(B)$$

(Bayes-tétel, majd normalizálás: $\alpha = 1/p(Sz)$ állandó.) A $p(Sz \mid B)$ felbontása a teljes eseményrendszerre $\{R, \neg R\}$ szerint, láncszabállyal és a feltételes függetlenséggel ($Sz$ csak $R$-től függ):

$$p(Sz \mid B) = p(Sz \mid R)\,p(R \mid B) + p(Sz \mid \neg R)\,p(\neg R \mid B)$$

Behelyettesítve: $\alpha \cdot [0{,}9 \cdot 0{,}95 + 0{,}05 \cdot 0{,}05] \cdot 0{,}001 = \alpha \cdot 0{,}0008575$.

Hasonlóan $p(\neg B \mid Sz) = \alpha \cdot [0{,}9 \cdot 0{,}001 + 0{,}05 \cdot 0{,}999] \cdot 0{,}999 = \alpha \cdot 0{,}0507991$.

A két érték összegének 1-nek kell lennie, így $\alpha = 19{,}3585$ és

$$p(B \mid Sz) = 0{,}0166.$$

Vagyis annak ellenére, hogy a szomszéd telefonált, a betörés valószínűsége csak kb. 1,7% (a kis a priori $p(B)$ miatt).

### Többszörösen kötött háló: a locsoló példa

Russel–Norvig kétszeresen kötött hálója: $Esős\ évszak$ (EÉ) $\to$ $Locsoló$ (L), $Eső$ (E); $L, E \to Vizes\ pázsit$ (VP). Itt EÉ-ből két úton is eljut a hatás VP-hez, ezért nem fa-gráf.

FVT-k: $p(EÉ{=}i) = 0{,}5$; $p(L{=}i \mid EÉ{=}i) = 0{,}0$, $p(L{=}i \mid EÉ{=}h) = 0{,}9$; $p(E{=}i \mid EÉ{=}i) = 0{,}8$, $p(E{=}i \mid EÉ{=}h) = 0{,}1$; $p(VP{=}i \mid L{+}E)$: $ii \to 0{,}95$, $ih \to 0{,}9$, $hi \to 0{,}8$, $hh \to 0{,}1$.

Három redukáló eljárás-család:

#### a) Összevonásos eljárások

Változók (csúcsok) összevonásával fa-gráfot kapunk; az összevont csúcs FVT-jét meg kell határozni. A példában $Locsoló$ és $Eső$ összevonva egyetlen $L{+}E$ csúcs (értékei $ii, ih, hi, hh$), amelynek FVT-je az EÉ-től függ; sor: $EÉ{=}i$: $0, 0, 0{,}8, 0{,}2$; $EÉ{=}h$: $0{,}09, 0{,}81, 0{,}01, 0{,}09$ (a két eredeti FVT megfelelő értékeinek szorzata, mivel L és E EÉ-ra nézve feltételesen független). Az így kapott lánc $EÉ \to L{+}E \to VP$ már egyszeresen kötött.

#### b) Vágóhalmaz-feltételezésen alapuló eljárások

Változók elhagyásával (értékük rögzítésével) annyi azonos szerkezetű fa-gráfot kapunk, ahányféleképpen az elhagyott változók értéke rögzíthető. Minden fa-gráf súlya az a valószínűség, amellyel az elhagyott változók a rögzített értékeket felveszik; a fa-gráfok FVT-it újra kell számolni. A válasz az egyes (esetleg csak a valószínűbb) fa-gráfokból kiszámolt eredmények **súlyozott átlaga**.

A példában EÉ-t rögzítjük: "esős évszak igen" (súly $0{,}5$) és "esős évszak nem" (súly $0{,}5$) két külön fa-gráfot ad, ahol L és E FVT-je már csak az EÉ rögzített értékének megfelelő sor (pl. igen: $L{=}i: 0{,}0$, $E{=}i: 0{,}8$; nem: $L{=}i: 0{,}9$, $E{=}i: 0{,}1$).

**Adott pontosságú vágóhalmaz-feltételezés.** Nem szükséges az összes fa-gráfra kiszámolni a keresett feltételes valószínűséget; sokszor elég a legvalószínűbb hálókra a súlyozott átlagot számolni. A számolási hiba a ki nem értékelt hálók valószínűségeinek összege.

#### c) Sztochasztikus szimulációs eljárások

A háló valószínűségi értékeit figyelembe véve **példákat generálunk**; a válasz a jó példák relatív gyakorisága az összes példához képest:

$$p(A \mid B) = \frac{p(A, B)}{p(B)} = \frac{\text{jó hasznos példák száma}}{\text{összes hasznos példa száma}}$$

- Egy példa **hasznos**, ha a feltételt ($B$) teljesíti.
- Hogy csak hasznos példát generáljunk, a feltételt alkotó **tényváltozók értékét rögzítjük**, de a példát azzal a valószínűséggel **súlyozzuk**, amellyel ezek a tényváltozók a kijelölt értékeket felveszik. A relatív gyakoriságot a példák súlyozott darabszáma alapján számítjuk.

**Egy hasznos példa a $p(VP \mid Eső)$ számára** (tényváltozó: $E = igaz$; a változókat a hálóban topologikus sorrendben mintavételezzük):

1. $EÉ = Random(0{,}5)$, mert $p(EÉ) = 0{,}5$; tegyük fel az eredmény: $EÉ = hamis$.
2. $L = Random(0{,}9)$, mert $p(L \mid \neg EÉ) = 0{,}9$; eredmény: $L = igaz$.
3. $E$ tényváltozó, értéke igaz; ez garantálja a példa hasznosságát, a példa **súlya** pedig $p(E \mid \neg EÉ)$ (a dián $0{,}2$).
4. $VP = Random(0{,}95)$, mert $p(VP \mid E, L) = 0{,}95$; eredmény: $VP = igaz$.

Ez egy jó hasznos példa, súlya a 3. lépés valószínűsége.

### Értékelés

Előnyök: kevesebb a priori valószínűséget kell tárolni, mint a teljes együttes eloszlásfüggvényhez; egyszerűen bővíthető anélkül, hogy a korábbi valószínűségeket újra kellene gondolni; a következtetés felhasználható magyarázatadásra. Hátrány: matematikailag jól megalapozott, de igen számításigényes.

## Kapocs

- [[concepts/mesint/bayes-halo]] — a háló, amelyen a következtetés fut
- [[concepts/mesint/bayes-tetel]] — a számítás alapja
- [[concepts/mesint/felteteles-fuggetlenseg]] — a felbontás egyszerűsítése ezen múlik
- [[concepts/mesint/bayes-halo-tervezese]] — a példák hálói itt épülnek fel
- [[concepts/mesint/heurisztikus-technikak-bizonytalansagra]] — a pontos valószínűségi számítás olcsóbb, közelítő alternatívái
- [[concepts/bigdata/naive-bayes]] — a Bayes-tétel gépi tanulási alkalmazása
