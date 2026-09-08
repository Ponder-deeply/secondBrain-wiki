---
tags: [concept]
sources: [DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
---

# Integritási tartomány

Kommutatív, nullosztómentes gyűrű — az a legszűkebb keret, amelyben az oszthatóság és az egység fogalma a megszokott módon értelmezhető.

## Tartalom

### Definíció

A kommutatív, nullosztómentes gyűrűt **integritási tartománynak** nevezzük.

Példa: $(\mathbb{Z}; +, \cdot)$.

### Oszthatóság

Az $(R; \oplus, \otimes)$ egységelemes integritási tartományban az $a, b \in R$ elemekre azt mondjuk, hogy **$a$ osztója $b$-nek**, ha van olyan $c \in R$, amire $b = a \otimes c$. Jelölése: $a \mid b$.

### Egység

Az egységelem osztóját **egységnek** nevezzük.

Nem szabad összekeverni az *egységelem* és az *egység* fogalmát: egységelemből csak egyetlen egy van (jelölése $1$), egységből viszont tipikusan több is. Az egységelem persze mindig egység is, hiszen $1 \mid 1$, mivel $1 = 1 \otimes 1$.

$\mathbb{Z}$-ben például az egységelem az $1$, az egységek pedig a $1$ és a $-1$.

### Miért fontos

Ez a fogalmi réteg készíti elő az oszthatóságelméletet: a legnagyobb közös osztó, a felbonthatatlan és a prímelem fogalma mind integritási tartományban fogalmazódik meg, és ezt a keretet használja a polinomok oszthatóságelmélete is.

## Kapocs

- [[concepts/dimatii/nullosztomentes-gyuru]] — a definíció egyik fele
- [[concepts/dimatii/gyuru]] — a kommutativitás és az egységelem fogalma
- [[concepts/dimatii/test]] — az a szűkítés, ahol minden nemnulla elem egység
- [[concepts/dimatii/polinomgyuru]] — integritási tartomány fölött $R[x]$ is az
