---
tags: [concept]
sources: [SimonP-Anal2.pdf, 04_gyak_An_III_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf]
references: ["Simon Péter: Analízis II., 2.1. xi)–xviii) megjegyzések"]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Függvényhatárérték metrikus terekben

Az $f \in X \to Y$ függvénynek az $a$ torlódási pontban vett határértéke az az egyértelmű $A \in Y$, amelynek minden környezetét felveszi $f$ az $a$ egy kipontozott környezetén. A fogalom lokális: sem $f(a)$, sem az $a \in D_f$ kérdés nem számít.

## Tartalom

### Definíció

Legyenek $(X,\rho)$, $(Y,\sigma)$ metrikus terek, $f \in X \to Y$ és $a \in D_f'$ (az értelmezési tartomány **torlódási pontja**). Azt mondjuk, hogy $f$-nek az $a$ helyen van **határértéke**, ha létezik olyan $A \in Y$, hogy minden $K(A) \subset Y$ környezethez van olyan $k(a) \subset X$ környezet, amellyel

$$f\bigl[\bigl(k(a)\setminus\{a\}\bigr) \cap D_f\bigr] \subset K(A),$$

azaz $f(x) \in K(A)$ minden $a \ne x \in k(a) \cap D_f$ esetén.

**Ekvivalens megfogalmazás (gyak 4. lap).** $\mathbb{R}^2\to\mathbb{R}$ esetben a határértéket a folytonos kiterjesztéssel is definiálhatjuk: $\lim_{(a_1,a_2)}f=A$, ha az $\tilde f=f$ ($D_f\setminus\{(a_1,a_2)\}$-n), $\tilde f(a_1,a_2)=A$ függvény folytonos $(a_1,a_2)$-ben. Ezzel egyenértékű: $\forall\varepsilon>0\;\exists\delta>0$: $0<\|(x,y)-(a_1,a_2)\|<\delta\Rightarrow|f(x,y)-A|<\varepsilon$. Hasznos fordulat: $\lim_a f=A\iff\lim_a(f-A)=0\iff\lim_a|f-A|=0$.

### Az egyértelműség

**Állítás.** Ilyen $A$ legfeljebb egy van.

*Bizonyítás.* Ha $B \ne A$ is teljesítené a feltételt, akkor $0 < r < \sigma(A,B)/2$ mellett $K(A) := K_r(A)$ és $K(B) := K_r(B)$ diszjunktak: $y \in K_r(A)$ esetén
$$\sigma(y,B) \ge \sigma(A,B) - \sigma(y,A) > \sigma(A,B) - r > r,$$
tehát $y \notin K_r(B)$. Viszont a $k(a) \cap k^*(a)$ környezet pontjaiban $f(x)$-nek egyszerre kellene $K(A)$-ban és $K(B)$-ben lennie. $\blacksquare$

Az így egyértelműen létező elemet $f$ **$a$-beli határértékének** nevezzük:

$$\lim_a f := \lim_{x\to a} f(x) := A, \qquad\text{illetve}\qquad f(x) \to A \quad (x \to a).$$

### Lokalitás

Ha $f, g \in X \to Y$ megegyeznek $a$ egy kipontozott környezetén — azaz alkalmas $k(a)$-val
$$\emptyset \ne D := \bigl(k(a)\setminus\{a\}\bigr)\cap D_f = \bigl(k(a)\setminus\{a\}\bigr)\cap D_g$$
és $f = g$ a $D$-n —, akkor $a \in D_f' \cap D_g'$ esetén $\lim_a f$ pontosan akkor létezik, ha $\lim_a g$ létezik, és ilyenkor egyenlők. A határérték tehát **lokális tulajdonság**: az $a \in D_f$ kérdés és az $f(a)$ helyettesítési érték szempontjából érdektelen.

### Kapcsolat a folytonossággal

- Ha $a \in D_f' \cap D_f$, akkor $f \in C\{a\}$ ekvivalens azzal, hogy $\lim_a f$ létezik és $\lim_a f = f(a)$.
- Ha $a \in D_f \setminus D_f'$ (izolált pont), akkor $f$ automatikusan folytonos $a$-ban, határértékről viszont nem beszélünk.

### Műveletek

Legyen $(Y,\|\cdot\|)$ normált tér, $\sigma(y,z) = \|y-z\|$, $a \in (D_f\cap D_g)'$, és létezzenek az $A := \lim_a f$, $B := \lim_a g$ határértékek. Ekkor minden $\lambda \in \mathbb{K}$ mellett

$$\lim_a (f + \lambda g) = A + \lambda B,$$

és $Y := \mathbb{K}$ esetén

$$\lim_a (fg) = AB, \qquad \lim_a \frac{f}{g} = \frac{A}{B} \quad (B \ne 0).$$

Mindez az [[concepts/analiii/atviteli-elv-metrikus-terben|átviteli elv]] és a sorozatokra vonatkozó műveleti szabályok egyszerű következménye. Többváltozós vektorfüggvényekre — $h, l \in \mathbb{K}^s \to \mathbb{K}$, $f, g \in \mathbb{K}^s \to \mathbb{K}^m$ — ugyanezt az alakot kapjuk.

### Koordinátánként

Szorzattérbe képező $f = (f_1,f_2) \in X \to Y\times Z$ függvényre: $\lim_a f$ akkor és csak akkor létezik, ha léteznek az $A_1 := \lim_a f_1$ és $A_2 := \lim_a f_2$ határértékek, és ekkor $\lim_a f = (A_1,A_2)$. Speciálisan $f = (f_1,\dots,f_m) \in \mathbb{K}^s \to \mathbb{K}^m$ esetén

$$\lim_a f = \bigl(\lim_a f_1, \dots, \lim_a f_m\bigr),$$

amint mind az $m$ koordinátahatárérték létezik. Ez a [[concepts/analiii/koordinatafuggvenyek-folytonossaga|2.9. Tétel]] határértékes párja.

### Feladatok

Az eszköztár (egyenesek/görbék menti vizsgálat, közrefogás, polárkoordináta, konjugált): [[concepts/analiii/tobbvaltozos-hatarertek-modszerei]]. Itt a megoldott kérdések.

- **Behelyettesítés.** Ha a függvény folytonos a pontban, a határérték az értéke: $\lim_{(1,2)}\dfrac{x^2+xy}{x+y^2}=\tfrac35$; $\lim_{(6,3)}xy\cos(x-2y)=18\cos0=18$ (az átviteli elvvel: $x_n-2y_n\to0$, $\cos$ folytonos).
- **Nem létezik** (két út, két érték; gyak 4. lap, 6(b), 7(a) feladat: $\tfrac{x^4}{(x^2+y^2)^2}$ az $y=mx$ mentén $\tfrac1{(1+m^2)^2}$, azaz $1$ és $\tfrac14$): $\dfrac{x^2}{x^2+y^2}$ ($1$ és $0$), $\dfrac{(x+y)^2}{x^2+y^2}$ ($y=0$: $1$; $y=x$: $2$), $\dfrac{xy}{x^2+y^2}$ ($0$ és $\tfrac12$), $\dfrac{(x+y)^3}{5x^3+y^3}$ ($\tfrac15$ és $1$), $\dfrac{xy+yz+zx}{x^2+y^2+z^2}$ az origóban ($x$-tengelyen $0$, $x=y=z$ mentén $1$).
- **Létezik, közrefogással.** $\dfrac{xy}{\sqrt{x^2+y^2}}\to0$, mert $|xy|\le\tfrac12(x^2+y^2)$, így $|f|\le\tfrac12\|(x,y)\|_2$; $\varepsilon$–$\delta$: $\delta=2\varepsilon$. $\dfrac{x^3+y^4}{x^2+y^2}\to0$ ($\le r+r^2$); $\dfrac{x^2y^3}{|x|+|y|}\to0$ ($\le r^4$); $\dfrac{xy^4}{x^2+3y^2}\to0$ ($\tfrac{y^4}{x^2+3y^2}\le\tfrac{y^2}{3}$).
- **Konjugálttal.** $\dfrac{x^2+y^2}{\sqrt{x^2+y^2+1}-1}=\sqrt{x^2+y^2+1}+1\to2$. A gyak 4. lap megoldása a $|f-2|\to0$ alakot használja: $\bigl|\sqrt{x^2+y^2+1}+1-2\bigr|=\sqrt{x^2+y^2+1}-1=\dfrac{x^2+y^2}{\sqrt{x^2+y^2+1}+1}\le\dfrac{x^2+y^2}{\sqrt{x^2+y^2}}=\|(x,y)\|<\varepsilon$, tehát $\delta=\varepsilon$ ($\delta\in(0,\varepsilon)$) jó; a $\tfrac{xy}{\sqrt{x^2+y^2}}$ esetében $\delta\in(0,2\varepsilon)$ (gyak 4. lap, 5. feladat).
- **Polárkoordinátával.** $(x^2+y^2)\ln(x^2+y^2)=r^2\ln r^2\to0$ ($t\ln t\to0$); $(x^2+y^2)^{x^2y^2}=e^{x^2y^2\ln(x^2+y^2)}\to e^0=1$, mert $x^2y^2\ln(x^2+y^2)$ abszolút értéke $\le r^4|\ln r^2|\to0$.
- **Iterált és kétváltozós határérték.** $f=\dfrac{x^2y^2}{x^2y^2+(x-y)^2}$: $\lim_{x\to0}\lim_{y\to0}f=0$ és $\lim_{y\to0}\lim_{x\to0}f=0$ (a belső határérték $0$, ill. $-0/y^2$ alakból $0$), de az $y=x$ mentén $f\equiv1$, tehát $\nexists\lim_{(0,0)}f$. Hasonlóan $f=\dfrac{x-y}{x+y}$-ra: az iterált határértékek léteznek, de $1$ és $-1$, különbözőek, ezért $\nexists\lim_{(0,0)}f$. Fordított eset: $f=(x+y)\sin\tfrac1x\sin\tfrac1y$: $\lim_{(0,0)}f=0$ ($|f|\le|x|+|y|$), de egyik iterált határérték sem létezik (rögzített $x$-nél $y\to0$-ra $\sin\tfrac1y$ nem konvergál). Tehát egyik irány sem következik a másikból.

## Kapocs

- [[concepts/analiii/folytonossag-metrikus-terben]] — torlódási pontban a folytonosság a határérték felvételét jelenti
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a határérték sorozatos jellemzése és a nemlétezés bizonyítása
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a torlódási és az izolált pont fogalma
- [[concepts/analiii/koordinatafuggvenyek-folytonossaga]] — a koordinátánkénti felbontás folytonosságra
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
