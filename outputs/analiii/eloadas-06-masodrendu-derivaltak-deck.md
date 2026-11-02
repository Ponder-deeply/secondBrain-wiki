`button-fc-review` | `button-fc-cram`

#flashcards/analiii/eloadas-06-masodrendu-derivaltak

## Legyen $f \in \mathbb{R}^n \to \mathbb{R}$ és $f \in D\{a\}$. Milyen $v \in \mathbb{R}^n$ irányban lesz a $\partial_v f(a)$ iránymenti derivált értéke nulla?
?
Azokban a $v$ irányokban, amelyek merőlegesek a gradiensre: $\partial_v f(a) = \langle\operatorname{grad} f(a), v\rangle = 0 \iff v \perp \operatorname{grad} f(a)$.
---

## Mikor mondjuk, hogy az $f \in \mathbb{R}^n \to \mathbb{R}$ függvény kétszer differenciálható az $a \in \operatorname{int}\mathcal{D}_f$ pontban?
?
Ha van olyan $K(a) \subset D_f$ környezet, amelyen $f \in D\{x\}$ minden $x$-re, és $\partial_i f \in D\{a\}$ minden $i=1,\dots,n$-re — ezzel ekvivalensen, ha $\operatorname{grad}f \in D\{a\}$. Jele: $f \in D^2\{a\}$.
---

## Mikor mondjuk, hogy az $f \in \mathbb{R}^n \to \mathbb{R}$ függvény kétszer folytonosan differenciálható az $a \in \operatorname{int}\mathcal{D}_f$ pontban?
?
Ha egy $K(a) \subset D_f$ környezetben $f \in D^2\{x\}$ minden pontban, és minden másodrendű parciális deriváltfüggvény ($\partial_{ij}f$) folytonos $a$-ban. Jele: $f \in C^2\{a\}$.
---

## Mikor mondjuk, hogy az $f \in \mathbb{R}^n \to \mathbb{R}$ függvény $s$-szer ($s \in \mathbb{N}, s \geq 2$) differenciálható az $a \in \operatorname{int}\mathcal{D}_f$ pontban?
?
Indukcióval: ha van olyan $K(a) \subset D_f$ környezet, amelyen $f \in D^{s-1}\{x\}$ minden pontban, és minden $(s-1)$-edrendű parciális deriváltfüggvénye differenciálható $a$-ban. Jele: $f \in D^s\{a\}$. Vektorértékű $f=(f_1,\dots,f_m)$ esetén ez azt jelenti, hogy minden koordinátafüggvénye $s$-szer differenciálható.
---

## Adja meg Hesse-féle mátrix fogalmát!
?
Ha $f \in \mathbb{R}^n \to \mathbb{R}$ és $f \in D^2\{a\}$, akkor a második derivált a másodrendű parciális deriváltakból álló $f''(a) := \bigl(\partial_{ij}f(a)\bigr)_{i,j=1}^n \in \mathbb{R}^{n\times n}$ mátrix — a **Hesse-mátrix**. A Young-tétel miatt szimmetrikus, és a hozzá tartozó $Q^f_a(x) = \langle f''(a)x,x\rangle$ kvadratikus alak dönti el a szélsőérték kérdését.
---

## Mondja ki a Young-tételt!
?
Ha $f \in C^s\{a\}$ ($s \geq 2$), akkor az $s$-edrendű parciális deriváltak értéke nem függ a deriválás sorrendjétől: $\partial_{k_1\dots k_s}f(a) = \partial_{j_1\dots j_s}f(a)$ tetszőleges $(j_1,\dots,j_s)$ permutációra. Speciálisan $\partial_{ij}f(a) = \partial_{ji}f(a)$. A pusztán $D^2\{a\}$ (folytonosság nélküli) feltétel nem elég — van ellenpélda, amelyre a vegyes parciális deriváltak léteznek, de nem egyeznek.
---

## Mit állít a "Taylor-formula a Lagrange-féle maradéktaggal" című tétel?
?
Ha $f \in \mathbb{R}^n \to \mathbb{R}$, $f \in D^{s+1}$, akkor bármely $[a,b] \subset D_f$ szakaszhoz van olyan $c \in [a,b]$, hogy $f(b) = T_{a,s}f(b) + \sum_{|i|=s+1} \dfrac{\partial^i f(c)}{i!}(b-a)^i$, ahol $T_{a,s}f$ az $s$-edfokú Taylor-polinom. A maradéktag tehát egy közbülső $c$ pont $(s+1)$-edrendű deriváltjaival van kifejezve — a bizonyítás a szakasz $F(t)=f(a+th)$ paraméterezésével egyváltozós Taylor-formulára vezet vissza.
---
