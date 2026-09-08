---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Felszín szerinti és felületi integrál (fluxus)

Skalár- vagy vektormező integrálása paraméteres felületen. A felszínelemmel súlyozva felszín szerinti integrált, az irányított felületelemmel szorozva felületi integrált — skaláris szorzás esetén fluxust — kapunk.

## Tartalom

Legyen $P\in\mathcal{J}(\mathbb{R}^2)$ kompakt és $S : P\to\mathbb{R}^3$ darabonként folytonosan differenciálható felület.

### Felszín szerinti integrál

Ha $f$ valamilyen skalár- vagy vektormező, akkor $f$ *felszín szerinti integrálja* az $S$ felületen

$$\int_{(u,v)\in P} f(S(u,v))\,|D_1S\times D_2S|\,\mathrm{d}u\,\mathrm{d}v, \qquad \text{jele: } \int_S f\,|\mathrm{d}A| .$$

Ez a görbén vett ívhossz szerinti integrál megfelelője: az **irányítatlan** változat, amely nem függ a felület átparaméterezésének irányításától. $f\equiv 1$ esetén a felszínt kapjuk vissza.

### Általános felületi integrál

Ha $*$ valamilyen szorzás (bilineáris függvény), akkor

$$\int_{(u,v)\in P} f(S(u,v)) * (D_1S\times D_2S)\,\mathrm{d}u\,\mathrm{d}v, \qquad \text{jele: } \int_S f * \overrightarrow{\mathrm{d}A}.$$

Ez ugyanaz a gondolat, mint az általános vonalintegrálnál: a sebességvektor helyére a területvektor lép, és a szorzás szabadon választható. Az integráltételek jobb oldalán mindig egy ilyen alakú integrál áll — a Newton–Leibniz formulában skalár-vektor szorzással, a Gauss–Osztrogradszkij tételben skaláris szorzással, a Stokes-tételben vektoriális szorzással.

### Fluxus

Speciálisan, ha $*$ a skaláris szorzás, akkor $f$ *felületi integrálja* vagy *fluxusa* az $S$ felületen

$$\int_{(u,v)\in P}\bigl\langle f(S(u,v)),\, D_1S\times D_2S\bigr\rangle\,\mathrm{d}u\,\mathrm{d}v, \qquad \text{jele: } \int_S\langle f, \overrightarrow{\mathrm{d}A}\rangle .$$

Szemléletesen: a felületen egységnyi idő alatt átáramló mennyiség, illetve az erővonalas képben a felületet átdöfő erővonalak (előjeles) száma. A fluxus **irányításfüggő**: a felület normálisának megfordítása előjelet vált.

## Kapocs

- [[concepts/analiii/parameteres-felulet]] — a $\overrightarrow{\mathrm{d}A}$ és $|\mathrm{d}A|$ elemek definíciója
- [[concepts/analiii/altalanos-vonalintegral]] — az azonos szerkezetű, egy dimenzióval alacsonyabb fogalom
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a fluxust a divergenciával összekötő tétel
- [[concepts/analiii/divergencia]] — a fluxus és a forráserősség kapcsolata
- [[concepts/analiii/kelvin-stokes-tetel]] — a rotáció fluxusa peremes felületen
