---
tags: [concept, dimatii/hibakorlatozo-es-linearis-kodok]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Szindrómadekódolás

Lineáris kód dekódolása a vett szó szindrómájából: a szindróma meghatározza a hibavektor mellékosztályát, ebből a minimális súlyú mellékosztály-vezetőt levonva kapjuk a kódszót.

## Tartalom

### Szindróma és hibavektor

Adott $v \in \mathbb{F}_q^n$ esetén az $s = \mathbf{H}v \in \mathbb{F}_q^{n-k}$ vektort $v$ **szindrómájának** nevezzük. A $v$ pontosan akkor kódszó, ha $s = 0$.

Legyen $c$ a kódszó, $v$ a vett szó. Az $e = v - c$ vektor a **hibavektor**.

**Állítás.** $\mathbf{H}v = \mathbf{H}e$.

*Bizonyítás.* $\mathbf{H}v = \mathbf{H}(c + e) = \mathbf{H}c + \mathbf{H}e = 0 + \mathbf{H}e = \mathbf{H}e$. $\square$

A dekódolás elve tehát: $v$-ből kiszámítjuk a $\mathbf{H}v$ szindrómát, ami alapján megbecsüljük az $e$ hibavektort, majd meghatározzuk $c$-t a $c = v - e$ képlet segítségével.

### Mellékosztályok

Valamely $e$ hibavektorhoz tartozó **mellékosztály** az $\{e + c : c \text{ kódszó}\}$ halmaz. Az $e = 0$-hoz tartozó mellékosztály maga a kód.

**Állítás.** Az azonos mellékosztályban lévő szavak pontosan az azonos szindrómájú szavak.

### Mellékosztály-vezető és az algoritmus

Minden $s$ szindróma esetén legyen $e_s$ az a minimális súlyú szó, melynek $s$ a szindrómája. Ez a $s$ szindrómához tartozó **mellékosztály-vezető**; a mellékosztály elemei $e_s + c$ alakúak, ahol $c \in K$ kódszó.

**Szindrómadekódolás.** Adott $v$ esetén tekintsük az $s = \mathbf{H}v$ szindrómát, és az $e_s$ mellékosztály-vezetőt. Dekódoljuk $v$-t $c = v - e_s$-nek.

### Helyesség

**Állítás.** Legyen $c$ a kódszó, $v = c + e$ a vett szó, ahol $e$ a hiba, és $w(e) < d/2$, ahol $d$ a kód távolsága. Ekkor a szindrómadekódolás a minimális távolságú dekódolásnak felel meg.

*Bizonyítás.* Egyrészt a korábbi állítás alapján $s = \mathbf{H}v = \mathbf{H}e$, másrészt $e_s$ definíciója miatt $s = \mathbf{H}e_s$. Ezért $e$ és $e_s$ ugyanabban a mellékosztályban van, továbbá $w(e_s) \le w(e)$. Így
$$w(e - e_s) = d(e, e_s) \le d(e, 0) + d(0, e_s) = w(e) + w(e_s) < d .$$
De $\mathbf{H}(e - e_s) = 0$ miatt $e - e_s$ kódszó, így $e = e_s$. $\square$

### Példa

Tekintsük a $(*)$ kódot. $v = (1,1,0,1,1)^T$ esetén $\mathbf{H}v = 0$, így $v$ kódszó. $v = (1,1,0,0,1)^T$ esetén $\mathbf{H}v = (0,1,0)^T = s$. A $(0,0,0,1,0)^T$ szó súlya 1, és a szindrómája a keresett $(0,1,0)^T$, tehát ez lesz a mellékosztály-vezető. Így
$$c = v - e_s = (1,1,0,0,1)^T - (0,0,0,1,0)^T = (1,1,0,1,1)^T .$$

## Kapocs

- [[concepts/dimatii/ellenorzo-matrix]] — a szindrómát előállító mátrix
- [[concepts/dimatii/linearis-kod]] — a lineáris szerkezet, amely a mellékosztályokat értelmessé teszi
- [[concepts/dimatii/hibajelzes-es-hibajavitas]] — a minimális távolságú dekódolás, amelynek ez a hatékony megvalósítása
- [[concepts/dimatii/hamming-kod]] — ahol a szindróma közvetlenül a hibás pozíció sorszámát adja
