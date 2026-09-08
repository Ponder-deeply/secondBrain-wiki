---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 5. előadás"]
derivation: source
updated: 2026-09-04
---

# Taylor-polinom és Taylor-sor

A $D^\infty$ osztályba tartozó függvények tetszőleges rendig deriválhatók, ezért egy adott $a$ ponthoz hozzárendelhetjük a függvény „legjobb polinomiális közelítőjét" — a Taylor-polinomot — valamint a teljes hatványsort — a Taylor-sort.

## Motiváció

Hatványsorok összegfüggvényének értékét nem tudjuk pontosan kiszámítani, de közelítő értékét elvben tetszőleges pontossággal meghatározhatjuk véges sok alapművelet alkalmazásával. Kérdés: egy adott (bonyolult) függvény előállítható-e konvergens hatványsor összegeként, és ha igen, hogyan határozhatók meg az együtthatók?

A kiindulópont a hatványsorok tagonkénti deriválhatóságának tétele:

**Tétel.** Ha $\sum_{n=0}^{+\infty} \alpha_n (x-a)^n$ hatványsor $R > 0$ konvergenciasugara pozitív, és összegfüggvénye $f$, akkor minden $x \in K_R(a)$ pontban $f \in D\{x\}$, és

$$f'(x) = \sum_{n=1}^{+\infty} n\alpha_n (x-a)^{n-1} \qquad (\forall x \in K_R(a)).$$

Teljes indukcióval: minden $n \in \mathbb{N}^+$ esetén $f \in D^\infty\{x\}$ és

$$f^{(n)}(x) = \sum_{k=n}^{+\infty} k(k-1)\cdots(k-n+1)\,\alpha_k(x-a)^{k-n}.$$

Az $x = a$ helyettesítéssel:

$$\boxed{\alpha_n = \frac{f^{(n)}(a)}{n!}} \qquad (n \in \mathbb{N}).$$

Ez azt jelenti, hogy egy konvergens hatványsor együtthatói egyértelműen meghatározottak az összegfüggvény deriváltjaiból.

## Definíció

Legyen $f \in D^\infty\{a\}$. Az $f$ függvény $a \in \operatorname{int} \mathcal{D}_f$ ponthoz tartozó **Taylor-sora**:

$$T_a f(x) := \sum_{k=0}^{+\infty} \frac{f^{(k)}(a)}{k!}(x-a)^k \qquad (x \in \mathbb{R}).$$

Az $n$-edik **Taylor-polinomja** ($n$-edik részletösszege):

$$T_{a,n} f(x) := \sum_{k=0}^{n} \frac{f^{(k)}(a)}{k!}(x-a)^k \qquad (x \in \mathbb{R}).$$

Az $a = 0$ ponthoz tartozó Taylor-sort az $f$ függvény **Maclaurin-sorának** nevezzük.

## Az egyediség tétele és az interpolációs tulajdonság

**4° megjegyzés.** A Taylor-polinom explicit alakja:

$$T_{a,n}f(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \cdots + \frac{f^{(n)}(a)}{n!}(x-a)^n.$$

A $T_{a,n}f$ **interpolálja** $f$-et $a$-ban $n$-edik rendig: teljesülnek az

$$(*)\quad T_{a,n}f(a) = f(a),\quad (T_{a,n}f)'(a) = f'(a),\quad \ldots,\quad (T_{a,n}f)^{(n)}(a) = f^{(n)}(a)$$

feltételek.

**Egyediség:** $T_{a,n}f$ az **egyetlen** legfeljebb $n$-edfokú polinom, amely az $(*)$ interpolációs feltételeket teljesíti.

*Bizonyítás.* Legyen $P$ egy másik ilyen polinom, és $Q := P - T_{a,n}f$. Ekkor $Q(a) = Q'(a) = \cdots = Q^{(n)}(a) = 0$, tehát $a$-nak legalább $(n+1)$-szeres gyöke $Q$-ban, így $Q \equiv 0$, vagyis $P \equiv T_{a,n}f$. $\blacksquare$

**1° megjegyzés** (konvergens sor = Taylor-sor). Ha $f$ előállítható konvergens hatványsor összegeként, akkor az a sor szükségképpen $f$ Taylor-sora.

## Kapcsolat más fogalmakkal

- [[concepts/analii/linearkozelites]] — az $n=1$ eset a lineáris közelítés: $T_{a,1}f(x) = f(a) + f'(a)(x-a)$
- [[concepts/analii/taylor-sor-eloallitas]] — mikor állítja elő a Taylor-sor ténylegesen $f$-et?
- [[concepts/analii/taylor-formula-maradektag]] — a Lagrange-maradéktag méri az $n$-edik Taylor-polinom és $f$ eltérését
- [[concepts/analii/nevezetes-sorfejtesek]] — konkrét függvények Taylor-sorai bizonyítással
- [[concepts/analii/magasabb-rendu-derivaltak]] — $f \in D^\infty$ feltétel és az $n$-edik derivált fogalma
- [[concepts/analii/derivalasi-szabalyok]] — hatványsor tagonkénti deriválásának alapja

## Kapocs

- [[concepts/analii/taylor-sor-eloallitas]] — a konvergencia és az előállítás kérdésének szétválasztása
- [[concepts/analii/taylor-formula-maradektag]] — Lagrange-maradéktag a hibabecsléshez
- [[concepts/analii/nevezetes-sorfejtesek]] — $e^x$, $\ln(1+x)$, $\arctan x$, binomiális sor, $\arcsin x$
- [[concepts/analii/linearkozelites]] — speciális eset: elsőrendű Taylor-közelítés
- [[concepts/analii/magasabb-rendu-derivaltak]] — $D^\infty$ osztály és Leibniz-szorzatszabály
