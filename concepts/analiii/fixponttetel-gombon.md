---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.5.2. Tétel, 1.6. viii)–xi) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# A fixponttétel gömbre szűkített változata

A Banach-fixponttétel nem kívánja meg, hogy a kontrakció az egész téren értelmezve legyen: elég egy zárt gömbön kontrakciónak lenni, ha a gömb középpontja „nem mozdul el túl messze". A tétel élessége is szigorú: a $q<1$ konstans nem cserélhető a gyengébb szigorú egyenlőtlenségre.

## Tartalom

### A gömbre szűkített tétel

**Tétel.** Legyen $(X,\rho)$ **teljes** metrikus tér, $a \in X$, $r>0$, és

$$Y := \{x\in X : \rho(x,a)\leq r\}.$$

Tegyük fel, hogy az $f \in X \to X$ leképezésre

- $Y \subset D_f$;
- van olyan $0\leq q<1$, hogy $\rho\bigl(f(x),f(y)\bigr) \leq q\cdot\rho(x,y)$ minden $x,y\in Y$-ra;
- $\rho\bigl(a,f(a)\bigr) \leq (1-q)r$.

Ekkor egyértelműen létezik olyan $\alpha \in Y$, hogy $f(\alpha)=\alpha$; továbbá bármely $x_0 \in Y$ mellett az $x_{n+1}:=f(x_n)$ sorozat konvergens, $\lim(x_n)=\alpha$, és

$$\rho(x_n,\alpha) \leq \frac{q^n}{1-q}\cdot\rho\bigl(x_0,f(x_0)\bigr) \qquad (n\in\mathbb{N}).$$

*Bizonyítás vázlata.* Tekintsük az $(Y,\sigma)$ alteret ($\sigma := \rho|_{Y^2}$) és az $F := f|_Y$ leszűkítést.

1. **$F : Y \to Y$.** A harmadik feltétel miatt minden $x \in Y$-ra
$$\rho\bigl(F(x),a\bigr) \leq \rho\bigl(f(x),f(a)\bigr)+\rho\bigl(f(a),a\bigr) \leq q\rho(x,a)+(1-q)r \leq qr+(1-q)r = r.$$
2. **$F$ kontrakció** $(Y,\sigma)$-n, ugyanazzal a $q$-val.
3. **$(Y,\sigma)$ teljes.** Egy $Y$-beli Cauchy-sorozat $X$-ben is Cauchy, tehát $X$ teljessége miatt van $\alpha := \lim(x_n) \in X$ határértéke. Ha $\alpha\notin Y$ lenne, azaz $\rho(a,\alpha)>r$, akkor volna olyan $n$, hogy $\rho(x_n,\alpha)<\rho(a,\alpha)-r$, és ekkor
$$\rho(x_n,a) \geq \rho(a,\alpha)-\rho(x_n,\alpha) > r,$$
ami ellentmond $x_n \in Y$-nak.

Erre a teljes térre és kontrakcióra alkalmazva a Banach-fixponttételt éppen az állítást kapjuk. $\blacksquare$

### Hibabecslések

A globális tétel $\rho(x_n,\alpha)\leq \frac{q^n}{1-q}\rho(x_0,x_1)$ **a priori** becsléséből az $y_n := x_{m-1+n}$ eltolt sorozatra $n:=1$-gyel adódik az **a posteriori** alak: minden $0<m\in\mathbb{N}$ esetén

$$\rho(x_m,\alpha) \leq \frac{q}{1-q}\cdot\rho(x_m,x_{m-1}).$$

Ez az, ami numerikus gyakorlatban használható: az utolsó két iterált távolságából ad korlátot a valódi hibára.

### A $q<1$ konstans nem gyengíthető

A kontrakciós feltétel **nem** helyettesíthető a látszólag rokon

$$\rho\bigl(f(x),f(y)\bigr) < \rho(x,y) \qquad (x,y\in X,\ x\neq y)$$

feltétellel. Legyen ugyanis $X:=\mathbb{R}$ a szokásos metrikával (teljes tér) és

$$f(x) := \ln\bigl(1+e^x\bigr).$$

Ekkor $f$ differenciálható és $f'(x)=\frac{e^x}{1+e^x}<1$, tehát a Lagrange-középértéktétel szerint $x<y$ esetén egy alkalmas $\xi\in(x,y)$-vel

$$|f(x)-f(y)| = |f'(\xi)|\cdot|x-y| < |x-y|.$$

Az $f$-nek mégsincs fixpontja: az $\alpha = \ln(1+e^\alpha)$ egyenlet ekvivalens $1+e^\alpha=e^\alpha$-val, azaz $1=0$-val. A hiányzó mozzanat a **közös** $q<1$ korlát: itt $\sup f' = 1$, és a szuprémum nem vétetik fel.

### Fixpont és kontrakció

Az $f(\alpha)=\alpha$ egyenlőséget kielégítő $\alpha$-t az $f$ **fixpontjának**, a $q<1$ konstanssal a fenti becslésnek eleget tevő $f$-et **kontrakciónak** nevezzük — ez a magyarázata annak, hogy a Banach–Tyihonov–Cacciopoli-tételt fixponttételként emlegetjük.

## Kapocs

- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — a globális tétel, amelynek ez a lokalizált változata
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a teljesség, amit a bizonyítás mindkét szinten használ
- [[concepts/analiii/linearis-lekepezes-kontrakcio-volta]] — a kontrakciós feltétel konkrét mátrixos alakjai
- [[concepts/analiii/metrikabol-uj-metrika]] — az altér-metrika, amelyen az $(Y,\sigma)$ tér nyugszik
- [[concepts/nummodi/banach-fixponttetel-rn]] — a tétel numerikus módszerekben betöltött szerepe
