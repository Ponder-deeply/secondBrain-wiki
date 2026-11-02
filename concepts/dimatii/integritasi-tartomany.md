---
tags: [concept]
sources: [DimatIIEa04.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Integritási tartomány

Kommutatív, nullosztómentes gyűrű — az a legszűkebb keret, amelyben az oszthatóság és az egység fogalma a megszokott módon értelmezhető.

## Tartalom

### Definíció

A kommutatív, nullosztómentes gyűrűt **integritási tartománynak** nevezzük.

Példa: $(\mathbb{Z}; +, \cdot)$. A Farkas-diák szerint az integritási tartomány legalább kételemű. Véges integritási tartomány test. A diák hierarchiájában az egységelemes integritási tartomány után a Gauss-gyűrű (UFD), a főideálgyűrű és az euklideszi gyűrű következik; főideálgyűrű: [[concepts/dimatii/reszgyuru-es-idealok]].

### Oszthatóság

Az $(R; \oplus, \otimes)$ egységelemes integritási tartományban az $a, b \in R$ elemekre azt mondjuk, hogy **$a$ osztója $b$-nek**, ha van olyan $c \in R$, amire $b = a \otimes c$. Jelölése: $a \mid b$.

### Egység

Az egységelem osztóját **egységnek** nevezzük.

Nem szabad összekeverni az *egységelem* és az *egység* fogalmát: egységelemből csak egyetlen egy van (jelölése $1$), egységből viszont tipikusan több is. Az egységelem persze mindig egység is, hiszen $1 \mid 1$, mivel $1 = 1 \otimes 1$.

$\mathbb{Z}$-ben például az egységelem az $1$, az egységek pedig a $1$ és a $-1$.

### Az egységek csoportja és az egységelem megléte (előadásdiák)

Egységelemes integritási tartományban az egységek halmaza, $U(R)$, a szorzásra csoportot alkot; az asszociáltság ekvivalenciareláció, és két elem asszociáltságának szükséges és elégséges feltétele a kölcsönös oszthatóság. Integritási tartományban akkor és csak akkor létezik egységelem, ha létezik egység (lásd [[concepts/dimatii/euklideszi-gyuru]]). A hierarchia: Gauss-gyűrű $\subset$ egységelemes integritási tartomány ([[concepts/dimatii/gauss-gyuru]]).

### Miért fontos

Ez a fogalmi réteg készíti elő az oszthatóságelméletet: a legnagyobb közös osztó, a felbonthatatlan és a prímelem fogalma mind integritási tartományban fogalmazódik meg, és ezt a keretet használja a polinomok oszthatóságelmélete is.

### Feladattípusok és módszerek (gyakorlati feladatsor, 2020 ősz, 6. sor)

Véges, legalább két elemű integritási tartomány test: minden $a\ne0$-ra az $x\mapsto ax$ injektív, ezért véges halmazon bijektív, így van $x$, amelyre $ax=1$ (részletesebben a [[concepts/dimatii/test]] lap feladattípusai között). A tétel a $\mathbb{Z}_p$ test voltának egy másik indoka is: $\mathbb{Z}_p$ véges és ($p$ prím esetén) nullosztómentes.

## Kapocs

- [[concepts/dimatii/nullosztomentes-gyuru]] — a definíció egyik fele
- [[concepts/dimatii/gyuru]] — a kommutativitás és az egységelem fogalma
- [[concepts/dimatii/test]] — az a szűkítés, ahol minden nemnulla elem egység
- [[concepts/dimatii/polinomgyuru]] — integritási tartomány fölött $R[x]$ is az
