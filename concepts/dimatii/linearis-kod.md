---
tags: [concept, dimatii/hibakorlatozo-es-linearis-kodok]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Lineáris kód

Véges test feletti $n$-dimenziós vektortér egy altere mint kód; a lineáris szerkezettől a kódolás mátrixszorzássá, a távolság pedig minimális súllyá válik.

## Tartalom

### Definíció

Legyen $\mathbb{F}$ véges test. Ekkor az $\mathbb{F}$ elemeiből képzett rendezett $n$-esek a komponensenkénti összeadással, valamint az $n$-es minden elemének ugyanazzal az $\mathbb{F}$-beli elemmel való szorzásával egy $\mathbb{F}$ feletti $n$-dimenziós $\mathbb{F}^n$ lineáris teret alkotnak. Ennek a térnek egy tetszőleges altere egy **lineáris kód**.

Itt $\mathbb{F}$ elemei a betűk, $\mathbb{F}^n$ elemei a szavak, az altér elemei a kódszavak.

### Jelölés

Ha az altér $k$-dimenziós, a kód távolsága $d$, a test elemeinek száma pedig $q$, akkor $[n, k, d]_q$ **kódról** beszélünk. Ha nem lényeges $d$ és $q$ értéke, akkor elhagyjuk őket a jelölésből, és $[n,k]$-t írunk.

Egy $[n,k,d]_q$ kód esetén a Singleton-korlát alakja egyszerűsödik:
$$q^k \le q^{\,n-d+1} \iff k \le n - d + 1 .$$

### Példák

1. A $(*)$ kód egy $[5,2,3]_2$ kód:
   $$(0,0) \mapsto (0,0,0,0,0),\ (0,1) \mapsto (0,1,1,1,0),\ (1,0) \mapsto (1,0,1,0,1),\ (1,1) \mapsto (1,1,0,1,1).$$
2. $\mathbb{F}_q$ felett az ismétléses kód, például a háromszori ismétlés kódja: $a \mapsto (a,a,a)$. Ez egy $[3,1,3]_q$ kód.
3. A paritásbites kód (ha páros sok egyesre egészítünk ki):
   $$(b_1, b_2, \dots, b_k) \mapsto \left(b_1, b_2, \dots, b_k, \sum_{j=1}^k b_j\right).$$
   Ez egy $[n, n-1, 2]_2$ kód.

### Súly

Az $\mathbb{F}$ ábécé feletti $n$ hosszú $u \in \mathbb{F}^n$ szó **súlya** a nem-nulla koordinátáinak a számát jelenti; jelölése $w(u)$. Egy $K$ kód súlya a nem-nulla kódszavak súlyainak minimuma:
$$w(K) = \min_{u \ne 0} w(u).$$

Egy szó súlya megegyezik a $0$-tól vett távolságával: $w(u) = d(u, (0,0,\dots,0))$.

**Állítás.** Ha $K$ lineáris kód, akkor $d(K) = w(K)$.

*Bizonyítás.* $d(u,v) = w(u-v)$, és mivel $K$ linearitása miatt $u, v \in K$ esetén $u - v \in K$, ezért a minimumok is megegyeznek. $\square$

Ez a lineáris kódok gyakorlati előnye: a kód távolságát nem kell az összes kódszópáron végignézni, elég a nem-nulla kódszavak súlyainak minimumát meghatározni.

## Kapocs

- [[concepts/dimatii/generatormatrix]] — a kódolás mátrixszorzásként
- [[concepts/dimatii/ellenorzo-matrix]] — a kód mint egy mátrix magtere, és a távolság leolvasása
- [[concepts/dimatii/szindroma-dekodolas]] — a lineáris szerkezetre épülő dekódolás
- [[concepts/dimatii/hamming-tavolsag]] — a távolság fogalma, amely itt súllyá egyszerűsödik
- [[concepts/dimatii/veges-testek]] — az alaptest, amely felett a kód él
- [[concepts/dimatii/ciklikus-kod]] — a lineáris kódok egy további szerkezettel gazdagított osztálya
