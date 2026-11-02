---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 09_ea_An3_2022_tavasz.pdf, 11_ea_An3_2022_tavasz.pdf, 10_gyak_An_III_2022_tavasz.pdf, 11_gyak_An_III_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, gyakorlat.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Szukcesszív integrálás

Téglán integrálható függvény többszörös integrálja egymás utáni egyváltozós integrálásokra bontható; a nem tégla alakú tartományon a függvényt nullával kiterjesztve dolgozunk, és az integrálási határokra külön ügyelni kell.

## Tartalom

### A tétel

**A szukcesszív integrálás 1. tétele (gyakorlati megfogalmazás).** Legyen $I=[a,b]\times[c,d]$, $f:I\to\mathbb{R}$, és tegyük fel, hogy (a) $f\in R(I)$, (b) minden $x\in[a,b]$-re $f_x=f(x,\cdot)\in R[c,d]$, (c) minden $y\in[c,d]$-re $f^y=f(\cdot,y)\in R[a,b]$. Ekkor $\iint_I f=\int_a^b\left(\int_c^d f\,\mathrm{d}y\right)\mathrm{d}x=\int_c^d\left(\int_a^b f\,\mathrm{d}x\right)\mathrm{d}y$. **A 2. tétel:** folytonos $f$ esetén (a)–(c) automatikusan teljesül, így az integrálás sorrendje felcserélhető. *(10. gyak. 1. old.)*

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

### Példa: paraméteres valós integrál a sorrend megcserélésével

Mutassuk meg, hogy minden $0 < a < b$ valós paraméter esetén

$$\int_0^1 \frac{x^b - x^a}{\ln x}\,\mathrm{d}x = \ln\left(\frac{b+1}{a+1}\right).$$

A $g(x) := \frac{x^b-x^a}{\ln x}$ ($x\in(0,1)$) függvény folytonosan kiterjeszthető $[0,1]$-re ($\lim_{x\to 0+0} g(x) = 0$, $\lim_{x\to 1-0} g(x) = b-a$), tehát az integrál létezik.

Vegyük észre, hogy $g(x) = \int_a^b x^y\,\mathrm{d}y$ (hiszen $\frac{\mathrm{d}}{\mathrm{d}y}x^y = x^y\ln x$, így $\int_a^b x^y\,\mathrm{d}y = \left[\frac{x^y}{\ln x}\right]_{y=a}^{y=b} = \frac{x^b-x^a}{\ln x}$). Ezért a keresett integrál az $f(x,y) := x^y$ ($(x,y)\in[0,1]\times[a,b] =: I$) folytonos függvény kettős integrálja, és a Fubini-tétel szerint a szukcesszív integrálás sorrendje felcserélhető:

$$\int_0^1\left(\int_a^b x^y\,\mathrm{d}y\right)\mathrm{d}x = \iint_I f(x,y)\,\mathrm{d}x\,\mathrm{d}y = \int_a^b\left(\int_0^1 x^y\,\mathrm{d}x\right)\mathrm{d}y.$$

Az $x$ szerinti belső integrál elemi: $\int_0^1 x^y\,\mathrm{d}x = \left[\frac{x^{y+1}}{y+1}\right]_{x=0}^{x=1} = \frac{1}{y+1}$, tehát

$$\int_a^b\left(\int_0^1 x^y\,\mathrm{d}x\right)\mathrm{d}y = \int_a^b \frac{1}{y+1}\,\mathrm{d}y = \ln\left(\frac{b+1}{a+1}\right),$$

ami éppen a bal oldal, hiszen a $y$ szerinti belső integrál $\int_a^b x^y\,\mathrm{d}y = g(x)$ definíció szerint. Ez a második, a Gauss-integrálhoz hasonló példa arra, hogy a sorrend felcserélése egy egyváltozós szempontból nehéz (elemi primitív függvény nélküli) integrált kettős integrálon keresztül kiszámíthatóvá tesz.

### Feladatok

**Módszer.** Téglán: tetszőleges sorrend, a változók szétválnak, ha az integrandus szorzat. Normáltartományon: a belső határok a külső változótól függenek. Először mindig ábra, a határgörbék metszéspontjai, majd annak a változónak a kiválasztása, amely szerint a tartomány egyszerűbben „szeletelhető". *(An III gyak. 10–11.; gyakorlat.pdf, Többdimenziós integrálok 5–9.; 10. és 11. gyak. lap megoldásai szerint ellenőrizve.)*

**Normáltartományok.** $H_x=\{(x,y):a\le x\le b,\ \varphi_1(x)\le y\le\varphi_2(x)\}$ az $x$ tengelyre nézve normáltartomány ($\varphi_i$ folytonos, $\varphi_1\le\varphi_2$); ekkor folytonos $f$-re $f\in R(H_x)$ és $\iint_{H_x}f=\int_a^b\left(\int_{\varphi_1(x)}^{\varphi_2(x)}f\,\mathrm{d}y\right)\mathrm{d}x$. Hasonlóan $H_y=\{c\le y\le d,\ \psi_1(y)\le x\le\psi_2(y)\}$ és $\iint_{H_y}f=\int_c^d\left(\int_{\psi_1(y)}^{\psi_2(y)}f\,\mathrm{d}x\right)\mathrm{d}y$. Az integrálhatóság itt úgy értelmezett, hogy $f$-et a $H$-t tartalmazó $I$ intervallumra nullával kiterjesztjük ($\tilde f=f$ $H$-n, $0$ $I\setminus H$-n), és $\iint_H f:=\iint_I\tilde f$; ez nem függ $I$ választásától. Szokásos jelölés: $\int_a^b\int_{\varphi_1(x)}^{\varphi_2(x)}f\,\mathrm{d}y\,\mathrm{d}x$ (a belső integrál a belső differenciálhoz tartozik). *(10. és 11. gyak.)*

- $\iint_{[0,1]\times[0,2]} x^3\sqrt y$: $\int_0^1x^3\,\mathrm{d}x\cdot\int_0^2\sqrt y\,\mathrm{d}y=\frac14\cdot\frac{4\sqrt2}{3}=\frac{\sqrt2}{3}$.
- $\iint_{[1,3]\times[0,\pi/2]} x\sin(xy)$: előbb $y$ szerint: $\int_0^{\pi/2}x\sin(xy)\,\mathrm{d}y=1-\cos\frac{\pi x}{2}$, majd $\int_1^3\left(1-\cos\frac{\pi x}2\right)\mathrm{d}x=\left[x-\frac2\pi\sin\frac{\pi x}2\right]_1^3=2+\frac4\pi$. A fordított sorrendben $\int_1^3x\sin(xy)\,\mathrm{d}x$ parciális integrálást igényel: $g(y)=\frac{\sin y-\sin3y}{y}=\left(\frac{-2\cos2y\sin y}{y}\right)'$ ($g(0):=0$), a primitív függvény $G(y)=\frac{-2\cos2y\sin y}{y}$ ($G(0)=-2$), és $\int_0^{\pi/2}g=G(\pi/2)-G(0)=\frac4\pi+2$ — ugyanaz az érték, de lényegesen több munkával. Tanulság: a tétel az eredmény egyezését garantálja, a számolás nehézségét nem. *(10. gyak. 2. feladat)*
- $\iint_H(2xy-x^3)$, $H$ az $y=x^2$ és $y=x+2$ közötti tartomány: metszéspontok $x=-1,2$; $\int_{-1}^{2}\int_{x^2}^{x+2}=\int_{-1}^2(-x^4-x^3+4x^2+4x)\,\mathrm{d}x=\frac{153}{20}$.
- $\iint_H(x+y)$, $H=\{0\le x\le1,\,0\le y\le1-x\}$: $\int_0^1\left(\frac12-\frac{x^2}2\right)\mathrm{d}x=\frac13$.
- $\iint_H ye^x$, $H$ a $(0,2),(1,1),(3,2)$ csúcsú háromszög: az $AB$ egyenes $x=2-y$, a $BC$ egyenes $x=2y-1$, így $H=\{1\le y\le2,\ 2-y\le x\le2y-1\}$ ($x$ szerint belül egyszerűbb; ha $x$ a külső változó, a $[0,1]$ és $[1,3]$ intervallumokra két részre kell bontani). $\int_1^2y\left(e^{2y-1}-e^{2-y}\right)\mathrm{d}y=e^{-1}\int_1^2ye^{2y}\mathrm{d}y-e^2\int_1^2ye^{-y}\mathrm{d}y$, két parciális integrállal $\int_1^2ye^{2y}=\frac{e^2}4(3e^2-1)$, $\int_1^2ye^{-y}=\frac{2e-3}{e^2}$; az eredmény $\frac34e^3-\frac94e+3=\frac{3e^3-9e+12}{4}$. *(10. gyak. 5. feladat)*
- $\iint_He^x(\sqrt x+y)$, $H$ az $x=1$ és $y^2=x$ által határolt tartomány, $x$-normál: $0\le x\le1$, $-\sqrt x\le y\le\sqrt x$. A belső integrál $\left[\sqrt x\,y+\frac{y^2}2\right]_{-\sqrt x}^{\sqrt x}=2x$, így $\int_0^12xe^x\,\mathrm{d}x=2$ (parciálisan). $H$ $y$-normál is ($-1\le y\le1$, $y^2\le x\le1$), de a belső integrál $x$ szerint nem elemi. *(10. gyak. 6. feladat)*
- Normáltartomány kétféle felbontása: az $\iint_H(2xy-x^3)$ feladatnál $H$ $y$-normál alakban két részre esik ($H_1:\ 0\le y\le1,\ -\sqrt y\le x\le\sqrt y$; $H_2:\ 1\le y\le4,\ y-2\le x\le\sqrt y$), ezért jóval több számítás — válasszuk azt a változót belsőnek, amelyre a tartomány nem esik szét. *(10. gyak. 3. feladat)*
- Sorrendcsere: $\int_0^1\int_{-\sqrt{1-y^2}}^{1-y}f\,\mathrm{d}x\,\mathrm{d}y=\int_{-1}^0\int_0^{\sqrt{1-x^2}}f\,\mathrm{d}y\,\mathrm{d}x+\int_0^1\int_0^{1-x}f\,\mathrm{d}y\,\mathrm{d}x$ (a bal határ az egységkör $x=-\sqrt{1-y^2}$ negyede, a jobb az $x=1-y$ egyenes; $H_1:\ -1\le x\le0,\ 0\le y\le\sqrt{1-x^2}$, $H_2:\ 0\le x\le1,\ 0\le y\le1-x$, és $\iint_H=\iint_{H_1}+\iint_{H_2}$). *(11. gyak. 1. feladat)*
- $\int_0^1\int_{y^2}^1 y\sin x^2\,\mathrm{d}x\,\mathrm{d}y$: $x$ szerint nem primitiválható, ezért cserélünk: $0\le x\le1$, $0\le y\le\sqrt x$, a belső integrál $\sin x^2\left[\frac{y^2}2\right]_0^{\sqrt x}=\frac x2\sin x^2$, az eredmény $\frac14\int_0^12x\sin x^2\,\mathrm{d}x=\frac14\left[-\cos x^2\right]_0^1=\frac{1-\cos1}{4}$. *(11. gyak. 2. feladat)* A gyakorlat listája a tipikus „nem elemi primitívű” függvényekről: $e^{\pm x^2}$, $\sin x^2$, $\cos x^2$, $\frac{\sin x}x$, $\frac{\cos x}x$, $\frac{e^x}x$, $\frac1{\ln x}$, $\sqrt{x^3+1}$ — ha ilyen adódik a belső integrálban, érdemes a sorrendet felcserélni. Hasonlóan $\int_0^1\int_x^1\frac{x\sin y}{y}\,\mathrm{d}y\,\mathrm{d}x=\frac{\sin1-\cos1}{2}$.
- Szorzatfüggvény: ha $f\in R[a,b]$, $g\in R[c,d]$, akkor $h(x,y)=f(x)g(y)$ integrálható és $\iint h=\int_a^bf\cdot\int_c^dg$ (lásd [[concepts/analiii/szorzathalmaz-merteke-es-integralja]]).
- Háromszoros: $\int_0^x\int_0^y\int_0^z f(t)\,\mathrm{d}t\,\mathrm{d}z\,\mathrm{d}y=\frac12\int_0^x(x-t)^2f(t)\,\mathrm{d}t$ (a sorrend megcserélésével, ismételt integrálás).
- Szimplexen: $\iiint\frac{1}{(1+x+y+z)^3}$ az $x+y+z\le1$ tartományon: az $u=x+y+z$ szintű szeletek térfogata $u^3/6$, így $\int_0^1\frac{u^2/2}{(1+u)^3}\mathrm{d}u=\frac{\ln2}2-\frac5{16}$. Hasonlóan $\iiint\frac1{1+x+y+z}=\frac{\ln2}2-\frac14$.

## Kapocs

- [[concepts/analiii/lebontasi-tetel]] — az az állítás, amelynek ez a következménye
- [[concepts/analiii/kettos-integralok-felcserelhetosege]] — mikor szabad a sorrendet felcserélni, és mikor nem
- [[concepts/analiii/tobbvaltozos-integral-muveletei]] — a nullával való kiterjesztés tétele, amely a nem tégla alakú tartományt kezelhetővé teszi
- [[concepts/analiii/grafikon-alatti-halmaz-terfogata]] — a normáltartomány mérhetősége innen származik
- [[concepts/analiii/tobbszoros-integral-fizikai-alkalmazasai]] — a szukcesszív integrálás tipikus felhasználása konkrét testekre
- [[concepts/analii/hatarozott-integral-helyettesites]] — a belső integrálok kiszámítása mindig egyváltozós technikákkal történik
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
