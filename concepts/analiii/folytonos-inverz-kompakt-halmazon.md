---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.5. Tétel"]
derivation: source
updated: 2026-09-07
---

# Folytonos inverz kompakt tartományon

Ha egy folytonos, invertálható függvény értelmezési tartománya kompakt, akkor az inverze is folytonos. Kompaktság nélkül ez hamis: a folytonos bijekció inverze általában nem folytonos.

## Tartalom

### A tétel

**2.5. Tétel.** Legyen az $f \in X \to Y$ függvény folytonos, invertálható, és $D_f$ kompakt. Ekkor az $f^{-1}$ inverzfüggvény is folytonos.

### Bizonyítás

Indirekt: tegyük fel, hogy valamilyen $y \in D_{f^{-1}} = R_f$ helyen $f^{-1} \notin C\{y\}$. Ekkor van olyan $\varepsilon > 0$, hogy minden $\delta > 0$-hoz alkalmas $z \in R_f$, $\sigma(z,y) < \delta$ mellett

$$\rho\bigl(f^{-1}(z), f^{-1}(y)\bigr) \ge \varepsilon.$$

Speciálisan $\delta := 1/n$ választással olyan $z_n \in R_f$ pontokat kapunk, hogy $z_n \to y$ és $\rho\bigl(f^{-1}(z_n), f^{-1}(y)\bigr) \ge \varepsilon$.

Legyen $x_n := f^{-1}(z_n) \in D_f$. A $D_f$ kompaktsága miatt van olyan $(\nu_n)$ indexsorozat, amellyel $\xi := \lim(x_{\nu_n}) \in D_f$. Az [[concepts/analiii/atviteli-elv-metrikus-terben|átviteli elv]] szerint

$$f(\xi) = \lim f(x_{\nu_n}) = \lim(z_{\nu_n}) = y,$$

és az invertálhatóság miatt $f^{-1}(y) = \xi$. Így viszont

$$\varepsilon \le \rho\bigl(f^{-1}(z_{\nu_n}), f^{-1}(y)\bigr) = \rho(x_{\nu_n}, \xi) \to 0 \qquad (n\to\infty),$$

ami lehetetlen. $\blacksquare$

### Miért kell a kompaktság

A tétel lényege, hogy a kompaktság „nem engedi elszökni" az ősképeket: a $z_n \to y$ konvergenciából az $x_n$ ősképek konvergenciáját csak részsorozat-kiválasztással lehet kicsikarni, és épp ezt adja a kompaktság. Kompaktság nélkül az inverz folytonossága általában nem következik — a differenciálszámításban ezért kell a lokális inverz létezéséhez a jóval erősebb $\det f'(a) \ne 0$ feltétel, lásd [[concepts/analiii/inverzfuggveny-tetel]].

## Kapocs

- [[concepts/analiii/kompakt-halmazok]] — a felhasznált kompaktsági tulajdonság
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a bizonyítás eszköze
- [[concepts/analiii/weierstrass-tetel-kompakt-halmazon]] — a kompaktság másik következménye folytonos leképezésre
- [[concepts/analiii/inverzfuggveny-tetel]] — a differenciálható eset, ahol a kompaktságot a derivált regularitása váltja fel
