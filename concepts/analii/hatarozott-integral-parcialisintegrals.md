---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 10. előadás"]
derivation: source
updated: 2026-09-04
---

# Parciális integrálás (határozott integrál)

A szorzatszabály inverze határozott integrálra: lehetővé teszi az $\int_a^b fg'$ típusú integrálok visszavezetését $\int_a^b f'g$-re.

## Tétel

**T.f.h.** $f, g : [a,b] \to \mathbb{R}$, $f, g \in D[a,b]$ és $f', g' \in R[a,b]$. Ekkor

$$\int_a^b f g' = f(b)g(b) - f(a)g(a) - \int_a^b f' g.$$

## Bizonyítás

Egyrészt $f \in D[a,b] \Rightarrow f \in C[a,b] \Rightarrow f \in R[a,b]$. Mivel $g' \in R[a,b]$, ezért $fg' \in R[a,b]$. Hasonlóan $f'g \in R[a,b]$. Így $f'g + fg' \in R[a,b]$.

Másrészt $fg$ primitív függvénye az $f'g + fg'$ függvénynek (ui. $(fg)' = f'g + fg'$). A [[concepts/analii/newton-leibniz-tetel|Newton–Leibniz-tétel]] szerint tehát

$$\int_a^b (f'g + fg') = \bigl[fg\bigr]_a^b = f(b)g(b) - f(a)g(a).$$

A határozott integrál additivitását felhasználva rendezés után azt kapjuk, hogy

$$\int_a^b fg' = \bigl[fg\bigr]_a^b - \int_a^b f'g. \qquad \blacksquare$$

## Wallis-formula és a $\sin^k$ integrálok

**Jelölés.** Legyen $I_k := \int_0^\pi \sin^k x\, dx$ ($k \in \mathbb{N}$).

Könnyen adódik: $I_0 = \pi$ és $I_1 = [-\cos x]_0^\pi = (-\cos\pi) - (-\cos 0) = 2$.

**Rekurzió ($k \geq 2$).** Parciálisan integrálva $\sin^{k-1} x \cdot (-\cos x)' = \sin^{k-1} x \cdot \sin x$ szerint:

$$I_k = \bigl[\sin^{k-1} x \cdot (-\cos x)\bigr]_0^\pi - \int_0^\pi (k-1)\sin^{k-2}x \cdot \cos x \cdot (-\cos x)\, dx = 0 + (k-1)\int_0^\pi (1-\sin^2 x)\sin^{k-2} x\, dx,$$

amiből

$$I_k = (k-1)(I_{k-2} - I_k) \implies I_k = \frac{k-1}{k} \cdot I_{k-2}.$$

**Eredmény.**

$$I_{2n} = \frac{2n-1}{2n} \cdot \frac{2n-3}{2n-2} \cdots \frac{1}{2} \cdot I_0 = \frac{1 \cdot 3 \cdots (2n-1)}{2 \cdot 4 \cdots 2n} \cdot \pi \qquad (n \in \mathbb{N}^+),$$

$$I_{2n+1} = \frac{2n}{2n+1} \cdot \frac{2n-2}{2n-1} \cdots \frac{2}{3} \cdot I_1 = \frac{2 \cdot 4 \cdots 2n}{1 \cdot 3 \cdots (2n+1)} \cdot 2 \qquad (n \in \mathbb{N}).$$

**Wallis-formula.** A $\sin^{2n+2} x \leq \sin^{2n+1} x \leq \sin^{2n} x$ ($x \in (0, \pi/2)$) egyenlőtlenségből $I_{2n+2} \leq I_{2n+1} \leq I_{2n}$ következik, amelyből rendezés után:

$$\lim_{n \to +\infty} \frac{2^2 \cdot 4^2 \cdots (2n)^2}{1^2 \cdot 3^2 \cdots (2n-1)^2} \cdot \frac{1}{2n+1} = \frac{\pi}{2}.$$

## Kapocs

- [[concepts/analii/newton-leibniz-tetel]] — a bizonyítás a Newton–Leibniz-tételt alkalmazza $(fg)'$ primitívjére
- [[concepts/analii/hatarozatlan-integral]] — határozatlan integrál parciális integrálása (analóg szabály)
- [[concepts/analii/hatarozott-integral-helyettesites]] — a másik fő integrálási technika határozott integrálra
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — $D[a,b] \subset C[a,b] \subset R[a,b]$ a bizonyításban
