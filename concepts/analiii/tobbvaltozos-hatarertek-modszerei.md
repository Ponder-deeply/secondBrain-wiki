---
tags: [concept]
sources: [04_gyak_An_III_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Többváltozós határérték és folytonosság vizsgálata

Az $f:\mathbb{R}^n\to\mathbb{R}^m$ függvény $a$ pontbeli határértékének kiszámítására vagy cáfolására, illetve a folytonosság eldöntésére használt módszerek gyűjteménye, a gyakorlatokon használt sorrendben.

## Tartalom

### Döntési sorrend

Cél: eldönteni, hogy $\lim_{x\to a}f(x)$ létezik-e, és mennyi. Folytonosságnál ugyanez a kérdés $a$-ban, és az $f(a)$ értékkel kell egyeznie.

1. **Behelyettesítés.** Ha $f$ az $a$-ban folytonos (polinom, racionális törtfüggvény nem nulla nevezővel, folytonos függvények kompozíciója), a határérték $f(a)$. Pl. $\lim_{(6,3)}xy\cos(x-2y)=18$ ([[concepts/analiii/atviteli-elv-metrikus-terben]]).
2. **Algebrai átalakítás.** Ha $\tfrac00$ alakú, de az egyváltozós trükkök működnek: konjugálttal bővítés ($\frac{x^2+y^2}{\sqrt{x^2+y^2+1}-1}=\sqrt{x^2+y^2+1}+1\to2$), egyszerűsítés.
3. **Sejtés: két út.** Közelítsük a pontot a tengelyek, az átló, majd az $y=mx$ egyenesek, és görbék ($y=x^2$, $x=y^2$) mentén. Ha két úton különböző értéket kapunk, **a határérték nem létezik** (az átviteli elv szerint). Ha mindegyik ugyanazt adja, az csak sejtés.
4. **Bizonyítás: közrefogás.** $|f(x)-A|\le K\cdot\|x-a\|^p\to0$ ($p>0$) alakú becslés, jellemzően az $|xy|\le\tfrac12(x^2+y^2)$, $|x|,|y|\le\|(x,y)\|$, $\tfrac{x^2}{x^2+y^2}\le1$ egyenlőtlenségekkel. Ez egyben az $\varepsilon$–$\delta$ definíció konkrét kitöltése: $\dfrac{|xy|}{\sqrt{x^2+y^2}}\le\tfrac12\|(x,y)\|_2<\varepsilon$, ha $\delta=2\varepsilon$.
5. **Polárkoordináta.** $x=r\cos\varphi$, $y=r\sin\varphi$: a határérték létezik és $A$, ha $|f-A|\le g(r)\to0$ **$\varphi$-től függetlenül** (nem elég, hogy minden rögzített $\varphi$-re $\to A$ — az $x^2y/(x^4+y^2)$ ellenpélda). Jó $\ln$, $\exp$, hatványkitevős kifejezéseknél: $r^2\ln r^2\to0$; $(x^2+y^2)^{x^2y^2}=\exp(x^2y^2\ln(x^2+y^2))\to1$.

### Az út megválasztása (gyak 4. lap)

- **Azonos fokszám**: az $y=mx$ egyenes mentén az érték csak $m$-től függ (pl. $\tfrac{(x+y)^2}{x^2+y^2}\to\tfrac{(1+m)^2}{1+m^2}$, $\tfrac{x^4}{(x^2+y^2)^2}\to\tfrac1{(1+m^2)^2}$) — két különböző $m$ két különböző határértéket ad, a határérték nem létezik.
- **Nem homogén nevező** ($x^4+y^2$): az $y=mx^2$ parabolák mentén $\tfrac{x^2y}{x^4+y^2}=\tfrac m{1+m^2}$ konstans; az $y=mx$ egyenesek ($m\ne0$) és a tengelyek mentén viszont $0$ — innen az „egyenesenként folytonos, mégsem folytonos" jelenség.
- **Fokszám-összehasonlítás**: $\dfrac{xy}{\sqrt{x^2+y^2}}$ számlálója másodfokú, a nevező elsőfokú nagyságrendű, ezért $0$-t várunk; közrefogással $|xy|/\sqrt{x^2+y^2}\le\tfrac12\sqrt{x^2+y^2}$.
- **Konjugálttal bővítés** a gyökös alakoknál; a $|f-A|\to0$ alakot kell közrefogni.

### Mikor melyik

- **Homogén fokszámok.** Ha a számláló fokszáma nagyobb, mint a nevezőé (pl. $\frac{x^3+y^4}{x^2+y^2}$, $\frac{x^2y^3}{|x|+|y|}$), jellemzően $0$ a határérték, közrefogással. Azonos fokszámnál ($\frac{x^2}{x^2+y^2}$, $\frac{xy}{x^2+y^2}$, $\frac{(x+y)^2}{x^2+y^2}$) az irány számít: nincs határérték.
- **Nem egyforma fokszám a nevezőben** ($x^4+y^2$, $x^2y^2+(x-y)^2$): az egyenesek félrevezetnek; görbék kellenek ($y=x^2$; $y=x$ a másodikra, ahol $f\equiv1$).
- **Kétváltozós határérték vs. iterált határérték.** $\lim_{x\to0}\lim_{y\to0}f$ és $\lim_{y\to0}\lim_{x\to0}f$ létezhet és egyezhet is, miközben $\nexists\lim_{(0,0)}f$ ($\frac{x^2y^2}{x^2y^2+(x-y)^2}$); fordítva a kétváltozós határérték létezhet, miközben az iterált nem ($(x+y)\sin\frac1x\sin\frac1y$). Ha a kétváltozós határérték és egy iterált határérték is létezik, akkor egyeznek; így két különböző iterált érték cáfolja a kétváltozós határérték létezését, de egyezésük semmit sem bizonyít.
- **Több változó.** $\mathbb{R}^3$-ban is ugyanez: $\frac{xy+yz+zx}{x^2+y^2+z^2}$ nem konvergál az origóban ($x$-tengely: $0$; $x=y=z$: $1$).

### A folytonosság ellenőrző listája

Az $f$ ágankénti függvény folytonosságának vizsgálata az $a$ pontban:

1. A képletes ágon az $f$ folytonos (műveletek, kompozíció), kivéve az osztópontokban.
2. A kritikus pontban: $f(a)=\lim_{x\to a}f$? Számítsuk ki a határértéket a fenti módszerekkel, és hasonlítsuk $f(a)$-hoz (pl. ha $\lim=0$, de $f(0,0):=1$, akkor nem folytonos).
3. A koordinátánkénti folytonosság (rögzített $y_0$ mellett $x\mapsto f(x,y_0)$ és fordítva) **szükséges, de nem elégséges**: $\frac{xy}{x^2+y^2}$ minden szeletén folytonos, de az $y=x$ mentén $\tfrac12\ne0$ ([[concepts/analiii/folytonossag-metrikus-terben]]).
4. Az egyenesek menti folytonosság sem elég: $\frac{x^2y}{x^4+y^2}$ minden origón átmenő egyenesen folytonos, az $y=x^2$ parabolán azonban a határérték $\tfrac12$.

### Példák (összefoglaló)

| Függvény (az origóban) | Eredmény | Indok |
|---|---|---|
| $\frac{xy}{\sqrt{x^2+y^2}}$ | $0$ | $\le\tfrac12 r$ |
| $\frac{x^2+y^2}{\sqrt{x^2+y^2+1}-1}$ | $2$ | konjugált |
| $\frac{x^2y^3}{2x^2+y^2}$ | $0$ | $\le|y|^3/2$ |
| $\frac{xy^4}{x^2+3y^2}$ | $0$ | $\le|x|y^2/3$ |
| $(x^2+y^2)\ln(x^2+y^2)$ | $0$ | $r^2\ln r^2$ |
| $\frac{x^4y}{(x^2+y^2)^2}$ | $0$ | $\le|y|$ |
| $\frac{x^4}{(x^2+y^2)^2}$ | nincs | $1$ ($y=0$) és $0$ ($x=0$) |
| $\frac{(x+y)^2}{x^2+y^2}$ | nincs | $1$ és $2$ |
| $\frac{x^2y}{x^4+y^2}$ | nincs | $0$ (egyenes), $\tfrac12$ ($y=x^2$) |
| $\frac{x^2y^2}{x^2y^2+(x-y)^2}$ | nincs | $y=x$: $1$; tengelyek: $0$ |

További kidolgozott feladatok: [[concepts/analiii/fuggvenyhatarertek-metrikus-terben]], [[concepts/analiii/folytonossag-metrikus-terben]].

## Kapocs

- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a cáfolás elméleti alapja: két sorozat, két határérték
- [[concepts/analiii/fuggvenyhatarertek-metrikus-terben]] — a határérték definíciója és megoldott példák
- [[concepts/analiii/folytonossag-metrikus-terben]] — folytonosság és feladatai
- [[concepts/analiii/koordinatafuggvenyek-folytonossaga]] — vektorértékű eset koordinátánként
- [[concepts/analiii/polarkoordinatas-helyettesites]] — a polárkoordináta-helyettesítés a többszörös integrálnál
- [[concepts/analiii/frechet-derivalt]] — a differenciálhatóságnál ugyanezek a becslések kellenek
