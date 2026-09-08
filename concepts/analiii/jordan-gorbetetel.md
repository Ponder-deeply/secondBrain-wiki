---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Jordan-féle görbetétel

Egyszerű zárt síkgörbe a síkot pontosan két tartományra bontja: egy korlátos belsőre és egy nem korlátos külsőre, és mindkettőnek a görbe a határa. Ez adja a Jordan-tartomány fogalmát, amelyen a síkbeli integráltételeket kimondjuk.

## Tartalom

### Egyszerű zárt görbe

A $\gamma : [a,b] \to \mathbb{R}^p$ görbe *egyszerű, zárt*, ha folytonos, $\gamma(a) = \gamma(b)$, és a két végpont kivételével injektív (azaz az $[a,b)$ intervallumra megszorítva injektív). A síkbeli ($p = 2$) egyszerű zárt görbét **Jordan-görbének** nevezzük.

Az „egyszerű" tehát azt jelenti, hogy a görbe nem metszi önmagát, a „zárt" azt, hogy a végpontja megegyezik a kezdőpontjával.

### A tétel

**Tétel (Jordan-féle görbetétel).** Ha $\gamma : [a,b] \to \mathbb{R}^2$ egyszerű, zárt görbe, akkor az

$$\mathbb{R}^2 \setminus \gamma([a,b])$$

nyílt halmaz pontosan két összefüggő komponensből áll: az egyik korlátos (a görbe *belseje*), a másik nem korlátos (a görbe *külseje*), és mindkét komponens határa maga a $\gamma$.

A jegyzet bizonyítás nélkül közli. Az állítás szemléletesen nyilvánvaló, precízen viszont hírhedten nehéz — Erdős Pálnak az a mondása, hogy valaki *a Jordan-tételt tanulmányozza*, azt jelentette: az illető börtönben van.

Vegyük észre, mennyi mindent állít: hogy legalább két komponens van (a görbe elválaszt), hogy legfeljebb kettő van, és hogy a határ mindkét oldalon a teljes görbe — egyik sem következik triviálisan a másikból.

### Irányítás

A görbe **külső** pontokra vonatkozó indexe $0$, a **belső** pontokra vonatkozó index pedig vagy mindenhol $+1$, vagy mindenhol $-1$. Az első esetben a görbét *pozitív irányításúnak*, a másodikban *negatív irányításúnak* nevezzük.

Az irányítás tehát nem külön definíciót igényel, hanem a körülfordulási szám olvassa le. Ez teszi egyértelművé, mit jelent „pozitív körüljárás" egy tetszőleges, akár csúnya alakú görbén.

### Jordan-tartomány

$K \subset \mathbb{R}^2$ *Jordan-tartomány*, ha egy egyszerű, zárt, folytonos görbe belseje. A határgörbét — **mindig pozitív irányítással** — $\partial K$ jelöli.

Ez a szereplő a síkbeli integráltételek bal oldalán: a Green-tételt, a síkbeli Newton–Leibniz formulát, a Gauss–Osztrogradszkij és a Stokes-tételt olyan Jordan-tartományokra mondjuk ki, amelyeknek a határa ezen felül szakaszonként $C^1$.

## Kapocs

- [[concepts/analiii/korulfordulasi-szam]] — az index, amellyel a belső/külső és az irányítás megkülönböztethető
- [[concepts/analiii/green-tetel]] — az első integráltétel, amelyet Jordan-tartományon mondunk ki
- [[concepts/analiii/jordan-tartomany-terulete]] — a tartomány területe a határgörbén vett integrállal
- [[concepts/analiii/newton-leibniz-formula-tobbvaltozos]] — további síkbeli integráltétel ugyanezen a tartományosztályon
