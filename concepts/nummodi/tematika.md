---
tags: [concept]
sources: [NM1_ea00.pdf]
derivation: source
updated: 2026-08-05
---

# Numerikus módszerek I. — Tematika

A kurzus tematikájának áttekintése félév és témakör szerint; az egyes módszerek részletező fogalomlapjain hivatkozunk vissza erre.

## I. félév

### 1. Gépi számábrázolás és hibaszámítás

A lebegőpontos számrendszer, kerekítési hibák, abszolút és relatív hiba; a numerikus számítások megbízhatóságának alapjai.

### 2. Lineáris egyenletrendszerek megoldása

**Direkt módszerek** — véges lépésben egzakt (kerekítési hibától eltekintve) megoldást adnak:

| Módszer | Leírás |
|---|---|
| Gauss-elimináció | Sorekvivalens transzformációk; hátra-helyettesítés |
| LU-felbontás | $A = LU$; alsó-felső háromszög mátrixok szorzata |
| LDU-felbontás | $A = LDU$; diagonális mátrixot is explicit kiemelve |
| Cholesky-felbontás | $A = LL^T$ szimmetrikus pozitív definit esetén |
| QR-felbontás | $A = QR$; ortogonális $Q$ és felső háromszöges $R$ |

A QR-felbontás két fő módszere:
- **Gram–Schmidt-ortogonalizáció** — oszlopvektoros megközelítés
- **Householder-transzformáció** — tükrözéses módszer

**Iteratív módszerek** — közelítő sorozatot képeznek, konvergencia szükséges:

| Módszer | Jelleg |
|---|---|
| Jacobi-iteráció | Párhuzamos frissítés átlós skálázással |
| Gauss–Seidel-iteráció | Sorban frissít, azonnal felhasználja az új értékeket |
| Richardson-iteráció | Egyszerű relaxációs séma |

Az iteratív módszerek konvergenciájának elméleti alapja: **Banach-féle fixponttétel** és **mátrixnormák**. Szükséges feltétel: az iterációs mátrix spektrálrádiusza kisebb 1-nél.

### 3. Nemlineáris egyenletek megoldása

Az $f(x) = 0$ egyenlet gyökeinek közelítő meghatározása:

| Módszer | Jelleg |
|---|---|
| Intervallumfelezés | Biszekcló; garantáltan konvergál, ha $f$ előjelet vált |
| Fixpont-iteráció | $x_{n+1} = g(x_n)$; Banach fixponttétel ad konvergenciát |
| Newton-módszer | $x_{n+1} = x_n - f(x_n)/f'(x_n)$; kvadratikus konvergencia |
| Szelőmódszer | Numerikus derivált (két pont); szuperlineáris konvergencia |
| Húrmódszer | Regula falsi; monoton konvergencia |

### 4. Polinomok gyökeinek becslése — Horner-algoritmus

A Horner-algoritmus hatékony módszer polinom és deriváltjainak egy adott pontban való kiértékelésére. Alapja a gyökök numerikus meghatározásának (pl. Newton-módszerrel való kombinálásnak).

## II. félév

### 5. Sajátértékfeladatok (csak A szakirány)

Az $Av = \lambda v$ sajátérték-egyenlet numerikus megoldása.

### 6. Interpoláció és approximáció

Adott pontokra illesztett függvény (pontos egyezés: interpoláció; legjobb közelítés: approximáció).

### 7. Numerikus integrálás

$\int_a^b f(x)\,dx$ közelítő kiszámítása véges összegekkel (pl. trapézszabály, Simpson-szabály, Gauss-kvadratúra).

## Kapocs

- [[subjects/nummodi]] — kurzus áttekintése, követelmények, irodalom
- [[concepts/nummodi/kovetelmenyek]] — vizsga- és jegykövetelmények
