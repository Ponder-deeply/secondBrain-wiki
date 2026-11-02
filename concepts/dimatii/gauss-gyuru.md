---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-21
---

# Gauss-gyűrű (UFD) és a $\mathbb{Z}[\sqrt{-5}]$ ellenpélda

Gauss-gyűrűben (egyértelmű faktorizációs tartományban) fennáll a számelmélet alaptétele; itt a felbonthatatlan és a prím fogalma egybeesik. A $\mathbb{Z} + \mathbb{Z}\sqrt{-5}$ gyűrű egységelemes integritási tartomány, amely nem Gauss-gyűrű.

## Tartalom

### Definíció

Legyen $R$ egységelemes integritási tartomány, $U(R)$ az egységeinek halmaza. $R$ **Gauss-gyűrű** (**egyértelmű faktorizációs tartomány**, UFD), ha minden $r \in R^* \setminus U(R)$ felírható

$$r = p_1 p_2 \cdots p_n$$

alakban, ahol $n$ pozitív egész és a tényezők nem feltétlenül különböző felbonthatatlan elemek, és ha létezik egy $r = q_1 q_2 \cdots q_k$ előállítás is $k$ felbonthatatlannal, akkor $n = k$ és minden $1 \le i, j \le n$ esetén $p_i$ asszociáltja egy $q_j$-nek.

Másképp: Gauss-gyűrűben fennáll a **számelmélet alaptétele** (lásd [[concepts/dimatii/szamelmelet-alaptetele]]).

### Van-e egységelemes integritási tartomány, ami nem Gauss-gyűrű? — igen

Legyen $R = \mathbb{Z} + \mathbb{Z}\sqrt{-5}$, egységelemes integritási tartomány, egységeleme $1$.

**Az egységek.** Ha $c = a + b\sqrt{-5} \in R$, akkor $|c|^2 = a^2 + 5b^2 \equiv 0, \pm 1 \pmod 5$, és $d \mid c \Rightarrow |d|^2 \mid |c|^2$. Az $1$ osztóit keresve $|1|^2 = 1$ miatt $a = \pm 1$, $b = 0$; az egységek tehát $\pm 1$.

**A $9$ két felbontása.**

$$9 = (3 + 0\sqrt{-5})(3 + 0\sqrt{-5}) = (2 + \sqrt{-5})(2 - \sqrt{-5}).$$

- A $3$ irreducibilis: egy nemtriviális $d$ osztóra $|d|^2 \mid 9$ és $|d|^2 \equiv 0, \pm 1 \pmod 5$ kellene; a nemtriviális eset $|d|^2 = 3$ (az $1$ egységet, a $9$ egységszeres komplementert adna), de $3 \not\equiv 0, \pm 1 \pmod 5$. Nincs ilyen $d$.
- $2 + \sqrt{-5}$ és $2 - \sqrt{-5}$ is irreducibilis, mert hossznégyzetük is $4 + 5 = 9$, és a $3$-ra végzett érvelés szó szerint ismétlődik.

A két felbontás tényezői nem asszociáltak (az egységek csak $\pm 1$), tehát $R$ **nem Gauss-gyűrű**. A hierarchiában a Gauss-gyűrű az egységelemes integritási tartomány „alatt” van.

### Felbonthatatlan és prím integritási tartományban

**Tétel.** Tetszőleges $R$ egységelemes integritási tartományban, $a \in R^* \setminus U(R)$ esetén: ha $a$ **prím**, akkor $a$ **felbonthatatlan**.

*Bizonyítás.* Legyen $a$ prím és $a = bc$. Ekkor $1 \cdot a = bc$, így $a \mid bc$, és $a \mid b$ vagy $a \mid c$. Mondjuk $a \mid b$: ekkor $1 = \frac{b}{a} \cdot c$ (illetve $1 = b \cdot \frac{c}{a}$), ahol az első tényező $R$-beli, tehát $c$ (illetve $b$) egység. $\square$

**A megfordítás nem igaz általában.** Példa $R = \mathbb{Z} + \mathbb{Z}\sqrt{-5}$-ben: a $2$ irreducibilis. Ha $2 = (a + b\sqrt{-5})(e + g\sqrt{-5})$, konjugáltakkal szorozva $4 = (a^2 + 5b^2)(e^2 + 5g^2)$, így $a^2 + 5b^2 \mid 4$, vagyis $a^2 + 5b^2 \in \{1, 2, 4\}$; ebből $b = 0$, $a = \pm 1, \pm 2$, tehát az egyik tényező $\pm 1$. De $2 \mid (1 + \sqrt{-5})(1 - \sqrt{-5}) = 6$, miközben $2 \nmid 1 \pm \sqrt{-5}$, tehát a $2$ **nem prím**.

### Felbonthatatlan és prím Gauss-gyűrűben

**Tétel.** Gauss-gyűrűben $a \in R^* \setminus U(R)$ esetén $a$ prím $\iff$ $a$ felbonthatatlan.

*Bizonyítás.* ($\Rightarrow$) az előző tétel. ($\Leftarrow$) Legyen $a$ irreducibilis és $a \mid pq$, azaz $pq = ar$. A felbontások egyértelműsége miatt $p = p_1 \cdots p_k$, $q = q_1 \cdots q_l$, $r = r_1 \cdots r_t$ felbontásokkal $p_1 \cdots p_k q_1 \cdots q_l = a \cdot r_1 \cdots r_t$; az $a$ asszociált valamely $p_i$-vel vagy $q_j$-vel (különben nem lenne egyértelmű a felbontás), ezért $a \mid p$ vagy $a \mid q$. $\square$

(A diák kérdése: mely struktúrákban esik egybe a prím és a felbonthatatlan — a válasz: Gauss-gyűrűkben.)

### $\mathbb{Z}[x]$: Gauss-gyűrű, de nem euklideszi, nem főideálgyűrű (Farkas-diák)

Ha $R$ Gauss-gyűrű, akkor $R[x]$ is az (Gauss-tétel 2. része; lásd [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]]): $\mathbb{Z}$ euklideszi $\Rightarrow$ $\mathbb{Z}$ Gauss-gyűrű $\Rightarrow$ $\mathbb{Z}[x]$ Gauss-gyűrű.

- **$\mathbb{Z}[x]$ nem euklideszi gyűrű**, különben $(x, 2) = 1$ miatt lenne $1 = 2u + xv$ alakú előállítás ($u, v \in \mathbb{Z}[x]$), ami lehetetlen: a jobb oldal konstans tagja páros.
- **$\mathbb{Z}[x]$ nem főideálgyűrű**: a $J = \{f \in \mathbb{Z}[x] \mid f(0) \equiv 0 \pmod 2\} = \langle 2, x \rangle$ ideál nem főideál.

Ez mutatja, hogy az „euklideszi $\Rightarrow$ főideálgyűrű $\Rightarrow$ Gauss-gyűrű" lánc megfordítása hamis.

## Kapocs

- [[concepts/dimatii/felbonthatatlan-es-prim]] — a két definíció és a $\mathbb{Z}$-beli egybeesés
- [[concepts/dimatii/egyseg-es-asszocialt]] — az asszociáltság, amely nélkül az egyértelműség nem fogalmazható
- [[concepts/dimatii/szamelmelet-alaptetele]] — $\mathbb{Z}$-ben ez a tétel
- [[concepts/dimatii/integritasi-tartomany]] — az a keret, amelynél a Gauss-gyűrű szűkebb
- [[concepts/dimatii/euklideszi-gyuru]] — a Gauss-egészek euklideszi gyűrű példája
- [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]] — a Gauss-tétel: $R$ Gauss-gyűrű $\Rightarrow$ $R[x]$ is
