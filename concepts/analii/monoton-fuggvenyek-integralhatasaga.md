---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 9. előadás"]
derivation: source
updated: 2026-09-04
---

# Monoton függvények integrálhatósága

A monotonitás az integrálhatóság egy elégséges feltétele — monoton függvény mindig integrálható.

## Főtétel

**Tétel.** Ha $f : [a,b] \to \mathbb{R}$ függvény **monoton** az $[a,b]$ intervallumon, akkor **integrálható** $[a,b]$-n.

**Bizonyítás.** Az integrálhatóság oszcillációs összegekkel való jellemzését alkalmazzuk (Darboux-kritérium): igazoljuk, hogy

$$(*)\quad \forall \varepsilon > 0\ \exists \tau \in \mathcal{F}[a,b]: \Omega(f,\tau) < \varepsilon.$$

Legyen pl. $f \nearrow$. Ha $f(a) = f(b)$, akkor $f$ állandó, és az állítás nyilvánvaló.

Ha $f(a) < f(b)$, legyen $n \in \mathbb{N}^+$ olyan, hogy $\frac{b-a}{n} < \frac{\varepsilon}{f(b)-f(a)}$, és legyen $\tau$ az $[a,b]$ egyenletes felosztása ($x_i - x_{i-1} = \frac{b-a}{n}$). Ekkor $f \nearrow$ miatt $m_i = f(x_{i-1})$ és $M_i = f(x_i)$, ezért

$$\Omega(f,\tau) = \sum_{i=1}^n (f(x_i) - f(x_{i-1})) \cdot \frac{b-a}{n} = \frac{b-a}{n} \cdot \underbrace{\sum_{i=1}^n (f(x_i) - f(x_{i-1}))}_{\text{teleszkopikus: } f(b)-f(a)} = \frac{b-a}{n} \cdot (f(b) - f(a)) < \varepsilon.$$

Ezzel $(*)$-ot igazoltuk, tehát $f \in R[a,b]$. $\blacksquare$

## Szakaszonként monoton függvények

**Definíció.** Az $f : [a,b] \to \mathbb{R}$ függvény **szakaszonként monoton**, ha

$$\exists m \in \mathbb{N}^+\ \text{és}\ \tau = \{a = x_0 < x_1 < \cdots < x_m = b\} \in \mathcal{F}[a,b],$$

úgy hogy minden $i = 1,\ldots,m$ index esetén:
1. az $f|_{(x_{i-1},x_i)}$ függvény monoton,
2. $f$ korlátos $[a,b]$-n.

**Megjegyzés.** A (ii) feltétel garantálja az osztópontokban az egyoldali véges határértékek létezését.

**Tétel.** Legyen $f : [a,b] \to \mathbb{R}$ egy szakaszonként monoton függvény, és $\tau = \{a = x_0 < \cdots < x_m = b\}$ az előző definícióban szereplő felosztás. Ekkor $f \in R[a,b]$ és

$$\int_a^b f = \sum_{i=1}^m \int_{x_{i-1}}^{x_i} f.$$

## Kapocs

- [[concepts/analii/integralhato-fuggvenyek]] — Darboux-kritérium, Riemann-kritérium
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — folytonos $\Rightarrow$ integrálható (Heine-tétellel)
- [[concepts/analii/egyenletes-folytonossag]] — egyenletes folytonosság szükséges a folytonos eset bizonyításához
