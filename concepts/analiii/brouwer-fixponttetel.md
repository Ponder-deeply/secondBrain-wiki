---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.1. xix) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Brouwer-fixponttétel

Zárt gömböt önmagába képező folytonos leképezésnek van fixpontja. A Banach-fixponttétellel szemben itt nem kell kontrakció — cserébe a fixpont nem egyértelmű, és nem is konstruálható iterációval.

## Tartalom

### A tétel

Legyen $1 \le n \in \mathbb{N}$, $1 \le p \le +\infty$, $a \in \mathbb{R}^n$, $r > 0$, és

$$G := \{x \in \mathbb{R}^n : \|x-a\|_p \le r\}$$

a zárt gömb. Ha $f : G \to G$ **folytonos**, akkor van olyan $\alpha \in G$, amelyre $f(\alpha) = \alpha$.

Az $n \ge 2$ eset bizonyítása jóval összetettebb (topológiai eszközöket igényel), ezért az anyagban bizonyítás nélkül szerepel.

### Az $n = 1$ eset a Bolzano-tételből

Ekkor $G = [a-r, a+r] =: [u,v]$, és $f : [u,v]\to[u,v]$, azaz $u \le f(x) \le v$. A

$$g(x) := f(x) - x \qquad (u \le x \le v)$$

függvény folytonos, és

$$g(u) = f(u) - u \ge 0, \qquad g(v) = f(v) - v \le 0.$$

A [[concepts/analiii/bolzano-tetel-osszefuggo-halmazon|Bolzano-tétel]] szerint van olyan $\alpha \in [u,v]$, amelyre $g(\alpha) = 0$, azaz $f(\alpha) = \alpha$. $\blacksquare$

### Viszonya a Banach-fixponttételhez

| | Banach | Brouwer |
|---|---|---|
| Tér | teljes metrikus tér | $\mathbb{R}^n$-beli zárt gömb |
| Feltétel a leképezésre | kontrakció ($q < 1$) | csak folytonosság |
| Fixpont | egyértelmű | létezik, de nem feltétlenül egyértelmű |
| Konstruktív | igen, iterációval | nem |

A [[concepts/analiii/banach-fixponttetel-metrikus-terben|Banach-fixponttétel]] a numerikus eljárások és az implicit-, illetve inverzfüggvény-tétel bizonyításának eszköze; a Brouwer-tétel inkább egzisztenciaállítás, amely a többváltozós vektorfüggvények analízisében és az egyensúlyi feladatokban játszik szerepet.

## Kapocs

- [[concepts/analiii/bolzano-tetel-osszefuggo-halmazon]] — ebből következik az $n = 1$ eset
- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — az erősebb feltételű, konstruktív fixponttétel
- [[concepts/analiii/kompakt-halmazok]] — a zárt gömb kompaktsága $\mathbb{R}^n$-ben
- [[concepts/analiii/folytonossag-metrikus-terben]] — az egyetlen feltétel a leképezésre
