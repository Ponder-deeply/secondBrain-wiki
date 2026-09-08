---
tags: [concept]
sources: [NM1_ea08.pdf]
derivation: source
updated: 2026-08-05
---

# Iterációs módszerek LER megoldására — általános elmélet

Lineáris egyenletrendszer iteratív megoldásának alapötlete: $Ax=b$ LER-t egy ekvivalens $x = Bx + c$ fixpontegyenletté alakítjuk, majd a $x^{(k+1)} = Bx^{(k)} + c$ iterációt futtatjuk.

## Az iteráció felírása

Tekintsük a $\varphi: \mathbb{R}^n \to \mathbb{R}^n$, $\varphi(x) = Bx + c$ leképezést, ahol $B \in \mathbb{R}^{n \times n}$ az **átmenetmátrix** és $c \in \mathbb{R}^n$. Az iteráció:

$$x^{(0)} \in \mathbb{R}^n \text{ (tetszőleges)}, \qquad x^{(k+1)} = \varphi(x^{(k)}) = Bx^{(k)} + c \quad (k = 0, 1, 2, \ldots).$$

**Kapcsolat az $Ax=b$ LER-rel:** Ha a sorozat konvergens, $\lim_{k\to\infty} x^{(k)} = x^*$, akkor a $\varphi$ folytonosságából:

$$\varphi(x^*) = \lim_{k\to\infty} \varphi(x^{(k)}) = \lim_{k\to\infty} x^{(k+1)} = x^*,$$

azaz $x^* = Bx^* + c$, vagyis $(I - B)x^* = c$. Ha $A = I - B$ és $b = c$, akkor $x^*$ az $Ax = b$ LER megoldása.

## Az $A = P + Q$ felbontás általános kerete

Adott $Ax = b$ LER esetén vezessük be az $A = P + Q$ felbontást (ahol $P$ invertálható). Ekkor:

$$Px = -Qx + b \iff x = -P^{-1}Qx + P^{-1}b,$$

iterációs alakban:

$$x^{(k+1)} = \underbrace{-P^{-1}Q}_{B} \cdot x^{(k)} + \underbrace{P^{-1}b}_{c}.$$

A különböző $P$-választások adják a különböző iterációs módszereket (Jacobi, Gauss–Seidel, Richardson stb.).

## Speciális felbontás: $A = L + D + U$

Az $Ax = b$ LER mátrixát az elemek pozíciója szerint bontjuk három részre:

$$A = L + D + U,$$

ahol:
- $L$ — **alsó háromszögmátrix** ($l_{ij} = a_{ij}$ ha $i > j$, különben $0$),
- $D$ — **diagonális mátrix** ($d_{ij} = a_{ij}$ ha $i = j$, különben $0$),
- $U$ — **felső háromszögmátrix** ($u_{ij} = a_{ij}$ ha $i < j$, különben $0$).

**Fontos megjegyzés:** Ez az $L + D + U$ felbontás **semmi köze** az [[concepts/nummodi/lu-felbontas|LU-felbontáshoz]] — ott az $L$ és $U$ mátrixok nem az eredeti $A$ elemeit tartalmazzák, hanem az eliminációs lépések szorzóit és felső háromszög eredményét.

**Feltétel:** A továbbiakban tegyük fel, hogy $A$ diagonális elemei nem nullák (ha mégis, cseréljük fel a LER sorait).

## Konvergencia

A konvergencia részletes tételeit a [[concepts/nummodi/banach-fixponttetel-rn|Banach-féle fixponttétel]] adja meg. Az ekvivalens konvergenciafeltétel:

$$\varrho(B) < 1,$$

ahol $\varrho(B) = \max_i |\lambda_i(B)|$ az átmenetmátrix [[concepts/nummodi/matrixnormak|spektrálsugara]].

## Kapocs

- [[concepts/nummodi/banach-fixponttetel-rn]] — fixpont és kontrakció fogalma, konvergencia tétele és hibabecslések
- [[concepts/nummodi/jacobi-iteracio]] — Jacobi-iteráció: $P = D$, komponensenkénti alak, SDD konvergenciatétel
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER fogalma, megoldási módszerek osztályozása
- [[concepts/nummodi/lu-felbontas]] — LU-felbontás (ne keverjük az $L+D+U$ felbontással!)
- [[concepts/nummodi/matrixnormak]] — spektrálsugár $\varrho(B)$ és indukált normák
- [[concepts/nummodi/kondicioszam]] — kondíciószám és az iterációs módszerek pontossága
