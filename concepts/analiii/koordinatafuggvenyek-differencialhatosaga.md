---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 3.1.2. Tétel"]
derivation: source
updated: 2026-09-07
---

# Koordinátafüggvények differenciálhatósága

Egy $\mathbb{R}^n \to \mathbb{R}^m$ vektorfüggvény pontosan akkor differenciálható egy pontban, ha mind az $m$ koordinátafüggvénye differenciálható ott; a Jacobi-mátrix sorai a koordinátafüggvények gradiensei. Ez a tétel a vektorértékű esetet visszavezeti a skalárértékűre.

## Tartalom

### A tétel

**3.1.2. Tétel.** Legyen $1 \le n, m \in \mathbb{N}$. Az $f = (f_1, \dots, f_m) \in \mathbb{R}^n \to \mathbb{R}^m$ függvény akkor és csak akkor differenciálható az $a \in \operatorname{int} D_f$ helyen, ha minden $i = 1, \dots, m$ esetén az $f_i \in \mathbb{R}^n \to \mathbb{R}$ koordinátafüggvény differenciálható $a$-ban. Ekkor

$$f'(a) = \begin{pmatrix} \operatorname{grad} f_1(a) \\ \operatorname{grad} f_2(a) \\ \vdots \\ \operatorname{grad} f_m(a)\end{pmatrix}.$$

### Bizonyítás

**($\Rightarrow$)** Legyen $f \in D\{a\}$, és jelölje $A_i$ ($i = 1, \dots, m$) az $f'(a)$ Jacobi-mátrix sorvektorait. Alkalmas $\eta = (\eta_1, \dots, \eta_m)$, $\eta(h) \to 0$ ($\|h\|_2 \to 0$) függvénnyel

$$f(a+h) - f(a) = f'(a)h + \eta(h)\cdot\|h\|_2 = \bigl(\langle A_1, h\rangle, \dots, \langle A_m, h\rangle\bigr) + \bigl(\eta_1(h)\|h\|_2, \dots, \eta_m(h)\|h\|_2\bigr).$$

Koordinátánként kiolvasva

$$f_i(a+h) - f_i(a) = \langle A_i, h\rangle + \eta_i(h)\cdot\|h\|_2 \qquad (i = 1, \dots, m).$$

Mivel a vektorértékű $\eta$ nullához tartása ekvivalens minden $\eta_i$ koordinátafüggvényének nullához tartásával, ez éppen azt jelenti, hogy $f_i \in D\{a\}$, és $A_i = \operatorname{grad} f_i(a)$.

**($\Leftarrow$)** Ha minden $i$-re $f_i \in D\{a\}$ alkalmas $\eta_i \to 0$ hibafüggvénnyel, akkor az

$$A := \begin{pmatrix} \operatorname{grad} f_1(a) \\ \vdots \\ \operatorname{grad} f_m(a)\end{pmatrix} \in \mathbb{R}^{m\times n}, \qquad \eta := (\eta_1, \dots, \eta_m)$$

választással a koordinátánkénti egyenlőségek egyetlen vektoregyenlőséggé állnak össze:

$$f(a+h) - f(a) = Ah + \eta(h)\cdot\|h\|_2,$$

ahol $\eta(h) \to 0$. Tehát $f \in D\{a\}$, és a [[concepts/analiii/frechet-derivalt|derivált egyértelműsége]] miatt $f'(a) = A$. $\square$

### Mire jó

A tétel a többváltozós **vektorfüggvények** differenciálhatóságát maradéktalanul visszavezeti a többváltozós **valós** függvények differenciálhatóságára. Ezért elegendő a $\operatorname{grad} h(a)$ vektorok szerkezetét ismernünk ahhoz, hogy a Jacobi-mátrixot kiszámíthassuk — ezt szolgáltatja a [[concepts/analiii/gradiens-parcialis-derivaltakbol|gradiensre vonatkozó tétel]] a parciális deriváltakon keresztül.

Figyelem: a koordinátánkénti visszavezetés a **differenciálhatóságra** működik, nem az őt megelőző fogalmakra. Egy vektorfüggvény folytonossága ugyanígy koordinátánkénti, de a parciális deriválhatóság önmagában egyik esetben sem elég a differenciálhatósághoz.

## Kapocs

- [[concepts/analiii/frechet-derivalt]] — a definíció és a derivált egyértelműsége, amelyre a bizonyítás támaszkodik.
- [[concepts/analiii/jacobi-matrix]] — a sorvektoros írásmód, amelyben a tétel megfogalmazódik.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a gradiens szerkezete; a két tétel együtt adja a Jacobi-mátrix elemeit.
