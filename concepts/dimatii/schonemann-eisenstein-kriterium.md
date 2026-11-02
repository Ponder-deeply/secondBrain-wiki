---
tags: [concept]
sources: [DimatIIEa07.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy11_Polinomok.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-21
---

# Schönemann–Eisenstein-kritérium

Elégséges feltétel egész együtthatós primitív polinom $\mathbb{Z}$ fölötti felbonthatatlanságára: ha egy $p$ prím a főegyüttható kivételével minden együtthatót oszt, de $p^2$ nem osztja a konstans tagot, akkor a polinom irreducibilis.

## Tartalom

### A tétel

**Tétel (Schönemann–Eisenstein).** Legyen

$$f(x) = f_nx^n + f_{n-1}x^{n-1} + \dots + f_1x + f_0 \in \mathbb{Z}[x], \quad f_n \neq 0$$

legalább elsőfokú primitív polinom. Ha található olyan $p \in \mathbb{Z}$ prím, melyre

- $p \nmid f_n$,
- $p \mid f_j$, ha $0 \le j < n$,
- $p^2 \nmid f_0$,

akkor $f$ felbonthatatlan $\mathbb{Z}$ fölött.

### Bizonyítás

Tegyük fel, hogy $f = gh$. Mivel $p$ nem osztja $f$ főegyütthatóját, ezért sem $g$, sem $h$ főegyütthatóját nem osztja. Legyen $m$ a legkisebb olyan index, amelyre $p \nmid g_m$, és $o$ a legkisebb olyan index, amelyre $p \nmid h_o$. Ha $k = m + o$, akkor

$$p \nmid f_k = \sum_{i+j=k} g_ih_j,$$

mivel $p$ osztja az összeg minden tagját, kivéve azt, amelyben $i = m$ és $j = o$. Így $k = m + o \ge n$, ami csak $m = \deg(g)$ és $o = \deg(h)$ mellett lehetséges. Ekkor viszont $p \mid g_0$ és $p \mid h_0$, tehát $p^2 \mid g_0h_0 = f_0$ — hacsak nem $\deg(g) = 0$ vagy $\deg(h) = 0$, azaz valamelyik tényező egység. $\square$

### Megjegyzések

- A feltételben $f_n$ és $f_0$ **szerepe felcserélhető**: a tétel ugyanúgy alkalmazható, ha $p \nmid f_0$, $p \mid f_j$ minden $0 < j \le n$ esetén, és $p^2 \nmid f_n$.
- A tétel **nem használható test fölötti polinom** irreducibilitásának bizonyítására, mert testben nem léteznek prímek: minden nem-nulla elem egység.
- A $\mathbb{Q}$ fölötti irreducibilitás a Gauss-tétel következményén keresztül adódik: primitív $f \in \mathbb{Z}[x]$ pontosan akkor felbontható $\mathbb{Z}$ fölött, amikor $\mathbb{Q}$ fölött.

### Általános Gauss-gyűrűs alak (Farkas-diák)

**Tétel (Schönemann–Eisenstein).** Ha az $R$ Gauss-gyűrű fölötti legalább elsőfokú $f$ primitív polinomhoz van olyan $p \in R$ prímelem, amely nem osztója a főegyütthatónak, de osztója minden más együtthatónak, $p^2$ viszont nem osztója a konstans tagnak, akkor $f$ irreducibilis. Hasonlóan (a szerepek felcserélve): ha az $R$ Gauss-gyűrű fölötti legalább elsőfokú $f$ polinomhoz van olyan $p \in R$ prímelem, amely nem osztója a konstans tagnak, de osztója minden más együtthatónak, $p^2$ viszont nem osztója a főegyütthatónak, akkor $f$ irreducibilis.

**Speciális eset.** $f = x^n + p$, ahol $p$ prím és $n$ pozitív egész: $f$ irreducibilis $R$ és hányadosteste fölött is.

### Feladattípusok és módszerek (2020. 11. feladatsor)

**Prím keresése.** A kritérium primet kér, amely az összes együtthatót osztja a főegyüttható kivételével, $p^2$ pedig nem osztja az állandó tagot. Jelöltek: az állandó tag prímosztói (és a közös osztók). Példák ($\mathbb{Z}[x]$-ben irreducibilis):

- $x^4-8x^3+12x^2-6x+2$: $p=2$ ($2\mid 8,12,6,2$; $4\nmid 2$).
- $x^5-12x^3+36x-12$: $p=3$ ($3\mid 12,36,12$, a hiányzó $x^4$, $x^2$ együtthatói $0$; $9\nmid 12$).
- $3x^5+2x^3-12x^2+10x+14$: $p=2$ ($2\nmid 3$; $2\mid 0,2,12,10,14$; $4\nmid 14$), tehát irreducibilis $\mathbb{Z}$ és $\mathbb{Q}$ fölött — a „bontsuk fel” feladat válasza: nincs felbontás.
- $20x^4+26x^3+65x^2+91$: $p=13$ ($13\nmid 20$; $13\mid 26,65,0,91$; $169\nmid 91$), szintén irreducibilis.

**Eltolás.** Ha közvetlenül nem működik, $f(x)$ helyett $f(x+a)$-t vizsgáljuk (az irreducibilitás eltolásra invariáns). $x^4-x^3+2x+1$: $f(x+1)=x^4+3x^3+3x^2+3x+3$, és erre $p=3$ Eisenstein-feltétele teljesül ($3\mid 3,3,3,3$, $9\nmid 3$), tehát $f$ irreducibilis.

**Tipikus hibák.** A $p^2\nmid f_0$ feltétel ellenőrzésének kihagyása ($x^2+4$, $p=2$: $4\mid 4$ nem jó); nem primitív polinomon alkalmazni (a tartalmat előbb ki kell emelni); azt hinni, hogy a kritérium *megfordítható* — ha nincs megfelelő prím, a polinom még lehet irreducibilis.

## Kapocs

- [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]] — a primitivitás fogalma és a $\mathbb{Z}$–$\mathbb{Q}$ átvezetés
- [[concepts/dimatii/irreducibilis-polinom]] — a bizonyítandó tulajdonság
- [[concepts/dimatii/racionalis-gyokteszt]] — másik, elemibb irreducibilitási eszköz $\mathbb{Z}[x]$-ben
- [[concepts/dimatii/gauss-gyuru]] — az általános $R$ Gauss-gyűrű, amelyben a tétel is érvényes
