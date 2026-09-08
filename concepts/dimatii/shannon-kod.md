---
tags: [concept]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# Shannon-kód

Prefix kód, amelynek szóhosszait közvetlenül a betűk valószínűségeiből számoljuk; átlagos szóhossza az entrópiánál kevesebb mint 1-gyel nagyobb.

## Tartalom

### A konstrukció elve

A betűket relatív gyakoriságuk szerint csökkenő sorrendbe rendezzük, majd minden $a_j$ betűhöz azt az $\ell_j$ szóhosszat választjuk, amelyre
$$r^{-\ell_j} \le p_j < r^{-\ell_j + 1} .$$
A McMillan-egyenlőtlenség megfordítása miatt ezekkel a hosszakkal létezik prefix kód; a kódszavakat sorban, a kódábécé feletti számrendszerben eggyel növelve, majd szükség esetén jobbról 0-val a megfelelő hosszra kiegészítve kapjuk.

### Példa

Legyen a kódábécé $\{0,1,2\}$, a gyakoriságok pedig
$$f: 0{,}31;\quad a: 0{,}17;\quad h: 0{,}17;\quad c: 0{,}13;\quad j: 0{,}09;\quad i: 0{,}06;\quad b, d, g: 0{,}02;\quad e: 0{,}01 .$$

A szóhosszakat a fenti feltétel adja:
- $\frac{1}{9} \le 0{,}31;\ 0{,}17;\ 0{,}13 < \frac{1}{3}$, ezért $f$, $a$, $h$ és $c$ kódhossza 2;
- $\frac{1}{27} \le 0{,}09;\ 0{,}06 < \frac{1}{9}$, ezért $j$ és $i$ kódhossza 3;
- $\frac{1}{81} \le 0{,}02 < \frac{1}{27}$, ezért $b$, $d$ és $g$ kódhossza 4;
- $\frac{1}{243} \le 0{,}01 < \frac{1}{81}$, ezért $e$ kódhossza 5.

Az $f$ kódja 00, az $a$ kódja 01, a $h$ kódja 02, és ez utóbbihoz 1-et adva hármas alapú számrendszerben kapjuk a $c$ kódját, 10-et. Ehhez 1-et adva 11-et kapnánk, de $j$ kódjának hossza 3, ezért ezt még ki kell egészíteni jobbról egy 0-val, tehát $j$ kódja 110. Hasonlóan folytatva a teljes kód:
$$f: 00,\quad a: 01,\quad h: 02,\quad c: 10,\quad j: 110,\quad i: 111,$$
$$b: 1120,\quad d: 1121,\quad g: 1122,\quad e: 12000 .$$

Átlagos szóhossz: $2{,}3 < 1{,}73 + 1$, ahogy a Shannon-tétel megköveteli. Ugyanezen az eloszláson a Huffman-kód $1{,}79$-et ér el, tehát a Shannon-kód nem optimális.

## Kapocs

- [[concepts/dimatii/shannon-tetel-zajmentes-csatornara]] — a tétel, amelynek bizonyítása ezt a konstrukciót adja
- [[concepts/dimatii/mcmillan-egyenlotlenseg]] — a megfordítás garantálja, hogy a választott hosszakhoz van prefix kód
- [[concepts/dimatii/huffman-kod]] — az optimális alternatíva, amellyel a példa összeveti
- [[concepts/dimatii/kodfa]] — a kapott kód szemléltetése
