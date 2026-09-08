---
tags: [concept]
sources: ["Elsőrendű_logika_ bevezetés.pdf"]
derivation: source
updated: 2026-09-08
---

# Matematikai struktúra

A matematikai struktúra egy $\langle U, R, M, K\rangle$ halmaznégyes — univerzum, alaprelációk, alapműveletek és megjelölt elemek —, amelynek leírására az elsőrendű logika nyelve készül.

## Tartalom

### Történeti motiváció

Az 1800-as évek végén és az 1900-as évek elején a matematikai struktúrák — a halmazelmélet, valamint az aritmetika (számelmélet) — logikai vizsgálatához meg kellett teremteni mind a nulladrendű, mind az elsőrendű állítások leírására szolgáló eszközöket. Ehhez vált szükségessé a matematikai struktúrákat leíró **nyelv** definiálása. A struktúra tehát logikailag megelőzi a nyelvet: a nyelv annak leírására szolgál, ami a struktúrában van.

### Definíció

A **matematikai struktúra** egy $\langle U, R, M, K\rangle$ halmaznégyes, ahol

- $U$: nem üres halmaz, a struktúra **értelmezési tartománya** (univerzuma), amennyiben $U$ egyfajtájú elemekből áll;
- $R$: az $U$-n értelmezett $n$-változós ($n = 1, 2, \dots, k$) logikai függvények, az **alaprelációk** halmaza;
- $M$: az $U$-n értelmezett $n$-változós ($n = 1, 2, \dots, k$) matematikai függvények, az **alapműveletek** halmaza;
- $K$: az $U$ **megjelölt elemeinek** egy — esetleg üres — részhalmaza.

A **struktúra szignatúrája** a $\nu_1, \nu_2, \nu_3$ egészértékű függvényegyüttes, amely megadja az alaprelációk és az alapműveletek **aritását**, valamint $K$ elemszámát.

### Példa: elemi aritmetika

Az elemi aritmetika struktúrája az $\langle \mathbb{N}_0;\ =;\ s, +, *;\ 0 \rangle$ együttes, ahol

- az individuumváltozók ($x, y, \dots$) $\mathbb{N}_0$-t futják be,
- $=$ az $\{(x,x)\}$ igazhalmazú alapreláció,
- $s$ az egyváltozós rákövetkezés függvény,
- $+$ és $*$ az összeadás, illetve a szorzás művelete,
- $0$ a megjelölt univerzumelem: az az elem, amely nem tartozik a rákövetkezés függvény értékkészletébe.

Szignatúrája: $\nu_1(=) = 2$, $\nu_2(s) = 1$, $\nu_2(+) = 2$, $\nu_2(*) = 2$, $\nu_3 = 1$.

| $=$ | $s$ | $+$ | $*$ | $0$ |
|---|---|---|---|---|
| 2 | 1 | 2 | 2 | 1 |

Figyeljük meg, mi *nincs* a struktúrában: a $\le$ reláció nem alapreláció. Az aritmetika nyelvén csak összetett állításként definiálható:

$$x \le y \ =_{def}\ \exists z\,\big((x + z) = y\big)$$

Ez mutatja, hogy a struktúra megválasztása döntés arról, mi számít primitívnek és mi definiáltnak.

### Egyfajtájú és többfajtájú univerzum

Az aritmetika univerzuma **egyfajtájú** elemekből, a természetes számokból áll. Egy struktúra univerzuma azonban **többfajtájú** elemekből is állhat: a térgeometriában például pontok, egyenesek és síkok együtt alkotják az értelmezési tartományt. Ekkor a fajtákat is el kell nevezni — mondjuk $p, e, s$ —, az értelmezési tartomány $U_p \cup U_e \cup U_s$ lesz, a struktúra pedig $\langle U_p \cup U_e \cup U_s, R, M, K\rangle$. Ez a megkülönböztetés a nyelv, a termek és a formulák definícióján is végigvonul.

## Kapocs

- [[concepts/logika/leiro-nyelv-es-szignatura]] — a struktúrát leíró nyelv és annak ábécéje
- [[concepts/logika/nulladrendu-es-elsorendu-allitas]] — a struktúráról tett állítások két fajtája
- [[concepts/logika/elsorendu-interpretacio]] — a struktúra és a nyelv összekapcsolása a szemantikában
- [[concepts/bvszam/elsorendu-logika]] — az interpretáció mint $\langle U, I_{Pred}, I_{Func}, I_{Const}\rangle$ struktúra
