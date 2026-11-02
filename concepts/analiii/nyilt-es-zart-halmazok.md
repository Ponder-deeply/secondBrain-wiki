---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, An_III_Gyak_2022_tavasz.pdf, gyakorlat.pdf, ElozetesMegajanlottVizsgaTetelek1.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, 03_gyak_An_III_2022_tavasz.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Nyílt és zárt halmazok

A nyíltság és a zártság a metrikus tér *topológiája*: az a szerkezet, amely eldönti, mely halmazok „tartalmazzák a saját szélüket". Nyíltság és zártság nem egymást kizáró, és nem is kimerítő tulajdonságok.

## Tartalom

Legyen $(M,d)$ metrikus tér, $H \subset M$.

### Definíciók

- $H$ **nyílt**, ha minden pontja belső pont.
- $H$ **zárt**, ha az alábbi egyenértékű feltételek valamelyike teljesül:
  - a komplementere nyílt;
  - részhalmaza a határa, azaz $\partial H \subset H$;
  - $H = (\operatorname{int} H) \cup (\partial H)$;
  - bármely $H$-beli konvergens pontsorozat limesze is $H$-ban van.

### Példák

- Az egész tér és az üres halmaz **egyszerre nyílt és zárt**.
- Az egypontú halmazok zártak; $\mathbb{R}^p$-ben nem nyíltak.
- A nyílt gömbök nyílt halmazok, a zárt gömbök zárt halmazok. $\mathbb{R}^p$-ben a nyílt gömbök nem zártak, a zárt gömbök nem nyíltak.
- $\mathbb{R}^p$-ben az $(a_1,b_1) \times \dots \times (a_p,b_p)$ nyílt téglák nyíltak, de nem zártak; az $[a_1,b_1] \times \dots \times [a_p,b_p]$ zárt téglák zártak, de nem nyíltak.

### Műveleti tulajdonságok

**Tétel.**

- Egy halmaz akkor és csak akkor zárt, ha az elemeiből képzett konvergens sorozatok limeszei is elemei.
- Nyílt halmazok **tetszőleges** rendszerének uniója nyílt.
- **Véges** sok nyílt halmaz metszete nyílt.
- Zárt halmazok **tetszőleges** rendszerének metszete zárt.
- **Véges** sok zárt halmaz uniója zárt.

A végességi megszorítás lényeges: $\mathbb{R}^p$-ben a $B(0,1/n)$ nyílt gömbök metszete a $\{0\}$ egypontú halmaz, ami nem nyílt; a $\overline{B}(0,1-1/n)$ zárt gömbök uniója az egységgömb belseje, ami nem zárt.

### A topológia metrikafüggése

Nemcsak a konvergencia, hanem maga a topológia is függ a metrikától. A $C[0,1]$ térben az

$$f_n(x) = \begin{cases} 1 - nx & x < 1/n \\ 0 & x \geq 1/n \end{cases}$$

sorozatra $\|f_n\|_1 = \int_0^1 |f_n| = \frac{1}{2n} \to 0$, tehát $L^1$-ben a konstans $0$-hoz tart; $L^\infty$-ben viszont $\|f_n\|_\infty = 1$, tehát nem tart hozzá. Ennek megfelelően az $\{f_1, f_2, \dots\}$ halmaz $L^\infty$-ben zárt (nincs torlódási pontja), $L^1$-ben viszont nem az (a konstans $0$ torlódási pontja, de nem eleme).

### Feladatok

*Forrás: An_III_Gyak_2022_tavasz.pdf 3. gyakorlat 2.; gyakorlat.pdf „Metrikus terek" 14, 21.*

- **A nyílt gömb nyílt, a zárt gömb zárt.** Ha $x\in K_r(a)$, akkor $K_{r-\|x-a\|}(x)\subset K_r(a)$ a háromszög-egyenlőtlenség miatt. Ha $\|y-a\|>r$, akkor $K_{\|y-a\|-r}(y)$ nem metszi $\overline K_r(a)$-t, így a komplementer nyílt.
- **Zártság sorozatokkal.** $A$ zárt $\iff$ minden $x:\mathbb N\to A$ konvergens sorozat limesze $A$-ban van. ($\Rightarrow$: a limes torlódási pont vagy a sorozat tagja; $\Leftarrow$: ha $a\in A'$, a $K_{1/n}(a)\setminus\{a\}$ pontjaiból sorozat készíthető.)
- **Altér nyílt halmazai.** $(A,\rho|_{A\times A})$ nyílt halmazai pontosan az $U\cap A$ alakúak, $U$ nyílt $X$-ben: mert $K^A_r(a)=K_r(a)\cap A$, és az uniók/metszetek ezt örökítik.

- **Pontosított bizonyítás (3. gyak 2. feladat).** Nyílt gömb: $b\in K_r(a)$ esetén az $s$ sugár $0<s<r-\|a-b\|$ (pozitív, mert $\|a-b\|<r$); $x\in K_s(b)$-re $\|x-a\|\le\|x-b\|+\|a-b\|<s+\|a-b\|<r$. Zárt gömb: $b\notin\overline K_r(a)$ esetén $0<s<\|a-b\|-r$; $x\in K_s(b)$-re $\|a-b\|\le\|x-a\|+\|x-b\|<\|x-a\|+\|a-b\|-r$, így $\|x-a\|>r$, azaz $K_s(b)\cap\overline K_r(a)=\emptyset$ (gyak 3. lap megoldása szerint).
- **Definíciók (3. gyak emlékeztető).** $a\in A'\iff$ minden $K(a)$-ra $K(a)\cap A$ végtelen $\iff(K(a)\setminus\{a\})\cap A\ne\emptyset$; $a\in\operatorname{int}A\iff\exists K(a)\subset A$ (és $\operatorname{int}\emptyset=\emptyset$).

## Kapocs

- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a belső pont és a határ fogalma, amire a definíció épül
- [[concepts/analiii/konvergencia-metrikus-terben]] — a zártság sorozatos jellemzése
- [[concepts/analiii/ekvivalens-normak]] — véges dimenzióban a topológia normafüggetlen
- [[concepts/analiii/kompakt-halmazok]] — minden kompakt halmaz korlátos és zárt
- [[concepts/analiii/osszefuggo-halmazok]] — $\mathbb{R}^p$-ben csak $\emptyset$ és az egész tér nyílt és zárt egyszerre
- [[concepts/analiii/topologikus-ter]] — a műveleti tulajdonságok axiómává emelése
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
