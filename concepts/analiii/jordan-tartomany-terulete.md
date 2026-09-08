---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Jordan-tartomány területe vonalintegrállal

A Green-tétel következménye: egy síkbeli tartomány területe kiszámítható pusztán a határgörbéjén vett vonalintegrállal, kettős integrál nélkül.

## Tartalom

### A képlet

**Következmény.** Ha $K$ Jordan-tartomány, amelynek határa szakaszonként $C^1$, akkor

$$t(K) = \int_{\partial K} x\,\mathrm{d}y = -\int_{\partial K} y\,\mathrm{d}x = \frac{1}{2}\int_{\partial K} \mathbf{x} \times \mathrm{d}\mathbf{x} .$$

A harmadik alak az első kettő számtani közepe, keresztszorzattal írva.

### Bizonyítás

A Green-tétel az $f(x,y) = x$, illetve $f(x,y) = -y$ függvényre:

$$\int_{\partial K} x\,\mathrm{d}y = \int_K \frac{\partial x}{\partial x}\,\mathrm{d}x\,\mathrm{d}y = \int_K 1\,\mathrm{d}x\,\mathrm{d}y = t(K),$$

$$-\int_{\partial K} y\,\mathrm{d}x = \int_K \frac{\partial y}{\partial y}\,\mathrm{d}x\,\mathrm{d}y = \int_K 1\,\mathrm{d}x\,\mathrm{d}y = t(K).$$

A trükk mindkét esetben ugyanaz: olyan $f$-et választunk, amelynek a Green-tételben szereplő parciális deriváltja azonosan $1$, tehát a területi integrál a terület lesz.

### Példa: a kör területe

Legyen $K = B(0,r)$, határgörbéje $\gamma(t) = (r\cos t, r\sin t)$, $0 \le t \le 2\pi$, tehát $\mathrm{d}\mathbf{x} = \dot\gamma(t)\,\mathrm{d}t = (-r\sin t, r\cos t)\,\mathrm{d}t$. Ekkor

$$t(B(0,r)) = \frac{1}{2}\int_{\partial K}\mathbf{x}\times\mathrm{d}\mathbf{x} = \frac{1}{2}\int_{t=0}^{2\pi}(r\cos t, r\sin t)\times(-r\sin t, r\cos t)\,\mathrm{d}t = \frac{1}{2}\int_0^{2\pi} r^2\,\mathrm{d}t = r^2\pi,$$

hiszen a keresztszorzat $r^2\cos^2 t + r^2\sin^2 t = r^2$.

### Miért hasznos

A képlet a terület mérését a határ bejárására redukálja: ez az elve a planiméternek, és ez teszi lehetővé, hogy sokszög területét pusztán a csúcsainak koordinátáiból számoljuk (a „cipőfűző-képlet" éppen a $\tfrac12\int \mathbf{x}\times\mathrm{d}\mathbf{x}$ diszkrét változata). A több görbével határolt „krumplira" is érvényes, ha a határgörbéket a Green-tételnél leírt módon irányítjuk — a lyukak határai így negatív járulékot adnak.

## Kapocs

- [[concepts/analiii/green-tetel]] — a tétel, amelynek ez közvetlen következménye
- [[concepts/analiii/sikvektorok-keresztszorzata]] — a $\tfrac12\int \mathbf{x}\times\mathrm{d}\mathbf{x}$ alak szorzása
- [[concepts/analiii/jordan-gorbetetel]] — a tartomány- és irányításfogalom
- [[concepts/analii/sikido-terulete]] — az egyváltozós, függvénygrafikon alatti területszámítás
