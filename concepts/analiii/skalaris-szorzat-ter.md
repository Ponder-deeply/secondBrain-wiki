---
tags: [concept]
sources: [SimonP-Anal2.pdf, 01_ea_An3_2025_osz.pdf]
references: ["Simon Péter: Analízis II., 1.2. vi) és 1.6. v) megjegyzés"]
derivation: source
updated: 2026-09-14
---

# Skaláris szorzat tér, euklideszi tér, Hilbert-tér

A skaláris szorzat az a többlet-struktúra, amely a normánál is erősebb: szöget és merőlegességet is értelmez, és a $\|x\| = \sqrt{\langle x,x\rangle}$ képlettel normát generál. A $\mathbb{K}^n$-beli $\|\cdot\|_p$ normák közül **pontosan** a $p=2$ származik skaláris szorzatból.

## Tartalom

### Definíció

Legyen $X$ lineáris tér $\mathbb{K}$ ($=\mathbb{R}$ vagy $\mathbb{C}$) felett. Az $s : X^2 \to \mathbb{K}$ függvény **skaláris szorzat**, ha $\langle x,y\rangle := s(x,y)$ jelöléssel minden $x,y,z \in X$, $\lambda \in \mathbb{K}$ esetén

1. $\langle x,y\rangle = \overline{\langle y,x\rangle}$ (hermitikus szimmetria);
2. $\langle x,x\rangle > 0$, ha $x \neq 0$ (pozitív definitség);
3. $\langle \lambda x, y\rangle = \lambda\langle x,y\rangle$ (első változóban homogén);
4. $\langle x+y, z\rangle = \langle x,z\rangle + \langle y,z\rangle$ (első változóban additív).

Az $(X, \langle\cdot,\cdot\rangle)$ párt **skaláris szorzat térnek** vagy **euklideszi térnek** nevezzük.

Az axiómákból közvetlenül adódik $\langle 0,x\rangle = \langle x,0\rangle = 0$, valamint

$$\langle x, \lambda y\rangle = \overline{\langle \lambda y, x\rangle} = \overline{\lambda}\cdot\langle x,y\rangle .$$

Valós euklideszi térben ($\mathbb{K} = \mathbb{R}$) a konjugálás elmarad: $\langle x,y\rangle = \langle y,x\rangle$ és $\langle x,\lambda y\rangle = \lambda\langle x,y\rangle$.

### Példák

| Tér | Skaláris szorzat |
|---|---|
| $\mathbb{K}^n$ | $\langle x,y\rangle = \sum_{i=1}^n x_i \overline{y_i}$ |
| $\ell^2$ (négyzetesen összegezhető sorozatok) | $\langle x,y\rangle = \sum_{n=0}^\infty x_n \overline{y_n}$ |
| $C[a,b]$ | $\langle f,g\rangle = \int_a^b fg$ |

Mindhárom esetben $\|x\|_2 = \sqrt{\langle x,x\rangle}$, tehát az $L^2$-norma a skaláris szorzat által indukált norma. Az $n=1$ esetben $\langle x,y\rangle = x\overline{y}$ és $\|x\| = |x|$.

### Az indukált norma és a Cauchy–Bunyakovszkij-egyenlőtlenség

**Tétel.** Tetszőleges $(X,\langle\cdot,\cdot\rangle)$ euklideszi térben $\|x\| := \sqrt{\langle x,x\rangle}$ norma.

A háromszög-egyenlőtlenség bizonyításának kulcsa az önmagában is alapvető

$$|\langle x,y\rangle| \leq \|x\|\cdot\|y\| \qquad (x,y \in X)$$

**Cauchy–Bunyakovszkij-egyenlőtlenség.** A fenti három példára lefordítva ez rendre

$$\Bigl|\sum_{i=1}^n x_i y_i\Bigr| \leq \sqrt{\sum |x_i|^2}\cdot\sqrt{\sum|y_i|^2}, \qquad
\Bigl|\sum_{i=1}^\infty x_i y_i\Bigr| \leq \sqrt{\sum |x_i|^2}\cdot\sqrt{\sum|y_i|^2},$$

$$\Bigl|\int_a^b fg\Bigr| \leq \sqrt{\int_a^b f^2}\cdot\sqrt{\int_a^b g^2}.$$

Koordinátás alakja a [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] $q=r=2$ speciális esete.

### Paralelogramma-szabály: mely norma származik skaláris szorzatból?

**Állítás.** Ha $\|x\| = \sqrt{\langle x,x\rangle}$, akkor minden $x,y \in X$-re

$$\|x+y\|^2 + \|x-y\|^2 = 2\bigl(\|x\|^2 + \|y\|^2\bigr).$$

*Bizonyítás.* A skaláris szorzat kifejtésével

$$\langle x+y,x+y\rangle + \langle x-y,x-y\rangle = 2\langle x,x\rangle + 2\langle y,y\rangle + \bigl(\langle x,y\rangle + \langle y,x\rangle - \langle x,y\rangle - \langle y,x\rangle\bigr),$$

ahol a zárójeles tag eltűnik. $\blacksquare$

**Következmény.** A $(\mathbb{K}^n, \|\cdot\|_p)$ normált terek közül **pontosan** a $p=2$ esetben származik a norma skaláris szorzatból.

*Bizonyítás.* A $p=2$ irány a fenti példa. Fordítva, $n=2$-re legyen $x=(1,0)$, $y=(0,1)$. Ekkor $1 \leq p < \infty$ mellett

$$\|x+y\|_p^2 + \|x-y\|_p^2 = \|(1,1)\|_p^2 + \|(1,-1)\|_p^2 = 2^{1+2/p}, \qquad 2\bigl(\|x\|_p^2+\|y\|_p^2\bigr) = 4,$$

így a paralelogramma-szabály a $2^{1+2/p} = 4$ egyenletre redukálódik, amiből $p=2$. A $p=\infty$ esetben a bal oldal $2$, a jobb oldal $4$, tehát a szabály nem teljesül: $\|\cdot\|_\infty$ nem skaláris szorzatból származik. $\blacksquare$

### Neumann–Jordan-tétel

A fenti gondolatmenet csak a szükségességet mutatja: ha a norma skaláris szorzatból származik, akkor teljesül a paralelogramma-azonosság. A megfordítás — hogy ez a feltétel **elégséges** is — jóval mélyebb tétel.

**Tétel (Neumann János – Ernst Pascual Jordan, 1935).** Egy $(X, \|\cdot\|)$ normált térben a norma akkor és csak akkor származik egy $\langle\cdot,\cdot\rangle$ skaláris szorzatból a $\|x\| = \sqrt{\langle x,x\rangle}$ összefüggés szerint, ha a norma a tér bármely két $x,y$ elemére teljesíti a paralelogramma-azonosságot.

A szükségesség a fenti számolás; az elégségesség bizonyítása lényegesen hosszabb (a skaláris szorzatot magából a normából kell polarizációval visszaállítani). A tételből azonnal adódik, hogy a $(\mathbb{R}^n, \|\cdot\|_p)$ és a $(C[a,b], \|\cdot\|_p)$ terek normája pontosan $p=2$ esetén származtatható skaláris szorzatból.

### Hilbert-tér

Az $(X,\langle\cdot,\cdot\rangle)$ euklideszi tér **teljes**, más szóval **Hilbert-tér**, ha a $\|x\| = \sqrt{\langle x,x\rangle}$ normával $(X,\|\cdot\|)$ Banach-tér. Így $(\mathbb{K}^n, \langle\cdot,\cdot\rangle)$ ($1 \leq n \in \mathbb{N}$) és $(\ell^2, \langle\cdot,\cdot\rangle)$ Hilbert-tér; $(C[a,b], \langle\cdot,\cdot\rangle)$ viszont **nem** az, hiszen az általa indukált norma az $L^2$-norma, amelyre nézve $C[a,b]$ nem teljes.

### A skaláris szorzat sorozatfolytonossága

**Állítás.** Ha $(x_n)$, $(y_n)$ konvergens sorozatok az $(X,\langle\cdot,\cdot\rangle)$ euklideszi térben, $\alpha = \lim(x_n)$, $\beta = \lim(y_n)$, akkor

$$\langle x_n,\beta\rangle \to \langle\alpha,\beta\rangle \qquad\text{és}\qquad \langle x_n,y_n\rangle \to \langle\alpha,\beta\rangle .$$

*Bizonyítás.* Az elsőhöz a Cauchy–Bunyakovszkij-egyenlőtlenség:

$$\bigl|\langle x_n,\beta\rangle - \langle\alpha,\beta\rangle\bigr| = \bigl|\langle x_n-\alpha,\beta\rangle\bigr| \leq \|x_n-\alpha\|\cdot\|\beta\| \to 0 .$$

A másodikhoz a $C := \sup\{\|x_n\| : n \in \mathbb{N}\} < \infty$ korláttal

$$\bigl|\langle x_n,y_n\rangle - \langle\alpha,\beta\rangle\bigr| \leq \bigl|\langle x_n, y_n-\beta\rangle\bigr| + \bigl|\langle x_n-\alpha,\beta\rangle\bigr| \leq C\|y_n-\beta\| + \|x_n-\alpha\|\|\beta\| \to 0 . \qquad \blacksquare$$

## Kapocs

- [[concepts/analiii/normalt-vektorter]] — a norma, amit a skaláris szorzat generál
- [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] — a Cauchy–Bunyakovszkij-egyenlőtlenség koordinátás alakja
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a teljesség, ami a Hilbert-tér definíciójában szerepel
- [[concepts/analiii/metrikus-terek-szorzata]] — euklideszi terek szorzata is euklideszi tér
- [[concepts/analiii/konvergencia-metrikus-terben]] — a sorozatfolytonossághoz használt limeszfogalom
