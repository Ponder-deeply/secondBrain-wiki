---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 01_gyak_An_III_2024_25_Ifelev.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Gamma-függvény

Az Euler-féle $\Gamma(s) = \int_0^\infty x^{s-1} e^{-x}\,\mathrm{d}x$ paraméteres improprius integrál, amely a faktoriálist terjeszti ki a pozitív valós számokra, és a paraméteres integrálok elméletének mintapéldája.

## Tartalom

### Definíció és alaptulajdonságok

**Definíció (Euler-féle Gamma-függvény).**

$$\Gamma(s) = \int_{x=0}^{\infty} x^{s-1} e^{-x}\,\mathrm{d}x \qquad (s > 0).$$

Az integrál improprius mindkét végén: $0$-ban az $x^{s-1}$ tényező robbanhat ($s < 1$ esetén), a végtelenben viszont az $e^{-x}$ minden hatványt legyőz, ezért a konvergencia $s > 0$-ra fennáll.

Alaptulajdonságok:

- $\Gamma(1) = \int_0^\infty e^{-x}\,\mathrm{d}x = 1$;
- parciális integrálással $\Gamma(s+1) = s\cdot\Gamma(s)$;
- innen indukcióval $\Gamma(n+1) = n!$ minden $n$ természetes számra.

A funkcionálegyenlet az, ami a $\Gamma$-t a faktoriális „természetes" folytatásává teszi: az $n! = n\cdot (n-1)!$ rekurzió pontos analogonja.

### Folytonosság és differenciálhatóság

A természetes kérdések: folytonos-e a Gamma-függvény, differenciálható-e, és igaz-e, hogy a deriválás bevihető az integráljel alá:

$$\Gamma'(s) \overset{?}{=} \int_{x=0}^{\infty} \frac{\partial}{\partial s}\bigl(x^{s-1}e^{-x}\bigr)\,\mathrm{d}x = \int_{x=0}^{\infty} x^{s-1}e^{-x}\log x\,\mathrm{d}x.$$

**Következmény.** A Gamma-függvény differenciálható, és

$$\Gamma'(s) = \int_0^\infty x^{s-1} e^{-x} \log x\,\mathrm{d}x.$$

**Bizonyítás.** Legyen $f(s,x) = x^{s-1}e^{-x}$; ekkor $\frac{\partial}{\partial s} f(s,x) = x^{s-1}e^{-x}\log x$. Az egész $(0,\infty)$ paramétertartományon nincs egyetlen domináns függvény, ezért **lokalizálunk**: szűkítsük le a paramétert egy tetszőleges $(c,d)$ intervallumra, ahol $0 < c < d < \infty$, és legyen

$$g(x) = \begin{cases} x^{c-1}\bigl|\log x\bigr| & \text{ha } 0 < x \leqslant 1,\\ x^{d-1} e^{-x}\log x & \text{ha } 1 < x.\end{cases}$$

Ha $c \leqslant s \leqslant d$, akkor $g(x)$ dominálja $x^{s-1}e^{-x}\log x$-et: a $(0,1]$ szakaszon $x^{s-1} \leqslant x^{c-1}$ és $e^{-x} \leqslant 1$, az $[1,\infty)$ félegyenesen pedig $x^{s-1} \leqslant x^{d-1}$. A $g$ integrálja $(0,1]$-en és $[1,\infty)$-en is véges. A paraméteres integrál differenciálásáról szóló tétel improprius része tehát alkalmazható: a $(c,d)$ intervallumon $\Gamma$ differenciálható, és a formula igaz.

Végül a $(c,d)$ intervallumok uniója az egész $(0,\infty)$, és a differenciálhatóság **lokális** tulajdonság, ezért az állítás minden $s > 0$-ban érvényes.

Ugyanez az érvelés — csak $f$-re és nem a deriváltjára — adja a $\Gamma$ folytonosságát is.

### A lokalizálás mint minta

A „nincs globális domináns függvény, tehát kompakt paraméterrészeken dolgozunk, majd az uniót vesszük" lépés a paraméteres integrálok elméletének standard fogása, és a $\Gamma$-nál látszik a legtisztábban, hogy miért kell: a $c$ és a $d$ a két végtelen végén más-más okból korlátoz.

### A konvergencia és a funkcionálegyenlet elemi bizonyítása (1. gyak)

Az 1. gyakorlatlap (6. feladat) a $\Gamma(x)$ konvergenciáját az integrál 1-nél való kettévágásával mutatja meg, $x>0$ esetén. A $(0,1]$ szakaszon $t^{x-1}e^{-t}<t^{x-1}=1/t^{1-x}$, és $1-x<1$, így konvergens majoráns van; a $[1,\infty)$ szakaszon $t^{x-1}e^{-t}<1/t^2$ elég nagy $t$-re, mert $t^{x+1}e^{-t}\to0$. A $\Gamma(x+1)=x\Gamma(x)$ parciális integrálással jön ki, a határérték-tag $s^xe^{-s}\to0$ miatt tűnik el, és indukcióval $\Gamma(n+1)=n!$. Az improprius integrál alapjai az [[subjects/analii]] anyagához tartoznak.

## Kapocs

- [[concepts/analiii/parameteres-integral-differencialasa]] — az az általános tétel, amelyből a $\Gamma$ differenciálhatósága következik.
- [[concepts/analiii/parameteres-integral]] — a domináns függvény fogalma, amelyet a bizonyítás konstruál.
- [[concepts/analiii/gauss-integral]] — az $x = u^2$ helyettesítéssel a Gauss-integrál éppen $\Gamma(1/2) = \sqrt{\pi}$-t adja.
- [[concepts/analii/improprius-integral]] — a $\Gamma$ mindkét végén improprius integrál; a konvergenciakritériumok onnan jönnek.
- [[concepts/analii/hatarozott-integral-parcialisintegrals]] — a $\Gamma(s+1) = s\Gamma(s)$ funkcionálegyenlet parciális integrálással adódik.
