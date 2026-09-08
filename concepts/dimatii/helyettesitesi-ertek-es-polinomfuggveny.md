---
tags: [concept]
sources: [DimatIIEa05.pdf]
derivation: source
updated: 2026-09-08
---

# Helyettesítési érték és polinomfüggvény

A polinom formális objektum (együtthatósorozat), a polinomfüggvény pedig a hozzá tartozó $r \mapsto f(r)$ leképezés — a kettő nem ugyanaz, és véges gyűrű fölött különböző polinomokhoz tartozhat azonos függvény.

## Tartalom

### Helyettesítési érték és gyök

**Definíció.** Az $f(x) = f_0 + f_1x + f_2x^2 + \dots + f_nx^n \in R[x]$ polinom $r \in R$ helyen felvett **helyettesítési értéke** az

$$f(r) = f_0 + f_1r + f_2r^2 + \dots + f_nr^n \in R$$

elem.

**Definíció (gyök).** Ha $f(r) = 0$, akkor $r$-et a polinom **gyökének** nevezzük.

**Példa.** Az $f(x) = x^2 + x - 2 \in \mathbb{Z}[x]$ polinomnak a $-2$ helyen felvett helyettesítési értéke $(-2)^2 + (-2) - 2 = 0$, ezért $-2$ gyöke $f$-nek.

### Polinomfüggvény

**Definíció.** Az $\hat{f} : r \mapsto f(r)$ leképezés az $f$ polinomhoz tartozó **polinomfüggvény**.

A megkülönböztetés lényeges: más tárgyakban gyakran az itt polinomfüggvénynek nevezett objektumot hívják „polinomnak”. Bizonyos esetekben ez nem okoz gondot, de ebben a tárgyban a két fogalmat élesen szét kell választani.

### Miért nem esik egybe a két fogalom

**Véges $R$ esetén** csak véges sok $R \to R$ függvény van, míg végtelen sok $R[x]$-beli polinom. Ezért szükségképpen vannak olyan különböző polinomok, amelyekhez ugyanaz a polinomfüggvény tartozik — például $x$ és $x^2$ a $\mathbb{Z}_2[x]$-ben, hiszen $0^2 = 0$ és $1^2 = 1$.

**Végtelen elemszámú nullosztómentes $R$ esetén** hiába van végtelen sok $R \to R$ függvény és végtelen sok $R[x]$-beli polinom, mégis lesznek olyan függvények, amelyek egyetlen polinomhoz sem tartozhatnak polinomfüggvényként (a számosságok nem esnek egybe).

A pozitív irányú állítás — hogy **végtelen egységelemes integritási tartomány fölött két különböző polinomhoz nem tartozhat ugyanaz a polinomfüggvény** — a gyökök számára vonatkozó korlátból következik, lásd [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]].

## Kapocs

- [[concepts/dimatii/polinomgyuru]] — a polinom mint formális együtthatósorozat
- [[concepts/dimatii/horner-elrendezes]] — a helyettesítési érték hatékony kiszámítása
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — mikor határozza meg a polinomfüggvény a polinomot
- [[concepts/dimatii/gyok-multiplicitasa]] — a gyök finomabb jellemzése
