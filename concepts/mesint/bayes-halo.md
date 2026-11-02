---
tags: [concept]
sources: [10.bizonytalansag.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Bayes-háló

A Bayes- (valószínűségi) háló a minimálisan szükséges apriori valószínűségeket tömören tárolja úgy, hogy a feltételes függetlenségek felismerése egyértelmű és automatizálható legyen.

## Tartalom

### Reprezentáció

1. A tárgyprobléma valószínűségi változóit megfeleltetjük egy **körmentes irányított gráf** csúcsainak.
2. Az irányított élek a változók közötti közvetlen **ok-okozati összefüggéseket** ábrázolják (ezzel implicit módon a feltételes függetlenségeket is rögzítjük).
3. Minden csúcshoz megadjuk a **feltételes valószínűségi táblát** (FVT):
$$p(X_i = x_i \mid szülő(X_i) = x_{i1},\dots,x_{ik}),$$
ahol $szülő(X_i)$ az $X_i$ szülőcsúcsaihoz rendelt változók együttese.

Példa: a *Szuvas* csúcs két gyereke *Fáj* és *Lyukas*; FVT-k: $p(szuvas)=0.65$; $p(fáj \mid szuvas)=0.5$, $p(fáj \mid \neg szuvas)=0.1$; $p(lyukas \mid szuvas)=0.95$, $p(lyukas \mid \neg szuvas)=0.01$.

### Feltételes függetlenség felismerése

Legyenek $A$, $B$, $E$ összetett (több csúcsú) események. $A$ és $B$ feltételesen független $E$-re nézve, ha minden $A$-beli és $B$-beli csúcs közötti **irányítatlan útvonalra** az alábbi 4 eset valamelyike teljesül:

1. az úton van $E$-beli csúcs, és az út ott „soros" (az él $E$ felé, majd tovább megy: $\to X \to$);
2. az úton van $E$-beli csúcs, és az út ott „soros" a másik irányban ($\leftarrow Y \leftarrow$);
3. az úton van $E$-beli csúcs, ahonnan mindkét irányba kifelé mutat él (közös ok, $\leftarrow Z \rightarrow$);
4. az úton van egy $W$ csúcs, amelybe mindkét irányból él fut be (közös következmény, $\to W \leftarrow$), és sem $W$, sem leszármazottai nincsenek $E$-ben.

### Kifejező erő

A láncszabály szerint
$$p(X_1=x_1,\dots,X_n=x_n) = \prod_{i=1}^{n} p(X_i = x_i \mid X_1=x_1,\dots,X_{i-1}=x_{i-1}).$$

Ha a változókat úgy számozzuk, hogy $i > j$ esetén $X_i$-ből ne vezessen irányított út $X_j$-be, akkor $szülő(X_i) \subseteq \{X_1,\dots,X_{i-1}\}$, és a feltételes függetlenség miatt
$$p(X_i = x_i \mid X_1=x_1,\dots,X_{i-1}=x_{i-1}) = p(X_i = x_i \mid szülő(X_i)).$$

Így az együttes valószínűségi eloszlás közvetlenül megkapható a háló FVT-iből:
$$p(X_1=x_1,\dots,X_n=x_n) = \prod_{i=1}^{n} p(X_i = x_i \mid szülő(X_i) = x_{i1},\dots,x_{ik}).$$

A Bayes-háló tehát az együttes eloszlás tömör reprezentációja: nem kell az összes elemi esemény valószínűségét tárolni.

A háló tervezése, a következtetés és a tanulás a [[concepts/mesint/bayes-halo-tervezese]], [[concepts/mesint/bayes-halo-kovetkeztetes]] és [[concepts/mesint/bayes-halo-tanulasa]] lapokon szerepel.

## Kapocs

- [[concepts/mesint/bayes-tetel]] — a háló a Bayes-i frissítés módszerét általánosítja
- [[concepts/mesint/felteteles-fuggetlenseg]] — a háló szerkezete ezt rögzíti
- [[concepts/mesint/klasszikus-valoszinuseg-szamitas]] — az együttes eloszlás tárolásának problémája
- [[concepts/mesint/bayes-halo-tervezese]] — hogyan építsünk hálót
- [[concepts/mesint/bayes-halo-kovetkeztetes]] — lekérdezés a hálón
- [[concepts/mesint/bayes-halo-tanulasa]] — háló tanulása adatból
- [[concepts/bigdata/naive-bayes]] — a legegyszerűbb Bayes-háló (egy szülő, sok független gyerek)
