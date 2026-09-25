---
tags: [concept, dimatii/hibakorlatozo-es-linearis-kodok]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Hamming-kód

1-hibajavító perfekt lineáris kód, amelynek ellenőrző mátrixát az összes nem-nulla oszlopvektor alkotja; a szindróma közvetlenül megmutatja a hibás pozíciót.

## Tartalom

### Definíció

Az 1-hibajavító perfekt lineáris kódot **Hamming-kódnak** nevezzük. (Perfekt kód: olyan kód, amelyre a Hamming-korlát egyenlőséggel teljesül.)

### Konstrukció

Ha egy olyan bináris kódot készítünk, amelyre a $\mathbf{H}$ ellenőrző mátrix oszlopainak a különböző nemnulla, $r$ hosszú vektorokat választjuk, akkor egy 1-hibajavító kódot kapunk: nincs $\mathbf{H}$-nak 1, se 2 lineárisan összefüggő oszlopa, tehát a kód távolsága legalább 3.

Ekkor a Hamming-korlát alakja:
$$2^k (1 + n) \le 2^n .$$
Egyenlőség esetén $n = 2^{\,n-k} - 1$, és pont ennyi $n-k$ hosszú, nemnulla vektor van.

$n = 2^r - 1$ esetén $k = n - \log(n+1)$, így a megfelelő $(n,k)$ párok:

| $n$ | 3 | 7 | 15 | 31 | 63 | 127 | $\cdots$ |
|---|---|---|---|---|---|---|---|
| $k$ | 1 | 4 | 11 | 26 | 57 | 120 | $\cdots$ |

### Dekódolás

Ha csak 1 hiba van, akkor a hibavektornak csak egy koordinátája 1, a többi 0, így a szindróma az ellenőrző mátrix valamely oszlopa lesz. Ennek az oszlopnak megfelelő koordinátája hibás az üzenetben — a javítás tehát egyetlen táblázatkeresés.

### Példa

$n = 7$, $k = 4$:
$$\mathbf{H} = \begin{pmatrix} 1 & 0 & 1 & 1 & 1 & 0 & 0 \\ 1 & 1 & 0 & 1 & 0 & 1 & 0 \\ 1 & 1 & 1 & 0 & 0 & 0 & 1 \end{pmatrix}, \qquad \mathbf{G} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \\ 1 & 0 & 1 & 1 \\ 1 & 1 & 0 & 1 \\ 1 & 1 & 1 & 0 \end{pmatrix}.$$

$v = (1,1,0,0,1,1,1)^T$ esetén $\mathbf{H}v = (0,1,1)^T = s$, ami a $\mathbf{H}$ 2. oszlopa, így a 2. koordináta romlott el; az elküldött kódszó $c = (1,0,0,0,1,1,1)^T$.

### Gyakorlati változatok

A $[7,4]$-es Hamming-kódot egy paritásbittel kiegészítve kapjuk a teletextnél használt kódolást. A $[15,11]$-es Hamming-kódot egy paritásbittel kiegészítve a műholdas műsorszórásnál (DBS) használják.

## Kapocs

- [[concepts/dimatii/hamming-korlat]] — a perfektség definíciója, amelyet a kód teljesít
- [[concepts/dimatii/ellenorzo-matrix]] — a konstrukció közvetlenül az oszlopok megválasztása
- [[concepts/dimatii/szindroma-dekodolas]] — a dekódolás általános elve, itt különösen egyszerű alakban
- [[concepts/dimatii/linearis-kod]] — a kódcsalád, amelybe tartozik
