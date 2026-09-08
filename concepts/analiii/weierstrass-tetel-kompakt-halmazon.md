---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.4. Tétel"]
derivation: source
updated: 2026-09-07
---

# Weierstrass-tétel: folytonos kép kompakt halmazon

Kompakt halmaz folytonos képe kompakt. Valós értékű esetben ebből következik a klasszikus Weierstrass-tétel: kompakt értelmezési tartományon folytonos valós függvénynek van minimuma és maximuma.

## Tartalom

### A tétel

**2.4. Tétel (Weierstrass).** Ha az $f \in X \to Y$ függvény folytonos és a $D_f$ értelmezési tartomány kompakt, akkor az $R_f$ értékkészlet is kompakt. Speciálisan $f \in X \to \mathbb{R}$ esetén $R_f$-nek van legkisebb és legnagyobb eleme.

### Bizonyítás

Legyen $(y_n) : \mathbb{N} \to R_f$ tetszőleges sorozat; a sorozatkompaktság szerint konvergens részsorozatot kell találnunk $R_f$-beli határértékkel. Alkalmas $x_n \in D_f$ pontokkal $y_n = f(x_n)$. A $D_f$ kompaktsága miatt van olyan $(\nu_n)$ indexsorozat, amelyre $(x_{\nu_n})$ konvergens és $a := \lim(x_{\nu_n}) \in D_f$. Mivel $f \in C\{a\}$, az [[concepts/analiii/atviteli-elv-metrikus-terben|átviteli elv]] szerint

$$\lim(y_{\nu_n}) = \lim f(x_{\nu_n}) = f(a) \in R_f. \qquad \blacksquare$$

### A valós értékű eset

Ha $f \in X \to \mathbb{R}$, akkor $R_f$ kompakt, tehát korlátos és zárt, így az

$$m := \inf R_f, \qquad M := \sup R_f$$

értékek valósak. Megmutatjuk, hogy $M \in R_f$. A szuprémum tulajdonsága szerint van olyan $(y_n) : \mathbb{N}\to R_f$, amelyre

$$M - \frac1n < y_n \le M \qquad (1 \le n \in \mathbb{N}),$$

tehát $\lim(y_n) = M$. Írjuk $y_n = f(x_n)$ alakba; $D_f$ kompaktságából $a := \lim(x_{\nu_n}) \in D_f$ egy alkalmas részsorozatra, és az átviteli elvvel

$$M = \lim(y_n) = \lim(y_{\nu_n}) = \lim f(x_{\nu_n}) = f(a) \in R_f.$$

Az $m \in R_f$ állítás ugyanígy adódik. A szélsőértéket tehát $f$ **felveszi** — ez a klasszikus, $[a,b]$-n megfogalmazott Weierstrass-tétel absztrakt megfelelője.

### Mire használjuk

Ez a tétel a többváltozós szélsőérték-feladatok létezési fele: korlátos és zárt (tehát $\mathbb{R}^p$-ben a [[concepts/analiii/heine-borel-tetel|Heine–Borel-tétel]] szerint kompakt) tartományon folytonos függvény szélsőértéke garantáltan létezik, és már csak a helyét kell megkeresni a [[concepts/analiii/lokalis-szelsoertek-feltetelei|lokális feltételekkel]] és a peremvizsgálattal.

## Kapocs

- [[concepts/analiii/kompakt-halmazok]] — a kompaktság definíciója és alaptulajdonságai
- [[concepts/analiii/heine-borel-tetel]] — $\mathbb{R}^p$-ben a kompaktság korlátosság + zártság
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a bizonyítás eszköze
- [[concepts/analiii/folytonos-inverz-kompakt-halmazon]] — a kompakt tartomány másik következménye
- [[concepts/analiii/egyenletes-folytonossag-metrikus-terben]] — a Heine-tétel, a kompaktság harmadik következménye
- [[concepts/analiii/bolzano-tetel-osszefuggo-halmazon]] — az összefüggőségre vonatkozó párja
