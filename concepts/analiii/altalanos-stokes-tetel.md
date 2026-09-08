---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Általános Stokes-tétel

A négy térbeli integráltétel közös alakja: $\int_K (\nabla * \mathbf{f})\,\mathrm{d}V = \int_{\partial K}\overrightarrow{\mathrm{d}A} * \mathbf{f}$, ahol $*$ tetszőleges bilineáris szorzás. A konkrét tételeket a szorzás megválasztása különbözteti meg.

## Tartalom

### Az összehasonlítás

Érdemes egymás mellé tenni az eddigi térbeli integráltételeket:

| Tétel | Alak |
|---|---|
| Green-tétel (3D lemma) | $\int_K D_i f\,\mathrm{d}V = \int_{\partial K} f\cdot\overrightarrow{\mathrm{d}A}_i$ |
| Newton–Leibniz formula | $\int_K (\operatorname{grad} f)\,\mathrm{d}V = \int_{\partial K} f\cdot\overrightarrow{\mathrm{d}A}$ |
| Gauss–Osztrogradszkij tétel | $\int_K (\operatorname{div}\mathbf{f})\,\mathrm{d}V = \int_{\partial K}\langle\mathbf{f}, \overrightarrow{\mathrm{d}A}\rangle$ |
| Stokes-tétel | $\int_K (\operatorname{rot}\mathbf{f})\,\mathrm{d}V = -\int_{\partial K}\mathbf{f}\times\overrightarrow{\mathrm{d}A}$ |

Mind a négyben bal oldalon a $\nabla$ operátor „szorzódik" $\mathbf{f}$-fel, jobb oldalon ugyanaz a szorzás áll $\overrightarrow{\mathrm{d}A}$-val. Csak a szorzás más.

### A tétel

**Tétel (általánosabb Stokes-tétel).** Legyenek $q, r$ pozitív egészek, és legyen $* : \mathbb{R}^3\times\mathbb{R}^q\to\mathbb{R}^r$ valamilyen szorzás (bilineáris leképezés). Legyen $G\subset\mathbb{R}^3$ nyílt, $K\subset G$ korlátos, zárt krumpli, amelynek $\partial K$ határa darabonként folytonosan differenciálható felület, ezeken az irányított normálvektor mindig kifelé mutat, és legyen $\mathbf{f} : G\to\mathbb{R}^q$ folytonosan differenciálható. Ekkor

$$\int_K (\nabla * \mathbf{f})\,\mathrm{d}V = \int_{\partial K}\overrightarrow{\mathrm{d}A} * \mathbf{f}.$$

A tétel a fenti példák alapján könnyen bizonyítható: minden bilineáris leképezés koordinátánként a $D_i f_j$ alakú tagok lineáris kombinációja, és minden ilyen tagra a Green-tétel háromdimenziós lemmája alkalmazható.

### Melyik tétel melyik szorzás

| Tétel | $q$ | $r$ | a $*$ szorzás |
|---|---|---|---|
| Newton–Leibniz formula | $1$ | $3$ | vektor szorzása skalárral |
| Gauss–Osztrogradszkij tétel | $3$ | $1$ | vektorok skaláris szorzata |
| Stokes-tétel | $3$ | $3$ | vektoriális szorzás |

A tényezőket a konkrét tételekben persze fordított sorrendben szeretjük írni; a Stokes-tételben ezért — a vektoriális szorzás antiszimmetriája miatt — jelenik meg a negatív előjel.

### Magasabb dimenzióban

A tétel magasabb dimenziós általánosításához a $\overrightarrow{\mathrm{d}A}$ felületelemet kell értelmezni, ehhez pedig a vektoriális szorzást kell kiterjeszteni $(p-1)$ darab $p$-dimenziós vektorra. Ez a differenciálformák nyelvén válik igazán természetessé, ahol mind a négy tétel — és az egyváltozós Newton–Leibniz formula is — egyetlen $\int_K \mathrm{d}\omega = \int_{\partial K}\omega$ állítás.

## Kapocs

- [[concepts/analiii/green-tetel-harom-dimenzioban]] — az az alapeset, amelyből a tétel bizonyítható
- [[concepts/analiii/newton-leibniz-formula-tobbvaltozos]] — a skalár-vektor szorzásos eset
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a skaláris szorzásos eset
- [[concepts/analiii/stokes-tetel]] — a vektoriális szorzásos eset
- [[concepts/analiii/feluleti-integral]] — a jobb oldalon álló általános felületi integrál
- [[concepts/analiii/altalanos-vonalintegral]] — ugyanez a „tetszőleges bilineáris szorzás" ötlet görbékre
- [[concepts/analii/newton-leibniz-tetel]] — az egydimenziós ős
