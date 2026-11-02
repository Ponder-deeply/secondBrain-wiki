---
tags: [concept]
sources: [NM1_ea12.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-21
---

# Newton-módszer

Az $f(x) = 0$ egyenlet gyökét úgy közelíti, hogy $x_k$-ban $f$-et az érintőjével helyettesíti, és annak zérushelyét veszi: $x_{k+1} = x_k - f(x_k)/f'(x_k)$. Elég közelről indítva másodrendben konvergál (lokális konvergenciatétel); $f'$, $f''$ állandó előjele és $f(x_0)f''(x_0) > 0$ mellett monoton konvergál. Többváltozós alakja lépésenként egy Jacobi-mátrixos LER-t old meg.

## Tartalom

### Levezetés

**Geometriai úton** (érintő zérushelye). Az $(x_k, f(x_k))$ ponton átmenő érintő:

$$y - f(x_k) = f'(x_k)(x - x_k).$$

Zérushelye ($y = 0$, $x = x_{k+1}$): $-f(x_k) = f'(x_k)(x_{k+1} - x_k)$, azaz

$$x_{k+1} = x_k - \frac{f(x_k)}{f'(x_k)}.$$

**Analitikus úton.** $f$ gyökét az $x_k$ körüli elsőfokú Taylor-polinom gyökével közelítjük: $0 = f(x) \approx f(x_k) + f'(x_k)(x - x_k)$.

**Definíció.** Differenciálható $f : \mathbb{R} \to \mathbb{R}$ és $x_0 \in \mathbb{R}$ esetén a **Newton-módszer**:

$$x_{k+1} = x_k - \frac{f(x_k)}{f'(x_k)} \qquad (k = 0, 1, 2, \dots).$$

**Szemléltetés:** $x_k$-ból felmegyünk a görbére, behúzzuk az érintőt, és ahol az metszi az $x$ tengelyt, az $x_{k+1}$. **Példa:** $f(x) = x^2 - 2$-re $x_{k+1} = \tfrac12\bigl(x_k + \tfrac{2}{x_k}\bigr)$ — a babiloni módszer $\sqrt2$-re.

### Monoton konvergencia tétele

**Tétel.** Ha $f \in C^2[a;b]$ és

1. $\exists\, x^* \in [a;b]$: $f(x^*) = 0$,
2. $f'$ és $f''$ állandó előjelű $[a;b]$-n,
3. $x_0 \in [a;b]$: $f(x_0)\cdot f''(x_0) > 0$,

akkor az $x_0$-ból indított Newton-módszer monoton konvergál $x^*$-hoz.

(Négy eset van $f'$ és $f''$ előjele szerint; a bizonyítás egyre, a többi hasonló.)

**Biz.** ($f' > 0$, $f'' > 0$ eset; ekkor a 3. feltételből $f(x_0) > 0$.)

1. **$f(x_k) > 0$ minden $k$-ra.** Taylor-formula $x_k$ középponttal, másodfokú maradéktaggal, az $x_{k+1}$ helyen: $\exists\,\xi_k$ $x_k$ és $x_{k+1}$ között,
   $$f(x_{k+1}) = \underbrace{f(x_k) + f'(x_k)(x_{k+1} - x_k)}_{= 0 \text{ (a módszer definíciója)}} + \underbrace{\frac{f''(\xi_k)}{2}}_{> 0}\underbrace{(x_{k+1} - x_k)^2}_{> 0} > 0.$$
2. **Monoton fogyó és alulról korlátos.** $x_{k+1} = x_k - \underbrace{f(x_k)/f'(x_k)}_{> 0} < x_k$. Továbbá $f$ szigorúan nő és $f(x^*) = 0 < f(x_k)$, ezért $x^* < x_k$. Monoton korlátos sorozat konvergens: $\hat x := \lim x_k$.
3. **$\hat x = x^*$.** Elég $f(\hat x) = 0$ (mert $f$ szigorúan monoton, a gyök egyértelmű). $f$ folytonos, így
   $$f(\hat x) = \lim_{k\to\infty} f(x_{k+1}) = \lim_{k\to\infty}\underbrace{\frac{f''(\xi_k)}{2}}_{\text{korlátos}}\cdot\underbrace{(x_{k+1} - x_k)^2}_{\to 0 \text{ (Cauchy)}} = 0. \ \square$$

### Lokális konvergencia tétele

**Tétel.** Ha $f \in C^2[a;b]$ és

1. $\exists\, x^* \in [a;b]$: $f(x^*) = 0$,
2. $f'$ állandó előjelű,
3. $m_1 = \min_{x\in[a;b]}|f'(x)| > 0$,
4. $M_2 = \max_{x\in[a;b]}|f''(x)| < +\infty$, és $M := \dfrac{M_2}{2m_1}$,
5. $x_0 \in [a;b]$: $|x_0 - x^*| < r := \min\bigl\{\tfrac1M, |x^* - a|, |x^* - b|\bigr\}$,

akkor az $x_0$-ból indított Newton-módszer másodrendben konvergál a gyökhöz, és

$$|x_{k+1} - x^*| \le M\,|x_k - x^*|^2.$$

Röviden: ha elég közelről indulunk, gyorsan odatalálunk ($r$ biztosítja azt is, hogy $[a;b]$-ben maradjunk).

**Biz.**

1. Taylor-formula $x_k$ középponttal az $x^*$ helyen: $\exists\,\xi_k$ $x_k$ és $x^*$ között,
   $$0 = f(x^*) = f(x_k) + f'(x_k)(x^* - x_k) + \frac{f''(\xi_k)}{2}(x^* - x_k)^2.$$
2. $f'(x_k)$-val osztva és átrendezve a Newton-lépést ismerjük fel:
   $$\underbrace{x_k - \frac{f(x_k)}{f'(x_k)}}_{x_{k+1}} - x^* = \frac{f''(\xi_k)}{2f'(x_k)}(x^* - x_k)^2 \implies |x_{k+1} - x^*| \le \frac{M_2}{2m_1}|x_k - x^*|^2 = M|x_k - x^*|^2.$$
3. Jelöljük $\varepsilon_k := x_k - x^*$; így $|\varepsilon_{k+1}| \le M|\varepsilon_k|^2$ — ez a hibabecslés, *feltéve*, hogy a sorozat $[a;b]$-ben marad.
4. **A rend.** A 2. lépés egyenlőségéből, ha $x_k \to x^*$:
   $$\lim_{k\to\infty}\frac{|x_{k+1} - x^*|}{|x_k - x^*|^2} = \lim_{k\to\infty}\frac{|f''(\xi_k)|}{2|f'(x_k)|} = \frac{|f''(x^*)|}{2|f'(x^*)|},$$
   tehát ($f''(x^*) \ne 0$ esetén pontosan, egyébként legalább) másodrendű a konvergencia.
5. **A sorozat a $K_r(x^*)$ környezetben marad** (teljes indukció). $|\varepsilon_0| < r$ feltétel. Ha $|\varepsilon_k| < r \le \tfrac1M$, akkor
   $$|\varepsilon_{k+1}| \le M|\varepsilon_k|^2 = \underbrace{(M|\varepsilon_k|)}_{< 1}|\varepsilon_k| < |\varepsilon_k| < r.$$
6. **$|\varepsilon_k| \to 0$.** Legyen $d_k := M|\varepsilon_k|$. A becslést $M$-mel szorozva $d_{k+1} \le d_k^2$, így
   $$d_k \le d_{k-1}^2 \le d_{k-2}^{2\cdot2} \le \dots \le d_0^{2^k} \implies |\varepsilon_k| \le \frac1M(M|\varepsilon_0|)^{2^k}.$$
7. $|\varepsilon_0| < \tfrac1M$ miatt $M|\varepsilon_0| < 1$, ezért $|\varepsilon_k| \to 0$, azaz $x_k \to x^*$. $\square$

**Megj.** A monoton konvergencia feltételei mellett is másodrendű lesz a konvergencia, mert előbb-utóbb „elég közel” kerülünk a gyökhöz. A tétel a [[concepts/nummodi/konvergenciarend|magasabb rendű konvergencia tételéből]] is következne $\varphi(x) = x - f(x)/f'(x)$-szel, de ahhoz $f \in C^3[a;b]$ kellene.

### Megjegyzések

- Ha $f'(x_k) = 0$, $x_{k+1}$ nincs értelmezve.
- Többszörös gyöknél ($f'(x^*) = 0$) a konvergencia csak elsőrendű, vagy instabil ($\tfrac00$ típusú osztás). Javítás: a $g(x) := f(x)/f'(x)$ függvényre alkalmazzuk a módszert, vagy $r$-szeres gyökre $x_{k+1} := x_k - r\,\dfrac{f(x_k)}{f'(x_k)}$, ami újra másodrendű.
- Néha akár harmadrendű is lehet.
- Más nevei: Newton–Raphson-, Newton–Fourier-módszer.
- Nem biztos, hogy konvergál; ciklusba kerülhet; a gyökök vonzási tartományain kívül kaotikus viselkedés.

### Többváltozós Newton-módszer

**Feladat:** $F : \mathbb{R}^n \to \mathbb{R}^n$, $F(x) = 0$. Közelítsük $F$-et az elsőfokú Taylor-polinomjával:

$$F(x) \approx F(x^{(k)}) + F'(x^{(k)})(x - x^{(k)}), \qquad F'(x^{(k)}) = \Bigl(\frac{\partial f_i(x^{(k)})}{\partial x_j}\Bigr)_{i,j=1}^n \in \mathbb{R}^{n\times n}$$

(a [[concepts/analiii/jacobi-matrix|Jacobi-mátrix]]). Ennek zérushelye lesz $x^{(k+1)}$:

1. $F'(x^{(k)})\,s^{(k)} = -F(x^{(k)})$ LER megoldása, ahol $s^{(k)} := x^{(k+1)} - x^{(k)}$ a továbblépés iránya;
2. $x^{(k+1)} = x^{(k)} + s^{(k)}$.

**Definíció:** $x^{(k+1)} = x^{(k)} - \bigl[F'(x^{(k)})\bigr]^{-1}F(x^{(k)})$. (A gyakorlatban nem invertálunk, hanem az 1. lépés LER-jét oldjuk meg.)

Javítható, hogy ne kelljen minden lépésben deriváltat számolni és LER-t megoldani: **Broyden-módszer** (lassabb).

**Példa.** $f_1(x) = x_1^2 + x_2^2 - 1$, $f_2(x) = -x_1^2 - x_2$ (egységkör és fordított parabola metszéspontjai). $\det F'(x) = \begin{vmatrix}2x_1 & 2x_2\\ -2x_1 & -1\end{vmatrix} = 2x_1(2x_2 - 1)$, így $x_1 = 0$ vagy $x_2 = 0{,}5$ esetén a lépés nem értelmezett. $x^{(0)} = [\pm1, 1]^\top$-ból divergens (az első koordináta sorozata konvergens, de rossz határértékhez).

### Vizsgán

- **26. b):** alapötlet; a lokális konvergencia tételének bizonyítása (1–7. lépés).
- **27. a):** alapötlet, szemléltetés, a képlet levezetése; a többváltozós Newton-módszer levezetése. (Az intervallumfelezés: [[concepts/nummodi/intervallumfelezes]].)
- **27. b):** a monoton konvergencia tételének bizonyítása.

## Kapocs

- [[concepts/nummodi/hurmodszer-szelomodszer]] — derivált nélküli társai; a 26. tétel összevetése
- [[concepts/nummodi/konvergenciarend]] — másodrendű konvergencia, a magasabb rendű tétel
- [[concepts/nummodi/intervallumfelezes]] — a 27. tétel első fele; robusztus, de lassú kezdés
- [[concepts/nummodi/nemlinearis-egyenletek-fixpont]] — a Newton-módszer mint fixpont-iteráció
- [[concepts/analii/taylor-formula-maradektag]] — mindkét bizonyítás eszköze
- [[concepts/analiii/jacobi-matrix]] — a többváltozós változat deriváltja
