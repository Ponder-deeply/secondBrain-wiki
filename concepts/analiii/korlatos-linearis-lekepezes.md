---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.1. vi) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Korlátos lineáris leképezés és operátornorma

Normált terek közötti lineáris leképezés akkor korlátos, ha $\|f(x)\| \le M\|x\|$ alkalmas $M$-mel. Minden ilyen leképezés egyenletesen folytonos, és a legkisebb ilyen $M$ maga is norma az $\mathcal{L}(X,Y)$ téren: ez az operátornorma.

## Tartalom

### Definíció

Legyenek $(X,\|\cdot\|_\bullet)$ és $(Y,\|\cdot\|_*)$ normált terek a $\mathbb{K}$ test felett. Az $f : X \to Y$ függvény **korlátos lineáris leképezés**, ha

1. **lineáris:** $f(x + \lambda y) = f(x) + \lambda f(y)$ ($x,y \in X$, $\lambda \in \mathbb{K}$);
2. **korlátos:** van olyan $M \ge 0$, hogy $\|f(x)\|_* \le M\|x\|_\bullet$ minden $x \in X$-re.

Minden ilyen $M$ számot a leképezés **korlátjának** nevezünk. Az összes korlátos lineáris leképezés halmazát $\mathcal{L}(X,Y)$ jelöli.

### Egyenletes folytonosság

A linearitás és a korlátosság együtt Lipschitz-tulajdonságot ad:

$$\|f(x) - f(y)\|_* = \|f(x-y)\|_* \le M\|x-y\|_\bullet \qquad (x,y \in X),$$

tehát **minden korlátos lineáris leképezés egyenletesen folytonos** — lásd [[concepts/analiii/egyenletes-folytonossag-metrikus-terben]]. A „korlátos" jelző itt tehát pontosan a folytonosságot kódolja.

### Az operátornorma

Az $\mathcal{L}(X,Y)$ halmaz a szokásos függvényműveletekkel vektortér $\mathbb{K}$ felett. Legyen

$$K_f := \{M \ge 0 : \|f(x)\|_* \le M\|x\|_\bullet \ (x \in X)\}, \qquad \|f\| := \inf K_f.$$

Az $f \mapsto \|f\|$ leképezés **norma** (a $\|\cdot\|_\bullet$, $\|\cdot\|_*$ normák által **indukált** norma), tehát $(\mathcal{L}(X,Y), \|\cdot\|)$ normált tér. Sőt, az infimum **minimum**:

$$\|f\| = \min K_f, \qquad\text{következésképpen}\qquad \|f(x)\|_* \le \|f\|\cdot\|x\|_\bullet \quad (x \in X).$$

Az operátornorma tehát $f$ **legkisebb korlátja**.

**Hibabecslés.** Ha egy modellben $f(x)$-et kell kiszámítani, de $x$-nek csak egy $z$ közelítését ismerjük $\|x-z\|_\bullet < \varepsilon$ hibakorláttal, akkor az öröklődő hiba

$$\|f(x) - f(z)\|_* = \|f(x-z)\|_* \le \|f\|\cdot\|x-z\|_\bullet \le \|f\|\cdot\varepsilon.$$

Az operátornorma tehát a lineáris modell **hibafelerősítési tényezője**.

### Mátrixnormák

Legyen $(X,\|\cdot\|_\bullet) := (\mathbb{K}^s,\|\cdot\|_p)$, $(Y,\|\cdot\|_*) := (\mathbb{K}^m,\|\cdot\|_q)$, és egy $A \in \mathbb{K}^{m\times s}$ mátrixszal

$$f_A(x) := Ax \qquad (x \in \mathbb{K}^s).$$

Ekkor $f_A \in \mathcal{L}(\mathbb{K}^s,\mathbb{K}^m)$ — először $p = q = 1$-re egyszerű számolással, majd a $\|\cdot\|_p$ normák [[concepts/analiii/ekvivalens-normak|ekvivalenciája]] miatt minden $p,q$-ra. Megfordítva, a lineáris algebrából ismert, hogy $\mathcal{L}(\mathbb{K}^s,\mathbb{K}^m)$ **minden** eleme ilyen alakú: minden $f$-hez egyértelműen van olyan $A$, amellyel $f = f_A$. Ezért értelmes a

$$\|A\|_{(p,q)} := \|f_A\|$$

**mátrixnorma**, amelyre $\|Ax\|_q \le \|A\|_{(p,q)}\|x\|_p$, és $\|A\|_{(p,q)}$ a legkisebb ilyen konstans. A $p = q$ esetben $\|A\|_{(p)}$-t írunk. $A = (a_{ik})$ mellett

$$\|A\|_{(\infty)} = \max\Bigl\{\sum_{k=1}^{s}|a_{ik}| : i = 1,\dots,m\Bigr\} \quad\text{(sornorma)},$$

$$\|A\|_{(1)} = \max\Bigl\{\sum_{i=1}^{m}|a_{ik}| : k = 1,\dots,s\Bigr\} \quad\text{(oszlopnorma)},$$

a $\|A\|_{(2)}$ **spektrálnormára** pedig csak becslés adódik:

$$\|A\|_{(2)} \le \sqrt{\sum_{i=1}^{m}\sum_{k=1}^{s}|a_{ik}|^2}$$

(a jobb oldal a Frobenius-norma). Ez a különbség lényeges: $2\times 2$-es esetben a $\max\{|\alpha|+|\beta|,\ |\gamma|+|\delta|\}$ és a $\max\{|\alpha|+|\gamma|,\ |\beta|+|\delta|\}$ együttható valóban a **legkisebb** korlát a $\|\cdot\|_\infty$, illetve a $\|\cdot\|_1$ normára, a Frobenius-féle $\sqrt{|\alpha|^2+|\beta|^2+|\gamma|^2+|\delta|^2}$ viszont a $\|\cdot\|_2$ normára már nem feltétlenül minimális.

### Miért fontos

A [[concepts/analiii/frechet-derivalt|Fréchet-derivált]] definíciója korlátos lineáris leképezéssel közelíti a megváltozást; a derivált mátrixalakja a [[concepts/analiii/jacobi-matrix|Jacobi-mátrix]], a hozzá tartozó operátornorma pedig a differenciálszámítás becsléseinek (középértéktétel, Taylor-formula maradéktagja, a fixponttételes bizonyítások kontrakciós konstansa) alapmennyisége.

## Kapocs

- [[concepts/analiii/normalt-vektorter]] — a norma fogalma, amire az egész építkezés épül
- [[concepts/analiii/ekvivalens-normak]] — ezért független a korlátosság a $p,q$ paraméterektől
- [[concepts/analiii/egyenletes-folytonossag-metrikus-terben]] — a Lipschitz-tulajdonság következménye
- [[concepts/analiii/frechet-derivalt]] — a derivált mint korlátos lineáris leképezés
- [[concepts/analiii/jacobi-matrix]] — a leképezést reprezentáló mátrix
