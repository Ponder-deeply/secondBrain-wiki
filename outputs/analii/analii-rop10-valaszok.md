---
tags: [synthesis]
sources: []
references: ["Analízis II. 10. gyakorlat röpZH kérdéssor (nincs a vaultban)"]
derivation: inferred
updated: 2026-04-22
---

# Analízis II. — 10. gyakorlat röpZH válaszok

## 1. Riemann-integrálhatóság ekvivalens átfogalmazása felosztássorozatok segítségével

**Tétel.** Legyen $f \in K[a,b]$. Ekkor $f \in R[a,b]$ és $\int_a^b f = I$ akkor és csak akkor, ha $\exists\, (\tau_n) \subset \mathcal{F}[a,b]$ felosztássorozat:

$$s(f, \tau_n) \to I \quad \text{és} \quad S(f, \tau_n) \to I \quad (n \to \infty).$$

Ekvivalens alak: $\Omega(f, \tau_n) = S(f,\tau_n) - s(f,\tau_n) \to 0$.

## 2. Riemann-integrálható függvények összege

**Tétel.** Ha $f, g \in R[a,b]$ és $\lambda \in \mathbb{R}$, akkor $\lambda f,\, f + g \in R[a,b]$ és

$$\int_a^b (\lambda f + g) = \lambda \int_a^b f + \int_a^b g$$

(linearitás). Külön:
- $\int_a^b (\lambda f) = \lambda \int_a^b f$
- $\int_a^b (f+g) = \int_a^b f + \int_a^b g$

## 3. Riemann-integrálható függvények szorzata

**Tétel.** Ha $f, g \in R[a,b]$, akkor $f \cdot g \in R[a,b]$.

**Megjegyzés.** A szorzat integráljára általában **nincs** egyszerű képlet ($\int fg \neq \int f \cdot \int g$).

## 4. Riemann-integrálható függvények hányadosa

**Tétel.** Ha $f, g \in R[a,b]$, és $\exists\, m > 0$ : $|g(x)| \geq m$ minden $x \in [a,b]$ esetén, akkor

$$\frac{f}{g} \in R[a,b].$$

A $|g| \geq m > 0$ feltétel lényeges, hogy $\tfrac{1}{g}$ korlátos legyen.

## 5. Függvényértékek megváltoztatása véges sok helyen

**Tétel.** T.f.h. $f, g \in K[a,b]$, $f \in R[a,b]$, és az $A := \{x \in [a,b] \mid f(x) \neq g(x)\}$ halmaz **véges**. Ekkor $g \in R[a,b]$ és

$$\int_a^b g = \int_a^b f.$$

Azaz véges sok pontban módosítva egy integrálható függvényt, sem az integrálhatóság, sem az integrál értéke nem változik.

## 6. A Riemann-integrál intervallum szerinti additivitása

**Tétel.** Legyen $a < c < b$. Ekkor $f \in R[a,b]$ akkor és csak akkor, ha $f \in R[a,c]$ és $f \in R[c,b]$, és ilyenkor

$$\int_a^b f = \int_a^c f + \int_c^b f.$$

**Kiterjesztés** (tetszőleges sorrend): $\int_a^a f := 0$ és $\int_b^a f := -\int_a^b f$ megállapodással a képlet az $a, b, c$ bármely sorrendjére érvényes.

## 7. Az integrálszámítás első középértéktétele

**Tétel.** Legyen $f, g \in R[a,b]$, $g \geq 0$, $m := \inf_{[a,b]} f$, $M := \sup_{[a,b]} f$. Ekkor:

**1°** $\displaystyle m \int_a^b g \leq \int_a^b f g \leq M \int_a^b g$.

**2°** Ha még $f \in C[a,b]$, akkor $\exists\, \xi \in [a,b]$:

$$\int_a^b f \cdot g = f(\xi) \int_a^b g.$$

**Speciális eset** ($g \equiv 1$, $f \in C[a,b]$): $\exists\, \xi \in [a,b]$ :

$$\int_a^b f = f(\xi)(b-a).$$

Az $\frac{1}{b-a}\int_a^b f$ érték az $f$ **integrálközepe**.

## 8. Cauchy–Bunyakovszkij–Schwarz-egyenlőtlenség

**Tétel.** Ha $f, g \in R[a,b]$, akkor $f \cdot g,\, f^2,\, g^2 \in R[a,b]$ és

$$\left(\int_a^b f \cdot g\right)^2 \leq \left(\int_a^b f^2\right) \cdot \left(\int_a^b g^2\right),$$

ekvivalensen

$$\left|\int_a^b f g\right| \leq \sqrt{\int_a^b f^2} \cdot \sqrt{\int_a^b g^2}.$$

**Bizonyítás vázlat.** $\forall\, \lambda \in \mathbb{R}$: $(f - \lambda g)^2 \geq 0$, ezért $\int_a^b (f - \lambda g)^2 \geq 0$, azaz

$$\lambda^2 \int_a^b g^2 - 2\lambda \int_a^b fg + \int_a^b f^2 \geq 0.$$

A $\lambda$-ban másodfokú kifejezés diszkriminánsa $\leq 0$, ami épp a CBS-egyenlőtlenséget adja. $\blacksquare$

## Források

- [[concepts/analii/integralhato-fuggvenyek]] — sorozatos / Riemann-kritérium
- [[concepts/analii/muvelet-integralhato-fuggvenyekkel]] — összeg, szorzat, hányados
- [[concepts/analii/riemann-integral-tulajdonsagok]] — véges sok pont megváltoztatása
- [[concepts/analii/integral-egyenlotlensegek]] — első középértéktétel, monotonitás
