---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 7. előadás"]
derivation: source
updated: 2026-09-04
---

# A határozott integrál értelmezése

A Riemann-féle határozott integrál korlátos függvényeken értelmezett, felosztásokhoz tartozó alsó/felső közelítő összegek szuprémuma ill. infimuma.

## Alapfogalmak

**Jelölés:** $[a,b]$ mindig korlátos és zárt $\mathbb{R}$-beli intervallum ($a, b \in \mathbb{R}$, $a < b$).

$$K[a,b] := \{f : [a,b] \to \mathbb{R} \mid f \text{ korlátos } [a,b]\text{-n}\}.$$

**Felosztás:**
$$\tau := \{a = x_0 < x_1 < x_2 < \cdots < x_n = b\}, \quad n \in \mathbb{N}^+.$$

A $\tau$ felosztás **finomságán** a
$$\|\tau\| := \max\{x_i - x_{i-1} \mid i = 1,\ldots,n\}$$
számot értjük. $\mathcal{F}[a,b]$ jelöli az $[a,b]$ intervallum felosztásainak halmazát.

- Ha $\tau_1, \tau_2 \in \mathcal{F}[a,b]$, akkor $\tau_1 \cup \tau_2,\ \tau_1 \cap \tau_2 \in \mathcal{F}[a,b]$.
- Ha $\tau_1 \subset \tau_2$, azt mondjuk: $\tau_2$ egy **finomítása** $\tau_1$-nek.

## Közelítő összegek

Legyen $f \in K[a,b]$, $\tau \in \mathcal{F}[a,b]$. Legyenek

$$m_i := \inf_{[x_{i-1},x_i]} f, \qquad M_i := \sup_{[x_{i-1},x_i]} f \quad (i = 1,\ldots,n).$$

Az $f$ függvény $\tau$ felosztáshoz tartozó **alsó**, ill. **felső közelítő összege**:

$$s(f,\tau) := \sum_{i=1}^n m_i(x_i - x_{i-1}), \qquad S(f,\tau) := \sum_{i=1}^n M_i(x_i - x_{i-1}).$$

**Megjegyzések:**
- $m_i$ és $M_i$ léteznek és végesek, mert $f$ korlátos (inf/sup ≠ min/max általában).
- Ha $f \geq 0$, akkor $s(f,\tau)$ a beírt, $S(f,\tau)$ a körülírt téglalapok területének összege.

## A Riemann-integrál definíciója

**Darboux alsó/felső integrál:**
$$I_*(f) := \sup_{\tau \in \mathcal{F}[a,b]} s(f,\tau), \qquad I^*(f) := \inf_{\tau \in \mathcal{F}[a,b]} S(f,\tau).$$

Az $f \in K[a,b]$ függvény **Riemann-integrálható** $[a,b]$-n, ha $I_*(f) = I^*(f)$. Jelölés: $f \in R[a,b]$. Az integrál értéke:
$$\int_a^b f := \int_a^b f(x)\,dx := I_*(f) = I^*(f).$$

## A finomítási tétel

**Tétel.** Legyen $f \in K[a,b]$, és t.f.h. $\tau_1, \tau_2 \in \mathcal{F}[a,b]$. Ekkor

**1°** Ha $\tau_2$ finomabb $\tau_1$-nél (azaz $\tau_1 \subset \tau_2$), akkor
$$s(f,\tau_1) \leq s(f,\tau_2) \qquad \text{és} \qquad S(f,\tau_1) \geq S(f,\tau_2),$$
azaz finomításkor az alsó összeg nem csökkenhet, a felső nem nőhet.

**2°** Ha $\tau_1, \tau_2 \in \mathcal{F}[a,b]$ tetszőleges, akkor $s(f,\tau_1) \leq S(f,\tau_2)$.

**Bizonyítás (1°, egy osztópont esete).** T.f.h. $\tau_2 = \tau_1 \cup \{x'\}$, ahol $x_{k-1} < x' < x_k$. Legyenek
$$m'_k := \inf_{[x_{k-1},x']} f, \quad m''_k := \inf_{[x',x_k]} f.$$
Akkor $m'_k \geq m_k$ és $m''_k \geq m_k$, ezért
$$s(f,\tau_2) - s(f,\tau_1) = m'_k(x'-x_{k-1}) + m''_k(x_k-x') - m_k(x_k-x_{k-1}) \geq 0.$$
Az általános eset osztópontok sorozatos hozzávételével adódik.

**Bizonyítás (2°).** Legyen $\tau = \tau_1 \cup \tau_2$. Ekkor $\tau \supset \tau_1$ és $\tau \supset \tau_2$, ezért
$$s(f,\tau_1) \leq s(f,\tau) \leq S(f,\tau) \leq S(f,\tau_2). \qquad\blacksquare$$

## Kapocs

- [[concepts/analii/hatarozott-integral-motivacio]] — síkidom területének közelítése, motiváció
- [[concepts/analii/integralhato-fuggvenyek]] — Darboux- és Riemann-kritérium
