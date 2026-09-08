---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# A Jordan-mérték kiszámítása szeleteléssel

Egy $(p+1)$-dimenziós Jordan-mérhető halmaz térfogata megkapható a tengelyirányú szeletei $p$-dimenziós mértékének egyváltozós Riemann-integráljaként — ez a Cavalieri-elv pontos alakja.

## Tartalom

### A szelettétel

**Tétel.** Legyen $A \in \mathcal{J}_{p+1}$, és jelölje

$$A_y = \{(x_1,\dots,x_p) : (x_1,\dots,x_p,y) \in A\} \qquad (a \leq y \leq b)$$

az $A$ halmaz $y$ magasságban vett szeletét. Ekkor

$$t_{p+1}(A) = \int_a^b k_p(A_y)\,\mathrm{d}y = \int_a^b b_p(A_y)\,\mathrm{d}y.$$

Külön kiemelendő, hogy a szeletek külső, illetve belső $p$-dimenziós mértéke mint $y$ függvénye **Riemann-integrálható**, holott az egyes szeletek nem feltétlenül mérhetők. Ha viszont minden $A_y$ szelet mérhető, akkor

$$t_{p+1}(A) = \int_a^b t_p(A_y)\,\mathrm{d}y.$$

### A bizonyítás menete

1. **Tégla.** Ha $A = [a_1,b_1] \times \dots \times [a_p,b_p] \times [a,b]$, az állítás triviális:
   $$t_{p+1}(A) = \big((b_1-a_1)\cdots(b_p-a_p)\big)(b-a) = \int_{y=a}^{b} t_p(A_y)\,\mathrm{d}y.$$

2. **Véges sok egymásba nem nyúló tégla uniója.** A mérték és az integrál is tagokra bontható:
   $$t_{p+1}(A) = \sum_{i=1}^n t_{p+1}(R^i) = \int_{y=a}^{b}\left(\sum_{i=1}^n t_p(R^i_y)\right)\mathrm{d}y = \int_{y=a}^{b} t_p(A_y)\,\mathrm{d}y.$$
   A téglahatároknál a szeletek egymásba lóghatnak, de ez csak véges sok $y$-ra fordul elő, ami az integrált nem befolyásolja.

3. **Általános eset.** Adott $\varepsilon > 0$-hoz vegyünk $F_1,\dots,F_n$ fedő és egymásba nem nyúló $B_1,\dots,B_m$ belső téglákat, melyekre $\sum t_{p+1}(F_i) < t_{p+1}(A) + \varepsilon$ és $\sum t_{p+1}(B_i) > t_{p+1}(A) - \varepsilon$. Legyen $F = \bigcup F_i$, $B = \bigcup B_i$. Monotonitással
   $$t_{p+1}(A) - \varepsilon < \underline{\int}_{y=a}^{b} b_p(A_y)\,\mathrm{d}y \leq \overline{\int}_{y=a}^{b} b_p(A_y)\,\mathrm{d}y < t_{p+1}(A) + \varepsilon,$$
   és ugyanez $k_p$-vel. Mivel ez minden $\varepsilon$-ra igaz, az alsó és felső integrál egybeesik $t_{p+1}(A)$-val, tehát a szeletmértékek integrálhatók, és az integráljuk $t_{p+1}(A)$. $\square$

### Alkalmazások

A tétel a térfogatszámítás munkaeszköze: általános henger és kúp térfogata, a paralelepipedon térfogata, valamint a $p$-dimenziós gömb térfogata mind ebből vezethető le.

## Kapocs

- [[concepts/analiii/p-dimenzios-gomb-terfogata]] — a szelettétel legfontosabb alkalmazása, indukcióval a dimenzió szerint
- [[concepts/analiii/jordan-merheto-halmazok-gyuruje]] — a bizonyítás a mérték téglaadditivitására épül
- [[concepts/analiii/grafikon-alatti-halmaz-terfogata]] — a szelettétel „függvény alatti tartomány" alakja, amely az integrált mértékként azonosítja
- [[concepts/analiii/szukcessziv-integralas]] — a szeletelés integrálokra vett megfelelője: a többszörös integrál egyváltozós integrálások sorozatává bomlik
- [[concepts/analii/forgastest-terfogata]] — az egyváltozós tananyag $\pi\int_a^b f^2$ képlete pontosan ennek a tételnek a $p = 2$, forgásszimmetrikus szeletekre vett esete: minden szelet egy $\pi f(x)^2$ területű körlap
