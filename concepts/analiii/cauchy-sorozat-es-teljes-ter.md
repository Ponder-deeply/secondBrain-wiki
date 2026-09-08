---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-07
---

# Cauchy-sorozat, teljes metrikus tér, Banach-tér

A Cauchy-tulajdonság a konvergencia *belső* megfogalmazása: nem hivatkozik a limeszre. Teljes az a tér, amelyben ez elég is a konvergenciához — a teljes normált vektorteret Banach-térnek hívjuk.

## Tartalom

### Cauchy-tulajdonság

**Definíció.** Az $(a_n)$ pontsorozat a $(H,d)$ metrikus térben **Cauchy-tulajdonságú**, ha

$$\forall \varepsilon > 0\ \ \exists n_0\ \ \forall m, n > n_0:\quad d(a_m, a_n) < \varepsilon.$$

**Trivialitás.** Minden konvergens pontsorozat Cauchy-tulajdonságú. Megfordítva: ha egy Cauchy-sorozatnak van konvergens **részsorozata**, akkor maga a sorozat is konvergens, ugyanoda.

*Bizonyítás.* Legyen $b = \lim a_n$ és $\varepsilon > 0$. Van olyan $n_0$, hogy $n > n_0$-ra $d(a_n,b) < \varepsilon/2$. Ekkor $m,n > n_0$ esetén $d(a_m,a_n) \leq d(a_m,b) + d(a_n,b) < \varepsilon$. $\blacksquare$

### Teljes tér, Banach-tér

**Definíció.**

- Egy metrikus tér **teljes**, ha érvényes benne a Cauchy-kritérium, azaz minden Cauchy-sorozat konvergens.
- A teljes normált vektortereket **Banach-tér**nek hívjuk.

**Példák.** $\mathbb{R}$ a szokásos $d(x,y)=|x-y|$ távolsággal teljes. $\mathbb{Q}$ ugyanezzel a metrikával **nem** teljes: a $\sqrt 2$ tizedesjegyeiből képzett $1;\,1{,}4;\,1{,}41;\,1{,}414;\dots$ sorozat $\mathbb{Q}$-ban is Cauchy, de nincs benne limesze.

### $\mathbb{R}^p$ Banach-tér

**Tétel.** $\mathbb{R}^p$ bármilyen normával teljes, tehát Banach-tér.

*Bizonyítás.* A normák ekvivalenciája miatt a Cauchy-tulajdonság minden normában ugyanazt jelenti; dolgozzunk az $L^2$ normával. Ha $(\mathbf{a}_n)$ Cauchy, akkor minden $1 \leq i \leq p$-re $|a_{n,i}-a_{m,i}| \leq |\mathbf{a}_n - \mathbf{a}_m|$, tehát az $i$-edik koordinátasorozat is Cauchy, így $\mathbb{R}$ teljessége miatt konvergens. A koordinátánkénti konvergencia miatt $(\mathbf{a}_n)$ konvergens. $\blacksquare$

### $C[a,b]$ a maximumnormával Banach-tér

**Tétel.** $\bigl(C[a,b], \|\cdot\|_\infty\bigr)$ teljes.

*Bizonyítás.* Legyen $(f_n)$ Cauchy:

$$\forall \varepsilon>0\ \exists n_0\ \forall n,m>n_0: \quad \|f_n-f_m\| = \max_{x\in[a,b]}|f_n(x)-f_m(x)| < \varepsilon. \tag{1}$$

Minden rögzített $x$-re az $(f_n(x))$ számsorozat Cauchy, tehát konvergens; legyen $g(x)$ a limesze, azaz $f_n \to g$ pontonként. Az (1)-ben $m \to \infty$ határátmenettel $\max_x |f_n(x)-g(x)| \leq \varepsilon$ minden $n > n_0$-ra, tehát $\|f_n - g\| \to 0$, vagyis $f_n \to g$ egyenletesen. Folytonos függvények egyenletes limesze folytonos, így $g \in C[a,b]$. $\blacksquare$

### Ellenpéldák: az $L^1$ norma nem teljes

- A $\bigl(C[-1,1], \|\cdot\|_1\bigr)$ térben az
$$f_n(x) = \begin{cases} -1 & x < -\tfrac1n \\ nx & -\tfrac1n \leq x \leq \tfrac1n \\ 1 & x > \tfrac1n \end{cases}$$
sorozat Cauchy, de nem tart semmilyen folytonos függvényhez (a „limesz" az előjelfüggvény lenne). Tehát $\bigl(C[-1,1],\|\cdot\|_1\bigr)$ **nem** Banach-tér.

- Még a Riemann-integrálható függvények $\bigl(R[0,1], \|\cdot\|_1\bigr)$ tere sem az. (Itt előbb faktorizálni kell az $N = \{f : \int_a^b|f| = 0\}$ altérrel, hiszen nemcsak a konstans $0$-nak tűnik el az abszolút integrálja.) Konstruáljunk **kövér Cantor-halmazt**: $H_1 = [0,1]$, és ha $H_n$ zárt intervallumok uniója, akkor mindegyik középső $\frac{1}{2^n}$ részét vegyük ki; legyen $C = \bigcap H_n$. Ha $f_n$ a $H_n$, $g$ pedig a $C$ karakterisztikus függvénye, akkor $(f_n)$ Cauchy, a limesze $g$ lenne, de $g$ nem Riemann-integrálható.

Ez a hiányosság mutatja, hogy a Riemann-integrál nem elég általános — a kiterjesztése a Mértékelmélet tárgya.

## Kapocs

- [[concepts/analiii/konvergencia-metrikus-terben]] — a limesz fogalma, amit a Cauchy-tulajdonság belsővé tesz
- [[concepts/analiii/ekvivalens-normak]] — ezért normafüggetlen a Cauchy-tulajdonság véges dimenzióban
- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — a teljesség első nagy alkalmazása
- [[concepts/analiii/baire-kategoriatetel]] — a teljesség másik nagy következménye
- [[concepts/analiii/skalaris-szorzat-ter]] — a teljes euklideszi tér a Hilbert-tér
- [[concepts/analiii/metrikus-terek-szorzata]] — a szorzattér akkor teljes, ha mindkét tényezője az
- [[concepts/analiii/felmetrikus-ter]] — az $R[a,b]$-beli faktorizálás pontos kerete
- [[concepts/analii/integralhato-fuggvenyek]] — a Riemann-integrálhatóság, amelynek korlátaira az utolsó példa mutat rá
