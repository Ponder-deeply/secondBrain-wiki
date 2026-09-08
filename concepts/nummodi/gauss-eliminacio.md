---
tags: [concept]
sources: [NM1_ea02.pdf, NM1_ea03.pdf]
derivation: source
updated: 2026-08-05
---

# Gauss-elimináció

A Gauss-elimináció (GE) a lineáris egyenletrendszerek megoldásának alap direkt módszere: az együtthatómátrixot felső háromszög alakra hozza, majd visszahelyettesítéssel meghatározza az ismeretleneket.

## Előkészítés — bővített mátrix

Legyen $a_{i,n+1} := b_i$, azaz $[A \mid b]$ a tárolási forma. Az elimináció célja:

1. **Előre** (balról jobbra): a főátló alatt kinullázzuk az elemeket — maga a Gauss-elimináció.
2. **Visszafelé** (jobbról balra): a főátló fölött nullázunk — visszahelyettesítés.

**Kezdő mátrix:**
$$A^{(0)} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} & b_1 \\ a_{21} & a_{22} & \cdots & a_{2n} & b_2 \\ \vdots & & \ddots & \vdots & \vdots \\ a_{n1} & a_{n2} & \cdots & a_{nn} & b_n \end{bmatrix}$$

## Az elimináció általános lépése

### $k$-adik lépés ($k = 1, \ldots, n-1$)

Az $1., 2., \ldots, k.$ egyenletet változatlanul hagyjuk. Ha $a_{kk}^{(k-1)} \ne 0$, akkor az $i$-edik egyenletből ($i = k+1, \ldots, n$) kivonjuk a $k$-adik egyenlet $\dfrac{a_{ik}^{(k-1)}}{a_{kk}^{(k-1)}}$-szorosát, hogy $a_{ik}^{(k-1)}$ kinullázódjon.

**Tétel — a $k$-adik lépés képlete:**

$$a_{ij}^{(k)} = a_{ij}^{(k-1)} - \frac{a_{ik}^{(k-1)}}{a_{kk}^{(k-1)}} \cdot a_{kj}^{(k-1)}$$

$$k = 1,\ldots,n-1;\quad i = k+1,\ldots,n;\quad j = k+1,\ldots,n,n+1.$$

### Eredmény

$n-1$ lépés után felső háromszögmátrix alakú LER-t kapunk:

$$A^{(n-1)} = \begin{bmatrix} a_{11}^{(0)} & a_{12}^{(0)} & \cdots & a_{1n}^{(0)} & b_1^{(0)} \\ 0 & a_{22}^{(1)} & \cdots & a_{2n}^{(1)} & b_2^{(1)} \\ \vdots & \ddots & \ddots & \vdots & \vdots \\ 0 & 0 & \cdots & a_{nn}^{(n-1)} & b_n^{(n-1)} \end{bmatrix}$$

## Visszahelyettesítés

A felső háromszögmátrixú LER megoldása:

$$x_n = \frac{a_{n,n+1}^{(n-1)}}{a_{nn}^{(n-1)}},$$

$$x_i = \frac{1}{a_{ii}^{(i-1)}} \left( a_{i,n+1}^{(i-1)} - \sum_{j=i+1}^{n} a_{ij}^{(i-1)} \cdot x_j \right) \quad (i = n-1,\ldots,1).$$

## Numerikus példa

Oldjuk meg az $Ax = b$ rendszert:
$$A = \begin{pmatrix} 2 & 0 & 3 \\ -4 & 5 & -2 \\ 6 & -5 & 4 \end{pmatrix}, \quad b = \begin{pmatrix} -1 \\ 3 \\ -3 \end{pmatrix}.$$

**1. lépés** (pivot: $a_{11}=2$; szorzók: $-4/2=-2$, $6/2=3$):
$$\begin{bmatrix}2&0&3&-1\\0&5&4&1\\0&-5&-5&0\end{bmatrix}$$

**2. lépés** (pivot: $a_{22}=5$; szorzó: $-5/5=-1$):
$$\begin{bmatrix}2&0&3&-1\\0&5&4&1\\0&0&-1&1\end{bmatrix}$$

**Visszahelyettesítés:**
- $x_3 = 1/(-1) = -1$
- $x_2 = (1 - 4 \cdot (-1))/5 = 5/5 = 1$
- $x_1 = (-1 - 3 \cdot (-1))/2 = 2/2 = 1$

**Megoldás:** $x = [1, 1, -1]^T$.

## Elvégezhetőség és főminorok

**Tétel:** A GE elvégezhető sor- és oszlopcsere nélkül $\iff$ $a_{kk}^{(k-1)} \ne 0$ minden $k = 1, \ldots, n-1$-re.

**Definíció — főminorok:** Az $A$ mátrix $k$-adik főminora:
$$D_k = \det\begin{pmatrix} a_{11} & \cdots & a_{1k} \\ \vdots & \ddots & \vdots \\ a_{k1} & \cdots & a_{kk} \end{pmatrix}, \quad k = 1,\ldots,n.$$

**Tétel:** $D_k \ne 0\;(k = 1,\ldots,n-1) \iff a_{kk}^{(k-1)} \ne 0\;(k = 1,\ldots,n-1)$.

**Bizonyítás:** A GE lépései determináns-tartók, ezért
$$D_k = a_{11} \cdot a_{22}^{(1)} \cdots a_{kk}^{(k-1)} = D_{k-1} \cdot a_{kk}^{(k-1)},$$
amiből az állítás adódik. ($D_n \ne 0$ és $a_{nn}^{(n-1)} \ne 0$ nem szükséges a GE-hoz, csak a LER megoldhatóságához.)

**Numerikus megjegyzés:** Főelemkiválasztás alkalmazásával a GE-s hányadosaink pontosabbak lesznek; determináns számításakor a cserékkel vigyázni kell.

## Főelemkiválasztás (Pivoting)

Ha $a_{kk}^{(k-1)} = 0$ (vagy numerikusan kicsi), cserére van szükség.

**Részleges főelemkiválasztás:** A $k$-adik lépésben válasszunk egy olyan $m$ indexet, melyre $\left|a_{mk}^{(k-1)}\right|$ maximális ($m \in \{k, k+1, \ldots, n\}$), majd cseréljük ki a $k$-adik és $m$-edik sort.

**Teljes főelemkiválasztás:** A $k$-adik lépésben válasszunk $(m_1, m_2)$ indexpárt, melyre $\left|a_{m_1 m_2}^{(k-1)}\right|$ maximális ($m_1, m_2 \in \{k, k+1, \ldots, n\}$), majd cseréljük ki a $k$-adik és $m_1$-edik sort, valamint a $k$-adik és $m_2$-edik oszlopot.

**Megjegyzések:**
- Sorcserénél a megoldás nem változik.
- Oszlopcserénél a megoldás komponensei a cserének megfelelően változnak.
- Biztos és stabil megoldás a főelemkiválasztással érhető el.

## A GE lépései mátrixszorzásként ($L_k$ mátrixok)

A Gauss-elimináció $k$-adik lépése felírható egy $L_k$ alsó háromszögmátrixszal való bal oldali szorzásként:

$$L_k \cdot A^{(k-1)} = A^{(k)}, \quad L_k := I - \ell_k e_k^\top,$$

ahol $\ell_k \in \mathbb{R}^n$, $(\ell_k)_i = 0\;(i \le k)$ és $(\ell_k)_i = l_{ik}$ ($i > k$) a GE-s hányadosok. Tehát:

$$L_{n-1} \cdots L_2 \cdot L_1 \cdot A = U,$$

és ebből $A = L_1^{-1} \cdots L_{n-1}^{-1} \cdot U = L \cdot U$, vagyis éppen az [[concepts/nummodi/lu-felbontas|LU-felbontást]] kaptuk meg.

Részletek az $L_k$ mátrixokról, inverzeikről és szorzatukról: [[concepts/nummodi/haromszogmatrixok|haromszogmatrixok]].

## Alkalmazások

### Determináns kiszámítása
A GE lépései determináns-tartók, ezért:
$$\det(A) = \det(\Delta\text{alak}) = \prod_{k=1}^{n} a_{kk}^{(k-1)}.$$
(Sor- vagy oszlopcsere esetén a determináns előjele változik.)

### Több jobboldal egyszerre
Több $b$ jobboldal esetén az egyenletrendszereket egyszerre oldhatjuk meg:
$$[A \mid b_1 \mid b_2 \mid b_3] \xrightarrow{\text{GE}} \xrightarrow{\text{visszahely.}} [I \mid x_1 \mid x_2 \mid x_3].$$

### Mátrix inverze
$A$ inverze az $A \cdot X = I$ mátrixegyenlet megoldása ($n$ darab LER). Kiterjesztett mátrixon hajtjuk végre:
$$[A \mid I] \xrightarrow{\text{GE}} \xrightarrow{\text{visszahely.}} [I \mid A^{-1}].$$

## Műveletigény

### Gauss-elimináció

**Tétel:** A Gauss-elimináció műveletigénye
$$\frac{2}{3}n^3 + \mathcal{O}(n^2).$$

**Bizonyítás:** A $k$-adik lépésben $(n-k)$ osztás, $(n-k)(n-k+1)$ szorzás és $(n-k)(n-k+1)$ összeadás szükséges — összesen $(n-k)(2(n-k)+3)$ művelet. Összegzés és az $s = n-k$ helyettesítéssel:
$$\sum_{k=1}^{n-1}(n-k)(2(n-k)+3) = \sum_{s=1}^{n-1}s(2s+3) = 2\cdot\frac{(n-1)n(2n-1)}{6} + 3\cdot\frac{(n-1)n}{2} = \frac{2}{3}n^3 + \mathcal{O}(n^2).$$

**Definíció — $\mathcal{O}(n^2)$ függvény:** Az $f(n)$ függvény $\mathcal{O}(n^2)$-nagyságrendű, ha $f(n)/n^2$ korlátos minden $n \in \mathbb{N}$-re.

Matlab-kísérlet ($n = 10, 20, 30, \ldots, 200$) megerősíti, hogy a GE futási ideje valóban $n^3$-szerű.

### Visszahelyettesítés

**Tétel:** A visszahelyettesítés műveletigénye
$$n^2 + \mathcal{O}(n).$$

**Bizonyítás:** Az $i$-edik sorra 1 osztás, $(n-i)$ szorzás és $(n-i)$ összeadás kell — összesen $2(n-i)+1$ művelet. Összegzés:
$$1 + \sum_{s=1}^{n-1}(2s+1) = 1 + 2\cdot\frac{n(n-1)}{2} + (n-1) = n^2 + \mathcal{O}(n).$$

## Kapocs

- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER fogalma, megoldhatóság, módszerek áttekintése
- [[concepts/nummodi/lu-felbontas]] — LU-felbontás: definíció, létezés, egyértelműség, közvetlen kiszámítás, alkalmazás
- [[concepts/nummodi/haromszogmatrixok]] — $L_k$ elimináló mátrixok, inverzeik, szorzatuk kompakt alakja
- [[concepts/nummodi/algoritmus-stabilitas]] — stabil vs. instabil algoritmus; főelemkiválasztás és stabilitás
- [[concepts/nummodi/hibaszamitas]] — kerekítési hibák, kondíciószám és LER megoldásának pontossága
- [[concepts/nummodi/tematika]] — kurzus tematikája
- [[subjects/nummodi]] — kurzus áttekintése
