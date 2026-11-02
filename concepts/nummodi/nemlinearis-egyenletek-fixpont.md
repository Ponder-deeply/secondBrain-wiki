---
tags: [concept]
sources: [NM1_ea11.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Nemlineáris egyenletek: létezés és fixpont-iteráció

Az $f(x) = 0$ egyenlet gyökét keressük, gyakran $x = \varphi(x)$ fixpont-alakban. A gyök létezését a Bolzano-tétel és a Brouwer-féle fixponttétel, a fixpont-iteráció konvergenciáját a Banach-féle fixponttétel $[a;b]$-re adja, amelynek feltétele $|\varphi'| < 1$-gyel ellenőrizhető.

## Tartalom

### A feladat

Keressük egy $f : \mathbb{R} \to \mathbb{R}$ nemlineáris függvény gyökét (zérushelyét): $f(x^*) = 0$, $x^* = ?$ — Létezik? Egy vagy több? Ekvivalensen (általában) átfogalmazható: keressük egy $\varphi : \mathbb{R} \to \mathbb{R}$ függvény **fixpontját**, $x^* = \varphi(x^*)$, és ezt az $x_{k+1} = \varphi(x_k)$ iterációval közelítjük — a LER-ek $x = Bx + c$ iterációjának analógiájára.

### Létezést biztosító állítások

**Bolzano-tétel** (biz. nélkül; lásd Analízis). Ha $f \in C[a;b]$ és $f(a)\cdot f(b) < 0$, akkor $\exists\, x^* \in (a;b)$: $f(x^*) = 0$. (A konstruktív bizonyítás az [[concepts/nummodi/intervallumfelezes|intervallumfelezés]].)

**Egyértelműség.** Ha ráadásul $f \in D(a;b)$ és $f' > 0$ (vagy $< 0$), akkor a gyök egyértelmű, mert $f$ szigorúan monoton.

**Brouwer-féle fixponttétel.** Ha $\varphi : [a;b] \to [a;b]$ és $\varphi \in C[a;b]$, akkor $\exists\, x^* \in [a;b]$: $\varphi(x^*) = x^*$.

**Biz.** Legyen $g(x) := x - \varphi(x)$; $g$ folytonos.

1. $\varphi(a), \varphi(b) \in [a;b]$ miatt $g(a) = a - \varphi(a) \le 0$ és $g(b) = b - \varphi(b) \ge 0$, így $g(a)\cdot g(b) \le 0$.
2. Ha $g(a)\cdot g(b) = 0$, akkor $g(a) = 0$ vagy $g(b) = 0$, azaz $a$ vagy $b$ fixpont.
3. Ha $g(a)\cdot g(b) < 0$, akkor a Bolzano-tétel szerint $\exists\, x^* \in (a;b)$: $g(x^*) = x^* - \varphi(x^*) = 0$, azaz $\varphi(x^*) = x^*$. $\square$

(A Brouwer-tétel csak létezést ad, egyértelműséget és konvergenciát nem.)

### Kontrakció $[a;b]$-n

**Definíció.** A $\varphi : [a;b] \to \mathbb{R}$ leképezés **kontrakció** $[a;b]$-n, ha $\exists\, q \in [0,1)$:

$$|\varphi(x) - \varphi(y)| \le q\,|x - y| \qquad \forall x, y \in [a;b].$$

$q$ a kontrakciós együttható. A kontrakciós tulajdonság függ az intervallumtól.

**Állítás (elégséges feltétel a kontrakcióra).** Ha $\varphi \in C^1[a;b]$ és $|\varphi'(x)| < 1$ minden $x \in [a;b]$-re, akkor $\varphi$ kontrakció $[a;b]$-n.

**Biz.** $|\varphi'|$ folytonos a kompakt $[a;b]$-n, így felveszi a maximumát: $q := \max_{x\in[a;b]}|\varphi'(x)| < 1$. Tetszőleges $x < y$ pontokra a [[concepts/analii/kozeptertekek|Lagrange-középértéktétel]] szerint $\exists\, \xi \in (x;y)$:

$$|\varphi(x) - \varphi(y)| = |\varphi'(\xi)|\cdot|x - y| \le q\,|x - y|. \ \square$$

(A maximum felvétele a lényeg: pontonként $|\varphi'| < 1$-ből így lesz egységes $q < 1$.)

### Banach-féle fixponttétel $[a;b]$-re (biz. nélkül)

**Tétel.** Ha $\varphi : [a;b] \to [a;b]$ kontrakció $q$ együtthatóval, akkor

1. $\exists!\, x^* \in [a;b]$: $x^* = \varphi(x^*)$;
2. $\forall x_0 \in [a;b]$ esetén az $x_{k+1} = \varphi(x_k)$ sorozat konvergens és $\lim x_k = x^*$;
3. hibabecslések: $|x_k - x^*| \le q^k|x_0 - x^*| \le q^k(b - a)$, valamint $|x_k - x^*| \le \dfrac{q^k}{1-q}|x_1 - x_0|$.

A bizonyítás az [[concepts/nummodi/banach-fixponttetel-rn|$\mathbb{R}^n$-beli tételé]] $n = 1$-re, $[a;b]$-n.

**Következmény.** Ha $\varphi : [a;b] \to [a;b]$, $\varphi \in C^1[a;b]$ és $|\varphi'(x)| < 1$ $\forall x \in [a;b]$, akkor az $x_{k+1} = \varphi(x_k)$ iteráció minden $x_0 \in [a;b]$-re konvergens. (Nem szükséges feltétel: ha valahol $|\varphi'| \ge 1$, a sorozat attól még konvergálhat.)

### Lokális fixponttétel

**Tétel.** Legyen $\varphi \in C^1[a;b]$, és legyen $\xi \in [a;b]$, $\delta > 0$ olyan, hogy $|\varphi'(x)| \le q < 1$ minden $x \in [\xi - \delta; \xi + \delta] \subset [a;b]$-re. Ha $\exists\, r$: $0 < r \le \delta$, amelyre $|\varphi(\xi) - \xi| \le (1-q)r$ ($\xi$ a fixpont elég jó közelítése), akkor $\varphi$ kontrakció $[\xi - r; \xi + r]$-en, és ezt az intervallumot önmagába képezi.

**Biz.** A kontrakció a fenti állításból következik $[\xi - \delta; \xi + \delta]$-n, így a részintervallumon is. Tetszőleges $x \in [\xi - r; \xi + r]$-re

$$|\varphi(x) - \xi| \le |\varphi(x) - \varphi(\xi)| + |\varphi(\xi) - \xi| \le q\underbrace{|x - \xi|}_{\le r} + (1-q)r \le r. \ \square$$

Ekkor a Banach-tétel feltételei teljesülnek $[\xi - r; \xi + r]$-en.

### Példa: $x = \cos x$ a $[0;1]$-en

1. $\varphi'(x) = -\sin x < 0$, tehát $\varphi$ szigorúan fogyó, $\varphi([0;1]) = [\cos 1; 1] \subset [0;1]$.
2. $q = \max_{[0;1]}|-\sin\xi| = \sin 1 \approx 0{,}8415 < 1$, tehát kontrakció.
3. A Banach-tétel szerint egyértelmű fixpont van, és a sorozat konvergál; $|x_k - x^*| \le 0{,}8415^k$.
4. $0{,}1$ pontossághoz $0{,}8415^k < \tfrac{1}{10} \iff k > \tfrac{-1}{\lg 0{,}8415} \approx 13{,}34$ lépés kell — lassú. (A tapasztalati kontrakciós együttható $\approx 0{,}6736$.)

Egyszerű iterációk: $x_{k+1} = x_k^2$ a $0 \le x_0 < 1$-re $0$-hoz, $x_0 = 1$-re $1$-hez tart; $x_{k+1} = \sqrt{x_k}$ a $0 < x_0 \le 1$-re $1$-hez tart. A fixpontok „vonzása” a $|\varphi'|$ értékétől függ.

### Vizsgán (25. tétel)

- **a)** a feladat; Bolzano-tétel (kimondás); Brouwer-tétel **bizonyítással**; kontrakció $[a;b]$-n, Banach-tétel (kimondás).
- **b)** az elégséges feltétel ($|\varphi'| < 1 \Rightarrow$ kontrakció) bizonyítása; a [[concepts/nummodi/konvergenciarend|konvergenciarend]] fogalma és tulajdonságai; a magasabb rendű konvergencia tételének bizonyítása (ott).

## Kapocs

- [[concepts/nummodi/konvergenciarend]] — a 25. b) második fele: konvergenciarend, $p$-edrendű fixpont-iterációk
- [[concepts/nummodi/banach-fixponttetel-rn]] — ugyanez a tétel $\mathbb{R}^n$-ben, bizonyítással
- [[concepts/nummodi/intervallumfelezes]] — a Bolzano-tétel konstruktív bizonyítása
- [[concepts/nummodi/newton-modszer]] — speciális fixpont-iteráció, $\varphi(x) = x - f(x)/f'(x)$
- [[concepts/analii/kozeptertekek]] — Lagrange-középértéktétel
