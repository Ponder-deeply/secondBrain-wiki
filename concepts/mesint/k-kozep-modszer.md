---
tags: [concept]
sources: [11.gepi_tanulas.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# k-közép módszer

A $k$-közép (k-means) módszer $\mathbb{R}^n$-beli pontokat $k$ klaszterbe sorol úgy, hogy az elemeknek a klaszterük középpontjától számított távolságnégyzet-összege minimális legyen. Iteratív: felváltva rendeli a pontokat a legközelebbi középponthoz, majd újraszámolja a középpontokat.

## Tartalom

### A feladat

Legyenek a klaszterezendő ($x_p$) elemek $\mathbb{R}^n$-beli pontok; soroljuk be őket $k$ klaszter valamelyikébe. Minden $S_i$ klasztert a középpontjával ($m_i$, centroid) reprezentálunk, ami a klaszterhez tartozó pontok átlaga:

$$m_i = \frac{1}{|S_i|}\sum_{x_j \in S_i} x_j .$$

Keressük azt a $k$ klasztert, amelyre minimális a távolságnégyzet-összeg; ez ekvivalens a klaszteren belüli pontok páronkénti távolságnégyzetének minimalizálásával:

$$\arg\min_S \sum_{i=1}^{k}\sum_{x\in S_i}\|x-m_i\|_2^2 = \arg\min_S \sum_{i=1}^{k}\frac{1}{2|S_i|}\sum_{x,y\in S_i}\|x-y\|_2^2 .$$

### Az algoritmus

1. Adott $k$ és az $x_p$ elemek. Inicializáljuk a $k$ centroidot: $m_1^{(1)},\dots,m_k^{(1)}$ — vagy véletlenszerűen választunk $k$ középpontot, vagy minden adatpontot véletlenszerűen egy-egy klaszterbe sorolunk, és kiszámoljuk azok középpontjait.
2. A középpontok $t$-edik változatát a $(t+1)$-edikre cseréljük:
   - **hozzárendelés**: $S_i^{(t+1)} = \{x_p \mid \forall j\in[1..k]: \|x_p-m_i^{(t)}\|_2^2 \le \|x_p-m_j^{(t)}\|_2^2\}$;
   - **frissítés**: $m_i^{(t+1)} = \frac{1}{|S_i^{(t+1)}|}\sum_{x_j\in S_i^{(t+1)}} x_j$.
3. Addig számolunk, amíg két lépés eredménye (a középpontok) közötti eltérés egy adott határ alá nem kerül.

A diák példája 2 dimenzióban mutatja az inicializálást és az első három menetet: a középpontok néhány iteráció alatt a sűrű csomósodások felé mozdulnak.

### Megjegyzések

- A $k$-közép **kemény klaszterező** eljárás (hard clustering): minden pont pontosan egy klaszterbe kerül.
- A klaszterek megtanulása után bármelyik $\mathbb{R}^n$-beli pont besorolható a legközelebbi klaszterbe; tulajdonképpen egy $\varphi: X \to Y$ leképezést tanulunk, $Y=[1..k]$, amely $X$ tetszőleges elemét osztályozza. Itt sem mindegy, mennyire reprezentálják a tanító példák az $X$ elemeit.
- Az optimális klaszterek megtalálása **NP-nehéz**; approximációt alkalmazunk, a módszer csak **lokális optimumot** biztosít.
- Problémát jelent, ha a megadott $k$ **túl nagy** (nagyon kevés elemet tartalmazó „üres" klaszterek) vagy **túl kicsi** (egy klaszteren belül szignifikánsan elkülönülő csomósodások).
- A módszert többször futtathatjuk különböző véletlen inicializációkkal.

## Kapocs

- [[concepts/mesint/felugyelet-nelkuli-tanulas]] — a klaszterezés mint felügyelet nélküli tanulás
- [[concepts/mesint/legkozelebbi-szomszed-modszer]] — távolságalapú, de felügyelt módszer
- [[concepts/mesint/felugyelt-tanulas]] — szembeállítás: a besorolás itt kimenet nélkül tanult
- [[concepts/bigdata/k-means]] — a nagy adat tárgy tárgyalása
