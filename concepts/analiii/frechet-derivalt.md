---
tags: [concept]
sources: [SimonP-Anal2.pdf, 04_ea_An3_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf, ElozetesMegajanlottVizsgaTetelek1.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, 05_gyak_An_III_2022_tavasz.pdf, 06_gyak_An_III_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 3.1. szakasz és 3.2. i)–iii) megjegyzés"]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Frécht-derivált: a többváltozós differenciálhatóság fogalma

Az $f \in \mathbb{R}^n \to \mathbb{R}^m$ függvény akkor differenciálható az $a \in \operatorname{int} D_f$ pontban, ha a megváltozása egy **korlátos lineáris leképezéssel** közelíthető úgy, hogy a hiba $\|h\|$-nál gyorsabban tűnik el. Ez a lineáris leképezés egyértelmű, és nem függ a választott normától.

## Tartalom

### Az egyváltozós eset átírása

Egyváltozóban $f \in \mathbb{R} \to \mathbb{R}$ differenciálható $a$-ban, ha alkalmas $q \in \mathbb{R}$ számmal és $\varepsilon \to 0$ függvénnyel

$$f(a+h) - f(a) = qh + \varepsilon(h)\cdot h .$$

Ha bevezetjük az $L(x) := qx$ **korlátos lineáris** leképezést, ugyanez így is írható:

$$f(a+h) - f(a) = L(h) + \eta(h)\cdot |h|, \qquad \eta(h) \to 0 \ \ (|h| \to 0).$$

Ebben az alakban már nincs osztás, és nincs benne semmi, ami az egydimenziósságra hivatkozna — ez általánosítható.

### A definíció

Legyen $1 \le n, m \in \mathbb{N}$, $1 \le p, q \le +\infty$, és tekintsük az $(\mathbb{R}^n, \|\cdot\|_p)$, $(\mathbb{R}^m, \|\cdot\|_q)$ normált tereket. Az $f$ függvény **differenciálható** az $a \in \operatorname{int} D_f$ helyen, ha van olyan $L \in \mathcal{L}(\mathbb{R}^n, \mathbb{R}^m)$ korlátos lineáris leképezés és olyan $\eta \in \mathbb{R}^n \to \mathbb{R}^m$ függvény, hogy

$$(\ast)\qquad f(a+h) - f(a) = L(h) + \eta(h)\cdot \|h\|_p \qquad (h \in \mathbb{R}^n,\ a+h \in D_f),$$

ahol $\eta(h) \to 0$, ha $\|h\|_p \to 0$. Jelölés: $f \in D\{a\}$; ha ez minden $a \in D_f$ pontban teljesül, $f \in D$.

Ekvivalens, osztásos alak:

$$\frac{\|f(a+h) - f(a) - L(h)\|_q}{\|h\|_p} \to 0 \qquad (\|h\|_p \to 0).$$

**Két apró technikai észrevétel.** Feltehető, hogy $\eta(0) = 0$, azaz $\eta \in C\{0\}$: $h = 0$ mellett mindkét oldal nulla ($L(0) = 0$ és $\|0\|_p = 0$), tehát $\eta(0)$ értéke szabadon átdefiniálható. Továbbá elég $(\ast)$-ot egyetlen $K_r(0)$ gömbön megkövetelni — $a \in \operatorname{int} D_f$ miatt van olyan $r > 0$, hogy $K_r(a) \subset D_f$, így ott $a + h \in D_f$ automatikus.

### A definíció nem függ a normától

A $\|\cdot\|_p$, $\|\cdot\|_q$ normáktól való függés csak látszólagos: $\mathbb{R}^n$-ben és $\mathbb{R}^m$-ben [[concepts/analiii/ekvivalens-normak|minden norma ekvivalens]], ezért $(\ast)$ vagy **minden** $1 \le p, q \le +\infty$ mellett teljesül, vagy egyik mellett sem. A gyakorlatban a $\|\cdot\|_\infty$, $\|\cdot\|_1$, $\|\cdot\|_2$ normák valamelyikét használjuk, aszerint, melyikkel könnyebb számolni.

### A derivált egyértelműsége

**3.1.1. Tétel.** Ha $f \in D\{a\}$, akkor a definícióban szereplő $L \in \mathcal{L}(\mathbb{R}^n, \mathbb{R}^m)$ egyértelműen létezik.

*Bizonyítás.* Tegyük fel, hogy $L$ és $\tilde L$ is jó, $\eta$, ill. $\tilde\eta$ hibataggal. Legyen $L^\ast := L - \tilde L$ és $p = q = \infty$. A két előállítás különbségéből

$$\frac{\|L^\ast(h)\|_\infty}{\|h\|_\infty} = \|\tilde\eta(h) - \eta(h)\|_\infty \le \|\tilde\eta(h)\|_\infty + \|\eta(h)\|_\infty \to 0 \qquad (\|h\|_\infty \to 0).$$

Válasszuk speciálisan $h := t e_i$-t, ahol $e_i$ az $i$-edik egységvektor. Mivel $\|t e_i\|_\infty = |t|$ és $L^\ast$ lineáris,

$$\frac{\|L^\ast(t e_i)\|_\infty}{\|t e_i\|_\infty} = \frac{|t| \cdot \|L^\ast(e_i)\|_\infty}{|t|} = \|L^\ast(e_i)\|_\infty .$$

Ez a **$t$-től független** szám tart nullához $t \to 0$ esetén, tehát nulla: $L^\ast(e_i) = 0$ minden $i$-re. Az $x = \sum_{i=1}^n x_i e_i$ előállítás és a linearitás miatt $L^\ast \equiv 0$, azaz $L = \tilde L$. $\square$

Ezért az $L$-t az $f$ **$a$-beli deriváltjának** nevezzük, jelölése $f'(a)$; mátrixalakja a [[concepts/analiii/jacobi-matrix|Jacobi-mátrix]].

### Lineáris leképezés deriváltja önmaga

Ha $L \in \mathcal{L}(\mathbb{R}^n, \mathbb{R}^m)$, akkor $L \in D\{a\}$ minden $a$-ban, és $L'(a) = L$. Valóban,

$$L(a+x) - L(a) = L(x) = L(x) + \eta(x)\cdot\|x\| \qquad \text{az } \eta \equiv 0 \text{ választással}.$$

Ez a differenciálhatóság alapmintája: a derivált az a lineáris leképezés, amellyel $f$ lokálisan „megegyezik".

### Absztrakt normált terek: a Fréchet-derivált

A definíció szó szerint átvihető tetszőleges normált terek közé. Legyenek $(X, \|\cdot\|_X)$, $(Y, \|\cdot\|_Y)$ normált terek és $f \in X \to Y$. Az $f$ differenciálható az $a \in \operatorname{int} D_f$ pontban, ha alkalmas $A \in \mathcal{L}(X, Y)$ korlátos lineáris leképezéssel és $\eta \in X \to Y$ függvénnyel

$$f(a+h) - f(a) = A(h) + \eta(h)\cdot\|h\|_X, \qquad \eta(h) \to 0 \ \ (\|h\|_X \to 0),$$

azaz

$$\frac{\|f(a+h) - f(a) - A(h)\|_Y}{\|h\|_X} \to 0 \qquad (\|h\|_X \to 0).$$

Az így egyértelműen létező $A$ az $f$ **Fréchet-deriváltja** $a$-ban. A véges dimenziós eset ennek az a speciális esete, amelyben $\mathcal{L}(\mathbb{R}^n, \mathbb{R}^m) \approx \mathbb{R}^{m\times n}$ miatt a derivált mátrixszal reprezentálható.

<!-- src: 04_ea_An3_2022_tavasz.pdf -->
### A lineáris közelítés mint geometriai kép

A definíció tartalma szemléletesen: az $a$ pont körüli $h\mapsto A\cdot h$ **lineáris leképezés** jól közelíti az $f(a+h)-f(a)$ megváltozást, ha $h\approx\theta_n$. Egyváltozós, ill. $\mathbb{R}^2\to\mathbb{R}$ esetben ennek geometriai megfelelője az érintőegyenes, ill. az [[concepts/analiii/fuggvenygrafikon-erintosikja|érintősík]]: a totális differenciálhatóság pontosan azt garantálja, hogy a grafikonnak van a pontban minden irányban elsőrendben illeszkedő érintő affin sokasága.

### Feladatok

Módszer (definícióból): (1) kifejtjük $f(a+h)-f(a)$-t; (2) a $h$-ban lineáris tagokból felírjuk $L(h)=Ah$-t; (3) megmutatjuk, hogy $\dfrac{\|f(a+h)-f(a)-Ah\|}{\|h\|}\to0$ — a számlálót felülről becsüljük, tipikusan a $\|\cdot\|_\infty$ normában ($|x|,|y|\le\|(x,y)\|_\infty$), majd közrefogás (az alsó korlát $0$); (4) ellenőrzés: a parciális deriváltak folytonosak $\Rightarrow$ $f\in D$, és $f'=$ Jacobi-mátrix.

- $f=2x^2+3xy-y^2$, $a=(1,2)$: $f(a+h)-f(a)=\underbrace{10x-y}_{\text{lineáris}}+\underbrace{2x^2+3xy-y^2}_{\text{maradék}}$ ($h=(x,y)$); $|2x^2+3xy-y^2|\le6\|h\|_\infty^2$, a hányados $\le6\|h\|_\infty\to0$. Tehát $f'(1,2)=[10\ \ -1]$; az ellenőrzés: $\operatorname{grad}f=(4x+3y,\,3x-2y)=(10,-1)$ polinomok, folytonosak.
- $f=x^3+xy$, $a=(2,3)$: $f'(a)=[15\ \ 2]$ ($(3x^2+y,\,x)$).
- $f=(x^2+xy,\;y^2-2x^2)$, $a=(-1,1)$: $f'(a)=\begin{bmatrix}-1&-1\\4&2\end{bmatrix}$ (Jacobi: $\begin{bmatrix}2x+y&x\\-4x&2y\end{bmatrix}$).
- $f=(x^2+y^2,\,x^2-y^2)$, $a=(1,2)$: $f'(a)=\begin{bmatrix}2&4\\2&-4\end{bmatrix}$.
- $f=(x^3+xy,\;x-y^2,\;1+y)$, $a=(1,2)$: $f'(a)=\begin{bmatrix}5&1\\1&-4\\0&1\end{bmatrix}\in\mathbb{R}^{3\times2}$; a maradék $(x^3+3x^2+xy,\,-y^2,\,0)$, 1-es normája $\le\|h\|_\infty^3+5\|h\|_\infty^2$ (az $xy$ és $y^2$ tagokat $\|h\|_\infty^2$-tel becsülve), a hányados $\le\|h\|_\infty^2+5\|h\|_\infty\to0$.
- $f=x^4+y^4$ a $(0,0)$-ban: $f'(0,0)=(0,0)$, mert a maradék $O(\|h\|^4)$.
- **Nem differenciálható.** $\sqrt{x^2+y^2}$ az origóban (nincs parciális derivált: a norma csúcsos); $\dfrac{xy-y}{(x-1)^2+y^2}$ ($0$ az $(1,0)$-ban): $=\dfrac{y(x-1)}{(x-1)^2+y^2}$, nem is folytonos ott; $\sqrt{|xy|}$ az origóban: folytonos és $\partial_1f=\partial_2f=0$, de $\dfrac{\sqrt{|xy|}}{|x|+|y|}$ az $x=y$ mentén $\tfrac12\ne0$.
- **Parciálisok nem folytonosak, mégis differenciálható.** $f=(x^2+y^2)\sin\tfrac1{x^2+y^2}$: $f'(0,0)=(0,0)$, mert $\dfrac{|f|}{\|h\|_2}=\|h\|_2\bigl|\sin\tfrac1{\|h\|^2}\bigr|\to0$ (itt a $2$-es norma kényelmes).
- **Tipikus hiba:** nem ágankénti függvényt is ágankénti módon kell deriválni a találkozási pontban; nem „csak" a képlet deriváltja számít.

- **$\mathbb{R}^2\to\mathbb{R}^2$ eset (gyak 5. lap).** $f\in D\{a\}\iff\exists A\in\mathbb{R}^{2\times2}:\ \lim_{h\to0}\dfrac{\|f(a+h)-f(a)-Ah\|^{(2)}}{\|h\|^{(1)}}=0$, a két normát külön is lehet választani. Példa: $f=(x^2+xy,\,y^2-2x^2)$, $a=(-1,1)$: $f(a+h)-f(a)=\begin{bmatrix}-1&-1\\4&2\end{bmatrix}h+\begin{bmatrix}h_1^2+h_1h_2\\-2h_1^2+h_2^2\end{bmatrix}$ (lineáris tag + maradéktag); a számlálóban az 1-es, a nevezőben a $\|\cdot\|_\infty$ norma: $\dfrac{3h_1^2+|h_1h_2|+h_2^2}{\|h\|_\infty}\le5\|h\|_\infty\to0$. Skalárértékű $2x^2+3xy-y^2$-nél a becslés $6\|h\|_\infty$.
- **Folytonos, parciálisan deriválható, nem differenciálható: $\sqrt{|xy|}$ (gyak 5. lap).** $\|\cdot\|_\infty$-ben $\sqrt{|xy|}\le\|(x,y)\|_\infty<\varepsilon$ ($\delta\le\varepsilon$), tehát folytonos; $\partial_1f(0,0)=(x\mapsto0)'=0=\partial_2f(0,0)$; ha differenciálható lenne, a határérték $\lim\frac{\sqrt{|h_1h_2|}}{\sqrt{h_1^2+h_2^2}}=0$ volna, de az $(\tfrac1n,\tfrac1n)$ sorozaton $\tfrac1{\sqrt2}$. A tanulság: a pontbeli folytonosságból és a parciálisok létezéséből sem következik a totális deriválhatóság.
- **$\dfrac{xy^2}{x^2+y^2}$ nem differenciálható (gyak 6. lap).** Itt minden irányban létezik az iránymenti derivált ($\cos\alpha\sin^2\alpha$), $f'(0,0)$ csak $(0,0)$ lehetne, de $\dfrac{|h_1|h_2^2}{(h_1^2+h_2^2)^{3/2}}\to\tfrac1{\sqrt8}$ az $x=y$ mentén. Részletek: [[concepts/analiii/iranymenti-derivalt]].
- **Differenciálható, pedig a parciálisok nem folytonosak (gyak 6. lap).** $f=(x^2+y^2)\sin\tfrac1{x^2+y^2}$: $A=[\partial_xf(0,0)\ \ \partial_yf(0,0)]=[0\ \ 0]$, és a 2-es normában $\dfrac{|f|}{\|(x,y)\|}\le\sqrt{x^2+y^2}\to0$. A $\partial_xf,\partial_yf\notin C\{(0,0)\}$ az $x_n=y_n=\tfrac1{2\sqrt{n\pi}}$ sorozattal látszik: $\partial_xf(x_n,y_n)=-2\sqrt{n\pi}\to-\infty$ ($\sin2n\pi=0$, $\cos2n\pi=1$).

## Kapocs

- [[concepts/analiii/fuggvenygrafikon-erintosikja]] — a differenciálhatóság geometriai jelentése $\mathbb{R}^2\to\mathbb{R}$ függvényekre.
- [[concepts/analiii/jacobi-matrix]] — a derivált mátrixreprezentációja, a gradiens és a deriváltvektor.
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — a definíció visszavezetése $m$ darab skalárértékű függvényre.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — hova illeszkedik ez a fogalom a folytonosság, az iránymenti és a parciális deriválhatóság mellé.
- [[concepts/analiii/normalt-vektorter]] — a keret, amelyben a definíció megfogalmazódik.
- [[concepts/analiii/ekvivalens-normak]] — ez teszi a definíciót normafüggetlenné.
- [[concepts/analii/derivalt-fogalma]] — az egyváltozós eset, amelyet a definíció általánosít.
- [[concepts/analiii/korlatos-linearis-lekepezes]] — a $\mathcal{L}(X,Y)$ tér és az operátornorma, amivel a derivált dolgozik
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
