---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Jordan-tartomány súlypontja vonalintegrállal

A síkbeli Newton–Leibniz formula alkalmazása: a tartomány súlypontja is kiszámítható pusztán a határgörbén vett integrállal, az $f(\mathbf{x}) = \tfrac12|\mathbf{x}|^2$ segédfüggvénnyel.

## Tartalom

### A feladat

Keressünk olyan $f : \mathbb{R}^2\to\mathbb{R}$ függvényt, amelyre bármely szakaszonként differenciálható határú $K$ krumpli súlypontja

$$S = \frac{\int_{\partial K} f(\mathbf{x})\,\mathbf{n}\,\mathrm{d}s}{t(K)} .$$

### A megoldás

A súlypont definíció szerint a pontok terület szerinti átlaga:

$$S = \frac{\int_K \mathbf{x}\,\mathrm{d}A}{t(K)} .$$

Az kellene tehát, hogy minden $K$-ra $\int_{\partial K} f(\mathbf{x})\,\mathbf{n}\,\mathrm{d}s = \int_K \mathbf{x}\,\mathrm{d}A$. A Newton–Leibniz formula szerint viszont

$$\int_{\partial K} f(\mathbf{x})\,\mathbf{n}\,\mathrm{d}s = \int_K \bigl(\operatorname{grad} f(\mathbf{x})\bigr)\,\mathrm{d}A,$$

tehát elég olyan $f$-et találni, amelyre

$$\operatorname{grad} f(\mathbf{x}) = \bigl(D_1f(x,y), D_2f(x,y)\bigr) = \mathbf{x} = (x,y).$$

Ilyen például

$$f(x,y) = \frac{1}{2}(x^2 + y^2) = \frac{1}{2}|\mathbf{x}|^2 .$$

### A módszer tanulsága

A recept általános: ha egy tartományon vett integrált a határra akarunk átvinni, keressünk olyan segédfüggvényt, amelynek a megfelelő deriváltja éppen a kívánt integrandus — ugyanaz a gondolat, mint az egyváltozós primitívfüggvény-keresés. A [[concepts/analiii/jordan-tartomany-terulete]] területképlete ugyanennek a receptnek az $\operatorname{grad} f \equiv$ konstans esete.

## Kapocs

- [[concepts/analiii/newton-leibniz-formula-tobbvaltozos]] — a felhasznált tétel
- [[concepts/analiii/jordan-tartomany-terulete]] — a nevezőben szereplő $t(K)$, szintén vonalintegrállal
- [[concepts/analiii/kulso-normalis]] — az $\mathbf{n}\,\mathrm{d}s$ jelölés
- [[concepts/analii/primitiv-fuggveny]] — az egyváltozós megfelelő: a keresett segédfüggvény szerepe
