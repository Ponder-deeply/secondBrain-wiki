---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Maxwell-egyenletek differenciális és integrális alakja

A négy Maxwell-egyenlet mindegyike kétféleképpen írható fel, és a két alak között pontosan a Gauss–Osztrogradszkij, illetve a Kelvin–Stokes tétel teremt kapcsolatot. Ez az integráltételek legfontosabb fizikai alkalmazása.

## Tartalom

### A négy egyenlet

A jelölésben $\cdot$ a skaláris szorzás, tehát „$\nabla\cdot$" $= \operatorname{div}$ és „$\nabla\times$" $= \operatorname{rot}$.

| | Differenciális alak | Integrális alak |
|---|---|---|
| I. (Gauss-törvény) | $\nabla\cdot\mathbf{E} = \dfrac{\rho}{\varepsilon_0}$ | $\oint_A \mathbf{E}\cdot\mathrm{d}\mathbf{A} = \displaystyle\int_V \dfrac{\rho}{\varepsilon_0}\,\mathrm{d}V = \dfrac{Q}{\varepsilon_0}$ |
| II. (Faraday–Lenz) | $\nabla\times\mathbf{E} = -\dfrac{\partial \mathbf{B}}{\partial t}$ | $\oint_L \mathbf{E}\cdot\mathrm{d}\mathbf{l} = -\dfrac{\mathrm{d}}{\mathrm{d}t}\displaystyle\int_A \mathbf{B}\cdot\mathrm{d}\mathbf{A}$ |
| III. (Gauss mágneses t.) | $\nabla\cdot\mathbf{B} = 0$ | $\oint_A \mathbf{B}\cdot\mathrm{d}\mathbf{A} = 0$ |
| IV. (Ampère-törvény) | $\nabla\times\mathbf{B} = \mu_0\mathbf{J} + \dfrac{1}{c^2}\dfrac{\partial\mathbf{E}}{\partial t}$ | $\oint_L \mathbf{B}\cdot\mathrm{d}\mathbf{l} = \mu_0\displaystyle\int_A \mathbf{J}\cdot\mathrm{d}\mathbf{A} + \dfrac{1}{c^2}\dfrac{\mathrm{d}}{\mathrm{d}t}\int_A \mathbf{E}\cdot\mathrm{d}\mathbf{A}$ |

A jelölések: $\mathbf{E}$ az elektromos térerősség (vektormező), $\mathbf{B}$ a mágneses indukció (térerősség, szintén vektormező), $Q$ a tartomány töltése, $\rho$ a töltéssűrűség (skalármező), $\mathbf{J}$ az elektromos áramsűrűség-vektor, $\varepsilon_0$ a vákuum permittivitása (dielektromos állandója), $\mu_0$ a vákuum permeabilitása.

Figyeljük meg a szerkezetet: az I. és a III. egyenlet **divergenciáról** szól, tehát zárt felületen vett fluxusra fordul; a II. és a IV. **rotációról**, tehát zárt görbe menti cirkulációra.

### I. — Gauss-törvény és a divergenciatétel

Az I. egyenlet egy térbeli zárt krumpli elektromos forráserősségéről szól. A differenciális alak azt mondja, hogy az elektromos forrássűrűség arányos a töltéssűrűséggel. Az egyenletet a krumplin integrálva, majd a Gauss–Osztrogradszkij tételt alkalmazva kapjuk az integrális alakot:

$$\int_{\partial K}\langle E, \overrightarrow{\mathrm{d}A}\rangle \overset{\text{GOt}}{=} \int_K (\operatorname{div} E)\,\mathrm{d}V \overset{\text{M.I.}}{=} \int_K \frac{\rho}{\varepsilon_0}\,\mathrm{d}V = \frac{Q}{\varepsilon_0}.$$

Az integrális alak tehát azt mondja, hogy a krumpli forráserőssége — vagyis az elektromos mező fluxusa a krumpli héján — arányos a krumpli töltésével.

### III. — a mágneses mező forrásmentessége

A III. egyenlet annyival egyszerűbb, hogy — jelenlegi ismereteink szerint — a mágneses mező forrásmentes: nincs mágneses monopólus. A differenciális alak azt mondja, hogy $\mathbf{B}$ divergenciamentes; az integrális alak pedig azt, hogy a krumpli héján a mágneses fluxus $0$. Éppen ezért jogos a mágneses mezőt erővonalakkal szemléltetni.

### IV. — Ampère-törvény és a Kelvin–Stokes tétel

A II. és a IV. egyenlet megértéséhez már nem a divergenciatétel, hanem a [[concepts/analiii/kelvin-stokes-tetel]] kell, hiszen itt egy **peremes felületen és annak határán** integrálunk. A Maxwell-féle kiegészítés nélküli, időben állandó elektromos mezőre érvényes Ampère-törvény:

$$\nabla\times\mathbf{B} = \mu_0\mathbf{J} \qquad \Longleftrightarrow \qquad \oint_L \mathbf{B}\cdot\mathrm{d}\mathbf{l} = \mu_0\int_A \mathbf{J}\cdot\mathrm{d}\mathbf{A},$$

a levezetés

$$\int_{\partial S}\langle B, \mathrm{d}\mathbf{x}\rangle \overset{\text{KSt}}{=} \int_S \langle\operatorname{rot} B, \overrightarrow{\mathrm{d}A}\rangle \overset{\text{M.IV.}}{=} \mu_0\int_S\langle J, \overrightarrow{\mathrm{d}A}\rangle = \mu_0 I,$$

ahol $I$ a felületen keresztülfolyó áram. Az integrális alak tehát: a felület határán a mágneses örvényerősség arányos a felületen átfolyó árammal.

### A minta

Mindkét irányban ugyanaz a recept működik: a **differenciális alak** egy pontbeli sűrűségről szól (forrássűrűség, örvénysűrűség), az **integrális alak** ennek egy kiterjedt tartományra vett összegéről (forráserősség, örvényerősség), és a kettőt az integráltétel köti össze. Az integráltételek tehát nem csupán számolási eszközök: ezek fordítják egymásba a fizika lokális és globális törvényalakjait.

## Kapocs

- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — az I. és III. egyenlet két alakja közti kapcsolat
- [[concepts/analiii/kelvin-stokes-tetel]] — a II. és IV. egyenlet két alakja közti kapcsolat
- [[concepts/analiii/divergencia]] — a forrássűrűség fogalma és az erővonalas szemléltetés
- [[concepts/analiii/rotacio]] — az örvénysűrűség fogalma
- [[concepts/analiii/osszekapcsolodasi-szam]] — az Ampère-törvény topológiai következménye
