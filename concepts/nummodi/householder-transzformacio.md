---
tags: [concept]
sources: [NM1_ea05.pdf]
derivation: source
updated: 2026-08-05
---

# Householder-transzformációk

A Householder-mátrix egy speciális [[concepts/nummodi/ortogonalis-matrixok|ortogonális mátrix]], amely egy hipersíkra való tükrözést valósít meg. A [[concepts/nummodi/qr-felbontas|QR-felbontás]] numerikusan stabil előállításához alkalmazzák.

## Definíció

**Householder-mátrix:**

Egy $H = H(v) \in \mathbb{R}^{n \times n}$ mátrixot *Householder-mátrixnak* nevezzük, ha

$$H(v) = I - 2vv^\top,$$

ahol $v \in \mathbb{R}^n$ és $\|v\|_2 = 1$.

**Megjegyzés:** A $H(v)$ transzformációs mátrixot nem kell explicit előállítani. Vektorra való alkalmazása a **Householder-transzformáció**:

- $x \in \mathbb{R}^n$-re: $H(v)x = (I - 2vv^\top)x = x - 2v\underbrace{(v^\top x)}_{\in\mathbb{R}}$.
- $y \in \mathbb{R}^n$-re (balról): $y^\top H(v) = y^\top(I - 2vv^\top) = y^\top - 2\underbrace{(y^\top v)}_{\in\mathbb{R}}v^\top$.

Mindkét esetben **$4n$ művelet** szükséges a mátrixszal való szorzás $2n^2 + \mathcal{O}(n)$-es műveletigénye helyett.

## Tulajdonságok

**Állítás — Householder-mátrixok tulajdonságai:**

1. $H^\top = H$ (szimmetrikus),
2. $H^2 = I$, azaz $H^{-1} = H$ (**ortogonális** és **involúció**),
3. $H(v) \cdot v = -v$,
4. $\forall y \perp v$: $H(v) \cdot y = y$.

**Bizonyítás** (felhasználva $v^\top v = 1$ és $v^\top y = 0$):

1. $(I - 2vv^\top)^\top = I^\top - 2(vv^\top)^\top = I - 2vv^\top$,
2. $(I - 2vv^\top)(I - 2vv^\top) = I - 2vv^\top - 2vv^\top + 4v\underbrace{v^\top v}_{1}v^\top = I$,
3. $(I - 2vv^\top)v = v - 2v\underbrace{v^\top v}_{1} = v - 2v = -v$,
4. $(I - 2vv^\top)y = y - 2v\underbrace{v^\top y}_{0} = y$. $\square$

**Geometriai értelmezés:** $H(v)$ tükröző mátrix a $v$-re merőleges (azaz $v$ normálvektorú) $n-1$ dimenziós altérre (0-n átmenő egyenesre, síkra stb.). Bármely $x \in \mathbb{R}^n$ vektor felbontható $x = a + b$ alakra, ahol $a \perp v$ és $b \| v$. Ekkor $H(v)x = H(v)a + H(v)b = a - b$. Mivel $H(v)$ ortogonális, $\|H(v)x\|_2 = \|x\|_2$ — a transzformáció a vektor hosszát **nem változtatja meg**.

## Tükrözési tétel

**Tétel:** Legyenek $a, b \in \mathbb{R}^n$, $a \neq b$ és $\|a\|_2 = \|b\|_2 \neq 0$. Ekkor a

$$v = \pm \frac{a - b}{\|a - b\|_2}$$

választással $H(v) \cdot a = b$.

**Bizonyítás:** Ismerve, hogy $H(v) = I - 2vv^\top$, számoljuk végig a $H(v) \cdot a$ szorzatot. Közben felhasználjuk, hogy $\|a\|_2 = \|b\|_2$, azaz $a^\top a = b^\top b$, valamint a skaláris szorzás kommutativitását ($a^\top b = b^\top a$):

$$\left(I - \frac{2(a-b)(a-b)^\top}{\|a-b\|_2^2}\right) \cdot a = a - \frac{2(a-b)(a^\top a - b^\top a)}{(a-b)^\top(a-b)} = a - \frac{2(a-b)(a^\top a - b^\top a)}{2(a^\top a - b^\top a)} = a - (a - b) = b. \quad \square$$

**Megjegyzés:** Egyébként $H(v) \cdot b = a$ is teljesül.

## Előjelfüggvény és numerikus stabilitás

**Definíció — előjel függvény:**

$$\text{sgn}: \mathbb{R} \to \mathbb{R}, \qquad \text{sgn}(x) = \begin{cases} 1 & \text{ha } x > 0, \\ 0 & \text{ha } x = 0, \\ -1 & \text{ha } x < 0. \end{cases}$$

**Megjegyzés:** A Householder-transzformációknál nem engedjük meg a 0 értéket — helyette akár $+1$-et, akár $-1$-et választhatunk.

**Numerikusan stabil előjelválasztás** — ha $a$ vektort $b = k \cdot e_1$ alakúra kell hozni:

$$\sigma := -\text{sgn}(a_{11}) \cdot \|a\|_2, \qquad v = \frac{a - \sigma e_1}{\|a - \sigma e_1\|_2}.$$

Az $a$ első elemével ellentétes előjel választásával elérjük, hogy $\|a - \sigma e_1\|_2 \geq \|a\|_2$, így az osztásban nem keletkezik jegyvesztés.

## QR-felbontás Householder-transzformációkkal

**Módszer — felső háromszög alakra hozás:**

Legyen adott $A \in \mathbb{R}^{n \times n}$ invertálható mátrix, első oszlopa $a_1$.

- Egy lépésben egy oszlopot kinullázunk a főátló alatt ($\sim$ GE).
- Így $n - 1$ lépésben felső háromszög alakot nyerünk.

**1. lépés:** $a_1 \Rightarrow \sigma_1 \cdot e_1$, ahol $\sigma_1 := -\text{sgn}(a_{11}) \cdot \|a_1\|_2$ (tehát $|\sigma_1| = \|a_1\|_2$):

$$v_1 := \frac{a_1 - \sigma_1 e_1}{\|a_1 - \sigma_1 e_1\|_2}, \qquad H_1 := H(v_1).$$

Ekkor:

$$H_1 \cdot A = H(v_1) \cdot A = \begin{pmatrix} \sigma_1 & * & \cdots & * \\ 0 & & & \\ \vdots & & B & \\ 0 & & & \end{pmatrix}.$$

A folyamat rekurzívan folytatódik a $B \in \mathbb{R}^{(n-1)\times(n-1)}$ részmátrixon.

**Eredmény:** $H_{n-1} \cdots H_1 \cdot A = R$ (felső háromszög), ahol $Q^\top = H_{n-1} \cdots H_1$, tehát

$$A = Q \cdot R, \qquad Q = H_1 \cdots H_{n-1}$$

(ortogonális mátrixok szorzata ortogonális).

## Numerikus példák

### Példa 1 — azonos hosszú vektorok tükrözése

Határozzuk meg azt a Householder-transzformációt, amely $a = [2,\,0,\,1]^\top$-t $b = [1,\,2,\,0]^\top$-ba viszi ($\|a\|_2 = \|b\|_2 = \sqrt{5}$).

$$a - b = \begin{bmatrix}1\\-2\\1\end{bmatrix}, \quad \|a-b\|_2 = \sqrt{6}, \quad v = \frac{1}{\sqrt{6}}\begin{bmatrix}1\\-2\\1\end{bmatrix}.$$

Ellenőrzés: $H(v) \cdot a = a - 2(v^\top a)v = a - 2 \cdot \frac{3}{\sqrt{6}} \cdot \frac{1}{\sqrt{6}}\begin{bmatrix}1\\-2\\1\end{bmatrix} = \begin{bmatrix}2\\0\\1\end{bmatrix} - \begin{bmatrix}1\\-2\\1\end{bmatrix} = \begin{bmatrix}1\\2\\0\end{bmatrix} = b. \checkmark$

### Példa 2 — vektor $k \cdot e_1$ alakúra hozása

Hozzuk az $a = [2,\,-2,\,1]^\top$ vektort $b = \sigma \cdot e_1$ alakra, stabil előjelválasztással.

$a$ első eleme pozitív, ezért $\sigma := -\|a\|_2 = -\sqrt{4+4+1} = -3$.

$$a - \sigma e_1 = \begin{bmatrix}2\\-2\\1\end{bmatrix} - (-3)\begin{bmatrix}1\\0\\0\end{bmatrix} = \begin{bmatrix}5\\-2\\1\end{bmatrix}, \quad \|a - \sigma e_1\|_2 = \sqrt{30}, \quad v = \frac{1}{\sqrt{30}}\begin{bmatrix}5\\-2\\1\end{bmatrix}.$$

Ellenőrzés: $H(v) \cdot a = a - 2(v^\top a)v = a - 2 \cdot \frac{15}{\sqrt{30}} \cdot \frac{1}{\sqrt{30}}\begin{bmatrix}5\\-2\\1\end{bmatrix} = \begin{bmatrix}2\\-2\\1\end{bmatrix} - \begin{bmatrix}5\\-2\\1\end{bmatrix} = \begin{bmatrix}-3\\0\\0\end{bmatrix} = \sigma \cdot e_1. \checkmark$

## Kapocs

- [[concepts/nummodi/ortogonalis-matrixok]] — ortogonális mátrix fogalma és tulajdonságai
- [[concepts/nummodi/qr-felbontas]] — a QR-felbontás, amelynek előállítása Householder-transzformációkkal végzendő
- [[concepts/nummodi/gram-schmidt-ortogonalizacio]] — alternatív QR-előállítás (kevésbé stabil, de kézi számoláshoz praktikusabb)
- [[concepts/nummodi/haromszogmatrixok]] — háromszögmátrixok halmazai
- [[concepts/nummodi/algoritmus-stabilitas]] — stabil algoritmus fogalma; a Householder-módszer numerikusan stabil
- [[subjects/nummodi]] — kurzus áttekintése
