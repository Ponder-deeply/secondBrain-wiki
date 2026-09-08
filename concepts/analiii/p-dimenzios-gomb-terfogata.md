---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# A $p$-dimenziós gömb térfogata

Az $r$ sugarú $p$-dimenziós gömb térfogata $\gamma_p r^p$, ahol a $\gamma_p$ konstans a szelettétel és a Wallis-integrálok segítségével zárt alakban megadható.

## Tartalom

### A tétel

Az $r$ sugarú gömb térfogata $\gamma_p r^p$, ahol

$$\gamma_{2k} = \frac{\pi^k}{k!}, \qquad \gamma_{2k+1} = \frac{\pi^k \cdot 2^{2k+1} k!}{(2k+1)!}.$$

Kiindulásként $\gamma_1 = 2$ (a $[-r,r]$ szakasz hossza) és $\gamma_2 = \pi$ (a körlap területe).

### A rekurzió felállítása

A [[concepts/analiii/jordan-mertek-szeletelessel]] szelettételét a gömbre alkalmazva a $y$ magasságú szelet egy $\sqrt{r^2-y^2}$ sugarú $p$-dimenziós gömb:

$$t_{p+1}(B(0,r)) = \int_{y=-r}^{r} t_p\!\left(B\!\left(0,\sqrt{r^2-y^2}\right)\right)\mathrm{d}y = \int_{y=-r}^{r} \gamma_p (r^2-y^2)^{p/2}\,\mathrm{d}y.$$

Az $y = r\sin t$, $-\pi/2 \leq t \leq \pi/2$ helyettesítéssel

$$t_{p+1}(B(0,r)) = \gamma_p \int_{-\pi/2}^{\pi/2} (\cos t)^{p+1}\,\mathrm{d}t \cdot r^{p+1} = (\gamma_p I_{p+1}) r^{p+1},$$

tehát

$$\gamma_{p+1} = \gamma_p \cdot I_{p+1}, \qquad I_n = \int_{-\pi/2}^{\pi/2} (\cos t)^n\,\mathrm{d}t.$$

### A Wallis-integrálok

$I_0 = \pi$, $I_1 = 2$. Parciális integrálással

$$I_n - I_{n+2} = \int_{-\pi/2}^{\pi/2} (\cos t)^n \sin^2 t\,\mathrm{d}t = \frac{1}{n+1} I_{n+2},$$

amiből a rekurzió

$$I_{n+2} = \frac{n+1}{n+2} I_n.$$

Ebből

$$I_{2k} = \pi \cdot \frac{1}{2}\cdot\frac{3}{4}\cdots\frac{2k-1}{2k}, \qquad I_{2k+1} = 2 \cdot \frac{2}{3}\cdot\frac{4}{5}\cdots\frac{2k}{2k+1}, \qquad I_n I_{n+1} = \frac{2\pi}{n+1}.$$

Az utolsó, szorzatalakú azonosság teszi a teleszkopikus összeszorzást lehetővé:

$$\gamma_{2k} = \gamma_2 (I_3I_4)(I_5I_6)\cdots(I_{2k-1}I_{2k}) = \pi \cdot \frac{\pi}{2}\cdot\frac{\pi}{3}\cdots\frac{\pi}{k} = \frac{\pi^k}{k!},$$

$$\gamma_{2k+1} = \gamma_1 (I_2I_3)(I_4I_5)\cdots(I_{2k}I_{2k+1}) = 2 \cdot \frac{2\pi}{3}\cdot\frac{2\pi}{5}\cdots\frac{2\pi}{2k+1} = \frac{\pi^k \cdot 2^{2k+1}k!}{(2k+1)!}.$$

A tankönyvekben az $I_n$ integrálok a *Wallis-formula* fejezetében szoktak szerepelni.

## Kapocs

- [[concepts/analiii/jordan-mertek-szeletelessel]] — a rekurziót előállító tétel
- [[concepts/analiii/jordan-mertek-linearis-transzformaltja]] — a $t(M(A)) = |\lambda|^p t(A)$ hasonlósági szabály, amely az $r^p$ tényezőt önmagában is megmagyarázza
- [[concepts/analii/hatarozott-integral-parcialisintegrals]] — az $I_n$ rekurzió az egyváltozós parciális integrálás technikájának közvetlen alkalmazása
- [[concepts/analii/hatarozott-integral-helyettesites]] — az $y = r\sin t$ helyettesítés az egyváltozós helyettesítéses integrálás szabálya szerint történik
