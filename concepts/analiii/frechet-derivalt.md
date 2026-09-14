---
tags: [concept]
sources: [SimonP-Anal2.pdf, 04_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 3.1. szakasz és 3.2. i)–iii) megjegyzés"]
derivation: source
updated: 2026-09-14
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

## Kapocs

- [[concepts/analiii/fuggvenygrafikon-erintosikja]] — a differenciálhatóság geometriai jelentése $\mathbb{R}^2\to\mathbb{R}$ függvényekre.
- [[concepts/analiii/jacobi-matrix]] — a derivált mátrixreprezentációja, a gradiens és a deriváltvektor.
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — a definíció visszavezetése $m$ darab skalárértékű függvényre.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — hova illeszkedik ez a fogalom a folytonosság, az iránymenti és a parciális deriválhatóság mellé.
- [[concepts/analiii/normalt-vektorter]] — a keret, amelyben a definíció megfogalmazódik.
- [[concepts/analiii/ekvivalens-normak]] — ez teszi a definíciót normafüggetlenné.
- [[concepts/analii/derivalt-fogalma]] — az egyváltozós eset, amelyet a definíció általánosít.
- [[concepts/analiii/korlatos-linearis-lekepezes]] — a $\mathcal{L}(X,Y)$ tér és az operátornorma, amivel a derivált dolgozik
