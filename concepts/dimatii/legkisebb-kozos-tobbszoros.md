---
tags: [concept, dimatii/elemi-szamelmelet]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Legkisebb közös többszörös

A legnagyobb közös osztó duálisa: a közös többszörösök közül az, amely az összes többinek osztója.

## Tartalom

**Definíció.** Az $a$ és $b$ **legkisebb közös többszöröse** az $m$ szám — jelölés: $m = [a,b] = \operatorname{lkkt}(a,b)$ —, ha

$$a \mid m, \quad b \mid m, \qquad \text{és} \qquad a \mid c,\ b \mid c \;\Rightarrow\; m \mid c.$$

A legnagyobb közös osztóhoz hasonlóan a „legkisebb” itt is az oszthatósági rendezésre utal, és $[a,b]$ csak asszociáltság erejéig egyértelmű; a továbbiakban $[a,b]$ a **pozitív** legkisebb közös többszöröst jelöli.

### Kapcsolat a kanonikus alakkal

Legyenek $n, m > 1$ pozitív egészek kanonikus alakja közös prímeken felírva:
$$n = p_1^{\alpha_1} p_2^{\alpha_2}\cdots p_\ell^{\alpha_\ell}, \qquad m = p_1^{\beta_1} p_2^{\beta_2}\cdots p_\ell^{\beta_\ell},$$
ahol most $\alpha_i, \beta_i \geq 0$ nemnegatív egészek. Ekkor

$$(m,n) = \prod_{i=1}^{\ell} p_i^{\min\{\alpha_i,\beta_i\}}, \qquad [m,n] = \prod_{i=1}^{\ell} p_i^{\max\{\alpha_i,\beta_i\}},$$

és mivel $\min\{\alpha,\beta\} + \max\{\alpha,\beta\} = \alpha + \beta$, ebből azonnal adódik a

$$(m,n)\cdot[m,n] = m\cdot n$$

összefüggés. Gyakorlati haszna, hogy a legkisebb közös többszörös prímfelbontás nélkül, az [[concepts/dimatii/euklideszi-algoritmus]]sal is számolható.

## Kapocs

- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a duális fogalom
- [[concepts/dimatii/szamelmelet-alaptetele]] — a kanonikus alak, amiből a képlet adódik
- [[concepts/dimatii/euklideszi-algoritmus]] — a hatékony számítási út
