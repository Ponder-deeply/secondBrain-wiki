---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.2. iv)–v) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Nívófelület és a gradiens merőlegessége

Az $f \in \mathbb{R}^n \to \mathbb{R}$ függvény $N_c := \{x \in D_f : f(x) = c\}$ nívófelületére írt bármely görbe érintővektora merőleges a gradiensre — ez adja a gradiens geometriai jelentését.

## Tartalom

### Nívófelület

Az $f \in \mathbb{R}^n \to \mathbb{R}$ függvény **nívófelületei** a

$$N_c := \{x \in D_f : f(x) = c\} \qquad (c \in R_f)$$

halmazok: azon pontok mértani helye, ahol a függvény ugyanazt az értéket veszi fel. Két változóban ezek a szintvonalak (térkép, izobár), háromban a szintfelületek (ekvipotenciális felület).

### A merőlegességi állítás

Legyen $a \in D_f$, és tekintsünk egy $g \in \mathbb{R} \to N_{f(a)}$ **felületi görbét**, amelyre $a = g(\alpha)$ valamilyen $\alpha \in D_g$ mellett. Ha $f \in D\{a\}$ és $g \in D\{\alpha\}$, akkor

$$\langle \operatorname{grad} f(a),\, g'(\alpha)\rangle = 0.$$

**Bizonyítás egy sorban.** A görbe a nívófelületen halad, ezért $F(t) := f(g(t)) = f(a)$ **konstansfüggvény**, tehát $F'(\alpha) = 0$. Ugyanakkor a [[concepts/analiii/lancszabaly|láncszabály]] szerint

$$0 = F'(\alpha) = f'(g(\alpha))\cdot g'(\alpha) = \langle \operatorname{grad} f(a),\, g'(\alpha)\rangle.$$

### Mit mond ez

A $g'(\alpha)$ vektor a nívófelület $a$ pontbeli érintővektora. Mivel az állítás **minden** ilyen görbére igaz, a gradiens merőleges a nívófelület teljes érintőterére. Innen a szemléletes olvasat: a gradiens a **legmeredekebb növekedés iránya**, hiszen az érintősík irányaiban a függvény elsőrendben nem változik. Az [[concepts/analiii/iranymenti-derivalt|iránymenti derivált]] $\partial_e f(a) = \langle \operatorname{grad} f(a), e\rangle$ alakja ugyanezt mondja: a skalárszorzat akkor nulla, ha $e$ merőleges a gradiensre.

### Példa

Legyen $f(x,y) := x^2 + y^2$ és $g(t) := (\sin t, \cos t)$, továbbá $a := (0,1)$, $\alpha := 0$. Ekkor $\operatorname{grad} f(x,y) = (2x, 2y)$ és $g'(t) = (\cos t, -\sin t)$, tehát

$$\operatorname{grad} f(a) = (0,2), \qquad g'(0) = (1,0), \qquad \langle (0,2), (1,0)\rangle = 0.$$

Az $f$ nívóvonalai koncentrikus körök, a $g$ épp az egységkör paraméterezése — az érintő valóban merőleges a sugárirányú gradiensre.

## Kapocs

- [[concepts/analiii/lancszabaly]] — az egyetlen eszköz, amivel az állítás bizonyítható.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a gradiens koordinátás alakja.
- [[concepts/analiii/iranymenti-derivalt]] — a merőlegesség másik megfogalmazása.
- [[concepts/analiii/felteteles-szelsoertek]] — ott ugyanez a merőlegesség lesz a Lagrange-szabály geometriai tartalma.
- [[concepts/analiii/implicitfuggveny]] — a nívófelület lokálisan függvénygrafikon.
- [[concepts/analiii/fuggvenygrafikon-erintosikja]] — a merőlegesség speciális esete, amikor a nívófelület maga egy függvénygrafikon.
