---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 5. előadás"]
derivation: source
updated: 2026-09-04
---

# Taylor-formula Lagrange-féle maradéktaggal

A Taylor-polinomtól való eltérés ($f(x) - T_{a,n}f(x)$) egy pontos, jól kezelhető alakban fejezhető ki a Lagrange-maradéktag segítségével. Ez az alaptétel adja az előállítás feltételét is.

## A Taylor-formula tétele

**Tétel.** Legyen $n \in \mathbb{N}$, és t.f.h. $f \in D^{n+1}(K(a))$. Ekkor minden $x \in K(a)$ ponthoz $\exists$ olyan $a$ és $x$ közé eső $\xi$ szám, hogy

$$f(x) - T_{a,n}f(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-a)^{n+1}.$$

Egyenértékű alakban:

$$f(x) = \sum_{k=0}^n \frac{f^{(k)}(a)}{k!}(x-a)^k + \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-a)^{n+1}.$$

## Bizonyítás

A [[concepts/analii/kozeptertekek|Cauchy-féle középértéktételt]] alkalmazzuk. Legyen

$$F(x) := f(x) - T_{a,n}f(x) \qquad (x \in K(a)).$$

A $T_{a,n}f$ polinom definíciójából következik:

$$F^{(i)}(a) = f^{(i)}(a) - (T_{a,n}f)^{(i)}(a) = 0 \qquad (i = 0, 1, \ldots, n).$$

Továbbá $F^{(n+1)}(x) = f^{(n+1)}(x)$, hiszen $(T_{a,n}f)^{(n+1)} \equiv 0$ (legfeljebb $n$-edfokú polinom).

Másrészt, legyen $G(x) := (x-a)^{n+1}$ ($x \in K(a)$). Ekkor:

$$G^{(i)}(a) = 0 \quad (i = 0, 1, \ldots, n), \qquad G^{(n+1)}(x) = (n+1)!$$

Tegyük fel, hogy $x > a$ (az $x < a$ eset hasonlóan vizsgálható). Az $F$ és $G$ függvényekre az $[a, x]$ intervallumon alkalmazható a Cauchy-féle középértéktétel, következésképpen

$$\exists \xi_1 \in (a, x): \quad \frac{F'(\xi_1)}{G'(\xi_1)} = \frac{F(x) - F(a)}{G(x) - G(a)} = \frac{F(x)}{G(x)} = \frac{f(x) - T_{a,n}f(x)}{(x-a)^{n+1}}.$$

A Cauchy-tételt most az $F'$ és $G'$ függvényekre alkalmazzuk az $[a, \xi_1]$ intervallumon:

$$\exists \xi_2 \in (a, \xi_1) \subset (a, x): \quad \frac{F''(\xi_2)}{G''(\xi_2)} = \frac{F'(\xi_1) - F'(a)}{G'(\xi_1) - G'(a)} = \frac{F'(\xi_1)}{G'(\xi_1)}.$$

Ha a gondolatmenetet $n$-szer megismételjük, a $k$-dik lépésben ($k = 1, 2, \ldots, n$):

$$\exists \xi_{k+1} \in (a, \xi_k) \subset (a, x): \quad \frac{F^{(k+1)}(\xi_{k+1})}{G^{(k+1)}(\xi_{k+1})} = \frac{F^{(k)}(\xi_k)}{G^{(k)}(\xi_k)}.$$

Az $n$ egyenlőséget egybevetve:

$$\frac{f(x) - T_{a,n}f(x)}{(x-a)^{n+1}} = \frac{F(x)}{G(x)} = \frac{F'(\xi_1)}{G'(\xi_1)} = \cdots = \frac{F^{(n)}(\xi_n)}{G^{(n)}(\xi_n)} = \frac{F^{(n+1)}(\xi_{n+1})}{G^{(n+1)}(\xi_{n+1})} = \frac{f^{(n+1)}(\xi_{n+1})}{(n+1)!},$$

ahol $\xi := \xi_{n+1}$ az $a$ és $x$ közé esik. $\blacksquare$

## Elégséges feltétel az előállításra

**Tétel.** Legyen $f \in D^\infty(K(a))$, és t.f.h.

$$\exists M > 0 : \quad |f^{(n)}(x)| \leq M \qquad (\forall x \in K(a),\; \forall n \in \mathbb{N}).$$

Ekkor $f$-nek az $a$ ponthoz tartozó Taylor-sora a $K(a)$ halmazon **előállítja** az $f$ függvényt:

$$f(x) = \sum_{k=0}^{+\infty} \frac{f^{(k)}(a)}{k!}(x-a)^k \qquad (x \in K(a)).$$

*Bizonyítás.* Legyen $x \in K(a)$ tetszőleges. A maradéktagra:

$$\left|f(x) - \sum_{k=0}^n \frac{f^{(k)}(a)}{k!}(x-a)^k\right| = \frac{|f^{(n+1)}(\xi)|}{(n+1)!}|x-a|^{n+1} \leq M \cdot \frac{|x-a|^{n+1}}{(n+1)!} \to 0,$$

mivel $\lim_{n \to +\infty} \frac{|x-a|^{n+1}}{(n+1)!} = 0$. $\blacksquare$

## Kapcsolat a Taylor-sorral

A maradéktag-tétel választ ad a [[concepts/analii/taylor-sor-eloallitas|sorfejté problémájára]]:
- A **konvergencia** kérdése (hol tart a sor?) és az **előállítás** kérdése (fennáll-e $f(x) = T_af(x)$?) egymástól független.
- Ha a deriváltak **egyenletesen korlátosak** ($|f^{(n)}| \leq M$), az előállítás garantált.
- Az $e^{-1/x^2}$ ellenpélda megmutatja, hogy a deriváltak korlátozottsága nélkül az előállítás megbukhat.

## Kapocs

- [[concepts/analii/taylor-polinom]] — $T_{a,n}f$ definíciója és az interpolációs tulajdonság
- [[concepts/analii/taylor-sor-eloallitas]] — konvergencia vs. előállítás; az ellenpélda
- [[concepts/analii/nevezetes-sorfejtesek]] — az előállítás elégséges feltételén alapuló nevezetes sorok
- [[concepts/analii/kozeptertekek]] — a Cauchy-féle középértéktétel a bizonyítás gerince
- [[concepts/analii/magasabb-rendu-derivaltak]] — $f^{(n+1)}$ derivált az $n$-edik Taylor-polinom után
