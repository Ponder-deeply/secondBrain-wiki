---
tags: [concept]
sources: [12_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Bézier-görbe

A Bézier-görbe véges sok síkbeli kontrollponthoz a Bernstein-féle alappolinomokkal rendelt paraméteres síkgörbe; a Weierstrass- és Bernstein-approximációs tételek szolgáltatják az elméleti hátteret ahhoz, hogy a kontrollpontokkal minden folytonos görbe tetszőlegesen jól közelíthető.

## Tartalom

### Történet

A módszert **Paul de Casteljau** dolgozta ki 1959-ben (Citroën), tőle függetlenül **Pierre Bézier** 1962-ben (Renault) — az autóipari karosszériatervezés motiválta mindkettőt.

### Bernstein-féle alappolinomok

A Bézier-féle előállítás alapja a **Bernstein-féle alappolinomok** rendszere: $n \in \mathbb{N}$ esetén az

$$B_{k,n}(x) := \binom{n}{k} x^k (1-x)^{n-k} \qquad (x \in [0,1],\ k = 0, 1, \dots, n)$$

$n$-edfokú polinomok.

### Weierstrass- és Bernstein-approximációs tétel

**Weierstrass approximációs tétele (1885).** Ha $f \in C[a,b]$, akkor minden $\varepsilon > 0$ valós számhoz van olyan $p$ algebrai polinom, amelyre

$$|f(x) - p(x)| < \varepsilon \qquad \text{egyenlőtlenség teljesül minden } x \in [a,b] \text{ pontban.}$$

A tétel azt állítja, hogy minden $f \in C[a,b]$ függvény tetszőleges pontossággal approximálható polinomokkal az egész $[a,b]$ intervallumon (vö. Taylor-polinomokkal, amelyek csak lokálisan közelítenek jól).

**Szergej Bernstein** ezeket a polinomokat használta fel az approximációelmélet alaptételének (Weierstrass tétele) az alábbi konstruktív bizonyításához.

**Bernstein tétele (1912).** Ha $f \in C[a,b]$, akkor minden $\varepsilon > 0$ valós számhoz van olyan $n_0 \in \mathbb{N}$, hogy az

$$\left| f(x) - \sum_{k=0}^{n} f\left(\frac{k}{n}\right) B_{k,n}(x) \right| < \varepsilon$$

egyenlőtlenség teljesül $\forall x \in [0,1]$ pontban és $\forall n > n_0$ indexre.

Vagyis maguk a $\sum_{k=0}^n f(k/n) B_{k,n}(x)$ **Bernstein-polinomok** konvergálnak egyenletesen $f$-hez — nem csak absztrakt approximáló polinom létezéséről van szó, hanem az approximáció explicit, $f$ értékeiből konstruálható sorozatáról.

### A Bézier-görbe definíciója

Legyen $n \in \mathbb{N}^+$, és tegyük fel, hogy adottak a síkon a $\mathbf{P}_k = \mathbf{P}_k(x_k, y_k)$ ($k = 0, 1, \dots, n$) **kontrollpontok**. A

$$\mathcal{B}(t) := \sum_{k=0}^{n} \mathbf{P}_k \cdot B_{k,n}(t) \qquad (t \in [0,1])$$

képlettel megadott síkbeli halmazt **$n$-edfokú Bézier-görbének** nevezzük.

A Bernstein-polinomok $\sum_{k=0}^n B_{k,n}(x) = 1$ tulajdonsága (binomiális tétel) miatt $\mathcal{B}(t)$ minden $t$-re a kontrollpontok egy súlyozott átlaga (konvex kombinációja, hiszen $B_{k,n}(t) \ge 0$ is teljesül $t\in[0,1]$-en), ezért a Bézier-görbe a kontrollpontok **konvex burkán** belül fut. A $\mathcal{B}$ leképezés az [[concepts/analiii/gorbe-erintoje|egyszerű sima görbe (paraméteres görbe)]] fogalmának egy konkrét, tervezésre optimalizált realizációja: a görbe alakja a kontrollpontok mozgatásával interaktívan formálható, ami a számítógépes grafikában és a betűtípus-tervezésben teszi nélkülözhetetlenné.

## Kapocs

- [[concepts/analiii/gorbe-erintoje]] — a paraméteres síkgörbe és az érintő általános fogalma, amelynek a Bézier-görbe egy speciális, konstruktív esete
- [[concepts/analiii/sikgorbe-megadasi-modok]] — a síkgörbék megadási módjainak áttekintése, amelybe a Bézier-féle paraméteres előállítás illeszkedik
- [[concepts/analii/taylor-polinom]] — a lokális polinomapproximáció, amellyel a Weierstrass-tétel globális, egyenletes approximációja szemben áll
- [[concepts/analiii/tobbvaltozos-taylor-polinom]] — a Taylor-polinom többváltozós általánosítása, szintén lokális approximációs eszköz
