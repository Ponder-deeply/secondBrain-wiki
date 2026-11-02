---
tags: [concept]
sources: [Laki_Lecture_3.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# CDMA — kódosztásos többszörös hozzáférés

A *Code Division Multiple Access* a harmadik generációs mobilhálózatok alapja (IS-95 szabvány). Minden állomás egyfolytában, a teljes frekvenciasávon sugározhat; a jelek lineárisan összeadódnak, és a vevő a küldő ismert **töredéksorozata** (*chip sequence*) segítségével szűri ki a neki szóló hasznos jelet.

## Tartalom

### Algoritmus

1. Minden bitidőt $m$ rövid intervallumra, **töredékre** (*chip*) osztunk.
2. Minden állomáshoz egy $m$ bites kód, a **töredéksorozat** tartozik.
3. 1-es bit küldésekor az állomás a saját töredéksorozatát küldi, 0-s bitnél annak **egyes komplemensét**.
4. A csatornán a párhuzamos jelek lineárisan összeadódnak.

Következmény: $m$-szeres sávszélesség kell, vagyis a CDMA **szórt spektrumú** kommunikáció.

### Bipoláris írásmód és ortogonalitás

Szemléltetésre bipoláris kódolást használunk: bináris 0 → $-1$, bináris 1 → $+1$. Az állomások töredéksorozatai **páronként ortogonálisak**: két különböző állomás $S$ és $T$ sorozatára

$$S \cdot T = \frac{1}{m}\sum_{i=1}^{m} S_i T_i = 0,\qquad S\cdot S = 1,\qquad S\cdot\overline{S} = -1.$$

Ezért ha a vevő a csatornán mért összegjelet skalárisan szorozza a keresett állomás sorozatával, a többi állomás járuléka kiesik, és $+1$ (1-es bit), $-1$ (0-s bit) vagy $0$ (az állomás nem adott) marad.

### Walsh-mátrix

Szinkron esetben a Walsh (Hadamard) mátrix sorai vagy oszlopai kölcsönösen ortogonális töredéksorozat-halmazt adnak:

$$H(2^1) = \begin{bmatrix}1 & 1\\ 1 & -1\end{bmatrix},\qquad H(2^k) = \begin{bmatrix}H(2^{k-1}) & H(2^{k-1})\\ H(2^{k-1}) & -H(2^{k-1})\end{bmatrix}\quad (k\ge 2).$$

Például $H(2^2)$ sorai: $(1,1,1,1)$, $(1,-1,1,-1)$, $(1,1,-1,-1)$, $(1,-1,-1,1)$ — bármely kettő skaláris szorzata 0.

### Kidolgozott példa

- **A állomás**: chipkód $(1,-1)$, adat `1011`. Egyedi szignál: $((1,-1),(-1,1),(1,-1),(1,-1))$.
- **B állomás**: chipkód $(1,1)$, adat `0011`. Egyedi szignál: $((-1,-1),(-1,-1),(1,1),(1,1))$.

A csatornán a kettő összege:

$$((0,-2),\,(-2,0),\,(2,0),\,(2,0)).$$

**Vevő 1** ismeri B kódját, $(1,1)$-et. Bitenként skaláris szorzat: $(0,-2)\cdot(1,1) = -2$, $(-2,0)\cdot(1,1) = -2$, $(2,0)\cdot(1,1)=2$, $(2,0)\cdot(1,1)=2$. Az eredmény $(-2,-2,2,2)$, előjelei $(-,-,+,+)$, tehát B üzenete `0011`. ✓

**Vevő 2** ismeri A kódját, $(1,-1)$-et: $(0,-2)\cdot(1,-1)=2$, $(-2,0)\cdot(1,-1)=-2$, $(2,0)\cdot(1,-1)=2$, $(2,0)\cdot(1,-1)=2$. Az eredmény $(2,-2,2,2)$, azaz $(+,-,+,+)$ — A üzenete `1011`. ✓

(Az $m=2$ hosszú kóddal normálva $\pm 2/2 = \pm 1$ adódik.)

**Vizsgaszempont:** tipikus feladat, hogy adott chipkódok és összegjel mellett dekódoljuk egy állomás bitjeit, vagy ellenőrizzük két kód ortogonalitását. A kulcs: a vevő **csak a keresett küldő kódját** ismeri, és a skaláris szorzat előjeléből dönt.

## Kapocs

- [[concepts/telekom/multiplexalas]] — a CDM a statikus multiplexálási módszerek egyike
- [[concepts/telekom/modulacio]] — a modulált jel a csatornán
