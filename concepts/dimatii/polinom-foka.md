---
tags: [concept, dimatii/polinomok]
sources: [DimatIIEa05.pdf]
derivation: source
updated: 2026-09-08
---

# Polinom foka

A fok viselkedése összeadás és szorzás alatt a polinomgyűrűvel való számolás legfőbb eszköze: nullosztómentes gyűrű fölött a szorzat foka a fokok összege, és erre épül minden későbbi felbonthatósági érvelés.

## Tartalom

A fok, a főegyüttható és a főtag definícióját lásd a [[concepts/dimatii/polinomgyuru]] lapon; ez a lap a fokra vonatkozó *állításokat* gyűjti össze.

### A nullpolinom foka

A **nullpolinomnak** ($0 = (0,0,\dots)$) nincs legnagyobb indexű nem-nulla együtthatója, ezért a fokát külön definiáljuk:

$$\deg(0) = -\infty.$$

Ez a megállapodás teszi kivételmentessé az alábbi becsléseket.

### Nevezetes polinomosztályok

- **konstans polinomok**: a legfeljebb nulladfokúak,
- **lineáris polinomok**: a legfeljebb elsőfokúak,
- **monomok**: az $f_i x^i$ alakba írható polinomok,
- **főpolinom**: olyan $f \in R[x]$, amelynek főegyütthatója $R$ egységeleme.

**Példák.** $x^3 + 1 \in \mathbb{Z}[x]$, $\tfrac{2}{3} \in \mathbb{Q}[x]$, $\pi x + (i + \sqrt{2}) \in \mathbb{C}[x]$.

### A fokra vonatkozó becslések

**Állítás.** Legyen $f, g \in R[x]$, $\deg(f) = n$ és $\deg(g) = k$. Ekkor

$$\deg(f+g) \le \max(n, k), \qquad \deg(f \cdot g) \le n + k.$$

*Bizonyítás.* Legyen $h = f+g$. Ha $j > \max(n,k)$, akkor $h_j = 0 + 0 = 0$. Legyen $h = f \cdot g$. Ha $j > n+k$, akkor

$$h_j = \sum_{i=0}^{j} f_i g_{j-i} = \sum_{i=0}^{n} f_i g_{j-i} + \sum_{i=n+1}^{j} f_i g_{j-i} = \sum_{i=0}^{n} f_i \cdot 0 + \sum_{i=n+1}^{j} 0 \cdot g_{j-i} = 0. \quad \square$$

### Nullosztómentes eset: a fokok összeadódnak

**Megjegyzés.** Ha $R$ nullosztómentes, a szorzatra vonatkozó becslésben **egyenlőség** áll:

$$h_{n+k} = \sum_{i=0}^{n+k} f_i g_{n+k-i} = \sum_{i=0}^{n-1} f_i g_{n+k-i} + f_n g_k + \sum_{i=n+1}^{n+k} f_i g_{n+k-i} = f_n g_k \neq 0,$$

vagyis

$$\deg(f\cdot g) = \deg(f) + \deg(g).$$

Ez a fokösszegzés a felbonthatóság vizsgálatának alapeszköze: egy $f = g\cdot h$ szorzat-előállításban a tényezők foka összeadódik, ezért az alacsony fokú polinomok felbonthatósága a fokok lehetséges összegbontásaiból leolvasható.

## Kapocs

- [[concepts/dimatii/polinomgyuru]] — a fok, a főegyüttható és a főtag definíciója
- [[concepts/dimatii/nullosztomentes-gyuru]] — a fokösszegzés feltétele
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a maradék fokára tett kikötés adja a tétel egyértelműségét
- [[concepts/dimatii/irreducibilis-polinom]] — a fokösszegzés adja a felbonthatóság fokszám szerinti elemzését
