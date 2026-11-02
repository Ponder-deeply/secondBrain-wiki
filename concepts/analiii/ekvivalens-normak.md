---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 02_ea_An3_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, gyakorlat.pdf, ElozetesMegajanlottVizsgaTetelek1.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Ekvivalens normák

Két norma ekvivalens, ha kölcsönösen becsülhetők egymással konstans szorzóval — ekkor ugyanazokat a sorozatokat találják konvergensnek és ugyanazt a topológiát adják. Véges dimenzióban **minden** norma ekvivalens, végtelen dimenzióban általában nem.

## Tartalom

### Definíció

A $\|\cdot\|$ és $\|\cdot\|'$ normák **ekvivalensek**, ha léteznek olyan $c_1, c_2 > 0$ számok, hogy bármely $x \in \mathbb{R}^p$ vektorra

$$c_1 \|x\| \leq \|x\|' \leq c_2 \|x\|.$$

### Példa — az $L^1$, $L^2$, $L^\infty$ normák

$$\frac{1}{\sqrt{p}}\,|x| \leq \|x\|_\infty \leq \|x\|_1 \leq \sqrt{p}\cdot|x|.$$

Az első egyenlőtlenség triviális: $\frac{1}{\sqrt p}|x| = \sqrt{\text{az } |x_i|^2 \text{ átlaga}} \leq \sqrt{\max |x_i|^2} = \|x\|_\infty$. A harmadik a Cauchy–Schwarz-egyenlőtlenség speciális esete:

$$\|x\|_1 = 1\cdot|x_1| + \dots + 1\cdot|x_p| \leq \sqrt{p\cdot 1^2}\cdot\sqrt{|x_1|^2+\dots+|x_p|^2} = \sqrt p\,|x|.$$

### Végtelen dimenzióban nem áll fenn

- $C[0,1]$-en $\|\cdot\|_1$ és $\|\cdot\|_\infty$ **nem** ekvivalensek.
- Ugyanezen a téren $\|f\|_{(2)} = \int_0^1 x|f(x)|\,\mathrm{d}x$ és $\|f\|_{(3)} = \int_0^1 (1-x)|f(x)|\,\mathrm{d}x$ két olyan norma, amelyek aránya sem alulról, sem felülről nem korlátos.

**Példa — a konvergencia normafüggő.** Legyen $f_k(x) := x^k$ ($x\in[0,1]$, $k\in\mathbb{N}$) a $C[0,1]$ lineáris tér eleme. Ekkor $(f_k)$ konvergens a $\|\cdot\|_1$ normában (a $0$ függvényhez, mert $\|f_k\|_1 = \int_0^1 x^k\,\mathrm dx = \frac1{k+1}\to 0$), de **divergens** a $\|\cdot\|_\infty$ normában: pontonként $f_k(x)\to 0$ minden $x\in[0,1)$-re, de $f_k(1)=1$ minden $k$-ra, így egyetlen folytonos limeszfüggvény sem illeszkedne mindkét feltételhez. Ez éppen azt mutatja, hogy $\|\cdot\|_1 \not\sim \|\cdot\|_\infty$ ezen a téren: ekvivalens normák esetén ugyanis egy sorozat vagy mindkettőben konvergens (ugyanazzal a limesszel), vagy egyikben sem — ez közvetlenül következik az ekvivalencia definíciójából.

### A normák ekvivalenciájának tétele

**Tétel.** $\mathbb{R}^p$-ben bármely $\|\cdot\|$ norma ekvivalens az $|\cdot|$ euklideszi normával: léteznek $c_1, c_2 > 0$, hogy minden $x \in \mathbb{R}^p$-re $c_1|x| \leq \|x\| \leq c_2|x|$.

**Bizonyítás.** *Felső becslés.* Legyenek $e_1,\dots,e_p$ a koordináta-egységvektorok. A háromszög-egyenlőtlenség és a homogenitás szerint

$$\|x\| = \|x_1e_1 + \dots + x_pe_p\| \leq |x_1|\|e_1\| + \dots + |x_p|\|e_p\| \leq \bigl(\|e_1\|+\dots+\|e_p\|\bigr)\cdot|x|,$$

tehát $c_2 = \|e_1\|+\dots+\|e_p\|$ megfelelő.

*Alsó becslés (indirekt).* Ha nincs ilyen $c_1$, akkor minden $n$-re $c_1 = \frac1n$ sem jó: van olyan $x_n$, hogy $\|x_n\| < \frac1n |x_n|$. Ez az $x_n$ nem lehet a nullvektor, és skálázással feltehető $|x_n| = 1$. A Bolzano–Weierstrass-tétel szerint a korlátos $(x_n)$-nek van konvergens $(x_{n_k})$ részsorozata; legyen $y = \lim x_{n_k}$. A koordinátánkénti konvergencia miatt $|y| = \lim |x_{n_k}| = 1$, tehát $y \neq 0$. A már bizonyított felső becslés és a rendőrelv szerint $\|x_{n_k} - y\| \leq c_2|x_{n_k}-y| \to 0$. Ekkor viszont

$$0 < \|y\| \leq \|x_{n_k}\| + \|y - x_{n_k}\| < \frac{1}{n_k} + c_2|y - x_{n_k}| \to 0,$$

ellentmondás. $\blacksquare$

### Következmény

Véges dimenziós vektorterekben

- a pontsorozatok **konvergenciája normafüggetlen**: bármelyik normát használjuk, ugyanazok a sorozatok konvergensek, és ugyanaz a limeszük;
- a **topológia normafüggetlen**: ugyanazok a halmazok nyíltak és zártak, ugyanaz egy halmaz belseje, külseje, határa.

Ez az a szerkezeti tény, ami miatt $\mathbb{R}^p$-ben soha nem kell megmondani, melyik normát használjuk.

**Tyihonov-tétel.** A fenti tétel általánosabb alakja: tetszőleges véges dimenziós $X$ lineáris téren bármely két norma ekvivalens egymással. Mivel minden $n$-dimenziós $X$ tér algebrailag izomorf $\mathbb{R}^n$-nel, ez visszavezethető a fenti, $\mathbb{R}^p$-re szóló tételre. A [[concepts/analiii/bolzano-weierstrass-kivalasztasi-tetel|Bolzano–Weierstrass-féle kiválasztási tétel]] éppen ebből következően igaz minden véges dimenziós normált térben, és éppen ezért nem automatikus végtelen dimenzióban.

### Feladatok

*Forrás: gyakorlat.pdf „Metrikus terek" 18–19, 23–24; An_III_Gyak_2022_tavasz.pdf 3. gyakorlat.*

- **Véges dimenzióban minden norma ekvivalens** (bizonyításvázlat). Bázis $\{e_i\}$, $x=\sum\lambda_ie_i$, $\|x\|:=\max|\lambda_i|$. Egy másik $\|\cdot\|^*$-ra $\|x\|^*\le\sum|\lambda_i|\|e_i\|^*\le M\|x\|$, $M=\sum\|e_i\|^*$. Így $g(\lambda)=\|\sum\lambda_ie_i\|^*$ folytonos $(\mathbb R^n,\|\cdot\|_\infty)$-n; az egységgömb felülete (zárt, korlátos, tehát kompakt) rajta felveszi a minimumát $m$-et, $m>0$, mert a felület nem tartalmazza a nullvektort; $x/\|x\|$-re $\|x\|^*\ge m\|x\|$.
- **Véges dimenziós normált térben egy halmaz akkor és csak akkor kompakt, ha korlátos és zárt.** A normák ekvivalenciája miatt az izomorfia $\mathbb R^n$-nel nem változtat a korlátosságon, zártságon, kompaktságon; így a Heine–Borel-tétel ([[concepts/analiii/heine-borel-tetel]]) átvihető.
- **Legközelebbi elem véges dimenziós altérben.** $L\le X$ véges dimenziós altér, $x\in X$: az $L\cap\overline K_{\|x\|}(x)$ halmaz zárt és korlátos, tehát kompakt, és tartalmazza $0$-t; a folytonos $y\mapsto\|x-y\|$ ezen felveszi a minimumát, ami az $L$-beli legjobb közelítés.
- **Végtelen dimenzióban nem ekvivalens normák:** a $C[0,1]$-ben a $\|\cdot\|_1$-ben korlátos, $\|\cdot\|_\infty$-ben nem korlátos háromszögfüggvény-sorozat (lásd [[concepts/analiii/normalt-vektorter]] Feladatok) és az $x^k$-sorozat ([[concepts/analiii/konvergencia-metrikus-terben]]).

## Kapocs

- [[concepts/analiii/normalt-vektorter]] — a norma fogalma és az $L^q$-normák
- [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] — a becslésekhez használt Cauchy–Schwarz
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a metrikafüggő topológia, amit ez a tétel véges dimenzióban egyértelműsít
- [[concepts/analiii/cantor-metszettetel]] — a bizonyításban használt Bolzano–Weierstrass-tétel
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a normaekvivalencia miatt a Cauchy-tulajdonság is normafüggetlen
- [[concepts/analiii/ekvivalens-metrikak]] — ugyanez a fogalom metrikákra, normastruktúra nélkül
- [[concepts/analiii/bolzano-weierstrass-kivalasztasi-tetel]] — a Tyihonov-tétel folyománya: véges dimenzióban minden korlátos sorozatnak van konvergens részsorozata, végtelen dimenzióban általában nem
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
