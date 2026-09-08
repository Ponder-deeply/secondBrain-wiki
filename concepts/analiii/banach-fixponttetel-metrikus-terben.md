---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.5.2. Tétel (Banach–Tyihonov–Cacciopoli)"]
derivation: source
updated: 2026-09-07
---

# Banach-fixponttétel teljes metrikus térben

A fixponttétel általános alakja: teljes metrikus tér **zárt** részhalmazán minden kontrakciónak pontosan egy fixpontja van. Az Analízis II-ben tanult, $[a,b] \to [a,b]$ kontrakciókra szóló változat ennek a speciális esete.

## Tartalom

### Kontrakció

**Definíció.** Legyen $(M,d)$ metrikus tér és $H \subset M$. Az $f : H \to H$ leképezés **kontrakció**, ha létezik olyan $0 < \alpha < 1$, hogy bármely $x, y \in H$ pontokra

$$d\bigl(f(x), f(y)\bigr) \leq \alpha \cdot d(x,y).$$

### A tétel

**Tétel (Banach-féle fixponttétel).** Legyen $(M,d)$ **teljes** metrikus tér, $Z \subset M$ **zárt** halmaz, és $f : Z \to Z$ kontrakció. Ekkor $f$-nek van $Z$-ben egyértelmű fixpontja, azaz egyetlen olyan $x \in Z$ pont, amelyre $f(x) = x$.

### Hogyan általánosít

Az [[concepts/analii/banach-fixponttetel]] alakja $f : [a,b] \to [a,b]$ kontrakciókra szól; ott a teljesség és a zártság a valós számok konkrét tulajdonságaiból jött ($\mathbb{R}$ teljes, $[a,b]$ zárt). Itt ugyanaz a két feltétel absztrakt formában szerepel, és ez az, ami a tételt használhatóvá teszi függvényterekben is: a $Z$ lehet például $C[a,b]$ egy zárt részhalmaza, amikor a „pont" egy függvény, és a fixpont egy differenciálegyenlet megoldása. A hibabecslés — a bizonyítás negyedik lépésének egyenlőtlenségéből $m \to \infty$ határátmenettel — ugyanúgy adódik, mint a valós esetben.

Tipikus alkalmazások: egyenletrendszerek megoldása iterációval, az inverzfüggvény-tétel bizonyítása, differenciálegyenletek megoldásának létezése (Picard–Lindelöf-tétel).

### Bizonyítás

Legyen $y_0 \in Z$ tetszőleges, és $y_{n+1} = f(y_n)$. Állítjuk, hogy ez a sorozat Cauchy, tehát konvergens, a limesze $Z$-ben van, és fixpont.

Legyen $h_n = d(y_n, y_{n+1})$. Ekkor

$$h_{n+1} = d\bigl(f(y_n), f(y_{n+1})\bigr) \leq \alpha \cdot d(y_n, y_{n+1}) = \alpha h_n,$$

így indukcióval $h_n \leq \alpha^n h_0$. Legyen $\varepsilon > 0$ tetszőleges és $n_0$ olyan nagy, hogy $\frac{\alpha^{n_0}}{1-\alpha}h_0 < \varepsilon$. Ha $m > n > n_0$, akkor a háromszög-egyenlőtlenséget lánccá fűzve és mértani sorral becsülve

$$d(y_n, y_m) \leq \sum_{k=n}^{m-1} h_k \leq \sum_{k=n}^{m-1}\alpha^k h_0 = \frac{\alpha^n - \alpha^m}{1-\alpha}h_0 < \frac{\alpha^{n_0}}{1-\alpha}h_0 < \varepsilon.$$

Tehát $(y_n)$ Cauchy, és $M$ teljessége miatt konvergens. Legyen $x = \lim y_n$; mivel $Z$ zárt, $x \in Z$. Bármely $n$-re

$$d\bigl(x, f(x)\bigr) \leq d(x, y_{n+1}) + d\bigl(f(y_n), f(x)\bigr) \leq d(x, y_{n+1}) + \alpha\, d(x, y_n) \to 0,$$

tehát $d(x, f(x)) = 0$, azaz $f(x) = x$.

### Hibabecslés

A bizonyítás $d(y_n,y_{n+s}) \leq \frac{\alpha^n}{1-\alpha}d(y_0,y_1)$ becsléséből $s\to\infty$ határátmenettel adódik az **a priori** hibakorlát:

$$d(y_n,x) \leq \frac{\alpha^n}{1-\alpha}\cdot d(y_0,y_1) \qquad (n\in\mathbb{N}).$$

Ugyanez az eltolt sorozatra alkalmazva az **a posteriori** alakot adja — lásd [[concepts/analiii/fixponttetel-gombon]].

*Egyértelműség.* Ha $x$ és $x'$ is fixpont, akkor $d(x,x') = d\bigl(f(x),f(x')\bigr) \leq \alpha\, d(x,x')$, ami $\alpha < 1$ mellett csak $d(x,x') = 0$ esetén állhat fenn. $\blacksquare$

## Kapocs

- [[concepts/analii/banach-fixponttetel]] — a valós intervallumon szóló változat, hibabecsléssel és fixpont-iterációs példákkal
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a teljesség, amit a bizonyítás használ
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a $Z$ zártsága teszi lehetővé, hogy a limesz $Z$-ben maradjon
- [[concepts/analiii/metrikus-ter]] — az általánosítás terepe
- [[concepts/analiii/fixponttetel-gombon]] — a zárt gömbre szűkített változat, hibabecslések és az élesség
- [[concepts/analiii/linearis-lekepezes-kontrakcio-volta]] — mikor kontrakció egy affin leképezés $\mathbb{K}^n$-en
- [[concepts/nummodi/banach-fixponttetel-rn]] — a tétel mátrixiterációkra alkalmazva
