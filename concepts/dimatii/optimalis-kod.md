---
tags: [concept]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# Optimális kód

Adott ábécéhez és betűeloszláshoz tartozó felbontható betűnkénti kód, amelynek átlagos szóhossza minimális.

## Tartalom

### Átlagos szóhossz

Legyen $A = \{a_1, a_2, \dots, a_n\}$ a kódolandó ábécé, $p_1, p_2, \dots, p_n$ a betűk eloszlása, $\varphi : A \to B^+$ injektív leképezés, továbbá $\ell_j = |\varphi(a_j)|$. Ekkor
$$\bar{\ell} = \sum_{j=1}^n p_j \ell_j$$
a **kód átlagos szóhossza**.

Ha adott elemszámú ábécé és eloszlás mellett egy felbontható betűnkénti kód átlagos szóhosszúsága minimális, akkor **optimális kódnak** nevezzük.

### Az optimális kód létezése nem triviális

Az átlagos kódhossz valós szám, és valós számok halmazában nem feltétlenül van minimális elem (például $\{\frac{1}{n} \mid n \in \mathbb{N}\}$), ezért optimális kód létezése nem magától értetődő.

**Állítás.** Adott ábécé és eloszlás esetén létezik optimális kód.

*Bizonyítás.* Válasszunk egy tetszőleges felbontható kódot (ilyen létezik, például egyenletes kód), ennek átlagos szóhosszúsága legyen $\ell$. Mivel $p_j \ell_j > \ell$ esetén a kód nem lehet optimális, ezért elég azokat a kódokat tekinteni, amelyekre
$$\ell_j \le \frac{\ell}{p_j}, \qquad j = 1, 2, \dots, n .$$
Ilyen kód csak véges sok van, így van köztük minimális átlagos hosszúságú. $\square$

### Korlátok

Az átlagos szóhossz alulról az entrópiával korlátozott, és az entrópiánál legfeljebb 1-gyel nagyobb érték már elérhető; ez a zajmentes csatorna Shannon-tétele és a Shannon-kód létezése. A ténylegesen optimális kódot a Huffman-algoritmus állítja elő.

## Kapocs

- [[concepts/dimatii/shannon-tetel-zajmentes-csatornara]] — $H_r(p_1,\dots,p_n) \le \bar{\ell}$, vagyis az alsó korlát
- [[concepts/dimatii/huffman-kod]] — az optimális kódot ténylegesen megkonstruáló algoritmus
- [[concepts/dimatii/entropia]] — az átlagos szóhossz elméleti alsó korlátja
- [[concepts/dimatii/betunkenti-kodolas]] — a kódolási keret, amelyben az optimalitás értelmezett
