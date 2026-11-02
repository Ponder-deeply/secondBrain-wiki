`button-fc-review` | `button-fc-cram`

#flashcards/analiii/eloadas-04-derivalas-alapjai

## Adja meg egy $\mathbb{R}^n \to \mathbb{R}$ típusú függvény pontbeli $i$-edik változó szerinti parciális deriváltjának fogalmát!
?
Legyen $h_{a,i}(t) := h(a_1,\dots,a_{i-1},t,a_{i+1},\dots,a_n)$ a **parciális függvény** (a többi koordináta rögzítve). Ha $h_{a,i}$ deriválható $a_i$-ben, akkor $\partial_i h(a) := h_{a,i}'(a_i) = \lim_{t\to0}\dfrac{h(a+te_i)-h(a)}{t}$ a $h$ $a$-beli, $i$-edik változó szerinti parciális deriváltja.
---

## Adja meg egy $\mathbb{R}^n \to \mathbb{R}$ típusú függvény pontbeli $v$ irányú iránymenti deriváltjának fogalmát!
?
Legyen $\|e\|=1$. A $h_e(t):=h(a+te)$ függvény a $h$ leszűkítése az $a$-n átmenő, $e$ irányú egyenesre. Ha $h_e$ deriválható $0$-ban, akkor $\partial_e h(a):=h_e'(0)$ a $h$ $a$-beli, $e$ irányú iránymenti deriváltja. A parciális derivált ennek speciális esete, ha $e$ koordinátaegységvektor.
---

## Mi a kapcsolat az $\mathbb{R}^n$-et $\mathbb{R}^m$-be képező lineáris lekézések és az $\mathbb{R}^{n\times m}$ típusú mátrixok között?
?
Az $\mathcal{L}(\mathbb{R}^n,\mathbb{R}^m)$ (korlátos lineáris leképezések tere) izomorf az $\mathbb{R}^{m\times n}$ mátrixtérrel: minden $L \in \mathcal{L}(\mathbb{R}^n,\mathbb{R}^m)$-hez egyértelműen létezik $A \in \mathbb{R}^{m\times n}$, hogy $L(x)=Ax$. Véges dimenzióban minden lineáris leképezés automatikusan korlátos.
---

## Definiálja $\mathbb{R}^n \to \mathbb{R}^m$ típusú függvényekre a totális derivált fogalmát!
?
$f$ **differenciálható** $a \in \operatorname{int}D_f$-ben, ha van olyan $L \in \mathcal{L}(\mathbb{R}^n,\mathbb{R}^m)$ és $\eta : \mathbb{R}^n \to \mathbb{R}^m$, hogy $f(a+h)-f(a) = L(h) + \eta(h)\cdot\|h\|$, ahol $\eta(h)\to0$ ha $\|h\|\to0$. Az egyértelműen létező $L$ az $f$ $a$-beli (Fréchet-)deriváltja, jele $f'(a)$.
---

## Hogyan fogalmazható át a totális deriválhatóság lineáris közelítéssel?
?
$f$ $a$-ban differenciálható pontosan akkor, ha $f$ megváltozása egy $L$ lineáris leképezéssel közelíthető úgy, hogy a hiba $\|h\|$-nál gyorsabban tűnik el: $\dfrac{\|f(a+h)-f(a)-L(h)\|}{\|h\|} \to 0$, ha $\|h\|\to0$. Azaz $f(a+h)\approx f(a)+L(h)$, és ez a legjobb lineáris közelítés.
---

## Milyen kapcsolat van a totális és az iránymenti deriváltak között?
?
Ha $f \in D\{a\}$, akkor minden $\|e\|=1$ irányra $\partial_e f(a) = f'(a)\,e$ — a totális derivált (Jacobi-mátrix) és az irányvektor szorzata. Speciálisan $m=1$-re $\partial_e f(a) = \langle\operatorname{grad}f(a), e\rangle$. Tehát a totális derivált egyetlen lineáris leképezésbe kódolja az összes iránymenti deriváltat.
---

## Mit nevezünk Jacobi-mátrixnak?
?
Az $f'(a) \in \mathcal{L}(\mathbb{R}^n,\mathbb{R}^m)$ derivált $\mathbb{R}^{m\times n}$-beli mátrixreprezentációját, amelyre $f(a+h)-f(a) = f'(a)h + \eta(h)\cdot\|h\|$. Az $i$-edik sor a $\partial_1 f_i(a),\dots,\partial_n f_i(a)$ parciális deriváltakból áll ($f_i$ az $i$-edik koordinátafüggvény gradiense). $m=1$-re a Jacobi-mátrix a gradiens.
---

## Írja fel az $(x_0,y_0) \in \mathbb{R}^2$ pontban differenciálható $f: \mathbb{R}^2 \to \mathbb{R}$ függvény $(x_0,y_0,f(x_0,y_0))$ ponthoz tartozó érintősíkjának egyenletét!
?
$$z = f(x_0,y_0) + \partial_x f(x_0,y_0)\,(x-x_0) + \partial_y f(x_0,y_0)\,(y-y_0).$$
Ez pontosan a totális derivált (a gradienssel vett lineáris közelítés) grafikonja: $z = f(x_0,y_0) + \langle \operatorname{grad}f(x_0,y_0),\,(x-x_0,y-y_0)\rangle$.
---
