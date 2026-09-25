---
tags: [concept, dimatii/algebrai-strukturak]
sources: [DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
---

# Gyűrű

Kétműveletes algebrai struktúra, amelyben az „összeadás" Abel-csoport, a „szorzás" félcsoport, és a kettőt a disztributivitás köti össze.

## Tartalom

### Disztributivitás

Legyen $(R; \oplus, \otimes)$ algebrai struktúra, ahol $\oplus$ és $\otimes$ bináris műveletek. A $\otimes$ művelet **bal oldali disztributivitása** a $\oplus$-ra, illetve **jobb oldali disztributivitása**:

$$\forall k, l, m \in R : k \otimes (l \oplus m) = (k \otimes l) \oplus (k \otimes m),$$
$$\forall k, l, m \in R : (l \oplus m) \otimes k = (l \otimes k) \oplus (m \otimes k).$$

$(\mathbb{Z}; +, \cdot)$ esetén mindkét oldali disztributivitás teljesül.

### Szokásos elnevezések

$(R; \oplus, \otimes)$ esetén a $\oplus$ műveletet „összeadásnak", a $\otimes$-t „szorzásnak" nevezzük. A $\oplus$-ra vonatkozó semleges elem a **nullelem** (jelölése $0$), a $\otimes$-ra vonatkozó semleges elem az **egységelem** (jelölése $1$, esetleg $e$).

### Definíció (gyűrű)

Az $(R; \oplus, \otimes)$ két bináris műveletes algebrai struktúra **gyűrű**, ha

- $(R; \oplus)$ Abel-csoport (kommutatív csoport a $0$ egységelemmel);
- $(R; \otimes)$ félcsoport;
- teljesül a $\otimes$-nak a $\oplus$-ra vonatkozó **mindkét oldali** disztributivitása.

A gyűrű $0$ nulleleme tehát az $(R; \oplus)$ Abel-csoport egységeleme.

### Egységelemes és kommutatív gyűrű

- Az $(R; \oplus, \otimes)$ gyűrű **egységelemes gyűrű**, ha $R$-en a $\otimes$ műveletre nézve is van egységelem ($1$ vagy $e$), azaz $(R; \otimes)$ egységelemes félcsoport.
- Az $(R; \oplus, \otimes)$ gyűrű **kommutatív gyűrű**, ha a $\otimes$ művelet kommutatív, azaz $(R; \otimes)$ kommutatív félcsoport.

### Példák

- $(\mathbb{Z}; +, \cdot)$ egységelemes kommutatív gyűrű.
- $(2\mathbb{Z}; +, \cdot)$ kommutatív gyűrű, de **nem** egységelemes.
- $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$ a szokásos műveletekkel egységelemes kommutatív gyűrűk.
- $(\mathbb{C}^{k \times k}; +, \cdot)$ a mátrixösszeadással és mátrixszorzással egységelemes gyűrű, de $k > 1$ esetén **nem** kommutatív.
- $(\mathbb{R}^3; +, \times)$, a 3-dimenziós euklideszi vektortér a vektoriális szorzattal **nem** gyűrű, mert $\times$ nem asszociatív; $(\mathbb{R}^3; \times)$ így nem félcsoport.

### Az osztás hiánya

Gyűrűben általában nem lehet elvégezni az osztást:

- $\mathbb{Z}$-ben nem oldható meg a $2x = 1$ egyenlet;
- $\mathbb{R}^{2 \times 2}$-ben nem oldható meg a $\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} \cdot X = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$ egyenlet;
- $\mathbb{Z}_4$-ben nem oldható meg a $2x \equiv 1 \pmod 4$ kongruencia.

### Állítás (a nullelem elnyelő)

Legyen $(R; \oplus, \otimes)$ gyűrű $0 \in R$ nullelemmel. Ekkor $\forall r \in R$ esetén

$$0 \otimes r = r \otimes 0 = 0.$$

**Bizonyítás.** $0 \otimes r = (0 \oplus 0) \otimes r = (0 \otimes r) \oplus (0 \otimes r)$, ahonnan $(R; \oplus)$ csoport volta miatt $0 = 0 \otimes r$. A másik oldal bizonyítása ugyanígy megy. $\square$

## Kapocs

- [[concepts/dimatii/csoport]] — a gyűrű additív része Abel-csoport
- [[concepts/dimatii/felcsoport-es-monoid]] — a gyűrű multiplikatív része félcsoport
- [[concepts/dimatii/nullosztomentes-gyuru]] — a gyűrűk fontos alosztálya, a karakterisztika fogalmával
- [[concepts/dimatii/integritasi-tartomany]] — kommutatív, nullosztómentes gyűrű
- [[concepts/dimatii/test]] — a gyűrűk azon esete, ahol az osztás is elvégezhető
- [[concepts/dimatii/polinomgyuru]] — az $R[x]$ polinomgyűrű mint gyűrűkonstrukció
