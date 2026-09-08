---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 2. előadás"]
derivation: source
updated: 2026-09-04
---

# Magasabb rendű deriváltak

Az $n$-szeri deriválhatóság rekurzív definíciója és a kapcsolódó jelölések; a Leibniz-szorzatszabály magasabb rendű deriváltakra.

## Kétszeri deriválhatóság

**Definíció.** Legyen $f \in \mathbb{R} \to \mathbb{R}$ és $a \in \operatorname{int} \mathcal{D}_f$. Az $f$ függvény **kétszer deriválható az $a$ pontban** (jelölése: $f \in D^2\{a\}$), ha

- $f$ deriválható $a$ egy $K_r(a)$ sugarú környezetében ($\exists r > 0 : f \in D(K_r(a))$), és
- az $f'$ deriváltfüggvény deriválható $a$-ban, azaz $f' \in D\{a\}$.

Legyen ekkor
$$f''(a) := (f')'(a),$$
az $f$ függvény **$a$-beli második deriváltja**.

Ha $H := \{x \in \operatorname{int} \mathcal{D}_f \mid f \in D^2\{x\}\} \neq \emptyset$, akkor a
$$H \ni x \mapsto f''(x)$$
leképezést az $f$ függvény **második deriváltfüggvényének** nevezzük; jelölése: $f''$.

## $n$-szeri deriválhatóság

Indukcióval értelmezzük az $n$-szeri deriválhatóságot: tegyük fel, hogy valamely $n \in \mathbb{N}$ esetén már értelmeztük az $(n-1)$-szeri deriválhatóságot és az $f^{(n-1)}$ deriváltfüggvényt.

**Definíció.** Legyen $f \in \mathbb{R} \to \mathbb{R}$, $a \in \operatorname{int} \mathcal{D}_f$, $n = 2, 3, \ldots$ Az $f$ függvény **$n$-szer deriválható az $a \in \operatorname{int} \mathcal{D}_f$ pontban** (jelölése: $f \in D^n\{a\}$), ha

- $\exists r > 0 : f \in D^{n-1}(K_r(a))$, és
- az $f^{(n-1)}$ függvény deriválható $a$-ban, azaz $f^{(n-1)} \in D\{a\}$.

Legyen ekkor
$$f^{(n)}(a) := \bigl(f^{(n-1)}\bigr)'(a),$$
az $f$ függvény **$a$-beli $n$-edik deriváltja**.

## Jelölések

$$f^{(1)}(a) := f'(a), \quad f^{(1)} := f',$$
$$f^{(2)}(a) := f''(a), \quad f^{(2)} := f'',$$
$$f^{(0)}(a) := f(a), \quad f^{(0)} := f.$$

Az $n$-edik deriváltfüggvényre: $f^{(n)}$.

## Akárhanyszor deriválható függvények

Ha minden $n \in \mathbb{N}$ esetén $f \in D^n\{a\}$, akkor $f$ **$a$-ban végtelen sokszor (akárhanyszor) deriválható**; jelölése: $f \in D^\infty\{a\}$.

Ha ez minden $a \in \operatorname{int} \mathcal{D}_f$ pontban igaz, akkor $f \in D^\infty$, azaz $f$ **végtelen sokszor deriválható**.

## Példák

1. $\exp \in D^\infty$ és $(e^x)^{(n)} = e^x$ ($x \in \mathbb{R}$, $n \in \mathbb{N}$).

2. $\sin, \cos \in D^\infty$ és minden $x \in \mathbb{R}$, $n \in \mathbb{N}$ esetén:
$$(\sin x)^{(2n)} = (-1)^n \sin x, \qquad (\sin x)^{(2n+1)} = (-1)^n \cos x,$$
$$(\cos x)^{(2n)} = (-1)^n \cos x, \qquad (\cos x)^{(2n+1)} = (-1)^{n+1} \sin x.$$

3. Az
$$f(x) := \begin{cases} e^{-1/x^2}, & \text{ha } x \in \mathbb{R} \setminus \{0\}, \\ 0, & \text{ha } x = 0 \end{cases}$$
függvényre $f \in D^\infty$ és $f^{(n)}(0) = 0$ ($n \in \mathbb{N}$). Ez az $e^{-1/x^2}$ ellenpélda a [[concepts/analii/taylor-sor-eloallitas|taylor-sor-eloallitas]] lapján tárgyalt konvergencia vs. előállítás problémájának kontextusában is kulcsfontosságú.

**Megjegyzés.** A magasabb rendű deriváltak kiszámolása általában nem egyszerű feladat.

## Leibniz-szorzatszabály magasabb rendekre

**Tétel.** Ha valamely $n \in \mathbb{N}$ esetén $f, g \in D^n\{a\}$, akkor

$$1^\circ \quad f + g \in D^n\{a\} \quad \text{és} \quad (f+g)^{(n)}(a) = f^{(n)}(a) + g^{(n)}(a),$$

$$2^\circ \quad f \cdot g \in D^n\{a\} \quad \text{és} \quad (f \cdot g)^{(n)}(a) = \sum_{k=0}^{n} \binom{n}{k} f^{(k)}(a)\, g^{(n-k)}(a).$$

Az utóbbi az $n$-edik rendű **Leibniz-szabály**, amely a binomiális tétellel analóg. Bizonyítás: teljes indukcióval.

## Kapocs

- [[concepts/analii/derivaltfuggveny]] — az első derivált és a [[concepts/analii/derivalasi-szabalyok|derivalasi-szabalyok]] mint kiindulópont
- [[concepts/analii/derivalasi-szabalyok]] — szorzat (Leibniz) szabály első rendű változata
- [[concepts/analii/egyoldali-derivaltak]] — az $f'$ deriváltfüggvény is vizsgálható egyoldalian
- [[concepts/analii/taylor-polinom]] — a $D^\infty$ feltétel szükséges a Taylor-sor értelmezéséhez
- [[concepts/analii/taylor-sor-eloallitas]] — $e^{-1/x^2}$ ellenpélda: $D^\infty$ nem garantál Taylor-előállítást
- [[concepts/analii/lokalis-szelsertekek]] — a második derivált alapvető eszköz a 2. rendű elégséges feltételben
