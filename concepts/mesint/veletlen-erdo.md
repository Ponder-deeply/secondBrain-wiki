---
tags: [concept]
sources: [11.gepi_tanulas.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Véletlen erdő

A véletlen erdő $K$ darab döntési fa, amelyek mindegyikét a tanító minták és az attribútumok egy-egy véletlen részhalmazából építjük; a kimenetet a fák értékeinek átlaga vagy leggyakoribb értéke adja.

## Tartalom

### Felépítés

$K$ döntési fát építünk a tanító minták alapján úgy, hogy egy-egy fa építéséhez a tanító mintáknak is ($P_k \subseteq P$) és az attribútumoknak is ($A_k \subseteq A$) csak egy-egy véletlenül kiválasztott részhalmazát használjuk fel. Az egyes fák építése a [[concepts/mesint/dontesi-fa-tanulo-algoritmus]] szerint történik.

### Kiértékelés

Egy $x \in X$ bemenetről a véletlen erdő minden fájában külön-külön megállapítjuk, melyik levélre képződik le. Az ezekhez a levelekhez tartozó tanító mintahalmazok kimenetei alapján becsüljük $x$ kimenetét. Ez lehet az egyes fák

- adott leveleinek értékeiből képzett **átlag**, vagy
- adott leveleinek értékei közül a **leggyakoribb**.

$$f(\Theta, x) = \frac{1}{K}\sum_{k=1}^{K} \text{value}\big(x, \text{decision\_tree}(A_k, P_k)\big)$$

$$f(\Theta, x) = \arg\max_{k=1..K} \sum_{i=1}^{K} \mathbb{I}\big(\text{value}(x, dt(A_k,P_k)) = \text{value}(x, dt(A_i,P_i))\big)$$

A diák szerint a kimenet a minták kimeneteinek súlyozott átlaga is felfogható, ahol a súly attól függ, hogy egy minta hány fa $x$-hez tartozó levelében szerepel, és az a levélhalmaz hány elemű. $\Theta$ maga az erdő; „optimalizálása" az erdő felépítése.

### Előnyök, hátrányok

- **Előny**: a tanító minták helyett csak az erdőt kell tárolni; a véletlen generálás miatt kevésbé mohó, elkerüli a túltanulást; az $x$-re adott eredmény számolása párhuzamosítható.
- **Hátrány**: az eredmény kevésbé értelmezhető, mint egy fáé; az erdő építése NP-teljes.

## Kapocs

- [[concepts/mesint/dontesi-fa-tanulo-algoritmus]] — az erdő egyes fái ezzel épülnek
- [[concepts/mesint/dontesi-fa-epitese]] — egyetlen döntési fa
- [[concepts/mesint/felugyelt-tanulas]] — a keret, amelyben az erdő tanul
- [[concepts/bigdata/random-forest]] — a nagy adat tárgy tárgyalása
