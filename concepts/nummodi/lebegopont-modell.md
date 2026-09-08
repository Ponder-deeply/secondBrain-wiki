---
tags: [concept]
sources: [NM1_ea01.pdf]
derivation: source
updated: 2026-08-05
---

# Lebegőpontos számok modellje

A valós számok véges, diszkrét gépi reprezentációja: a normalizált lebegőpontos számhalmaz $M(t, k^-, k^+)$ formális modellje és alapvető tulajdonságai.

## Motiváció

A számítógépeken csak véges sok szám tárolható, amelyek emellett több nagyságrenddel is eltérhetnek egymástól. A lebegőpontos modell ezt a két igényt — széles értéktartomány és kezelhető reprezentáció — egyensúlyozza.

A bevezető „furcsa jelenségek" rámutatnak a modell korlátaira:
- $\sin(\pi)$ gépileg nem pontosan $0$, hanem $\approx 1{,}22 \cdot 10^{-16}$
- A harmonikus sor részletösszegei előre és visszafelé számolva különböző eredményt adnak $n = 10^8$-ra
- $\sqrt{2017} - \sqrt{2016}$ kétféle algebrai alakban számolva különbözik (jobb alak: $\frac{1}{\sqrt{2017}+\sqrt{2016}}$)
- $a = 10^{-20},\; b = 1$: $(a+b)-b \ne a + (b-b)$ — az összeadás **nem asszociatív** gépi számokra
- $\cosh(20) - \sinh(20)$ direkten $0$-t ad, holott értéke $e^{-20} \approx 2{,}06 \cdot 10^{-9}$
- A $T_n = \int_0^1 \frac{x^n}{x+10}\,dx$ rekurzió előre indítva instabil, visszafelé stabil

## Normalizált lebegőpontos szám — definíció

Legyen
$$m = \sum_{i=1}^{t} m_i \cdot 2^{-i}, \quad t \in \mathbb{N},\; m_1 = 1,\; m_i \in \{0,1\}.$$

Az $a = \pm m \cdot 2^k \quad (k \in \mathbb{Z})$ alakú számot **normalizált lebegőpontos számnak** nevezzük.

- $m$: a szám **mantisszája**, hossza $t$ bit
- $k$: a szám **karakterisztikája**, $k^- \le k \le k^+$

**Jelölés:** $a = \pm[m_1 \ldots m_t \mid k] = \pm 0.m_1 \ldots m_t \cdot 2^k$.

## A gépi számok halmaza

$$M(t, k^-, k^+) = \left\{ a = \pm 2^k \cdot \sum_{i=1}^{t} m_i \cdot 2^{-i} : \begin{array}{l} k^- \le k \le k^+ \\ m_i \in \{0,1\},\; m_1 = 1 \end{array} \right\} \cup \{0\}$$

Gyakorlatban kiegészítik: $\infty$, $-\infty$, NaN.

**Jelölés:** $M = M(t, k^-, k^+)$, ahol tipikusan $k^- < 0$ és $k^+ > 0$.

## Nevezetes értékek és tulajdonságok

| Jelölés                                                     | Leírás                                      | Értéke                                      |     |
| ----------------------------------------------------------- | ------------------------------------------- | ------------------------------------------- | --- |
| $\frac{1}{2} \le m < 1$                                     | mantissza tartomány                         | normalizált feltétel                        |     |
| $\varepsilon_0 = [100\ldots0 \mid k^-]$                     | $M$ legkisebb pozitív eleme                 | $\frac{1}{2} \cdot 2^{k^-} = 2^{k^--1}$     |     |
| $\varepsilon_1 = [100\ldots01\mid 1] - [100\ldots00\mid 1]$ | 1 utáni következő gépi szám és 1 különbsége | $2^{-t} \cdot 2^1 = 2^{1-t}$                |     |
| $M_\infty = [111\ldots11 \mid k^+]$                         | $M$ legnagyobb eleme                        | $(1 - 2^{-t}) \cdot 2^{k^+}$                |     |
| $M$                                                         | $M$ elemeinek száma                         | $2 \cdot 2^{t-1} \cdot (k^+ - k^- + 1) + 1$ |     |

$M$ szimmetrikus a 0-ra.

### Példa: $M(3, -1, 2)$

$k=0$ esetén az elemek: $0.100, 0.101, 0.110, 0.111$, azaz $\frac{1}{2}, \frac{5}{8}, \frac{6}{8}, \frac{7}{8}$.

$$\varepsilon_0 = 0.100 \cdot 2^{-1} = \frac{1}{2} \cdot \frac{1}{2} = \frac{1}{4} = 0{,}25$$
$$\varepsilon_1 = 0.101 \cdot 2^1 - 1 = \frac{5}{8} \cdot 2 - 1 = \frac{1}{8} \cdot 2 = \frac{1}{4} = 0{,}25$$
$$M_\infty = 0.111 \cdot 2^2 = \frac{7}{8} \cdot 4 = \frac{7}{2} = 3{,}5$$
$$|M| = 2 \cdot 2^2 \cdot 4 + 1 = 33$$

### Valós modellek

$$\text{float} \sim M(23, -128, 127), \quad \text{double} \sim M(52, -1024, 1023)$$

## Input függvény — valós számok ábrázolása

Legyen $\mathbb{R}_M = \{x \in \mathbb{R} : |x| \le M_\infty\}$ az **ábrázolható számok tartománya**.

**Definíció:** Az $fl\colon \mathbb{R}_M \to M$ függvényt **input függvénynek** nevezzük, ha
$$fl(x) = \begin{cases} 0 & \text{ha } |x| < \varepsilon_0, \\ \tilde{x} & \text{ha } \varepsilon_0 \le |x| \le M_\infty, \end{cases}$$
ahol $\tilde{x}$ az $x$-hez legközelebbi gépi szám (a kerekítés szabályai szerint).

### Input hiba — tétel

Minden $x \in \mathbb{R}_M$ esetén
$$|x - fl(x)| \le \begin{cases} \varepsilon_0 & \text{ha } |x| < \varepsilon_0, \\ \frac{1}{2}|x| \cdot \varepsilon_1 & \text{ha } \varepsilon_0 \le |x| \le M_\infty. \end{cases}$$

**Következmény (relatív hiba korlátja):** Ha $\varepsilon_0 \le |x| \le M_\infty$, akkor
$$\frac{|x - fl(x)|}{|x|} \le \frac{1}{2} \cdot \varepsilon_1 = 2^{-t}.$$

A hiba tehát lényegében $\varepsilon_1$-től, azaz a mantissza $t$ bitjétől függ.

**Bizonyítás vázlata:** Két szomszédos gépi szám $x' < x < x''$ távolsága $2^{k-t}$, ahol $x' = [1\_\ldots\_\mid k]$. Az $fl(x)$ az intervallum felénél közelebb van $x$-hez, tehát $|x - fl(x)| \le \frac{1}{2} \cdot 2^k \cdot 2^{-t}$. Mivel $|x| \ge 0.1 \cdot 2^k = \frac{1}{2} \cdot 2^k$, következik $|x - fl(x)| \le |x| \cdot 2^{-t} = \frac{1}{2}|x|\cdot\varepsilon_1$.

## Kapocs

- [[concepts/nummodi/hibaszamitas]] — abszolút és relatív hiba definíciói, hibák terjedése
- [[concepts/nummodi/algoritmus-stabilitas]] — stabil vs. instabil algoritmus fogalma, példák
- [[concepts/nummodi/tematika]] — kurzus tematikája
- [[subjects/nummodi]] — kurzus áttekintése
