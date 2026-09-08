---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 6. előadás"]
derivation: source
updated: 2026-09-04
---

# Primitív függvény

A deriválás „megfordítása": adott $f$ függvényhez olyan $F$ függvényt keresünk, amelynek deriváltja éppen $f$.

## Definíció

Legyen $I \subset \mathbb{R}$ nyílt intervallum és $f : I \to \mathbb{R}$. Az $F : I \to \mathbb{R}$ függvényt $f$ **primitív függvényének** nevezzük, ha

$$F \in D(I) \quad \text{és} \quad F'(x) = f(x) \quad (\forall x \in I).$$

## Mikor létezik primitív függvény?

Két alapkérdés merül fel:

1. Milyen $f$ függvénynek **van** primitív függvénye?
2. Ha van, hogyan lehet azt meghatározni?

### Elégséges feltétel

Ha $f$ **folytonos** az $I$ intervallumon, akkor van primitív függvénye. (Ez a határozott integrálból következik — Newton–Leibniz-tétel.)

### Szükséges feltétel: Darboux-tétel

Ha $f$-nek van primitív függvénye, akkor $f$ **Darboux-tulajdonságú** az $I$ intervallumon: tetszőleges $a, b \in I$, $a < b$ és bármely $h'(a)$ és $h'(b)$ közé eső $c$ esetén van olyan $\xi \in [a,b]$, hogy $h'(\xi) = c$.

**Bizonyítás.** Tekintsük a $\varphi(x) := h(x) - cx$ ($x \in I$) függvényt. Ekkor $\varphi \in D(I)$ és $\varphi'(x) = h'(x) - c$. Mivel $\varphi \in C[a,b]$, a Weierstrass-tételnél fogva vannak abszolút szélsőértékei. Mivel $\varphi'(a) = h'(a) - c < 0$ és $\varphi'(b) = h'(b) - c > 0$, ezért $\varphi$ az $a$-ban szigorúan fogy, $b$-ben pedig szigorúan nő — tehát ezek egyike sem lehet abszolút minimumhely. Az abszolút minimum egy belső pontban, $\xi \in (a,b)$-ben van, ahol $\varphi'(\xi) = h'(\xi) - c = 0$, azaz $h'(\xi) = c$. $\blacksquare$

**Megjegyzés.** A folytonosság elégséges, a Darboux-tulajdonság szükséges feltétel. Jelenleg nem ismert olyan egyszerűen megfogalmazható, csupán $f$ belső tulajdonságain alapuló feltétel, amely szükséges és elégséges egyszerre.

## Ellenpéldák

**Nincs primitív függvény.** Legyen
$$f(x) := \begin{cases} 0, & \text{ha } x \leq 0 \\ 1, & \text{ha } x > 0 \end{cases}.$$
Tegyük fel, hogy $F$ primitív függvény. Ekkor $x < 0$-ra $F'(x) = 0$, tehát $F(x) = c$, ha $x \leq 0$; $x > 0$-ra $F'(x) = 1$, tehát $F(x) = x + a$, ha $x \geq 0$. Ekkor $F'_-(0) = 0 \neq 1 = F'_+(0)$, tehát $F \notin D\{0\}$, így $f$-nek nincs primitív függvénye.

**Folytonosság nem szükséges.** Legyen
$$F(x) := \begin{cases} x^2 \cdot \sin\tfrac{1}{x}, & \text{ha } 0 \neq x \in \mathbb{R} \\ 0, & \text{ha } x = 0 \end{cases}.$$
Ekkor $F \in D(\mathbb{R})$ és $f := F'$ nem folytonos 0-ban ($\cos\tfrac{1}{x}$ határértéke 0-ban nem létezik), de $f$-nek van primitív függvénye ($F$ maga).

## Egyediség

Az $f$ primitív függvényei csak konstansban különböznek egymástól:

- Ha $F \in \int f$, akkor minden $c \in \mathbb{R}$-re $F + c$ is primitív függvénye $f$-nek.
- Ha $F_1, F_2$ primitív függvények, akkor $\exists c \in \mathbb{R}$: $F_1(x) = F_2(x) + c$ ($x \in I$).

A második pont a [[concepts/analii/derivalasi-szabalyok|deriváltak egyenlőségének tételéből]] következik.

**Megjegyzés.** A 2° tételben lényeges, hogy $f$ intervallumon értelmezett. Például
$$f(x) := \begin{cases} 2x, & x \in (0,1) \\ 0, & x \in (2,3) \end{cases}$$
esetén $F_1(x) = x^2$ ill. $1$, $F_2(x) = x^2$ ill. $0$ mindkettő primitív függvény, de nem egy konstansban különböznek — mert az értelmezési tartomány nem egyetlen intervallum.

## Nem elemi primitív függvények (Liouville)

Könnyű belátni, hogy egy elemi függvény deriváltja mindig elemi függvény. Ezzel szemben **vannak olyan elemi függvények, amelyeknek a primitív függvénye nem elemi függvény**. Ez az integráláás és a deriválás közötti lényeges különbség. Joseph Liouville (1809–1882) volt az első, aki bebizonyította ilyen elemi függvények létezését. Például:

$$e^{\pm x^2},\quad \sin x^2,\quad \cos x^2,\quad \frac{\sin x}{x},\quad \frac{\cos x}{x},\quad \frac{e^x}{x},\quad \frac{1}{\ln x},\quad \sqrt{x^3 + 1}$$

primitív függvénye nem elemi függvény.

## Kapocs

- [[concepts/analii/hatarozatlan-integral]] — a primitív függvények halmazának jelölése és számítási szabályok
- [[concepts/analii/alapintegralok]] — az elemi függvények alap-primitívjeinek táblázata
- [[concepts/analii/derivalasi-szabalyok]] — az egyediség bizonyításában használt deriváltak egyenlőségének tétele
- [[concepts/analii/folytonossag-es-derivalt]] — folytonosság és deriválhatóság kapcsolata
- [[concepts/analii/kozeptertekek]] — Darboux-tétel a középértéktételekkel rokon gondolat
