`button-fc-review` | `button-fc-cram`

#flashcards/analiii/eloadas-07-szelsoertek-kvadratikus-alak

## Mit állít a "Taylor-formula a Peano-féle maradéktaggal" című tétel?
?
Ha $f \in D^s\{a\}$ (csak az $a$ pontban), akkor van olyan $\eta:\mathbb{R}^n\to\mathbb{R}$, $\lim_0\eta=0$ függvény, hogy $f(a+h)-f(a) = \sum_{k=1}^s\sum_{|i|=k}\frac{\partial^i f(a)}{i!}h^i + \eta(h)\cdot\|h\|^s$. Kevesebbet tesz fel, mint a Lagrange-alak (nem kell $D^{s+1}$ egy környezetben), és a hibát nagyságrendben ($o(\|h\|^s)$) adja meg, nem egy ismeretlen pont deriváltjaival.
---

## Hogyan szól a lokális szélsőértékre vonatkozó elsőrendű szükséges feltétel többváltozós függvények esetén?
?
Ha $f$-nek $a \in \operatorname{int}D_f$-ben lokális szélsőértéke van és $f \in D\{a\}$, akkor $\operatorname{grad}f(a) = 0$, azaz $\partial_1f(a)=\dots=\partial_nf(a)=0$ ($a$ **stacionárius pont**). A feltétel nem elégséges (pl. nyeregpontok).
---

## Definiálja a kvadratikus alak fogalmát!
?
Legyen $A=(a_{ik})\in\mathbb{R}^{n\times n}$ szimmetrikus mátrix. A $Q(x) := \langle Ax,x\rangle = \sum_{i,k=1}^n a_{ik}x_ix_k$ ($x\in\mathbb{R}^n$) leképezés az $A$ által meghatározott kvadratikus alak. $n=2$-ben $A=\begin{bmatrix}a&b\\b&c\end{bmatrix}$ mellett $Q(u,v)=au^2+2buv+cv^2$.
---

## Mikor mondjuk, hogy egy kvadratikus alak pozitív definit?
?
Ha $Q(x) > 0$ minden $x \neq 0$-ra. $n=2$-ben (Sylvester-kritérium) ezzel ekvivalens: $a>0$ és $ac>b^2$ (azaz $d_1>0$, $d_2>0$ a sarokdeterminánsokra).
---

## Mikor mondjuk, hogy egy kvadratikus alak pozitív szemidefinit?
?
Ha $Q(x) \geq 0$ minden $x$-re. Pontosan akkor nem definit is egyben, ha van $x\neq0$, amelyre $Q(x)=0$.
---

## Mikor mondjuk, hogy egy kvadratikus alak negatív definit?
?
Ha $Q(x) < 0$ minden $x \neq 0$-ra. $n=2$-ben ezzel ekvivalens: $a<0$ és $ac>b^2$ (a sarokdeterminánsok előjele váltakozik: $d_1<0$, $d_2>0$).
---

## Mikor mondjuk, hogy egy kvadratikus alak negatív szemidefinit?
?
Ha $Q(x) \leq 0$ minden $x$-re.
---

## Mikor mondjuk, hogy egy kvadratikus alak indefinit?
?
Ha van olyan $x,y$, amelyekre $Q(y)<0<Q(x)$. $n=2$-ben ezzel ekvivalens: $ac < b^2$.
---

## Hogyan szól a lokális szélsőértékre vonatkozó másodrendű elégséges feltétel többváltozós függvények esetén?
?
Ha $a\in\operatorname{int}D_f$-ben (a) $f\in D^2\{a\}$, (b) $\operatorname{grad}f(a)=0$, (c) a $Q^f_a$ Hesse-kvadratikus-alak pozitív (negatív) definit, akkor $f$-nek $a$-ban lokális minimuma (maximuma) van. A bizonyítás kulcsa az egységgömb kompaktsága adta egyenletes $Q^f_a(\xi)\geq m\|\xi\|^2$ becslés, amely legyőzi a Taylor-formula hibatagját.
---

## Hogyan szól a lokális szélsőértékre vonatkozó másodrendű szükséges feltétel többváltozós függvények esetén?
?
Ha $f\in D^2\{a\}$ és $f$-nek $a$-ban lokális minimuma (maximuma) van, akkor $\operatorname{grad}f(a)=0$, és $Q^f_a$ pozitív (negatív) **szemi**definit. (A definitségnél gyengébb — a szemidefinit-de-nem-definit eset eldöntetlen marad.)
---

## Mit mondhatunk egy függvény lokális szélsőértékéről egy adott pontban, ha ott a Hesse-féle mátrix indefinit, és ez milyen feltételek mellett mondható ki?
?
Ha $f \in D^2\{a\}$, $\operatorname{grad}f(a)=0$, és $Q^f_a$ indefinit, akkor $f$-nek $a$-ban **nincs** lokális szélsőértéke ($a$ nyeregpont) — mert a másodrendű szükséges feltétel (szemidefinitség) sérül.
---
