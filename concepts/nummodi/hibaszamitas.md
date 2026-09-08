---
tags: [concept]
sources: [NM1_ea01.pdf]
derivation: source
updated: 2026-08-05
---

# Hibaszámítás elemei

A numerikus számítások során elkerülhetetlenül fellépő hibák mértékének jellemzése, az alapműveletek hibáinak becslése, és a függvényértékek hibájának elemzése.

## Hibák jellemzése — definíciók

Legyen $A$ egy pontos érték, $a$ pedig annak közelítője. Ekkor:

| Jelölés | Elnevezés | Definíció |
|---|---|---|
| $\Delta a := A - a$ | a közelítő érték (pontos) hibája | $A$ és $a$ különbsége |
| $|\Delta a| := |A - a|$ | **abszolút hiba** | a hiba nagysága |
| $\Delta_a \ge |\Delta a|$ | **abszolút hibakorlát** | felső becslés az abszolút hibára |
| $\delta a := \frac{\Delta a}{A} \approx \frac{\Delta a}{a}$ | **relatív hiba** | hiba az értékhez viszonyítva |
| $\delta_a \ge |\delta a|$ | **relatív hibakorlát** | felső becslés a relatív hibára |

**Példa:** A $3{,}14$ szám mint $\pi$ két tizedesjegyre kerekített közelítője:
- $\Delta(\pi) = \pi - 3{,}14 \approx 0{,}00159$
- $|\Delta(\pi)| \approx 0{,}00159$, $\delta(\pi) \approx 0{,}00051$

## Hibák terjedése az alapműveletekben

### Tétel: az alapműveletek hibakorlátai

| Művelet | Abszolút hibakorlát | Relatív hibakorlát |
|---|---|---|
| $a \pm b$ | $\Delta_{a \pm b} = \Delta_a + \Delta_b$ | $\delta_{a \pm b} = \dfrac{|a| \cdot \delta_a + |b| \cdot \delta_b}{|a \pm b|}$ |
| $a \cdot b$ | $\Delta_{a \cdot b} = |b| \cdot \Delta_a + |a| \cdot \Delta_b$ | $\delta_{a \cdot b} = \delta_a + \delta_b$ |
| $a / b$ | $\Delta_{a/b} = \dfrac{|b| \cdot \Delta_a + |a| \cdot \Delta_b}{b^2}$ | $\delta_{a/b} = \delta_a + \delta_b$ |

**Figyelem — kritikus esetek, ahol a korlátok nagyságrendileg megnőhetnek:**

1. **$\delta_{a \pm b}$ esetén**, amikor közel azonos méretű számokat vonunk ki egymásból: a nevező $|a \pm b|$ kicsi lesz, a relatív hiba felfúvódik (**catastrophic cancellation / jegyveszítés**).
2. **$\Delta_{a/b}$ esetén**, amikor kis számmal osztunk: a nevező $b^2$ kicsi.

### Bizonyítások vázlata

**Összeadás/kivonás:**
$$\Delta(a \pm b) = (A \pm B) - (a \pm b) = \Delta a \pm \Delta b$$
$$|\Delta(a \pm b)| \le |\Delta a| + |\Delta b| \le \Delta_a + \Delta_b = \Delta_{a \pm b}$$

**Szorzás** ($\Delta a \cdot \Delta b$ elhanyagolható):
$$\Delta(a \cdot b) = A \cdot B - a \cdot b = A(B - b) + b(A - a) = a \cdot \Delta b + b \cdot \Delta a$$
$$|\Delta(a \cdot b)| \le |a| \cdot \Delta_b + |b| \cdot \Delta_a = \Delta_{a \cdot b}$$
$$\delta(a \cdot b) = \frac{a \cdot \Delta b + b \cdot \Delta a}{a \cdot b} \approx \frac{\Delta b}{b} + \frac{\Delta a}{a} = \delta_b + \delta_a$$

**Osztás** ($\Delta b \cdot b$ elhanyagolható):
$$\Delta\!\left(\frac{a}{b}\right) = \frac{A}{B} - \frac{a}{b} = \frac{b \cdot \Delta a - a \cdot \Delta b}{(b + \Delta b) \cdot b} \approx \frac{b \cdot \Delta a - a \cdot \Delta b}{b^2}$$
$$\delta\!\left(\frac{a}{b}\right) = \delta a - \delta b, \quad \left|\delta\!\left(\frac{a}{b}\right)\right| \le \delta_a + \delta_b = \delta_{a/b}$$

## Függvényérték hibája

### 1. tétel (elsőrendű): $C^1$ esetén

Ha $f \in C^1(k_{\Delta_a}(a))$ és $\Delta_a(a) = [a - \Delta_a;\, a + \Delta_a]$, akkor
$$\Delta_{f(a)} = M_1 \cdot \Delta_a, \quad \text{ahol } M_1 = \max\{|f'(\xi)| : \xi \in k_{\Delta_a}(a)\}.$$

**Bizonyítás:** Lagrange-féle középértéktétel:
$$\Delta f(a) = f(A) - f(a) = f'(\xi) \cdot (A - a) = f'(\xi) \cdot \Delta a$$
$$|\Delta f(a)| = |f'(\xi)| \cdot |\Delta a| \le M_1 \cdot \Delta_a.$$

### 2. tétel (másodrendű): $C^2$ esetén

Ha $f \in C^2(k_{\Delta_a}(a))$, akkor
$$\Delta_{f(a)} = |f'(a)| \cdot \Delta_a + \frac{M_2}{2} \cdot \Delta_a^2, \quad M_2 = \max\{|f''(\xi)| : \xi \in k_{\Delta_a}(a)\}.$$

**Bizonyítás:** Taylor-formula:
$$\Delta f(a) = f'(a) \cdot (A - a) + \frac{f''(\xi)}{2}(A-a)^2$$
$$|\Delta f(a)| \le |f'(a)| \cdot \Delta_a + \frac{M_2}{2} \cdot \Delta_a^2.$$

### Következmény: relatív hiba és kondíciószám

Ha $\Delta_a$ kicsi, a másodfokú tag elhanyagolható, ezért
$$\delta_{f(a)} \approx \frac{|a| \cdot |f'(a)|}{|f(a)|} \cdot \delta_a =: c(f, a) \cdot \delta_a.$$

**Definíció:** Az $f$ függvény $a$-beli **kondíciószáma**:
$$c(f, a) = \frac{|a| \cdot |f'(a)|}{|f(a)|}.$$

Ha $c(f,a) \gg 1$, a függvénykiértékelés **rosszul kondicionált**: a bemeneti relatív hiba felerősödve jelenik meg a kimenetben.

## Kapocs

- [[concepts/nummodi/lebegopont-modell]] — gépi számok modellje, input hiba, $\varepsilon_1$
- [[concepts/nummodi/algoritmus-stabilitas]] — stabil vs. instabil algoritmus; a hibaterjedés algoritmikus vetülete
- [[concepts/nummodi/kondicioszam]] — mátrixok kondíciószáma $\operatorname{cond}(A) = \|A\|\cdot\|A^{-1}\|$; tulajdonságok, normafüggőség
- [[concepts/nummodi/ler-erzekenysege]] — LER perturbációs tételei; kondíciószám szerepe a hibabecslésnél
- [[concepts/nummodi/tematika]] — kurzus tematikája
- [[subjects/nummodi]] — kurzus áttekintése
