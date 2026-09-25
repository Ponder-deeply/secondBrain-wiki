---
tags: [concept, bigdata/deep-learning-bevezetes]
sources: [BDAEM-2022-EA12.pdf]
references: ["https://en.wikipedia.org/wiki/Activation_function"]
derivation: source
updated: 2026-09-12
---

# Aktivációs függvények

Az aktivációs függvény adja a mesterséges neuron nemlineáris kimenetét a
súlyozott bemeneti összegből; a választott függvény alakja meghatározza a
hálózat kifejezőerejét és taníthatóságát.

## Tartalom

### Szerepük a neuronmodellben

Az aktivációs függvény a neuron $\mathbf{w}^\top \mathbf{x}$ nettó bemenetét
alakítja a neuron kimenetévé: $y = f(\mathbf{w}^\top \mathbf{x})$ — lásd
[[concepts/bigdata/mesterseges-neuron]]. A nemlinearitás nélkülözhetetlen:
tisztán lineáris aktivációval egymásra épített rétegek egyetlen lineáris
leképezéssé vonhatók össze, így a hálózat nem tudna nemlineáris döntési
határokat tanulni — lásd [[concepts/bigdata/perceptron]] a lineáris
szeparálhatóság korlátairól.

### A forrásban felsorolt függvények

A dia a Wikipédia aktivációs függvény táblázatát idézi:

| Név | Definíció |
|---|---|
| Identity | $f(x) = x$ |
| Binary step | $f(x) = 0$ ha $x < 0$, $1$ ha $x \geq 0$ |
| Logistic (soft step) | $f(x) = \dfrac{1}{1 + e^{-x}}$ |
| TanH | $f(x) = \tanh(x) = \dfrac{2}{1 + e^{-2x}} - 1$ |
| ArcTan | $f(x) = \tan^{-1}(x)$ |
| Softsign | $f(x) = \dfrac{x}{1 + \lvert x \rvert}$ |
| Rectified linear unit (ReLU) | $f(x) = 0$ ha $x < 0$, $x$ ha $x \geq 0$ |

### Hagyományos vs. jelenleg elterjedt választás

A forrás két csoportot emel ki:

- **Hagyományosan használt (traditionally used)**: a **logistic** (szigmoid)
  és a **TanH** függvény — ezek sima, korlátos, mindenütt deriválható
  görbék, amelyek a hibavisszaterjesztéshez ($f'(x)$ szükséges) jól
  illeszkednek — lásd [[concepts/bigdata/hibavisszaterjesztes]].
- **Jelenleg legelterjedtebb (currently most widely used)**: a **ReLU**.
  Empirikusan könnyebben tanítható, és ritka (sparse) aktivációjú
  hálózatokat eredményez — a forrás Nair & Hinton (2010) és Glorot, Bordes &
  Bengio (2011) munkáira hivatkozik e két tulajdonság alátámasztásaként.

## Kapocs

- [[concepts/bigdata/mesterseges-neuron]] — a neuronmodell, amelynek
  kimenetét az aktivációs függvény adja
- [[concepts/bigdata/perceptron]] — bináris lépcsőfüggvényt (binary step)
  használó, lineáris osztályozó speciális eset
- [[concepts/bigdata/hibavisszaterjesztes]] — a hibavisszaterjesztéshez az
  aktivációs függvény deriváltjára van szükség
