---
tags: [concept]
sources: [DimatIIEa05.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_Polinomok.pdf, dm2gy07.pdf, dm2gy07_Polinomok.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
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

### Farkas-diák kiegészítése

A diák a főegyüttható szorzására is kimondja: ha $h = fg$, akkor $h$ főegyütthatója $a_n b_m$ ($k = n+m$); a nullpolinom foka a diákon $-1$ vagy $-\infty$ megállapodás. A fokfüggvény szerepe: test fölött $\varphi(f) = \deg(f)$ ($f \in R[x]^*$) euklideszi normával $R[x]$ **euklideszi gyűrű** (a maradékos osztás egyértelműségéből; lásd [[concepts/dimatii/polinomok-maradekos-osztasa]]).

### Feladattípusok és módszerek: szorzat foka és együtthatói (gyakorlati feladatsorok, 6–7. hét)

**Módszer.** A szorzat $k$-adik együtthatója a konvolúció: $h_k=\sum_{i+j=k}f_ig_j$, azaz csak azok a párok számítanak, amelyek indexösszege $k$. A $\deg f+\deg g$ fölötti együtthatók mind $0$, és mindig ellenőrizni kell, hogy $f_n g_m$ nem tűnik-e el a gyűrűben.

**Példa ($\mathbb{Z}$ és $\mathbb{Z}_{24}$).** $f=3x^8+5x^6-11x^3+7x^2-15x+8$, $g=16x^7-13x^6+6x^3-13x+21$. $\mathbb{Z}$ fölött $\deg(fg)=15$, és a $0$-, $9$-, $14$-, $15$-, $20$-adfokú tag együtthatója $168,\ 246,\ -39,\ 48,\ 0$. $\mathbb{Z}_{24}$ fölött ugyanezek modulo $24$: $0,\ 6,\ 9,\ 0,\ 0$, így a főegyüttható $48\equiv0$ miatt **a szorzatpolinom foka csak $14$** (a fokösszeg $15$ lenne). A konstans tag $8\cdot21=168=7\cdot24\equiv0$ is eltűnik.

**Példa ($\mathbb{Z}_{72}$).** $(8x^2+12)(18x+36)=144x^3+288x^2+216x+432$, és $144=2\cdot72$, $288=4\cdot72$, $216=3\cdot72$, $432=6\cdot72$, tehát a szorzat a **nullpolinom**: két nemnulla polinom szorzata $0$, a fok $-\infty$. Ez a nullosztós gyűrű jele.

**Példa (7. hét, $\deg f=7$, $\deg g=8$).** $\mathbb{Q}$ fölött $f=3x^7+5x^6+4x^5-7x+1$, $g=-x^8+5x^7-11x^6+7x^3+5x-9$ szorzatának foka $15$, az együtthatók ($0$-, $2$-, $14$-, $15$-ödfokú tag): $-9,\ -35,\ 10,\ -3$. $\mathbb{Z}_5$ fölött (az $f=3x^7+3x^6+4x^5+3x+1$, $g=4x^8+3x^7+4x^6+7x^3+4x+1$ párra; itt $7\equiv2$) a fok $15$, az együtthatók $1,\ 2,\ 1,\ 2$. $\mathbb{Z}_2$ fölött ($f=x^7+x^6+x^5+x+1$, $g=x^8+x^7+x^6+x^3+x+1$) a fok $15$, az együtthatók $1,\ 1,\ 0,\ 1$.

**Tipikus hibák.** (1) Véges gyűrű fölött a fokösszeg-képletet vakon alkalmazni; csak nullosztómentes gyűrűben ($\mathbb{Z}_p$, $p$ prím, vagy $\mathbb{Z}$) igaz, $\mathbb{Z}_{24}$-ben, $\mathbb{Z}_{72}$-ben nem. (2) Az együtthatókat a végén nem redukálni modulo $n$. (3) A $\mathbb{Z}_5$ fölötti polinom „$7x^3$” együtthatóját nem redukálni ($7\equiv2$).

## Kapocs

- [[concepts/dimatii/polinomgyuru]] — a fok, a főegyüttható és a főtag definíciója
- [[concepts/dimatii/nullosztomentes-gyuru]] — a fokösszegzés feltétele
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a maradék fokára tett kikötés adja a tétel egyértelműségét
- [[concepts/dimatii/irreducibilis-polinom]] — a fokösszegzés adja a felbonthatóság fokszám szerinti elemzését
- [[concepts/dimatii/nullosztomentes-gyuru]] — a fokösszeg-szabály feltétele
