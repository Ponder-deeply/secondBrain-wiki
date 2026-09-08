---
tags: [concept]
sources: [DimatIIEa03.pdf, DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
---

# Művelettartó leképezés

Két, műveletekkel ellátott halmaz közötti függvény, amely a művelet elvégzését „átviszi": előbb műveletet végezni, majd leképezni ugyanaz, mint előbb leképezni, majd műveletet végezni.

## Tartalom

### Definíció

Legyen $X$ halmaz a $*$ művelettel, $Y$ halmaz a $\circ$ művelettel. Az $f : X \to Y$ függvény **művelettartó**, ha $\forall x, y \in X$ esetén

$$f(x * y) = f(x) \circ f(y).$$

### Példák

- Legyen $X = \mathbb{R}$ a $+$ művelettel, $Y = \mathbb{R}^+$ a $\cdot$ művelettel. Ekkor az $x \mapsto a^x$ leképezés művelettartó: $a^{x + y} = a^x \cdot a^y$.
- Legyen $X = Y = \mathbb{C}$ a $+$ művelettel. Ekkor a $z \mapsto \overline{z}$ konjugálás művelettartó: $\overline{z + w} = \overline{z} + \overline{w}$.
- Legyen $X = \mathbb{Z}$ a $+$ művelettel, $Y = \mathbb{Z}_m$ a $+_m$ (összeadás modulo $m$) művelettel. Ekkor az $n \mapsto n \bmod m$ leképezés művelettartó:

$$(k + n) \bmod m = (k \bmod m) +_m (n \bmod m).$$

- Legyen $X = \{\mathrm{I}, \mathrm{H}\}$ a XOR/$\wedge$ művelettel, $Y = \mathbb{Z}_2$ a $+$/$\cdot$ művelettel. Ekkor a $\mathrm{H} \mapsto 0$, $\mathrm{I} \mapsto 1$ hozzárendelés művelettartó (a XOR-nak az összeadás felel meg).

A művelettartó leképezés az algebrai struktúrák közötti *homomorfizmus* fogalmának alapesete: a struktúrák akkor tekinthetők „ugyanolyannak", ha van közöttük művelettartó bijekció.

## Kapocs

- [[concepts/dimatii/muvelet]] — a leképezés által megőrzött szerkezet
- [[concepts/dimatii/algebrai-struktura]] — a keret, amelyben a művelettartás értelmezhető
- [[concepts/bvszam/homomorfizmus]] — a formális nyelvek homomorfizmusa mint ugyanennek az elvnek egy másik példánya
