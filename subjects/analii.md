---
tags:
  - subject
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás", "An II A/B 3. előadás", "An II A/B 4. előadás", "An II A/B 5. előadás", "An II A/B 6. előadás", "An II A/B 7. előadás", "An II A/B 8. előadás", "An II A/B 9. előadás", "An II A/B 10. előadás", "An II A/B 11. előadás"]
derivation: source
updated: 2026-09-04
---

# Analízis II.

Valós-valós függvények differenciál- és integrálszámítása. A félév két fő területe: differenciálszámítás (derivált, Taylor-sor, függvényvizsgálat) és integrálszámítás (határozatlan és határozott integrál, improprius integrál).

## A tárgy célja

A félév célja függvénytulajdonságok (monotonitás, szélsőérték, konvexitás) jellemzése az analízis eszközeivel. Előfeltétel: határérték, folytonosság, hatványsorok, elemi függvények.

## Differenciálszámítás

### Alapfogalmak

- [[concepts/analii/derivalt-fogalma]] — pontbeli derivált definíciója, különbségi hányados, motiváció
- [[concepts/analii/egyoldali-derivaltak]] — jobb és bal oldali derivált; $f \in D\{a\} \iff f'_+(a) = f'_-(a)$
- [[concepts/analii/folytonossag-es-derivalt]] — deriválhatóság $\Rightarrow$ folytonosság; Weierstrass–Takagi–van der Waerden ellenpélda
- [[concepts/analii/linearkozelites]] — lineáris közelítés tétele, ekvivalens a deriválttal
- [[concepts/analii/erintofuggveny]] — grafikon érintőjének egyenlete
- [[concepts/analii/derivaltfuggveny]] — $f'$ mint operátor; jelölések

### Számítási szabályok

- [[concepts/analii/derivalasi-szabalyok]] — összeg, szorzat, hányados, lánc, inverz, hatványsor
- [[concepts/analii/elemi-fuggvenyek-derivaltjai]] — $x^n$, $\sqrt{x}$, $\sin$, $\cos$, $\exp$, $\ln$ deriváltjai táblázatban
- [[concepts/analii/elemi-fuggvenyek-kiegeszites]] — tg, ctg, arkusz-, hiperbolikus, areafüggvények
- [[concepts/analii/magasabb-rendu-derivaltak]] — $n$-edik derivált, $D^\infty$, Leibniz-szorzatszabály

### Középértéktételek és alkalmazások

- [[concepts/analii/kozeptertekek]] — Rolle-, Lagrange-, Cauchy-féle középértéktételek
- [[concepts/analii/monotonitas]] — monotonitás és derivált előjele
- [[concepts/analii/lokalis-szelsertekek]] — előjelváltás; 1. és 2. rendű elégséges feltétel; magasabb rendű feltétel
- [[concepts/analii/abszolut-szelsertekek]] — Weierstrass-tétel; keresési algoritmus zárt intervallumon
- [[concepts/analii/konvex-konkav-fuggvenyek]] — $\lambda$-feltétel; Jensen-egyenlőtlenség; $f'' \geq 0$ kritérium; érintős jellemzés
- [[concepts/analii/inflexios-pont]] — konvexitás irányváltása; $f''(c) = 0$ szükséges; $f''$ előjelváltása elégséges
- [[concepts/analii/aszimptota]] — aszimptota $\pm\infty$-ben; ferde aszimptota
- [[concepts/analii/lhospital-szabalyok]] — L'Hospital-szabály $0/0$ és $\infty/\infty$ esetekre
- [[concepts/analii/teljes-fuggvenyvizsgalat]] — 5 lépéses módszer; Gauss-görbe példa

### Taylor-sorok

- [[concepts/analii/taylor-polinom]] — Taylor-polinom és Maclaurin-sor definíciója
- [[concepts/analii/taylor-formula-maradektag]] — Lagrange-maradéktag; bizonyítás Cauchy-tétellel
- [[concepts/analii/taylor-sor-eloallitas]] — konvergencia vs. előállítás; $e^{-1/x^2}$ ellenpélda
- [[concepts/analii/nevezetes-sorfejtesek]] — $e^x$, $\ln(1+x)$, $\arctan x$, binomiális sor

## Integrálszámítás

### Határozatlan integrál

- [[concepts/analii/primitiv-fuggveny]] — primitív függvény definíciója; Darboux-tétel (szükséges feltétel); folytonosság (elégséges feltétel); Liouville-féle nem elemi primitívek
- [[concepts/analii/hatarozatlan-integral]] — határozatlan integrál fogalma; linearitás; első helyettesítési szabály (speciális esetekkel); parciális integrálás; második helyettesítési szabály (trigonometrikus helyettesítés)
- [[concepts/analii/alapintegralok]] — elemi integrálpárok alaptáblázata: hatványok, $\ln$, exp, trig, arkusz, hiperbolikus

### Határozott integrál — értelmezés és kritériumok

- [[concepts/analii/hatarozott-integral-motivacio]] — síkidom területe, $f(x)=x^2$ példa ($t(A_f)=1/3$); Arkhimédész, Newton, Leibniz, Cauchy történeti ív
- [[concepts/analii/hatarozott-integral-ertelmezese]] — $K[a,b]$, felosztás, finomság, $s(f,\tau)/S(f,\tau)$, Darboux alsó/felső integrál, $R[a,b]$ definíciója; finomítási tétel
- [[concepts/analii/integralhato-fuggvenyek]] — oszcillációs összeg $\Omega$; Darboux-kritérium; sorozatos kritérium; Riemann-féle közelítő összeg; Riemann-kritérium; Dirichlet ellenpélda

### Határozott integrál — tulajdonságok

- [[concepts/analii/riemann-fuggveny]] — $R(x)$ def; periodikus, irracionálisban folytonos; $R \in R[0,1]$, $\int_0^1 R = 0$ teljes bizonyítással
- [[concepts/analii/muvelet-integralhato-fuggvenyekkel]] — $\lambda f$, $f+g$, $f\cdot g$, $f/g$ integrálhatósága; linearitás; oszcillációs összeg-argumentum
- [[concepts/analii/riemann-integral-tulajdonsagok]] — függvényértékek megváltoztatása véges helyen; integrálhatóság kiterjesztése véges sok pontban nem értelmezett függvényekre
- [[concepts/analii/integral-egyenlotlensegek]] — előjeltartó integrál, integrálban monoton, első középértéktétel, CBS-egyenlőtlenség (stub)

### Integrálhatóság — elégséges feltételek

- [[concepts/analii/monoton-fuggvenyek-integralhatasaga]] — monoton $\Rightarrow$ integrálható (egyenletes felosztás, teleszkopikus összeg); szakaszonként monoton def + additív integráltétel
- [[concepts/analii/egyenletes-folytonossag]] — pontbeli vs. egyenletes folytonosság; 4 példa ($x^2$, $1/x$ kompakt/nem-kompakt intervallumokon); Heine-tétel indirekt bizonyítással (Bolzano–Weierstrass)
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — $C[a,b] \subset R[a,b]$; bizonyítás Heine-tétellel; valódi befoglalás ($R$-függvény ellenpélda)

### Newton–Leibniz és alkalmazások

- [[concepts/analii/integralfuggveny]] — $x_0$-ban eltűnő integrálfüggvény; folytonos; $f$ folytonossági pontjaiban deriválható és $F' = f$
- [[concepts/analii/newton-leibniz-tetel]] — $\int_a^b f = F(b) - F(a)$; Lagrange-középértéktétellel bizonyítva; alkalmazás: $\pi \notin \mathbb{Q}$
- [[concepts/analii/hatarozott-integral-parcialisintegrals]] — $\int_a^b fg' = [fg]_a^b - \int_a^b f'g$; Wallis-formula és $\sin^k$ rekurzió
- [[concepts/analii/hatarozott-integral-helyettesites]] — $\int_{g(\alpha)}^{g(\beta)} f = \int_\alpha^\beta f\circ g \cdot g'$; határok transzformálása
- [[concepts/analii/sikido-terulete]] — két görbe közé zárt síkidom területe; körterület ($= \pi$) levezetése

### Integrál alkalmazásai — geometria

- [[concepts/analii/ivhossz]] — függvénygrafikon ívhossza; rektifikálhatóság; $C^1$ ívhossz-tétel ($\int\sqrt{1+[f']^2}$); körkerület levezetése
- [[concepts/analii/forgastest-terfogata]] — forgástest térfogata ($\pi\int f^2$); gömb térfogata ($\frac{4}{3}R^3\pi$) levezetéssel
- [[concepts/analii/forgastest-felszine]] — forgásfelület felszíne ($2\pi\int f\sqrt{1+[f']^2}$); gömb felszíne ($4R^2\pi$) levezetéssel
- [[concepts/analii/osszegek-integrallal]] — összegek határértéke integrállal; $n^\alpha$ aszimptotika; harmonikus sor $\sim\ln n$; Euler-állandó $\gamma$

### Improprius integrál és közelítő módszerek

- [[concepts/analii/improprius-integral]] — kiterjesztés nem korlátos ÉT-ra/integrandusra; $\int 1/x^\alpha$; összehasonlító és abszolút konvergencia; integrálkritérium sorokra
- [[concepts/analii/banach-fixponttetel]] — egyenletek közelítő megoldása fixpont-iterációval; kontrakció, Banach-tétel, hibabecslés; $x=\cos x$ példa

### Gyakorlás

- [[concepts/analii/integral-mintak]] — integrálási minták katalógusa (Gy 7–12): helyettesítések, parciális integrálás, racionális és trigonometrikus esetek
- [[concepts/analii/integral-feladatok]] — egységes integrál-feladatbank (46 feladat) rövid megoldási ötletekkel

## Kapocs

- [[subjects/nummodi]] — numerikus módszerek, ahol a derivált fogalma is megjelenik (Newton-módszer)
