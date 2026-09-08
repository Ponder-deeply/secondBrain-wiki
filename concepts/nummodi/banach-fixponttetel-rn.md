---
tags: [concept]
sources: [NM1_ea08.pdf]
derivation: source
updated: 2026-08-05
---

# Banach-féle fixponttétel $\mathbb{R}^n$-re

A Banach-féle fixponttétel az [[concepts/nummodi/iteracios-modszerek-ler|iterációs módszerek]] konvergenciájának elméleti alapja: megmutatja, hogy kontrakciós leképezésnek egyértelműen létezik fixpontja, és a fixpont-iteráció minden kezdőértékből konvergens.

## Definíciók

**Definíció — fixpont:**

Az $x^* \in \mathbb{R}^n$ pontot a $\varphi: \mathbb{R}^n \to \mathbb{R}^n$ leképezés **fixpontjának** nevezzük, ha $x^* = \varphi(x^*)$. A $x = \varphi(x)$ egyenletet **fixpontegyenletnek** nevezzük.

**Definíció — kontrakció:**

A $\varphi: \mathbb{R}^n \to \mathbb{R}^n$ leképezés **kontrakció**, ha $\exists q \in [0, 1)$, hogy

$$\|\varphi(x) - \varphi(y)\| \leq q \cdot \|x - y\|, \qquad \forall x, y \in \mathbb{R}^n.$$

A $q$ értéket **kontrakciós együtthatónak** nevezzük (a kontrakció $\approx$ összehúzás).

**Állítás:** Ha $\|B\| < 1$, akkor a $\varphi(x) = Bx + c$ leképezés kontrakció:

$$\|\varphi(x) - \varphi(y)\| = \|(Bx+c) - (By+c)\| = \|B(x-y)\| \leq \underbrace{\|B\|}_{\,:=\,q\,<\,1} \cdot \|x - y\|. \quad\square$$

## A Banach-féle fixponttétel

**Tétel (Banach-féle fixponttétel $\mathbb{R}^n$-re):**

Ha $\varphi: \mathbb{R}^n \to \mathbb{R}^n$ kontrakció $q$ kontrakciós együtthatóval, akkor:

1. $\exists! x^* \in \mathbb{R}^n : x^* = \varphi(x^*)$ — egyértelműen létezik fixpont,
2. $\forall x^{(0)} \in \mathbb{R}^n$ esetén az $x^{(k+1)} = \varphi(x^{(k)})$ sorozat konvergens és $\lim_{k\to\infty} x^{(k)} = x^*$,
3. A következő **hibabecslések** teljesülnek:
$$\|x^{(k)} - x^*\| \leq q^k \cdot \|x^{(0)} - x^*\|,$$
$$\|x^{(k)} - x^*\| \leq \frac{q^k}{1-q} \cdot \|x^{(1)} - x^{(0)}\|.$$

**Bizonyítás vázlata:**

**(a) Folytonosság:** Kontrakciós tulajdonságból következik, hogy $\varphi$ egyenletesen folytonos ($\delta = \varepsilon/q$ választással).

**(b) Cauchy-sorozat:** Egymást követő tagok eltérésére:

$$\|x^{(k+1)} - x^{(k)}\| = \|\varphi(x^{(k)}) - \varphi(x^{(k-1)})\| \leq q \cdot \|x^{(k)} - x^{(k-1)}\| \leq \ldots \leq q^k \cdot \|x^{(1)} - x^{(0)}\|.$$

**(c) Konvergencia:** Két, $m$ távolságra lévő tag különbségére háromszög-egyenlőtlenséggel és mértani sor összegzésével:

$$\|x^{(k+m)} - x^{(k)}\| \leq q^k \cdot (q^{m-1} + \ldots + 1) \cdot \|x^{(1)} - x^{(0)}\| < \frac{q^k}{1-q} \cdot \|x^{(1)} - x^{(0)}\|.$$

Mivel $k \to \infty$ esetén $q^k \to 0$, a sorozat Cauchy-sorozat; $\mathbb{R}^n$-ben minden Cauchy-sorozat konvergens.

**(d) Fixpont:** $x^* := \lim x^{(k)}$. $\varphi$ folytonosságából: $\varphi(x^*) = \lim \varphi(x^{(k)}) = \lim x^{(k+1)} = x^*$.

**(e) Egyértelműség:** Indirekt: ha $x^* \neq x^{**}$ is fixpont, akkor $\|x^* - x^{**}\| = \|\varphi(x^*) - \varphi(x^{**})\| \leq q\|x^* - x^{**}\|$, ami $(1-q)\|x^*-x^{**}\| \leq 0$-t jelent. Ellentmondás, tehát $x^* = x^{**}$.

**(f) Hibabecslések:** Az első egyenlőtlenség: $\|x^{(k)} - x^*\| \leq q\|x^{(k-1)} - x^*\| \leq \ldots \leq q^k\|x^{(0)} - x^*\|$. A második: a (c) pontban kapott közbülső becslésből $m \to \infty$ határátmenettel (a vektornorma folytonos függvény). $\square$

## Konvergencia ekvivalens feltétele

**Következmény ($\|B\| < 1$ elégséges feltétel):** Ha $\|B\| < 1$, az $x^{(k+1)} = Bx^{(k)} + c$ iteráció konvergens minden kezdőértékre.

**Megjegyzés:** $\|B\| \geq 1$ esetén is konvergálhat az iteráció bizonyos kezdőértékekből — ez csak elégséges, nem szükséges feltétel.

**Lemma — spektrálsugár és indukált normák kapcsolata:**

$$\varrho(B) = \inf\{\|B\| : \|\cdot\| \text{ indukált mátrixnorma}\},$$

azaz $\forall \varepsilon > 0 : \exists$ indukált $\|\cdot\|$ : $\|B\| < \varrho(B) + \varepsilon$.

**Tétel (ekvivalens feltétel):** Az $x^{(k+1)} = Bx^{(k)} + c$ iteráció akkor és csak akkor konvergens minden kezdőértékre, ha

$$\varrho(B) < 1.$$

**Bizonyítás:**
- $(\Leftarrow)$: Az előző lemma alapján triviális ($\varrho(B) < 1 \Rightarrow \exists$ indukált norma amelyre $\|B\| < 1$).
- $(\Rightarrow)$: Indirekt: ha $\varrho(B) \geq 1$, legyen $|\lambda| \geq 1$ sajátérték, és $x^{(0)}$ legyen olyan, hogy $x^{(0)} - x^*$ a $\lambda$-hoz tartozó sajátvektor. Ekkor $x^{(k)} - x^* = B^k(x^{(0)} - x^*) = \lambda^k(x^{(0)} - x^*)$, tehát $\|x^{(k)} - x^*\| = |\lambda|^k \cdot \|x^{(0)} - x^*\| \not\to 0$. Ellentmondás. $\square$

## Tapasztalati kontrakciós együttható

Az iteráció futása során a $q$ kontrakciós együttható elméleti kiszámítása általában elméleti feladat. Helyette **tapasztalati kontrakciós együtthatót** alkalmazunk:

$$q^{(k)} \approx \frac{\|x^{(k+1)} - x^{(k)}\|}{\|x^{(k)} - x^{(k-1)}\|}.$$

Ennek ismeretében a hibabecslés:

$$\|x^{(k)} - x^*\| \leq \frac{q^{(k)}}{1 - q^{(k)}} \|x^{(k)} - x^{(k-1)}\|.$$

**Szabályok a tapasztalati $q^{(k)}$ alapján:**

1. Ha $|q^{(k)}| > 1$ az első néhány lépés után, az iteráció divergens — megállítható.
2. Ha a $(q^{(k)})$ sorozat nem monoton, érdemes $q \approx \sqrt{q^{(k)} q^{(k-1)}}$ mértani közepet alkalmazni.
3. Ezekkel „intelligens" iterációs módszer írható, amely menet közben ellenőrzi a pontosságot és divergencia esetén sem számol feleslegesen.

## Példa

Az iteráció $x^{(k+1)} := \frac{1}{5}\begin{bmatrix}2 & 1 \\ 1 & 2\end{bmatrix} \cdot x^{(k)} + \frac{1}{7}\begin{bmatrix}32.4 \\ \sqrt{\pi}\end{bmatrix}$ esetén

$$\|B\|_1 = \frac{3}{5} = q < 1,$$

tehát az iteráció bármely $x^{(0)} \in \mathbb{R}^2$ kezdőértékre konvergens. A hibabecslést az 1-es vektornormában írhatjuk fel.

## Kapocs

- [[concepts/nummodi/iteracios-modszerek-ler]] — iterációs módszerek általános kerete, $A=P+Q$ felbontás
- [[concepts/nummodi/jacobi-iteracio]] — Jacobi-iteráció mint a fixpont-iteráció speciális esete ($B = B_J$)
- [[concepts/nummodi/matrixnormak]] — spektrálsugár $\varrho(B)$, indukált normák
- [[concepts/nummodi/vektornormak]] — vektornorma konvergencia-fogalma
- [[concepts/nummodi/kondicioszam]] — kondíciószám kapcsolata az iteráció sebességével
