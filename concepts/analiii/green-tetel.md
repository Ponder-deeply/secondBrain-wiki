---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Green-tétel

Jordan-tartományon vett parciális derivált területi integrálját a határgörbén vett vonalintegrállal fejezi ki. Ez a síkbeli integráltételek közös alapköve: a Newton–Leibniz formula, a Gauss–Osztrogradszkij és a Stokes-tétel síkbeli alakja mind ebből következik.

## Tartalom

### A tétel

**Tétel (Green).** Legyen $K$ Jordan-tartomány, amelynek határa szakaszonként $C^1$, legyen $G \supset \operatorname{cl} K$ nyílt, és $f : G \to \mathbb{R}$ folytonosan differenciálható.

(a) Ha $\frac{\partial f}{\partial x}$ létezik és folytonos $\operatorname{cl} K$-n, akkor

$$\int_{\partial K} f\,\mathrm{d}y = \int_K \frac{\partial f}{\partial x}\,\mathrm{d}x\,\mathrm{d}y .$$

(b) Ha $\frac{\partial f}{\partial y}$ létezik és folytonos $\operatorname{cl} K$-n, akkor

$$\int_{\partial K} f\,\mathrm{d}x = -\int_K \frac{\partial f}{\partial y}\,\mathrm{d}x\,\mathrm{d}y .$$

A kettő együtt, két folytonosan differenciálható $f, g$ függvényre:

$$\int_{\partial K} (f\,\mathrm{d}x + g\,\mathrm{d}y) = \int_K \left( -\frac{\partial f}{\partial y} + \frac{\partial g}{\partial x} \right) \mathrm{d}x\,\mathrm{d}y .$$

Figyeljünk a **kereszteződésre**: az $x$ szerinti derivált az $y$ szerinti vonalintegrállal, az $y$ szerinti derivált az $x$ szerintivel áll párban, és az utóbbinál van egy mínusz. Ez az aszimmetria a határ pozitív irányításából jön.

### Bizonyítás normáltartományra

A bizonyítás lényege: $K$ minden függőleges szekcióján alkalmazzuk az **egyváltozós Newton–Leibniz formulát**.

Tegyük fel, hogy

$$K = \{(x,y) : x \in [a,b],\ \varphi(x) \le y \le \psi(x)\}$$

valamilyen $[a,b]$ intervallummal és szakaszonként differenciálható $\varphi \le \psi$ függvényekkel. A $\partial K$ határ négy részre vágható: az alsó és a felső határoló grafikon ($\gamma_3$, illetve $\gamma_1$), valamint két függőleges szakasz ($\gamma_2$, $\gamma_4$). A felső grafikonon a pozitív irányítás miatt jobbról balra kell végigmennünk; a függőleges szakaszokon pedig az $x$ szerinti vonalintegrál $0$, hiszen ott $x$ állandó. Így

$$\int_K \frac{\partial f}{\partial y}\,\mathrm{d}x\,\mathrm{d}y = \int_{x=a}^{b}\left(\int_{y=\varphi(x)}^{\psi(x)} \frac{\partial f}{\partial y}\,\mathrm{d}y\right)\mathrm{d}x = \int_{x=a}^{b}\bigl( f(x,\psi(x)) - f(x,\varphi(x)) \bigr)\,\mathrm{d}x = -\int_{\partial K} f\,\mathrm{d}x .$$

Az (a) állítás tükrözött normáltartományon, az $x$ és $y$ szerepének felcserélésével megy ugyanígy. A tükrözés megfordítja a határ irányítását, ezt vissza kell fordítani — innen jön a két állítás előjelkülönbsége.

### Az általános eset vázlata

1. A fentiek bizonyítanak például **konvex sokszögekre**.
2. Átlókkal vagy párhuzamos szakaszokkal szétvágva-összeragasztva megkapjuk az állítást **tetszőleges zárt töröttvonalra** (a belső vágásokon a vonalintegrálok kétszer, ellentétes irányítással szerepelnek, tehát kiesnek).
3. Az általános esetben a határgörbét belülről töröttvonalakkal közelítjük, majd határátmenet.

### Több görbével határolt tartomány („krumpli")

A tétel kiterjed olyan tartományokra is, amelyeket egynél több zárt görbe határol — például lyukas tartományokra. Legyen $K \subset G$ olyan halmaz, amelynek határa véges sok, diszjunkt, egyszerű zárt, szakaszonként $C^1$ görbéből áll; ezt a jegyzet **krumplinak** nevezi. Ekkor a határgörbék irányíthatók úgy, hogy $K$ külső pontjaira az indexösszeg $0$, a belső pontokra pedig $+1$ legyen. Ezután $\partial K$ (a „krumpli héja") ezeknek az irányított görbéknek a halmazát jelöli, $\int_{\partial K}$ pedig a rajtuk vett integrálok összegét.

Az összeragasztós-approximálós módszer ezekre is működik, így a Green-tétel és következményei erre az általánosabb tartományosztályra is kiterjeszthetők.

### Következmény: rotációmentesség

Szakaszonként $C^1$ Jordan-görbén, amelynek a belsejében egy vektormező rotációmentes, a valós vonalintegrál $0$:

$$\int_{\partial K}\langle f, \mathrm{d}\mathbf{x}\rangle = \int_{\partial K} f_1\,\mathrm{d}x + \int_{\partial K} f_2\,\mathrm{d}y = \int_K\left(\frac{\partial f_2}{\partial x} - \frac{\partial f_1}{\partial y}\right)\mathrm{d}x\,\mathrm{d}y = 0 .$$

Ezt a Goursat-lemmával már sokkal általánosabban is beláttuk (ott nem kellett a határ $C^1$ volta); a Green-tétel viszont közvetlen, számolós utat ad ugyanide.

## Kapocs

- [[concepts/analiii/jordan-gorbetetel]] — a tartományosztály, amelyen a tételt kimondjuk
- [[concepts/analii/newton-leibniz-tetel]] — az egyváltozós formula, amelyet a bizonyítás minden szekción alkalmaz
- [[concepts/analiii/jordan-tartomany-terulete]] — közvetlen következmény: területképlet vonalintegrállal
- [[concepts/analiii/stokes-tetel]] — a síkbeli Stokes-tétel a Green-tétel kétszeri alkalmazása
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — szintén közvetlenül a Green-tételből adódik
- [[concepts/analiii/valos-vonalintegral]] — a jobb oldalon szereplő integrálfogalom
