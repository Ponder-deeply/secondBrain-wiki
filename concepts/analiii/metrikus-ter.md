---
tags:
  - concept
sources:
  - Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf
  - SimonP-Anal2.pdf
  - An_III_Gyak_2022_tavasz.pdf
  - gyakorlat.pdf
  - RopzhKerdesek.pdf
  - ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf
  - 02_gyak_An_III_2024_25_Ifelev.pdf
  - 03_gyak_An_III_2022_tavasz.pdf
references:
  - "Simon Péter: Analízis II., 1.1–1.2. pont"
derivation: source
kind: definition
element: air
updated: 2026-10-21
studied: true
---

# Metrikus tér

A metrikus tér az a minimális struktúra, amelyben a „távolság" fogalma értelmes: egy nemüres ponthalmaz és egy három axiómának eleget tevő távolságfüggvény. Az Analízis III. topológiai apparátusa — konvergencia, nyíltság, teljesség, kompaktság — ezen az egyetlen definíción nyugszik.

## Tartalom

### Definíció

**Metrikus tér:** a $(M, d)$ pár, ahol

- $M \neq \emptyset$ a pontok halmaza (*a tér*),
- $d : M \times M \to [0, \infty)$ a *metrika* (távolság), amelyre

1. $\forall x, y \in M:\ d(x,y) \geq 0$, és $d(x,y) = 0 \iff x = y$;
2. $\forall x, y \in M:\ d(x,y) = d(y,x)$ (szimmetria);
3. $\forall x, y, z \in M:\ d(x,y) + d(y,z) \geq d(x,z)$ (háromszög-egyenlőtlenség).

### Példák

- **Diszkrét metrika.** Tetszőleges $M$-en $d(x,y) = 1$ ha $x \neq y$, és $0$ ha $x = y$.
- **Euklideszi távolság.** $M = \mathbb{R}^p$, $d(x,y) = |y - x| = \sqrt{\sum_{i=1}^p |y_i - x_i|^2}$.
- **Taxi-metrika.** $M = \mathbb{R}^p$, $d(x,y) = \sum_{i=1}^p |y_i - x_i|$.
- **Maximum-metrika.** $M = \mathbb{R}^p$, $d(x,y) = \max_{1 \leq i \leq p} |y_i - x_i|$.
- **Függvénytér.** $M = C[a,b]$, a folytonos $[a,b] \to \mathbb{R}$ függvények vektortere, $d(f,g) = \max_{x \in [a,b]} |g(x) - f(x)|$.

Ugyanazon az $M$ halmazon több, egymástól lényegesen különböző metrika is élhet, és a konvergencia is, a topológia is függhet a választástól — a $C[0,1]$ tér az $L^1$ és az $L^\infty$ metrikával erre a szokásos ellenpélda (lásd [[concepts/analiii/ekvivalens-normak]]).

### Feladatok

*Gyakorlati feladatok az An_III_Gyak_2022_tavasz.pdf 2. gyakorlatából és a gyakorlat.pdf „Metrikus terek" szakaszából; a megoldásötletek saját levezetések.*

**Módszer.** Metrikaaxiómák ellenőrzésénél a nemnegativitás/nulla-tulajdonság és a szimmetria általában azonnali; a munka a háromszög-egyenlőtlenség. Gyakori fogások: esetszétválasztás (diszkrét metrika), pozícióra bontás (Hamming), vagy visszavezetés ismert metrikára ([[concepts/analiii/metrikabol-uj-metrika]]).

- **Diszkrét metrika.** $\rho(x,z)\le\rho(x,y)+\rho(y,z)$: ha $x=z$, a bal oldal $0$; ha $x\neq z$, akkor $y$ legalább az egyiktől különbözik, így a jobb oldal $\ge 1$. Gömbök: $K_1(a)=\{a\}$, $K_r(a)=M$ ha $r>1$. Megjegyzés: itt $K_1(a)=K_{1/2}(a)=\{a\}$ *egyenlőség*, nem valódi tartalmazás, ezért ez még nem példa arra, hogy egy gömb valódi részgömbje nagyobb sugarú (javítva a 2. gyakorlat 5. feladata szerint; a valódi példa lent). Normált térben ilyen nem létezik (lásd [[concepts/analiii/normalt-vektorter]]).
- **Hamming-távolság.** $H=\mathcal K^n$, $\rho_H(x,y)$ = az eltérő pozíciók száma. Háromszög-egyenlőtlenség: ha $x_i\neq z_i$, akkor $x_i\neq y_i$ vagy $y_i\neq z_i$, tehát minden „rossz" pozíciót legalább az egyik tag megszámol. Konvergens sorozatai: a végül konstansak (a távolság egész szám, $<1$ csak $0$ lehet).
- **Az axiómák nem függetlenek.** Elég: $\rho(x,y)=0\iff x=y$ és $\rho(x,y)\le\rho(x,z)+\rho(y,z)$. $z:=x$-szel $\rho(x,y)\le\rho(y,x)$, cserével egyenlőség (szimmetria); $z:=x$, $y:=y$ esetén $0=\rho(x,x)\le 2\rho(x,y)$ adja a nemnegativitást.
- **Fordított háromszög-egyenlőtlenség.** $\rho(x,y)\ge|\rho(x,z)-\rho(y,z)|$: a háromszög-egyenlőtlenség kétszeri felírása.
- **Metrika $f\circ\rho$ alakban.** Az $f$ monoton növő, $f(x)=0\iff x=0$, szubadditív feltételei és a $\sqrt{x}$, $\frac{x}{1+x}$, $\ln(1+x)$ példák: [[concepts/analiii/metrikabol-uj-metrika]].
- **Visszahúzott metrika.** Ha $f:Y\to X$ bijekció (injekció is elég) és $(X,\rho)$ metrikus, akkor $\sigma(x,y)=\rho(f(x),f(y))$ metrika $Y$-on. Példák: $\varrho(x,y)=|f(x)-f(y)|$ minden szigorúan monoton $f:\mathbb R\to\mathbb R$-re (szokásos metrika: $f=\mathrm{id}$); $f=\operatorname{arctg}$-nál bármely két szám távolsága $<\pi$. Házi: $|e^x-e^y|$ ilyen, tehát metrika; $\frac{|x-y|}{1+|x-y|}$ és $\sqrt{|x-y|}$ is metrika; viszont $(x-y)^2$ (a háromszög-egyenlőtlenség $0,1,2$-n sérül), $|x^2-y^2|$ ($\rho(1,-1)=0$), $|x-2y|$ ($\rho(x,x)\ne0$) és a $x\le y$: $|x-y|$, $x>y$: $1+|x-y|$ alakú függvény (nem szimmetrikus) **nem** metrika.
- **Síkbeli körök távolsága.** $\rho(K_1,K_2)=T(K_1\,\triangle\,K_2)$ (a szimmetrikus differencia területe): a háromszög-egyenlőtlenség a $K_1\triangle K_3\subset(K_1\triangle K_2)\cup(K_2\triangle K_3)$ tartalmazásból jön.
- **Számsorozatok tere.** $\rho(x,y)=\sup_n\frac{|x_n-y_n|}{1+|x_n-y_n|}$ és $\rho(x,y)=\sum_{n}2^{-n}\frac{|x_n-y_n|}{1+|x_n-y_n|}$ metrika $\mathbb R^{\mathbb N}$-en: koordinátánként a $\frac{t}{1+t}$ trükk, aztán a szuprémum/korlátos sor megőrzi a háromszög-egyenlőtlenséget. A sorozatos változat **nem származik normából**: normából származó metrikára $\rho(\lambda x,\lambda y)=|\lambda|\rho(x,y)$ és eltolásinvariancia kell (megfordítva is igaz); itt $x\equiv1$ mellett $\rho(2x,0)=\tfrac23\ne 2\cdot\tfrac12=2\rho(x,0)$.
- **Két „lyukas" metrika $\mathbb N$-en.** $\rho(n,m)=2^{-\min(n,m)}$ ($n\neq m$) és $\rho(m,n)=\frac1{1+\min\{m,n\}}$ metrika (mindkettő *ultrametrika*: $\rho(m,n)\le\max\{\rho(m,k),\rho(k,n)\}$). Konvergens sorozataik a végül konstansak, de $(k)_k$ Cauchy-sorozat, ami nem konvergens: **nem teljesek** ([[concepts/analiii/cauchy-sorozat-es-teljes-ter]]).

- **Gömb nagyobb sugarú valódi részgömbbel (2. gyak 5. feladat).** $M=(-4,4]$, $\rho=|x-y|$: $K_4(4)=(0,4]$ és $K_3(2)=(-1,4]$, tehát $K_4(4)\subsetneq K_3(2)$ — a nagyobb sugarú gömb a kisebb sugarúnak valódi része, mert a tér a $4$-nél „le van vágva". Ez a jelenség normált térben nem fordulhat elő ([[concepts/analiii/normalt-vektorter]]).
- **Hamming-távolság mint diszkrét metrikák összege (2. gyak 2. feladat).** $\rho_H(x,y)=\sum_{k=1}^n\rho(x_k,y_k)$, ahol $\rho$ a diszkrét metrika a $\mathcal K$ karakterhalmazon; a háromszög-egyenlőtlenség pozíciónként a $\rho$-é, majd összegzés (gyak 2. lap megoldása szerint).
- **Metrika norma nélkül.** Minden norma metrikát ad ($\rho=\|x-y\|$), de a diszkrét metrika nem származtatható normából (2. gyak 7. feladat megjegyzése).

## Kapocs

- [[concepts/analiii/normalt-vektorter]] — a $d(x,y) = \|y-x\|$ képlet minden normából metrikát csinál
- [[concepts/analiii/konvergencia-metrikus-terben]] — a metrika első alkalmazása: gömbök és limesz
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — mikor „nincs lyuk" a térben
- [[concepts/analiii/kompakt-halmazok]] — kompaktság tetszőleges metrikus térben
- [[concepts/analiii/felmetrikus-ter]] — mi marad, ha a $\rho(x,y)=0 \Rightarrow x=y$ axiómát elejtjük
- [[concepts/analiii/metrikabol-uj-metrika]] — metrika transzformálása és leszűkítése
- [[concepts/analiii/metrikus-terek-szorzata]] — a szorzatmetrika; a $(\mathbb{K}^n,\rho_p)$ terek mint szorzatok
- [[concepts/analiii/ekvivalens-metrikak]] — mikor cserélhető fel két metrika büntetlenül
- [[concepts/analiii/topologikus-ter]] — a metrika elhagyása: csak a nyílt halmazok rendszere marad
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
