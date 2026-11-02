---
tags: [concept]
sources: [Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf]
references: [Lehman–Leighton–Meyer, Mathematics for Computer Science, 9.5 és 9.8–9.9 (Turing's code)]
derivation: source
kind: comparison
element: water
updated: 2026-10-22
---

# Turing kódja (1.0 és 2.0)

Turing feltételezett titkosítási ötlete: az üzenetet megszorozzuk egy titkos prímkulccsal. Az egész számokon és modulo $n$ is megtörhető, és jól mutatja, mire jó az lnko és a multiplikatív inverz.

## Tartalom

Az üzenetet számmá alakítjuk (például betűnként két számjegy: $A = 01$, $B = 02$, …, "victory" $\to$ $22\,09\,03\,20\,15\,18\,25$), és prímmé egészítjük ki további számjegyekkel. Az $m$ üzenetet a titkos $k$ prímkulccsal titkosítjuk.

### 1.0 változat: szorzás az egész számokon

- Titkosítás: $\hat m = m \cdot k$.
- Dekódolás: $\hat m / k = m$.
- Példa: $m = 2209032015182513$, $k = 22801763489$, $\hat m = 50369825549820718594667857$.

A biztonság a faktorizáció nehézségén alapul: $\hat m$-ből $m \cdot k$ szorzat felbontása kell.

**Törés két üzenettel.** Ugyanazzal a kulccsal titkosított $\hat m_1 = m_1 k$ és $\hat m_2 = m_2 k$ esetén $(\hat m_1, \hat m_2) = k \cdot (m_1, m_2) = k$, mert $m_1, m_2$ különböző prímek. Az lnko az euklideszi algoritmussal hatékonyan számolható ([[concepts/dimatii/euklideszi-algoritmus]]), így a kulcs kiderül, és minden további üzenet olvasható.

### 2.0 változat: szorzás modulo $n$

A küldő és a fogadó megegyezik egy (nyilvános) $n$ modulusban és a titkos $k < n$ prímben; $\hat m = m \cdot k$ a $\mathbb{Z}_n$-ben. A dekódolás nem osztás, hanem szorzás $k$ inverzével: $\hat m \cdot j = m k j = m$, ha $kj \equiv 1 \pmod n$. Az inverz a bővített euklideszi algoritmussal számolható, és létezik, ha $(k,n) = 1$: ezt biztosítja, hogy $n$ prím ([[concepts/dimatii/invertalhatosag-zm-ben]]).

**Törés ismert nyílt szöveggel.** Ha az ellenfél ismeri az $m$ üzenetet és a titkosított $\hat m$-et is (ismert nyílt szöveges támadás), kiszámolja $m$ inverzét $j'$-t, és $j' \cdot \hat m = j' m k = k$: megvan a kulcs. Ez a támadás az Enigma törésének is egyik eszköze volt (időjárásjelentések titkosított és nyílt alakja).

### Tanulságok

- Lineáris, kulcsonként nem változó titkosítás ismert nyílt szöveg ellen törhető: [[concepts/kript/tamadasmodellek]].
- Az RSA a szorzás helyett hatványozást használ, és nem prím, hanem két prím szorzata a modulus: [[concepts/dimatii/rsa]].
- Az 1.0 változat azt mutatja, hogy az lnko pár lépésben megtalálja a közös prímtényezőt, miközben a faktorizáció nehéz.

## Kapocs

- [[concepts/dimatii/euklideszi-algoritmus]] — az lnko-támadás eszköze
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az inverz kiszámítása a dekódoláshoz
- [[concepts/dimatii/invertalhatosag-zm-ben]] — mikor létezik az inverz
- [[concepts/dimatii/rsa]] — a működő nyilvános kulcsú utód
- [[concepts/kript/tamadasmodellek]] — az ismert nyílt szöveges támadás
- [[concepts/kript/enigma]] — a valódi Turing-féle törés
