---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Síkvektorok keresztszorzata

A vektoriális szorzat kétdimenziós, skalárértékű változata: két síkvektor determinánsa. A síkbeli integráltételek — a területképlet, a rotáció és a Stokes-tétel — ezzel a szorzással írhatók fel a legtömörebben.

## Tartalom

### Definíció

Az $\mathbf{a}, \mathbf{b} \in \mathbb{R}^2$ síkvektorok *keresztszorzata*

$$\mathbf{a} \times \mathbf{b} = a_1 b_2 - a_2 b_1 = \det\begin{pmatrix} a_1 & b_1 \\ a_2 & b_2 \end{pmatrix}.$$

Ez tehát **skalár**, nem vektor: bilineáris $\mathbb{R}^2 \times \mathbb{R}^2 \to \mathbb{R}$ függvény, ellentétben a háromdimenziós vektoriális szorzattal. Előjeles: $\mathbf{a} \times \mathbf{b} = -\,\mathbf{b} \times \mathbf{a}$, és abszolút értéke az $\mathbf{a}, \mathbf{b}$ által kifeszített paralelogramma területe.

### Irányított szög

Az $\mathbf{a}, \mathbf{b}$ vektorok *irányított szöge* az a $\varphi \in \mathbb{R}/2\pi\mathbb{Z}$ szög, amelyre egyszerre teljesül

$$|\mathbf{a}|\,|\mathbf{b}|\cos\varphi = \langle \mathbf{a}, \mathbf{b}\rangle, \qquad |\mathbf{a}|\,|\mathbf{b}|\sin\varphi = \mathbf{a}\times\mathbf{b}.$$

A skaláris szorzat tehát a szög koszinuszát, a keresztszorzat a szinuszát adja meg; a kettő együtt már a szöget magát is meghatározza (modulo $2\pi$), előjelesen. Ez az, ami a nem irányított szögnél többet mond: a keresztszorzat előjele dönti el, hogy $\mathbf{b}$ az $\mathbf{a}$-tól pozitív vagy negatív irányban van.

### Háromféle szorzat a síkon

Síkvektoroknak ezek után legalább háromféle szorzatát ismerjük, mind bilineáris:

| Szorzás | Típus | Érték |
|---|---|---|
| skaláris szorzás $\langle\cdot,\cdot\rangle$ | $\mathbb{R}^2\times\mathbb{R}^2 \to \mathbb{R}$ | $a_1b_1 + a_2b_2$ |
| keresztszorzat $\times$ | $\mathbb{R}^2\times\mathbb{R}^2 \to \mathbb{R}$ | $a_1b_2 - a_2b_1$ |
| komplex szorzás | $\mathbb{R}^2\times\mathbb{R}^2 \to \mathbb{R}^2$ | $(a_1b_1 - a_2b_2,\ a_1b_2 + a_2b_1)$ |

Mindhárom megengedett `*` szorzás az általános vonalintegrál definíciójában, tehát mindhármukhoz tartozik egy-egy vonalintegrál-fogalom.

### Hol használjuk

- Jordan-tartomány területe: $t(K) = \tfrac12\int_{\partial K} \mathbf{x}\times \mathrm{d}\mathbf{x}$.
- A síkbeli rotáció: $\operatorname{rot}\mathbf{f} = \nabla \times \mathbf{f} = \det(\nabla, \mathbf{f})$.
- A görbeindex egyik felírása: $n(\gamma,\mathbf{c}) = \frac{1}{2\pi}\int_{\mathbf{x}\in\gamma}\frac{\mathbf{x}-\mathbf{c}}{|\mathbf{x}-\mathbf{c}|^2}\times \mathrm{d}\mathbf{x}$.

## Kapocs

- [[concepts/analiii/altalanos-vonalintegral]] — a keresztszorzat mint megengedett `*` szorzás
- [[concepts/analiii/rotacio]] — a síkbeli rotáció definíciója keresztszorzattal
- [[concepts/analiii/jordan-tartomany-terulete]] — a területképlet keresztszorzatos alakja
- [[concepts/analiii/korulfordulasi-szam]] — az irányított szög összegzése mint körülfordulási szám
