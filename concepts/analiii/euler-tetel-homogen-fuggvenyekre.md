---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.2. x)–xi) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Euler-tétel homogén függvényekre

Egy differenciálható $f : \mathbb{R}^n \to \mathbb{R}$ függvény pontosan akkor $s$-edfokú homogén, ha $\langle \operatorname{grad} f(\xi), \xi\rangle = s\cdot f(\xi)$ minden $\xi$-re — egy globális skálázási tulajdonság pontos differenciálegyenlet-alakja.

## Tartalom

### Homogén függvény

A differenciálható $f : \mathbb{R}^n \to \mathbb{R}$ függvény **$s$-edfokú homogén**, ha

$$f(t\xi) = t^s\cdot f(\xi) \qquad (\xi \in \mathbb{R}^n,\ 0 < t \in \mathbb{R}).$$

### A tétel

$f$ akkor és csak akkor $s$-edfokú homogén, ha

$$\sum_{i=1}^n \xi_i\cdot \partial_i f(\xi) = s\cdot f(\xi) \qquad (\xi \in \mathbb{R}^n),$$

azaz $\langle \operatorname{grad} f(\xi), \xi\rangle = s f(\xi)$.

**Oda.** Rögzített $\xi$ mellett legyen $F(t) := f(t\xi)/t^s$. A homogenitás miatt $F \equiv f(\xi)$ konstans, tehát $F' \equiv 0$. A hányados- és a [[concepts/analiii/lancszabaly|láncszabály]] szerint

$$0 = F'(t) = \frac{t\langle \operatorname{grad} f(t\xi), \xi\rangle - s f(t\xi)}{t^{s+1}},$$

és $t = 1$ adja az állítást.

**Vissza.** Tegyük fel a differenciálegyenletet, és legyen $H(t) := f(t\xi)$. Ekkor $H'(t) = \langle \operatorname{grad} f(t\xi), \xi\rangle$, és a feltevésből $t H'(t) = s H(t)$. A $G(t) := H(t)/t^s$ függvényre

$$G'(t) = \frac{tH'(t) - sH(t)}{t^{s+1}} = 0,$$

tehát $G$ konstans; $t = 1$-ben $G(1) = H(1) = f(\xi)$, azaz $H(t) = f(t\xi) = t^s f(\xi)$.

A két irány ugyanaz az egy számolás, ellenkező olvasatban: egyszer a konstansságból következtetünk a deriváltra, egyszer a deriváltból a konstansságra.

### Példa

$f(x,y,z) := (x - 2y + 3z)^2$ nyilván másodfokú homogén. A parciális deriváltak $2(x-2y+3z)$, $-4(x-2y+3z)$, $6(x-2y+3z)$, tehát

$$\sum_{i=1}^3 \xi_i \partial_i f(\xi) = (2x - 4y + 6z)(x-2y+3z) = 2(x-2y+3z)^2 = 2f(\xi).$$

## Kapocs

- [[concepts/analiii/lancszabaly]] — a bizonyítás egyetlen eszköze.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a $\langle \operatorname{grad} f(\xi), \xi\rangle$ alak tartalma.
- [[concepts/analiii/nivofelulet-es-gradiens]] — a másik gradiens-azonosság, szintén láncszabályból.
