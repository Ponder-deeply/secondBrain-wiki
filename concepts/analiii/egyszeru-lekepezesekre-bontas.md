---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.5.4.2. Tétel"]
derivation: source
updated: 2026-09-07
---

# Felbontás egyszerű leképezésekre

Nemelfajuló Jacobi-mátrixú $C^1$ leképezés lokálisan előáll véges sok **egyszerű függvény** (csak egyetlen koordinátát változtat) és **csereoperátor** (két koordinátát felcserél) kompozíciójaként.

## Tartalom

### Egyszerű függvény

Az $f = (f_1,\dots,f_n) \in \mathbb{R}^n\to\mathbb{R}^n$ függvény **egyszerű**, ha legfeljebb egy koordinátáját változtatja meg: valamely $k$ indexre $f_i(x) = x_i$ minden $i \ne k$-ra. Ilyenkor a Jacobi-mátrix a $k$-adik sorát kivéve az egységmátrixé, tehát

$$\det f'(a) \ne 0 \iff \partial_k f_k(a) \ne 0.$$

$n = 2$-ben az egyszerű függvények alakja $f(x,y) = (x, g(x,y))$ vagy $f(x,y) = (h(x,y), y)$, és $\det f' = \partial_2 g$, illetve $\partial_1 h$.

### Csereoperátor

$T_{ij} : \mathbb{R}^n\to\mathbb{R}^n$ ($i < j$) az $i$-edik és $j$-edik koordinátát felcserélő leképezés. Mátrixa az egységmátrix két felcserélt sorral, tehát $\det T_{ij}' = -1$. $n = 2$-ben egyetlen ilyen van: $T_{12}(x,y) = (y,x)$.

### A tétel

Ha $2 \le n$, $f \in \mathbb{R}^n\to\mathbb{R}^n$ folytonosan differenciálható és $\det f'(a) \ne 0$, akkor van olyan $K(a) \subset D_f$ környezet, véges sok egyszerű függvény és véges sok csereoperátor, hogy ezek alkalmas kompozíciójának $K(a)$-ra vett leszűkítése épp $f|_{K(a)}$.

### A bizonyítás $n = 2$-re

Legyen $f = (g,h)$; $\det f'(a) \ne 0$ miatt a mátrix első sorának valamelyik eleme nem nulla, mondjuk $\partial_2 g(a) \ne 0$ (különben $T_{12}$-vel átrendezünk). Keressük a felbontást

$$f(x,y) = H\big(F(T_{12}(x,y))\big), \qquad F(x,y) := (G(x,y), y), \quad H(x,y) := (x, L(x,y))$$

alakban, azaz $G(y,x) = g(x,y)$ és $L(g(x,y), x) = h(x,y)$ kell. A $G$ nyilvánvaló. A $L$-hez tekintsük a $\Phi(u,v) := (g(u,v), u)$ segédfüggvényt: $\Phi \in C^1$, és

$$\det \Phi'(a) = \det\begin{bmatrix}\partial_1 g(a) & \partial_2 g(a)\\ 1 & 0\end{bmatrix} = -\partial_2 g(a) \ne 0,$$

így az [[concepts/analiii/inverzfuggveny-tetel|inverzfüggvény-tétel]] szerint $\Phi$ lokálisan invertálható; legyen $\Psi$ a lokális inverze és $L := h \circ \Psi$. Ekkor $L(g(x,y),x) = h(\Psi(\Phi(x,y))) = h(x,y)$, ami épp a kívánt azonosság.

**Az egész konstrukció az inverzfüggvény-tétel egyetlen alkalmazása** — ezért kellett azt előbb bebizonyítani.

### Mire jó

A felbontás azért értékes, mert a determináns multiplikatív: ha $f$ előáll egyszerű leképezések és cserék kompozíciójaként, akkor $\det f'$ is szorzattá esik, és minden tényező egyetlen parciális derivált (vagy $-1$). Ez a [[concepts/analiii/mertek-es-integraltranszformacio|mérték- és integráltranszformáció]] bizonyításának standard útja: a Jacobi-determinánsos helyettesítési szabály elég egyszerű leképezésekre belátni, onnan a kompozícióra öröklődik.

## Kapocs

- [[concepts/analiii/inverzfuggveny-tetel]] — a bizonyítás egyetlen eszköze.
- [[concepts/analiii/mertek-es-integraltranszformacio]] — a fő alkalmazás.
- [[concepts/analiii/jacobi-matrix]] — a determináns, ami szorzattá bomlik.
- [[concepts/analiii/jordan-mertek-linearis-transzformaltja]] — a lineáris eset, amit ez általánosít.
