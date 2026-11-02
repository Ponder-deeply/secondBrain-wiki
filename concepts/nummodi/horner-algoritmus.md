---
tags: [concept]
sources: [NM1_ea13.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Horner-algoritmus

Polinom helyettesítési értékének kiszámítása átzárójelezéssel: $n$ szorzás és $n$ összeadás elég egy $n$-edfokú polinomhoz. A közben kapott együtthatók a $P(x) = P(\xi) + (x - \xi)P_1(x)$ felbontást adják, ezért az algoritmust megismételve a deriváltak értékei, sőt a $\xi$ körüli Taylor-polinom is kiolvasható.

## Tartalom

### Levezetés — átzárójelezés

$$\begin{aligned}
P(x) &= a_nx^n + a_{n-1}x^{n-1} + \dots + a_1x + a_0\\
&= \underbrace{(a_nx^{n-1} + a_{n-1}x^{n-2} + \dots + a_2x + a_1)}_{a_1^{(1)}}\cdot x + a_0\\
&= \bigl(\underbrace{(a_nx^{n-2} + \dots + a_2)}_{a_2^{(1)}}\cdot x + a_1\bigr)\cdot x + a_0\\
&= \dots = \bigl(\dots(\underbrace{a_nx + a_{n-1}}_{a_{n-1}^{(1)}})\cdot x + \dots\bigr)\cdot x + a_0.
\end{aligned}$$

A legbelső zárójeltől kifelé haladva minden lépés egy szorzás $x$-szel és egy összeadás.

**Definíció — Horner-algoritmus.** $P$ értéke a $\xi$ helyen:

1. $a_n^{(1)} := a_n$,
2. $a_k^{(1)} := a_k + \xi\cdot a_{k+1}^{(1)}$ $(k = n-1, \dots, 1, 0)$;

ekkor $P(\xi) = a_0^{(1)}$. (Más néven Horner-módszer, Horner-elrendezés.)

**Állítás — műveletigény.** $n$-edfokú polinom egy helyen vett értéke $n$ szorzással és $n$ összeadással, azaz $\mathcal{O}(n)$ művelettel számolható. (Biz.: a 2. lépés $n$-szer fut, egy szorzással és egy összeadással.)

### Előnyös tulajdonságok

- **Olcsó:** $2n$ művelet; a hatványok külön kiszámolása ($x^k$ újraszámolással) ennél sokkal többe kerülne.
- **Nincs hatványozás**, nincs szükség $x^k$ tárolására; egy ciklus, kevés tár.
- **Melléktermékként** a $P_1(x) = P(x) - P(\xi)$ osztva $(x - \xi)$-vel hányados együtthatóit is adja — ezzel folytatva deriváltakat és Taylor-együtthatókat kapunk.
- Kézzel táblázatban jól számolható.

### Táblázatos számolás

$$\begin{array}{c|cccccc}
 & a_n & a_{n-1} & \dots & a_k & \dots & a_0\\
\xi & & \xi a_n^{(1)} & \dots & \xi a_{k+1}^{(1)} & \dots & \xi a_1^{(1)}\\ \hline
 & a_n^{(1)} & a_{n-1}^{(1)} & \dots & a_k^{(1)} & \dots & a_0^{(1)} = P(\xi)
\end{array}$$

**Példa.** $P(x) = x^5 + 6x^4 - x^3 + 3x^2 - 15x - 7$, $\xi = 2$:

$$\begin{array}{c|cccccc}
 & 1 & 6 & -1 & 3 & -15 & -7\\
2 & & 2 & 16 & 30 & 66 & 102\\ \hline
 & 1 & 8 & 15 & 33 & 51 & 95
\end{array}$$

$P(2) = 95$, összesen 10 művelettel.

### Horner-algoritmus és a derivált

**Állítás.** A $P$ polinom felírható

$$P(x) = a_0^{(1)} + (x - \xi)\cdot\underbrace{\bigl(a_1^{(1)} + a_2^{(1)}x + \dots + a_n^{(1)}x^{n-1}\bigr)}_{P_1(x)}$$

alakban, ahol $a_i^{(1)}$ a Horner-algoritmus értékei. Továbbá $P'(\xi) = P_1(\xi) = a_1^{(2)}$.

**Biz.**

1. **Együttható-összehasonlítás.** $x^n$ együtthatója a két oldalon $a_n = a_n^{(1)}$. ✓ Az $x^k$ együtthatója ($k = 0, \dots, n-1$) bal oldalon $a_k$, a jobb oldalon a kifejtés után $a_k^{(1)} - \xi a_{k+1}^{(1)}$ (az $x\cdot a_k^{(1)}x^{k-1}$ és a $-\xi\cdot a_{k+1}^{(1)}x^k$ tagokból). A Horner-algoritmus szerint $a_k^{(1)} = a_k + \xi a_{k+1}^{(1)}$, tehát a kettő egyenlő. ✓
2. **Derivált.** A fenti alakot deriválva (összeg és szorzat deriváltja):
   $$P'(x) = 1\cdot P_1(x) + (x - \xi)P_1'(x) \implies P'(\xi) = P_1(\xi).$$
3. $P_1(\xi)$ ugyanúgy, Horner-algoritmussal számolható $P_1$ együtthatóiból ($a_n^{(1)}, \dots, a_1^{(1)}$):
   $a_n^{(2)} := a_n^{(1)}$, $a_k^{(2)} := a_k^{(1)} + \xi a_{k+1}^{(2)}$ ($k = n-1, \dots, 1$), és $P_1(\xi) = P'(\xi) = a_1^{(2)}$. $\square$

Táblázatban: a második sor alá egy újabb Horner-sort írunk, amely eggyel rövidebb.

### Magasabb rendű deriváltak és a Taylor-polinom

**Állítás** (biz. indukcióval, nem kell).

$$P(x) = a_0^{(1)} + a_1^{(2)}(x - \xi) + a_2^{(3)}(x - \xi)^2 + \dots + a_n^{(n+1)}(x - \xi)^n,$$

ahol az $a_i^{(j+1)}$ értékeket az ismételt Horner-algoritmus adja, és

$$\frac{P^{(j)}(\xi)}{j!} = P_j(\xi) = a_j^{(j+1)}, \qquad P_j(x) = a_j^{(j)} + \dots + a_n^{(j)}x^{n-j}.$$

Ha a táblázatot addig folytatjuk, míg egyetlen elem marad, az „átlóban” a $\xi$ körüli Taylor-polinom együtthatói állnak.

**Példa.** $P(x) = x^4 - 2x^3 + 3x^2 - x + 1$, $\xi = 1$:

$$\begin{array}{c|ccccc}
 & 1 & -2 & 3 & -1 & 1\\ \hline
1 & 1 & -1 & 2 & 1 & \mathbf{2} = P(1)\\
1 & 1 & 0 & 2 & \mathbf{3} = P'(1) & \\
1 & 1 & 1 & \mathbf{3} = \tfrac{P''(1)}{2} & & \\
1 & 1 & \mathbf{2} = \tfrac{P'''(1)}{3!} & & & \\
1 & \mathbf{1} & & & &
\end{array}$$

Tehát $P(x) = (x-1)^4 + 2(x-1)^3 + 3(x-1)^2 + 3(x-1) + 2$ — az $1$ körüli Taylor-polinom.

### Vizsgán (28. tétel, b))

A Horner-algoritmus levezetése átzárójelezéssel; műveletigény és előnyök; alkalmazás a deriváltak értékére ($P = a_0^{(1)} + (x-\xi)P_1$ bizonyítása, $P'(\xi) = P_1(\xi)$). Az a) rész a [[concepts/nummodi/polinom-gyokbecsles]].

## Kapocs

- [[concepts/nummodi/polinom-gyokbecsles]] — a 28. tétel a) része
- [[concepts/nummodi/newton-modszer]] — polinom gyökkeresésénél $P(x_k)$ és $P'(x_k)$ egyszerre jön két Horner-sorból
- [[concepts/dimatii/horner-elrendezes]] — ugyanez az elrendezés polinomosztásként (diszkrét matematika)
- [[concepts/analii/taylor-polinom]] — az ismételt Horner-algoritmus a Taylor-együtthatókat adja
