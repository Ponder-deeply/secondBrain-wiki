---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 4. előadás"]
derivation: source
updated: 2026-09-04
---

# Teljes függvényvizsgálat

Adott $f$ valós-valós függvény **teljes függvényvizsgálatán** $f$ analitikus és geometriai tulajdonságainak szisztematikus megállapítását értjük, amelynek eredménye a függvény grafikonjának pontos felrajzolása.

## Az 5 lépéses módszer

### 0° Kezdeti vizsgálatok

- **Deriválhatóság:** meghatározzuk $\mathcal{D}_f$-t (az értelmezési tartományt) és $\mathcal{D}'_f$-t (ahol deriválható).
- **Paritás:** $f$ páros-e ($f(-x) = f(x)$) vagy páratlan-e ($f(-x) = -f(x)$)? Páros/páratlan esetén elég a félegyenesen vizsgálni, a grafikont tükrözéssel kapjuk.
- **Periodicitás:** van-e $T > 0$ periódus, amelyre $f(x+T) = f(x)$? Ha igen, elég egy periódust vizsgálni.

### 1° Monotonitási intervallumok. Lokális szélsőértékek

- Kiszámítjuk $f'(x)$-et.
- Meghatározzuk a stacionárius pontokat ($f'(x) = 0$) és a nem-differenciálható pontokat.
- Előjelváltás-vizsgálattal megállapítjuk a [[concepts/analii/monotonitas|monotonitási intervallumo]]kat és a [[concepts/analii/lokalis-szelsertekek|lokális szélsőértékek]]et.

### 2° Konvexitási, konkávitási intervallumok. Inflexiós helyek

- Kiszámítjuk $f''(x)$-et.
- $f'' > 0$ ahol konvex, $f'' < 0$ ahol konkáv.
- Az [[concepts/analii/inflexios-pont|inflexiós pontok]]at $f''$ előjelváltásánál keressük (szükséges feltétel: $f''(c) = 0$).

### 3° A határértékek $\mathcal{D}'_f \setminus \mathcal{D}_f$ pontokban

- Az értelmezési tartomány határain (ahol $f$ nem értelmezett vagy nem differenciálható) meghatározzuk $\lim f(x)$-et — esetleg végtelen határértéket.
- Ezek a pontok jelzik az esetleges **függőleges aszimptotákat**.

### 4° Aszimptota $(\pm\infty)$-ben

- Meghatározzuk az [[concepts/analii/aszimptota|aszimptotát]] $(\pm\infty)$-ben a tételt alkalmazva:

$$A = \lim_{x\to\pm\infty} \frac{f(x)}{x}, \qquad B = \lim_{x\to\pm\infty}(f(x) - Ax).$$

- Ha $A = 0$: vízszintes aszimptota $y = B$.
- Ha $A \neq 0$: ferde aszimptota $y = Ax + B$.
- Ha $A$ vagy $B$ nem véges: nincs (elsőfokú) aszimptota $(\pm\infty)$-ben.

### 5° A függvény grafikonjának felrajzolása

Az összegyűjtött adatok alapján: monotonitás, konvexitás, szélsőértékek, inflexiós pontok, aszimptoták, határpontok. Az összes jellemzőt egy táblázatban célszerű összefoglalni, majd a grafikont meghúzni.

## Példa: a Gauss-görbe ($f(x) = e^{-x^2}$)

**Alapadatok.** $\mathcal{D}_f = \mathbb{R}$, $f > 0$ $\mathbb{R}$-en. $f$ **páros** (azaz $f(x) = f(-x)$), $f \in D^2(\mathbb{R})$.

**Deriváltak:**

$$f'(x) = -2x \cdot e^{-x^2}, \qquad f'(x) = 0 \iff x = 0.$$

$$f''(x) = 2(2x^2-1)e^{-x^2}, \qquad f''(x) = 0 \iff x = \pm\frac{1}{\sqrt{2}}.$$

**Előjelváltás-táblázat:**

| $x$ | $x < -\frac{1}{\sqrt{2}}$ | $x = -\frac{1}{\sqrt{2}}$ | $-\frac{1}{\sqrt{2}} < x < 0$ | $x=0$ | $0 < x < \frac{1}{\sqrt{2}}$ | $x = \frac{1}{\sqrt{2}}$ | $x > \frac{1}{\sqrt{2}}$ |
|---|---|---|---|---|---|---|---|
| $f'$ | $+$ | | $+$ | $0$ | $-$ | | $-$ |
| $f''$ | $+$ | $0$ | $-$ | | $-$ | $0$ | $+$ |
| $f$ | $\nearrow$, konvex | infl. | $\nearrow$, konkáv | lok. (absz.) max. | $\searrow$, konkáv | infl. | $\searrow$, konvex |

**Határértékek.** $\mathcal{D}'_f \setminus \mathcal{D}_f = \overline{\mathbb{R}} \setminus \mathbb{R} = \{\pm\infty\}$:

$$\lim_{x\to+\infty} e^{-x^2} = \lim_{x\to+\infty} \frac{1}{e^{x^2}} = 0, \qquad \text{hasonlóan } \lim_{x\to-\infty} = 0.$$

**Aszimptota $(+\infty)$-ben:**

$$A = \lim_{x\to+\infty} \frac{e^{-x^2}}{x} = \lim_{x\to+\infty} \frac{1}{x \cdot e^{x^2}} = 0, \qquad B = \lim_{x\to+\infty} e^{-x^2} = 0.$$

Tehát az $y = 0$ egyenes (az $x$-tengely) az $f$ aszimptotája $(+\infty)$-ben (és $(-\infty)$-ben is, párosság miatt).

## Kapocs

- [[concepts/analii/aszimptota]] — aszimptota meghatározása, a vizsgálat 4. lépése
- [[concepts/analii/lhospital-szabalyok]] — kritikus határértékek kiszámításának eszköze a vizsgálatban
- [[concepts/analii/monotonitas]] — monotonitási intervallumok, a vizsgálat 1. lépése
- [[concepts/analii/lokalis-szelsertekek]] — lokális szélsőértékek, a vizsgálat 1. lépése
- [[concepts/analii/konvex-konkav-fuggvenyek]] — konvexitás/konkávitás, a vizsgálat 2. lépése
- [[concepts/analii/inflexios-pont]] — inflexiós helyek, a vizsgálat 2. lépése
- [[concepts/analii/abszolut-szelsertekek]] — abszolút szélsőértékek kapcsolata a lokálisokkal
