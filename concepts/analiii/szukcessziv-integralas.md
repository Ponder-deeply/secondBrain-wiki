---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Szukcesszív integrálás

Téglán integrálható függvény többszörös integrálja egymás utáni egyváltozós integrálásokra bontható; a nem tégla alakú tartományon a függvényt nullával kiterjesztve dolgozunk, és az integrálási határokra külön ügyelni kell.

## Tartalom

### A tétel

**Következmény (a szukcesszív integrálás tétele).** Legyen $R = [a_1,b_1]\times\dots\times[a_p,b_p] \subset \mathbb{R}^p$ tégla és $f : R \to \mathbb{R}$ integrálható. Ekkor

$$\int_R f = \int_{x_p=a_p}^{b_p}\left(\dots\int_{x_2=a_2}^{b_2}\left(\int_{x_1=a_1}^{b_1} f(x_1,\dots,x_p)\,\mathrm{d}x_1\right)\mathrm{d}x_2\dots\right)\mathrm{d}x_p,$$

feltéve, hogy mindegyik integrál létezik. Ez a [[concepts/analiii/lebontasi-tetel]] ismételt alkalmazása az $R = [a_1,b_1]\times(\text{a többi})$ szorzatfelbontásra.

### Nem tégla alakú tartomány

Minden korlátos, síkbeli halmaz belefoglalható egy $A \subset R = [a,b]\times[c,d]$ téglába. Az integrálandó függvényt a halmazon kívül $0$-nak definiáljuk:

$$g(x,y) = \begin{cases} f(x,y) & \text{ha } (x,y)\in A, \\ 0 & \text{ha } (x,y)\notin A, \end{cases}$$

ezután már a téglán vett tétel alkalmazható. Például $A = \{(x,y) : 0\leq y\leq x\leq 1\}$ esetén

$$\int_{x=0}^{1}\left(\int_{y=0}^{x} f(x,y)\,\mathrm{d}y\right)\mathrm{d}x = \int_{0\leq y\leq x\leq 1} f(x,y)\,\mathrm{d}x\mathrm{d}y = \int_{y=0}^{1}\left(\int_{x=y}^{1} f(x,y)\,\mathrm{d}x\right)\mathrm{d}y.$$

**Az integrálási határokra vigyázni kell!** Segít, ha az $A$ karakterisztikus függvényét kiírjuk:

$$\int_{x=0}^{1}\left(\int_{y=0}^{1}\chi(x,y)f(x,y)\,\mathrm{d}y\right)\mathrm{d}x = \int_{y=0}^{1}\left(\int_{x=0}^{1}\chi(x,y)f(x,y)\,\mathrm{d}x\right)\mathrm{d}y,$$

és csak a végén szűkítjük a határokat oda, ahol $\chi = 1$.

### Normáltartomány: két grafikon közötti integrálás

**Következmény.** Legyen $A \in \mathcal{J}_p$, $\varphi, \psi : A \to \mathbb{R}$ integrálhatók, $\varphi \leq \psi$, és

$$V = \{(x_1,\dots,x_p,y) : (x_1,\dots,x_p)\in A,\ \varphi(x)\leq y\leq\psi(x)\}.$$

Ha $f : V \to \mathbb{R}$ korlátos és folytonos, akkor

$$\int_V f = \int_{x\in A}\left(\int_{y=\varphi(x)}^{\psi(x)} f(x,y)\,\mathrm{d}y\right)\mathrm{d}x.$$

**Bizonyítás.** $V$ belefoglalható egy $R = A_0\times[a,b]$ téglába; $V$-n kívül legyen $f = 0$. Ekkor $\int_V f = \int_R f$, és a szukcesszív integrálást alkalmazva a belső integrál értelmezési tartománya $[\varphi(x), \psi(x)]$-re szűkül. $\square$

### Példa: a sorrend megcserélése mint számítási trükk

$$\int_{x=0}^{1}\left(\int_{y=x}^{1} e^{y^2}\,\mathrm{d}y\right)\mathrm{d}x = ?$$

Közvetlenül nem számolható ki, mert $e^{y^2}$ primitív függvénye nem elemi függvény. Cseréljük fel a sorrendet: a $0\leq x\leq y\leq 1$ tartományon

$$\int_{x=0}^{1}\left(\int_{y=x}^{1} e^{y^2}\,\mathrm{d}y\right)\mathrm{d}x = \int_{y=0}^{1}\left(\int_{x=0}^{y} e^{y^2}\,\mathrm{d}x\right)\mathrm{d}y = \int_{y=0}^{1} y e^{y^2}\,\mathrm{d}y = \left[\tfrac{1}{2}e^{y^2}\right]_{0}^{1} = \frac{e-1}{2}.$$

## Kapocs

- [[concepts/analiii/lebontasi-tetel]] — az az állítás, amelynek ez a következménye
- [[concepts/analiii/kettos-integralok-felcserelhetosege]] — mikor szabad a sorrendet felcserélni, és mikor nem
- [[concepts/analiii/tobbvaltozos-integral-muveletei]] — a nullával való kiterjesztés tétele, amely a nem tégla alakú tartományt kezelhetővé teszi
- [[concepts/analiii/grafikon-alatti-halmaz-terfogata]] — a normáltartomány mérhetősége innen származik
- [[concepts/analiii/tobbszoros-integral-fizikai-alkalmazasai]] — a szukcesszív integrálás tipikus felhasználása konkrét testekre
- [[concepts/analii/hatarozott-integral-helyettesites]] — a belső integrálok kiszámítása mindig egyváltozós technikákkal történik
