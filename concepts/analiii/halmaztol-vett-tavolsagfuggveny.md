---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.1. viii)–ix) megjegyzések"]
derivation: source
updated: 2026-09-07
---

# Halmaztól vett távolságfüggvény

Egy nemüres $A$ halmaztól mért $f(x) = \inf\{\rho(x,a) : a \in A\}$ távolság $1$-Lipschitz, tehát egyenletesen folytonos, és pontosan az $A$ lezártján tűnik el. Az approximációelmélet alapkérdése, hogy az infimum mikor minimum.

## Tartalom

### A függvény és az approximációs kérdés

Legyen $(X,\rho)$ metrikus tér, $\emptyset \ne A \subset X$, és

$$f(x) := \inf\{\rho(x,a) : a \in A\} \qquad (x \in X).$$

**Az approximációelmélet alapkérdése:** adott $x \in X$ mellett írható-e „$\inf$" helyett „$\min$", azaz van-e olyan $a^* \in A$, amelyre $f(x) = \rho(x,a^*)$? Az ilyen $a^*$ elemet **extremális elemnek** nevezzük. (Kompakt $A$ esetén az [[concepts/analiii/weierstrass-tetel-kompakt-halmazon|Weierstrass-tétel]] garantálja a létezését.)

### Egyenletes folytonosság

**Állítás.** Az $f$ függvény $1$-Lipschitz, tehát egyenletesen folytonos.

*Bizonyítás.* Bármely $x,y \in X$ és $a \in A$ esetén

$$f(x) \le \rho(x,a) \le \rho(x,y) + \rho(y,a),$$

és $a$-ban infimumot véve $f(x) \le \rho(x,y) + f(y)$, azaz $f(x) - f(y) \le \rho(x,y)$. Az $x$ és $y$ szerepét felcserélve

$$|f(x) - f(y)| \le \rho(x,y) \qquad (x,y \in X). \qquad \blacksquare$$

### A zérushalmaz a lezárt

**Állítás.** $\{x \in X : f(x) = 0\} = \overline{A}$.

*Bizonyítás.* ($\subset$) Ha $f(x) = 0$, akkor minden $n$-hez van olyan $a_n \in A$, hogy $0 \le \rho(x,a_n) < 1/n$, tehát $a_n \to x$. Ha $x \notin A$, akkor $x \in A'$, tehát $x \in \overline{A}$.

($\supset$) $A \subset \{f = 0\}$ nyilvánvaló. Ha $z \in \overline{A}\setminus A$, akkor $z \in A'$, így alkalmas $(a_n) : \mathbb{N}\to A$ sorozattal $z = \lim(a_n)$; ekkor minden $\varepsilon > 0$-hoz van olyan $a_n$, hogy $\rho(z,a_n) < \varepsilon$, tehát $f(z) < \varepsilon$, azaz $f(z) = 0$. $\blacksquare$

Ez egyben mutatja, hogy $\overline{A}$ egy folytonos függvény zérushalmazaként zárt, és hogy zárt $A$ esetén $f(x) = 0 \iff x \in A$ — a távolságfüggvény tehát az $A$ halmaz „karakterisztikus függvényének" folytonos helyettesítője.

## Kapocs

- [[concepts/analiii/egyenletes-folytonossag-metrikus-terben]] — a Lipschitz-tulajdonságból következő egyenletes folytonosság
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a lezárt és a torlódási pont fogalma
- [[concepts/analiii/kompakt-halmazok]] — kompakt és zárt halmaz távolsága; az extremális elem létezése
- [[concepts/analiii/folytonossag-metrikus-terben]] — a zérushalmaz zártsága folytonos függvényre
