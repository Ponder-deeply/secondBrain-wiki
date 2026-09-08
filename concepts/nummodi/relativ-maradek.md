---
tags: [concept]
sources: [NM1_ea07.pdf]
derivation: source
updated: 2026-08-05
---

# Relatív maradék

A [[concepts/nummodi/kondicioszam|kondíciószám]] a LER megoldási *feladatának* érzékenységét jellemzi, de nem mondja meg, hogy egy konkrét közelítő megoldás mennyire pontos. Erre szolgál a maradékvektor és a belőle képzett relatív maradék.

## Reziduum- (maradék-) vektor

**Definíció:** Legyen $\tilde{x}$ az $Ax = b$ LER egy közelítő megoldása. Ekkor az

$$r := b - A\tilde{x}$$

vektort a közelítő megoldás **reziduum-** vagy **maradékvektorának** nevezzük.

**Megjegyzés:** A reziduumvektor könnyen számítható — elég az $A\tilde{x}$ szorzatot elvégezni, majd kivonjuk $b$-ből. Alkalmazható direkt és iteratív módszereknél egyaránt; az utóbbiaknál leállási feltételként is használható.

## Relatív maradék

**Definíció:** Az

$$\eta := \frac{\|r\|}{\|A\| \cdot \|\tilde{x}\|}$$

mennyiséget **relatív maradéknak** nevezzük (jele: $\eta$, [éta]).

### Stabilitási értelmezés

A stabilitás inverz megfogalmazása alapján: a módszer stabil, ha a $\tilde{x}$ közelítő megoldáshoz tartozó $(A + \Delta A)\tilde{x} = b$ LER csak kicsit perturbált az eredetihez képest, azaz $\frac{\|\Delta A\|}{\|A\|}$ kicsi. A relatív maradék éppen ezt a mennyiséget becsli.

## Becslés: relatív maradék és $\Delta A$

### Tétel

Ha $A$ invertálható, akkor illeszkedő mátrixnormában

$$\eta \leq \frac{\|\Delta A\|}{\|A\|},$$

azaz ha $\eta$ nagy, akkor $\frac{\|\Delta A\|}{\|A\|}$ is nagy.

**Biz.:** $b = (A + \Delta A)\tilde{x} = A\tilde{x} + \Delta A\tilde{x}$, innen $b - A\tilde{x} = r = \Delta A\tilde{x}$. A mátrixnorma illeszkedéséből:

$$\|r\| \leq \|\Delta A\| \cdot \|\tilde{x}\|.$$

A relatív maradékot becsülve:

$$\eta = \frac{\|r\|}{\|A\|\cdot\|\tilde{x}\|} \leq \frac{\|\Delta A\|\cdot\|\tilde{x}\|}{\|A\|\cdot\|\tilde{x}\|} \leq \frac{\|\Delta A\|}{\|A\|}. \quad \square$$

## Relatív maradék 2-es normában

### Tétel

Ha $A$ invertálható, akkor

$$\eta_2 = \frac{\|\Delta A\|_2}{\|A\|_2},$$

ahol $\eta_2 := \frac{\|r\|_2}{\|A\|_2\cdot\|\tilde{x}\|_2}$.

**Biz.:** Megmutatjuk, hogy a

$$\Delta A = \frac{r\tilde{x}^\top}{\tilde{x}^\top\tilde{x}}$$

perturbáció jó lesz, azaz $\tilde{x}$ az $(A + \Delta A)\tilde{x} = b$ LER pontos megoldása:

$$(A + \Delta A)\tilde{x} = A\tilde{x} + \frac{r\tilde{x}^\top\tilde{x}}{\tilde{x}^\top\tilde{x}} = A\tilde{x} + r = A\tilde{x} + (b - A\tilde{x}) = b. \quad \checkmark$$

A $\|\Delta A\|_2$ normájára felhasználjuk, hogy $\|r\tilde{x}^\top\|_2 = \|r\|_2 \cdot \|\tilde{x}\|_2$:

$$\frac{\|\Delta A\|_2}{\|A\|_2} = \frac{\|r\tilde{x}^\top\|_2}{\|A\|_2 \cdot \|\tilde{x}\|_2^2} = \frac{\|r\|_2 \cdot \|\tilde{x}\|_2}{\|A\|_2 \cdot \|\tilde{x}\|_2^2} = \frac{\|r\|_2}{\|A\|_2 \cdot \|\tilde{x}\|_2} = \eta_2. \quad \square$$

**Megjegyzés:** Ez a bizonyítás beadható HF-nek van kitűzve az előadáson.

### Következmény

- Ha $\eta_2$ kicsi, akkor $\frac{\|\Delta A\|_2}{\|A\|_2}$ is kicsi: $\tilde{x}$ egy kicsit perturbált mátrixú LER pontos megoldása, azaz az algoritmus stabil.
- Ha $\eta_2 < \varepsilon_1$ (a gépi egység), akkor az adott aritmetikában pontosabb megoldás nem adható.

## Kapcsolat a kondíciószámmal

A relatív maradék és a kondíciószám együtt ad képet a megoldás tényleges relatív hibájáról:

$$\frac{\|\Delta x\|}{\|x\|} \lesssim \operatorname{cond}(A) \cdot \eta.$$

Kis $\eta$ szükséges, de nem elégséges feltétel a pontos megoldáshoz: ha $\operatorname{cond}(A)$ nagy, a kis relatív maradék ellenére $\Delta x$ is lehet nagy.

## Kapocs

- [[concepts/nummodi/kondicioszam]] — kondíciószám definíciója és tulajdonságai
- [[concepts/nummodi/ler-erzekenysege]] — LER perturbációs tételei (jobboldal és mátrix perturbációja)
- [[concepts/nummodi/matrixnormak]] — illeszkedő normák; $\|r\tilde{x}^\top\|_2 = \|r\|_2\cdot\|\tilde{x}\|_2$ azonosság
- [[concepts/nummodi/algoritmus-stabilitas]] — stabil algoritmus fogalma; inverz stabilitási definíció
- [[concepts/nummodi/lebegopont-modell]] — gépi egység $\varepsilon_1$; pontossági korlátok
- [[subjects/nummodi]] — kurzus áttekintése
