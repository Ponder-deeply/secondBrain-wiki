---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.5.5.2–4.5.5.3. Tétel"]
derivation: source
updated: 2026-09-07
---

# Feltételes szélsőérték másodrendű feltételei

A feltétel nélküli eset másodrendű feltételei szó szerint átvihetők, két cserével: az $f$ helyére az $F = f + \lambda g$ Lagrange-függvény lép, a definitséget pedig csak a $g'(c)$ **magterén** kell megkövetelni.

## Tartalom

### Feltételes definitség

Legyen $Q : \mathbb{R}^n\to\mathbb{R}$ kvadratikus alak, $B \in \mathbb{R}^{m\times n}$, $m < n$, $\operatorname{rang} B = m$, és

$$A_B := \{x \in \mathbb{R}^n : Bx = 0\}$$

a $B$ magtere (egy $n-m$ dimenziós altér). A $Q$ alak a $B$-re nézve

- **feltételesen pozitív definit**, ha $Q(x) > 0$ minden $0 \ne x \in A_B$-re;
- **feltételesen negatív definit**, ha $Q(x) < 0$ minden $0 \ne x \in A_B$-re;
- **feltételesen pozitív (negatív) szemidefinit**, ha $Q(x) \ge 0$ ($\le 0$) minden $x \in A_B$-re.

**A lényeg a szűkítés.** Egy indefinit alak lehet feltételesen pozitív definit — a nemkívánatos irányok egyszerűen nem tartoznak a megengedett elmozdulások közé. Ezért nem lehet a [[concepts/analiii/kvadratikus-alak-definitsege|Sylvester-kritériumot]] közvetlenül alkalmazni; a szokásos gyakorlati út a $Bx = 0$ egyenletrendszer megoldása és a $Q$ megszorításának vizsgálata a kapott bázison (vagy a peremes Hesse-determinánsok használata).

### Másodrendű elégséges feltétel

Legyen $m < n$, $U \subset \mathbb{R}^n$ nyílt, $f : U\to\mathbb{R}$, $g : U\to\mathbb{R}^m$, $f,g \in D^2$, $c \in \{g=0\}$, $\operatorname{rang} g'(c) = m$. Ha valamilyen $\lambda \in \mathbb{R}^m$-mel az $F := f + \lambda g$ függvényre

1. $\operatorname{grad} F(c) = 0$;
2. $Q^F_c$ a $g'(c)$ mátrixra nézve feltételesen pozitív (negatív) definit,

akkor $f$-nek $c$-ben a $g = 0$ feltételre nézve feltételes lokális minimuma (maximuma) van. Itt $Q^F_c(x) = \langle F''(c)x, x\rangle$, azaz a Lagrange-függvény [[concepts/analiii/hesse-matrix|Hesse-mátrixához]] tartozó alak.

### Másodrendű szükséges feltétel

Ugyanezen simasági és rangfeltételek mellett, ha $f$-nek $c$-ben feltételes lokális minimuma (maximuma) van, akkor van olyan $\lambda \in \mathbb{R}^m$, amellyel $F := f+\lambda g$-re

1. $\operatorname{grad} F(c) = 0$;
2. $Q^F_c$ a $g'(c)$-re nézve feltételesen pozitív (negatív) **szemi**definit.

A bizonyítás ugyanaz a redukció, mint az elsőrendű feltételnél: az [[concepts/analiii/implicitfuggveny-tetel|implicitfüggvény-tétellel]] $(K(a)\times K(b))\cap\{g=0\} = \operatorname{graf} h$, a minimumfeltétel $f(x,h(x)) \ge f(a,b)$ alakot ölt, és erre a [[concepts/analiii/tobbvaltozos-taylor-formula|Peano-maradéktagos Taylor-formulát]] írjuk fel. A $\{g=0\}$ mentén megengedett elmozdulások érintővektorai éppen $A_{g'(c)}$ elemei — innen a magtérre való szűkítés.

### Az analógia, tételről tételre

| feltétel nélküli | feltételes |
|---|---|
| $\operatorname{grad} f(c) = 0$ | $\operatorname{grad}(f+\lambda g)(c) = 0$ alkalmas $\lambda$-val |
| $Q^f_c$ definit $\Rightarrow$ szélsőérték | $Q^F_c$ feltételesen definit $\Rightarrow$ szélsőérték |
| szélsőérték $\Rightarrow$ $Q^f_c$ szemidefinit | szélsőérték $\Rightarrow$ $Q^F_c$ feltételesen szemidefinit |
| — | + rangfeltétel: $\operatorname{rang} g'(c) = m$ |

A **rangfeltétel** az egyetlen új összetevő; minden más a régi séma, $f \rightsquigarrow F$ és $\mathbb{R}^n \rightsquigarrow A_{g'(c)}$ cserével. A definit és a szemidefinit eset közötti rés itt is nyitva marad.

## Kapocs

- [[concepts/analiii/felteteles-szelsoertek]] — a fogalom és az elsőrendű feltétel.
- [[concepts/analiii/kvadratikus-alak-definitsege]] — a feltétel nélküli definitségfogalom.
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — a párhuzamos tételhármas.
- [[concepts/analiii/implicitfuggveny-tetel]] — a redukció eszköze.
- [[concepts/analiii/tobbvaltozos-taylor-formula]] — a bizonyítás formulája.
