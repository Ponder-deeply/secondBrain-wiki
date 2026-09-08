---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.6. xii)–xiv) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Mikor kontrakció egy affin leképezés $\mathbb{K}^n$-en?

Az $f(\xi) = A\xi+\eta$ affin leképezés kontrakció volta a választott metrikától függ, és mindhárom szokásos metrikában elemi mátrixfeltétellel jellemezhető. Innen adódik a fixponttétel révén a lineáris egyenletrendszerek közelítő megoldási módszere.

## Tartalom

### A feladat

Tekintsük a $(\mathbb{K}^2,\rho_\infty)$ teljes metrikus teret, egy $\eta := (a,b) \in \mathbb{K}^2$ vektort és egy

$$A := \begin{bmatrix}\alpha & \beta\\ \gamma & \delta\end{bmatrix} \in \mathbb{K}^{2\times 2}$$

mátrixot, valamint az $f(\xi) := A\xi+\eta$ ($\xi\in\mathbb{K}^2$) leképezést.

### A maximum-metrikában

**Állítás.** A $\rho_\infty$ metrika szerint

1. $f$ akkor és csak akkor kontrakció, ha $|\alpha|+|\beta|<1$ és $|\gamma|+|\delta|<1$;
2. a $q := \max\{|\alpha|+|\beta|,\ |\gamma|+|\delta|\}$ számmal minden $\xi,\omega$-ra $\rho_\infty\bigl(f(\xi),f(\omega)\bigr) \leq q\cdot\rho_\infty(\xi,\omega)$;
3. ez a $q$ a **lehető legkisebb** kontrakciós együttható: minden $\varepsilon>0$-hoz vannak olyan $\xi,\omega$ vektorok, amelyekre $\rho_\infty\bigl(f(\xi),f(\omega)\bigr) > (q-\varepsilon)\cdot\rho_\infty(\xi,\omega)$.

*A 2. bizonyítása.* $\xi=(x,y)$, $\omega=(u,v)$ esetén

$$\rho_\infty\bigl(f(\xi),f(\omega)\bigr) = \max\bigl\{|\alpha(x-u)+\beta(y-v)|,\ |\gamma(x-u)+\delta(y-v)|\bigr\}$$
$$\leq \max\bigl\{|\alpha|\,|x-u|+|\beta|\,|y-v|,\ |\gamma|\,|x-u|+|\delta|\,|y-v|\bigr\} \leq q\cdot\rho_\infty(\xi,\omega). \qquad\blacksquare$$

*Az élesség.* A $|\gamma|+|\delta| \leq |\alpha|+|\beta|$ esetben a $\xi := (\operatorname{sign}\alpha, \operatorname{sign}\beta)$, $\omega := (0,0)$ választással $\rho_\infty(\xi,\omega)=1$ és $\rho_\infty\bigl(f(\xi),f(\omega)\bigr) = |\alpha|+|\beta| = q$. Ez egyben az 1. állítás megfordítását is adja.

### A másik két metrikában

| Metrika | Kontrakciós együttható | Hibabecslés |
|---|---|---|
| $\rho_\infty$ | $q=\max\{|\alpha|+|\beta|,\ |\gamma|+|\delta|\}$ — *sorösszegek* | $\max\{|x_n-c|,|y_n-d|\} \leq \frac{q^n}{1-q}\max\{|x_0-x_1|,|y_0-y_1|\}$ |
| $\rho_1$ | $q=\max\{|\alpha|+|\gamma|,\ |\beta|+|\delta|\}$ — *oszlopösszegek* | $|x_n-c|+|y_n-d| \leq \frac{q^n}{1-q}\bigl(|x_0-x_1|+|y_0-y_1|\bigr)$ |
| $\rho_2$ | $q=\sqrt{|\alpha|^2+|\beta|^2+|\gamma|^2+|\delta|^2}$ | $\sqrt{|x_n-c|^2+|y_n-d|^2} \leq \frac{q^n}{1-q}\sqrt{|x_0-x_1|^2+|y_0-y_1|^2}$ |

A $\rho_1$ és $\rho_\infty$ esetben a feltétel szükséges **és** elégséges; a $\rho_2$ (euklideszi) esetben a $q<1$ feltétel **csak elégséges** — könnyen adható példa olyan kontrakcióra, amelyre ez a $q$ nem kisebb $1$-nél.

### Következmény: iteratív egyenletrendszer-megoldás

Ha $q<1$, akkor a fixponttétel szerint tetszőleges $(x_0,y_0)\in\mathbb{K}^2$ kezdőértékből az

$$x_{n+1} := \alpha x_n + \beta y_n + a, \qquad y_{n+1} := \gamma x_n + \delta y_n + b$$

rekurzióval definiált vektorsorozat konvergens, és a $(c,d) := \lim(x_n,y_n)$ határértékre $f(c,d)=(c,d)$, azaz

$$c = \alpha c + \beta d + a, \qquad d = \gamma c + \delta d + b.$$

Az állítás értelemszerűen megfogalmazható $(\mathbb{K}^n,\rho_\infty)$-ben tetszőleges $2 \leq n$-re. Ezzel a fixponttétel révén **közelítő megoldási módszerhez jutunk lineáris egyenletrendszerekre**.

## Kapocs

- [[concepts/analiii/fixponttetel-gombon]] — a fixponttétel változatai és a hibabecslések származtatása
- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — a tétel, amelynek ez az alkalmazása
- [[concepts/analiii/ekvivalens-metrikak]] — a $\rho_1,\rho_2,\rho_\infty$ ekvivalens, de a kontrakciós feltétel nem ugyanaz bennük
- [[concepts/nummodi/iteracios-modszerek-ler]] — a Jacobi- és Gauss–Seidel-iteráció, amely ugyanezt a sémát követi
