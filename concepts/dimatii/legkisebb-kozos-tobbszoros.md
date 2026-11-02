---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dimat2gyak02mo.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
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

### Következmények (Farkas-diák)

- Tetszőleges $a, b \in \mathbb{Z}$ számoknak létezik legkisebb közös többszöröse, és $(a,b)\cdot[a,b] = |ab|$.
- $[ac, bc] = c\cdot[a,b]$ (pozitív $c$-re; a diák $c \in \mathbb{Z}$-vel írják, asszociáltság erejéig).
- Több szám esetén is létezik, és páronként kiszámolható: $[a_1, a_2, \dots, a_n] = \big[[a_1,a_2], a_3, \dots, a_n\big]$.
- Ha $a$ is és $b$ is relatív prím $c$-hez, akkor $ab$ is az.

### Általános definíció (előadásdiák)

*(Farkas Gábor előadásdiái.)* Egységelemes integritási tartományban legyen $a_1,\dots,a_n \in R$ és $T \subseteq R$ olyan, hogy minden $t \in T$-re $a_i \mid t$ ($\forall i$) és $a_i \mid t'\ (\forall i) \Rightarrow t \mid t'$. Ekkor $T$ elemei az $a_1,\dots,a_n$ legkisebb közös többszörösei: $\operatorname{lkkt}(a_1,\dots,a_n) = [a_1,\dots,a_n] = t$; csak asszociáltság erejéig egyértelmű, ezért kijelölünk egyet.

### Feladattípusok és módszerek

Az lkkt a legtöbb feladatban az lnko-ból adódik: $[a,b] = ab/(a,b)$; számított példák: $[168,219] = 12\,264$, $[756,795] = 200\,340$ ([[concepts/dimatii/euklideszi-algoritmus]], gyakorlat 2.). Közös többszörös feltételnél (pl. $z^n = w^n = 1$ mikor, ha a rendek $4$ és $6$) a megoldás $n \in [4,6]\mathbb{Z} = 12\mathbb{Z}$; lásd [[concepts/dimatii/komplex-egysegiyokok-hatvanyai]].

## Kapocs

- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a duális fogalom
- [[concepts/dimatii/szamelmelet-alaptetele]] — a kanonikus alak, amiből a képlet adódik
- [[concepts/dimatii/euklideszi-algoritmus]] — a hatékony számítási út

