---
tags: [concept, nummodi/gepi-szamabrazolas-es-hibaszamitas]
sources: [NM1_ea01.pdf]
derivation: source
updated: 2026-08-05
---

# Algoritmus stabilitása

Numerikus algoritmusok definíciója és a stabilitás fogalma: mikor mondható el, hogy egy algoritmus kis bemeneti perturbációra kis kimeneti változással reagál?

## Definíciók

**Numerikus algoritmus:** aritmetikai és logikai műveletek véges sorozata.

**Stabil algoritmus:** A numerikus algoritmus **stabil**, ha létezik olyan $C > 0$ konstans, hogy a kétféle $B_1, B_2$ bemenő adatból kapott $K_1, K_2$ kimenő adatokra

$$\|K_1 - K_2\| \le C \cdot \|B_1 - B_2\|.$$

Vagyis a kimenet változása arányos a bemenet változásával — a hibák nem fúvódnak fel kontrollálhatatlanul.

## Motiváló példák

### A $T_n$ rekurzió stabilitása

Tekintsük az integrálsorozatot:
$$T_n := \int_0^1 f_n(x)\,dx = \int_0^1 \frac{x^n}{x + 10}\,dx.$$

Az integráció-per-partes elvégzése után kapott rekurzió:
$$T_0 = \ln(1{,}1), \quad T_n = \frac{1}{n} - 10 \cdot T_{n-1} \quad (n = 1, 2, \ldots).$$

**Előre haladó rekurzió** (növekvő $n$ irányában) **instabil**: az inicializálási hiba minden lépésben 10-szereződik ($T_{n-1}$ együtthatója $-10$), ezért $T_{20}$ értéke teljesen hibás ($\approx 7{,}48 \cdot 10^3$ helyett a helyes $\approx 0{,}0043$).

**Visszafelé haladó rekurzió** stabil: rendezzük át:
$$T_{n-1} = \frac{1}{10}\left(\frac{1}{n} - T_n\right).$$
Indítsuk $T_M := 0$ értékkel valamely $M \gg n$-re; a hiba minden lépésben $\frac{1}{10}$-edére csökken, így $T_{20}$ jó pontossággal kiszámítható.

### Fibonacci-rekurzió

A Fibonacci-sorozat rekurziója instabil (lásd gyakorlaton): az aritmetikai rekurzióban a hiba exponenciálisan terjed.

## Kapcsolat a hibaszámítással

A stabilitás és a [[concepts/nummodi/hibaszamitas|hibaszámítás]] szorosan összefügg:

- Az alapműveletek hibaterjedési tételei megmutatják, hogy egy-egy lépésben mennyit nőhet a hiba.
- Egy algoritmus stabilitása azt garantálja, hogy ezek a növekedések összességében kontroll alatt maradnak.
- A **kondíciószám** ($c(f,a)$) a *matematikai feladat* érzékenységét méri; a stabilitás az *algoritmus* implementációjának tulajdonsága. Rosszul kondicionált feladat stabil algoritmussal is nehéz; de instabil algoritmus jól kondicionált feladatnál is hibás eredményt adhat.

## Gyakorlati tanulságok

Az előadás „furcsa jelenségei" mind instabilitás vagy rossz kondícionáltság következményei:

| Jelenség | Ok |
|---|---|
| $\sin(\pi) \ne 0$ gépileg | input hiba: $\pi$ nem ábrázolható pontosan |
| $\sum 1/k$ előre $\ne$ visszafelé | lebegőpontos összeadás nem asszociatív |
| $\sqrt{2017}-\sqrt{2016}$ két értéke | jegyveszítés közel azonos számok kivonásakor |
| $(a+b)-b \ne a+(b-b)$ | asszociativitás gépi számokon nem teljesül |
| $\cosh(20)-\sinh(20)=0$ direktben | $\exp(20)$ dominálja, $\exp(-20)$ elvész |
| $T_{20}$ rekurzió felrobban | instabil előre-rekurzió, hiba 10-szereződik |

## Kapocs

- [[concepts/nummodi/lebegopont-modell]] — gépi számok modellje; $\varepsilon_0, \varepsilon_1, M_\infty$; input hiba
- [[concepts/nummodi/hibaszamitas]] — abszolút/relatív hiba, hibakorlátok, kondíciószám
- [[concepts/nummodi/tematika]] — kurzus tematikája
- [[subjects/nummodi]] — kurzus áttekintése
