---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf, dm2gy11.pdf, dm2gy12.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
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

### Feladattípusok és módszerek: lineáris-e a kód? (2024. 11–12. sorozat)

**Döntés.** A kód pontosan akkor lineáris, ha a kódszavak halmaza altér, azaz a kódolás minden komponense az $(c_1,\dots,c_k)$ üzenet **lineáris formája** a test fölött. Gyors nemlinearitási tesztek: (i) a $0$ üzenet nem a $0$ kódszóra megy (konstans tag, pl. $c_1+c_2+c_3+1$); (ii) egy komponens szorzat vagy $\max$ ($c_2c_3$, $\max\{c_1,c_2\}$, $1-c_2c_3$); (iii) két kódszó összege nem kódszó. Lineáris: $(c_1,c_2,c_3,c_1+c_2+c_3)$ és $(c_1,c_2,c_3,\,2c_1+3c_2,\,c_1+4c_3)$ $\mathbb{F}_5$ fölött (ez $n=5$, $k=3$, $d=2$).

**Nem lineáris kód példája: permutációk.** $\mathcal C=\{(c_1,\dots,c_7)\in\mathbb{F}_7^7:\{c_1,\dots,c_7\}=\{1,\dots,7\}\}$ nem lineáris: a $\mathbf 0$ nem kódszó (nem permutáció), és két kódszó összege általában nem az: $(1,2,\dots,7)+(7,6,\dots,1)=(8,8,\dots,8)=(1,1,\dots,1)$, ami nem permutáció. A kódtávolság $2$: két különböző permutáció legalább két helyen tér el, és egy transzpozíció pontosan kettőn.

**Súly = távolság.** Lineáris kódnál $d=\min\{w(v):v\in C,\,v\neq0\}$, mert $d(u,v)=w(u-v)$ és $u-v$ is kódszó; ezért elég a kódszavak súlyait nézni.

**Tipikus hibák.** A linearitást a paritásbites alak alapján „megérezni” a próba nélkül; $\mathbb{Z}_4$-es („modulo 4”) kódolást lineáris kódnak tekinteni testtel megegyezően (a gyűrű nem test, a Singleton-féle állítások nem érvényesek); a súly–távolság azonosságot nemlineáris kódra alkalmazni.

## Kapocs

- [[concepts/dimatii/generatormatrix]] — a kódolás mátrixszorzásként
- [[concepts/dimatii/ellenorzo-matrix]] — a kód mint egy mátrix magtere, és a távolság leolvasása
- [[concepts/dimatii/szindroma-dekodolas]] — a lineáris szerkezetre épülő dekódolás
- [[concepts/dimatii/hamming-tavolsag]] — a távolság fogalma, amely itt súllyá egyszerűsödik
- [[concepts/dimatii/veges-testek]] — az alaptest, amely felett a kód él
- [[concepts/dimatii/ciklikus-kod]] — a lineáris kódok egy további szerkezettel gazdagított osztálya
