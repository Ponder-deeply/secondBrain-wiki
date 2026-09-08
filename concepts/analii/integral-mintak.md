---
tags: [concept]
sources: [07_Gy_An_II_A_B.pdf, 08_Gy_An_II_A_B.pdf, 09_Gy_An_II_A_B.pdf, 10_Gy_An_II_A_B.pdf]
references: ["An II A/B 11–12. gyakorlat"]
derivation: source
updated: 2026-09-04
---

# Integrálási minták indexe

Az Analízis II. 7–12. gyakorlat anyagából kinyert primitív/határozott integrálási minták katalógusa. Minden minta egysoros leírással + jellegzetes felismerési jeggyel.

## Linearitás és alapintegrálok

- **Polinom kibontás** — $\int (6x^2-8x+3)\,dx$ típus: alapintegrálok lineáris kombinációja.
- **Racionális szétválasztás** — pl. $\frac{x^2}{x^2+1} = 1 - \frac{1}{1+x^2}$; nevező hozzáadása–levonása.
- **Gyökös hatványkitevő** — beágyazott gyökök $x^{p/q}$ alakra hozása.
- **Trigonometrikus azonosság** — pl. $1+\cos 2x = 2\cos^2 x$ helyettesítés alapintegrálokra.

## Első helyettesítési szabály speciális esetei

- **$\int f'/f\,dx = \ln|f|$** — felismerés: a számláló a nevező deriváltja (esetleg konstans szorzóig).
- **$\int f^\alpha\cdot f'\,dx = f^{\alpha+1}/(\alpha+1)$** — felismerés: $f$ és $f'$ szorzata az integrandus.
- **Lineáris helyettesítés $\int f(ax+b)\,dx = F(ax+b)/a$** — belső függvény lineáris.
- **Páratlan trig hatvány** — $\sin^{2k+1} = (1-\cos^2)^k\sin$ átalakítással $\int f^\alpha f'$ alaptípusra.
- **Linearizáló formula** — $\sin^2 x = \frac{1-\cos 2x}{2}$, $\cos^2 x = \frac{1+\cos 2x}{2}$ fokszámcsökkentés.

## Parciális integrálás

- **$\int P(x)\cdot G(ax+b)\,dx$, $G\in\{\exp,\sin,\cos,\operatorname{sh},\operatorname{ch}\}$** — $P$ fokszáma = parc. int. lépésszám; $g' = G$.
- **$\int e^{\alpha x+\beta}\cdot G(ax+b)\,dx$** — kétszeres parc. int. visszahozza az eredeti integrált; egyenletből kifejezhető.
- **$\int P(x)\cdot G^n(ax+b)\,dx$, $G\in\{\ln,\operatorname{arc}\ldots,\operatorname{ar}\ldots\}$** — most $f = G^n$, $g' = P$; $n$ parc. int.
- **$\int G(ax+b)\,dx = \int 1\cdot G$** — $\int \operatorname{arctg}, \int \ln$ stb. „1-trükk”-kel.
- **$\int \sqrt{1-x^2}\,dx$ parciálissal** — $\int 1\cdot \sqrt{1-x^2}$, egyenletből kifejezve.
- **$\int \cos^n x\,dx$ rekurzió** — $\int\cos^n = \frac{1}{n}\sin\cos^{n-1} + \frac{n-1}{n}\int\cos^{n-2}$.

## Racionális törtfüggvények — elemi alaptípusok

- **1. alaptípus: $\int 1/(ax+b)^n$** — lineáris helyettesítés; $n=1$-re $\ln$, egyébként hatvány.
- **2. alaptípus: $\int (2ax+b)/(ax^2+bx+c)$** — $\int f'/f \to \ln|ax^2+bx+c|$.
- **3. alaptípus: $\int 1/(ax^2+bx+c)$, $\Delta<0$** — teljes négyzetté alakítás → $arctg$.
- **4. alaptípus: $\int (Ax+B)/(ax^2+bx+c)$, $\Delta<0$** — számláló felbontás $\gamma(2ax+b)+\delta$ alakra; 2. + 3. típus.
- **5. alaptípus: $\int (Ax+B)/(ax^2+bx+c)^n$, $\Delta<0$** — rekurzív formula $\int 1/(x^2+1)^n$-re.

## Parciális törtekre bontás (általános P/Q)

1. **Polinomiális rész leválasztása** — maradékos osztás, ha $\deg P \ge \deg Q$.
2. **$Q$ faktorizálása** — valós első- és $\Delta<0$ másodfokú tényezőkre.
3. **Határozatlan együtthatós felbontás** — minden gyöktényezőhöz a kitevőig minden hatvány; másodfokúhoz $Bx+C$.
4. **Együtthatók meghatározása** — együttható-összehasonlítás vagy speciális $x$-érték behelyettesítés.

## Második helyettesítési szabály

- **$t = e^x$ ($x = \ln t$)** — $\int S(e^x)\,dx$, $S$ racionális → racionális tört $t$-ben.
- **$t = \sqrt[n]{(ax+b)/(cx+d)}$** — $\int R(x, \sqrt[n]{\cdot})\,dx$ típus; $x = (b-dt^n)/(ct^n-a)$.
- **$x = t^k$, $k = \text{lkkt}$ a gyökök kitevőinek** — pl. $\sqrt{x}+\sqrt[3]{x}$-re $x = t^6$.
- **$t = tg (x/2)$ Weierstrass** — $\sin x = \frac{2t}{1+t^2}$, $\cos x = \frac{1-t^2}{1+t^2}$, $dx = \frac{2}{1+t^2}dt$; $\int R(\sin x,\cos x)\,dx$ racionálissá válik.
- **$x = \sin t$ / $x = \cos t$** — pl. $\sqrt{1-x^2}$-re alternatíva parc. int. helyett.

## Trigonometrikus szorzatok

- **$\int \sin^n x\cos^m x\,dx$, valamelyik kitevő páratlan** — négyzetes azonosság + $\int f^\alpha f'$.
- **$\int \sin^n x\cos^m x\,dx$, mindkét kitevő páros** — linearizáló formula fokszámfelezésre; vagy rekurziós formula.

## Határozott integrál és alkalmazásai

- **Newton–Leibniz** — $\int_a^b f = [F]_a^b$; folytonosság ⇒ alkalmazható.
- **Helyettesítés határozott integrálban** — határok transzformálása $g(\alpha)\to\alpha$.
- **Síkidom területe** — $t(A) = \int_a^b (g-f)\,dx$ két görbe között; bonyolult tartomány szétbontása részekre.
- **Forgástest térfogata** — $V = \pi\int_a^b f^2\,dx$.
- **Forgásfelület felszíne** — $A = 2\pi\int_a^b f\sqrt{1+[f']^2}\,dx$.
- **Ívhossz** — $\ell = \int_a^b \sqrt{1+[f']^2}\,dx$.
- **Riemann-összeg határértéke** — $\lim \frac{1}{n}\sum f(k/n) = \int_0^1 f$; ismeretlen összegre integrálos azonosítás.

## Kapocs

- [[concepts/analii/hatarozatlan-integral]] — alapfogalom, szabályok
- [[concepts/analii/alapintegralok]] — kiindulási táblázat
- [[concepts/analii/integral-feladatok]] — feladatbank ezekre a mintákra
- [[concepts/analii/newton-leibniz-tetel]] — határozott integrál kiszámításához
- [[concepts/analii/sikido-terulete]], [[concepts/analii/ivhossz|ivhossz]], [[concepts/analii/forgastest-terfogata|forgastest-terfogata]], [[concepts/analii/forgastest-felszine|forgastest-felszine]] — geometriai alkalmazások
