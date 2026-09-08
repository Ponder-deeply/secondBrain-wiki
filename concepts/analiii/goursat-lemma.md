---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Goursat-lemma valós vonalintegrálokra

Ha $f$ differenciálható és rotációmentes, akkor bármely $G$-be eső (belsejével együtt) irányított háromszögvonalon a vonalintegrálja nulla. A felezéses háromszög-sorozattal bizonyított lemma a primitív függvény létezésének kulcsa.

## Tartalom

### Előkészítő lemma: lineáris mező

**Lemma.** Legyen $A \in \mathbb{R}^{p\times p}$ és $b \in \mathbb{R}^p$. Ha az $A$ mátrix **szimmetrikus**, akkor az $f(x) = Ax + b$ függvénynek van primitív függvénye.

*Bizonyítás.* Egy primitív függvény:

$$F(x) = \frac{1}{2}x^{\mathsf{T}}Ax + \langle b; x\rangle.$$

(A gradiens képzésekor a kvadratikus alakból $\frac{1}{2}(A + A^{\mathsf{T}})x = Ax$ adódik — itt használjuk a szimmetriát.) Következésképp az ilyen $f$ vonalintegrálja minden zárt görbén nulla.

### A Goursat-lemma

**Lemma.** Legyen $G \subset \mathbb{R}^p$ összefüggő nyílt, $f : G \to \mathbb{R}^p$ differenciálható és rotációmentes. Ha $\Delta$ irányított háromszögvonal, amely a belsejével együtt $G$-be esik, akkor

$$\int_\Delta f = 0.$$

### Bizonyítás — felezéses háromszög-sorozat

Rekurzívan konstruálunk egy $\Delta_0, \Delta_1, \Delta_2, \dots$ irányított háromszögsorozatot. A kiinduló háromszög $\Delta_0 = \Delta$, és mindegyik háromszög feleakkora, mint az előző, tehát az $n$-edik kerülete $k_n = \frac{\ell(\Delta)}{2^n}$. A $\Delta_n$ kerületén vett integrál legyen $I_n = \int_{\Delta_n}\langle f(x); \mathrm{d}x\rangle$.

**A konstrukció.** Ha $\Delta_n$ már megvan, a középvonalaival négy részre osztjuk, és a négy kis háromszöget megfelelően irányítjuk. Ha a négy kis háromszögön vett vonalintegrált összeadjuk, a **középvonalakon vett integrálok kiesnek** (mindegyiket két szomszédos kis háromszög ellenkező irányban járja be), így a négy integrál összege éppen $I_n$. Válasszuk $\Delta_{n+1}$-nek azt a kis háromszöget, amelyen a vonalintegrál abszolút értéke a legnagyobb; ekkor $|I_{n+1}| \geqslant \frac{1}{4}|I_n|$, és indukcióval

$$|I_n| \geqslant \frac{|I_0|}{4^n}.$$

**A közös pont.** A $\Delta_n$ háromszögek konvex burkai (a zárt háromszöglemezek) egy csökkenő, egymásba skatulyázott sorozatot alkotnak, amelynek van egy közös $c$ pontja. Már a nulladik háromszöglemez is $G$-ben volt, tehát $c \in G$, ott $f$ differenciálható; legyen $b = f(c)$ és $A = J_f(c)$. A rotációmentesség miatt $A$ szimmetrikus.

**A becslés.** Legyen $\varepsilon > 0$ tetszőleges. A differenciálhatóság miatt van olyan $\delta > 0$, hogy a $B(c,\delta)$ környezetben

$$\bigl|f(x) - b - A(x-c)\bigr| \leqslant \varepsilon\cdot|x-c|.$$

Ha $n$ elég nagy, akkor $\Delta_n \subset B(c,\delta)$. Bontsuk fel az integrált:

$$I_n = \underbrace{\int_{\Delta_n}\bigl\langle A(x-c) + b; \mathrm{d}x\bigr\rangle}_{= 0} + \int_{\Delta_n}\bigl\langle f(x) - A(x-c) - b; \mathrm{d}x\bigr\rangle.$$

Az első tag nulla, mert az $A(x-c)+b$ lineáris mezőnek — az előkészítő lemma szerint, $A$ szimmetriája miatt — van primitív függvénye, tehát zárt görbén nulla az integrálja.

A $\Delta_n$ minden pontja közelebb van $c$-hez, mint a háromszög kerülete, azaz $x \in \Delta_n$ esetén $|x - c| < k_n$. A vonalintegrál triviális becslésével:

$$\frac{|I_0|}{4^n} \leqslant |I_n| \leqslant \sup_{x\in\Delta_n}\bigl|f(x) - A(x-c) - b\bigr|\cdot k_n \leqslant \varepsilon k_n \cdot k_n = \varepsilon\left(\frac{\ell(\Delta)}{2^n}\right)^2.$$

Átszorozva $4^n$-nel — és itt látszik, miért kellett a **négyzetesen** kicsi becslés a **negyedelődő** alsó korláttal szemben —:

$$\left|\int_\Delta f\right| = |I_0| \leqslant \varepsilon\cdot\ell(\Delta)^2.$$

Ez minden $\varepsilon > 0$-ra igaz, ami csak úgy lehet, ha $\int_\Delta f = 0$.

### Miért háromszög

A háromszög két dolgot ad egyszerre: felezéssel önmagához hasonló, feleakkora példányokra bomlik (így a $4^n$ és a $2^{-n}$ mérlege eldönthető), és a belső élek irányítottan kiejtik egymást. Innen a lemma zárt töröttvonalakra való kiterjesztése már csak háromszögekre bontás kérdése.

## Kapocs

- [[concepts/analiii/rotaciomentes-vektormezo]] — a lemma feltétele, és ez teszi $J_f(c)$-t szimmetrikussá.
- [[concepts/analiii/primitiv-fuggveny-csillagszeru-tartomanyon]] — a lemma közvetlen következményei.
- [[concepts/analiii/valos-vonalintegral]] — a bizonyítás a triviális becslést és az additivitást használja.
- [[concepts/analiii/konzervativ-vektormezo]] — a zárt töröttvonalakon vett nulla integrál a primitív függvény létezésével ekvivalens.
