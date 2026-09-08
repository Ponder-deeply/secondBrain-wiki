---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 13. előadás"]
derivation: source
updated: 2026-09-04
---

# Banach-féle fixponttétel (Analízis II.)

Egyenletek $g(x) = 0$ közelítő megoldásának alapeszköze: a problémát $x = f(x)$ fixponti alakra hozzuk, és $x_{n+1} := f(x_n)$ iterációval konstruálunk gyökhöz konvergáló sorozatot. A Banach-tétel kontrakcióra mondja ki a fixpont egyértelmű létezését és az iteráció konvergenciáját explicit hibabecsléssel.

## Motiváció — közelítő módszerek

Adott $g : \mathbb{R} \to \mathbb{R}$ esetén $g(x) = 0$ gyökét keressük. Pontos képlet ritkán van: $x^2-x-8=0$-ra van ($1\pm\sqrt{33}\over 2$), $x^3-x-8=0$-ra Cardano-képlet, $x^5-x-8=0$-ra **nincs**. Ezért közelítő módszer kell.

**Megoldás létezése:** Bolzano-tétel ($g \in C[a,b]$, $g(a)\cdot g(b) < 0 \Rightarrow \exists x^* : g(x^*)=0$). Egyértelműséget szigorú monotonitás (pl. $g' > 0$) garantál.

**Három közelítő technika:**
1. **Intervallumfelezés** (Bolzano-tétel bizonyítása alapján).
2. **Newton-módszer** (pl. $\sqrt{5}$-re: $x_{n+1} = \frac{1}{2}(5/x_n + x_n)$, $x_0=2$, lásd Analízis I.).
3. **Fixpont-iteráció** — ennek elméleti hátterét adja a Banach-tétel.

## Fixpont-iteráció

A $g(x)=0$ egyenletet átírjuk **fixpontalakra** $x = f(x)$. Ekkor $x_0$-ból $x_{n+1} := f(x_n)$ rekurzív sorozat. Ha $f \in C$ és $(x_n)$ konvergens $x^*$-hoz, akkor $x^* = f(x^*)$ ($f$ **fixpontja**).

Ugyanazon $g(x)=0$-hoz többféle $f$ jöhet, ezek viselkedése (konvergens-e az iteráció) különbözhet. Pl. $g(x) = x^2-x-2 = 0$:
- $f(x) = x^2-2$: $x^* = 2$ fixpont, de $x_0 = 2+\varepsilon$-ra $x_n \to +\infty$ — **nem konvergál**.
- $f(x) = \sqrt{x+2}$ a $[-2,4]$-en: tetszőleges $x_0$-ra $x_n \to 2$ — **konvergál**.

A folytonosság garantálja a fixpont **létezését** ($f : [a,b] \to [a,b]$ folytonos $\Rightarrow$ van fixpont, Bolzano $h(x) := f(x)-x$-re), de nem elég az iteráció konvergenciájához. Erősebb feltétel: **kontrakció**.

## Kontrakció

**Definíció.** $f : [a,b] \to [a,b]$ **kontrakció**, ha
$$\exists\,0 \leq \alpha < 1 : \forall x,y \in [a,b] : |f(x)-f(y)| \leq \alpha\,|x-y|.$$

**Elégséges feltétel.** $f \in C^1[a,b]$ és $\alpha := \max_{[a,b]} |f'| < 1$ $\Rightarrow$ $f$ kontrakció (Lagrange-középértéktétel).

## Banach-féle fixponttétel

**Tétel.** Legyen $f : [a,b] \to [a,b]$ kontrakció ($0 \leq \alpha < 1$). Ekkor:
1. $\exists!$ $x^* \in [a,b] : x^* = f(x^*)$;
2. tetszőleges $x_0 \in [a,b]$-re az $x_{n+1} := f(x_n)$ iterációs sorozat konvergens és $\lim x_n = x^*$;
3. **hibabecslés:**
$$|x_n - x^*| \leq \frac{\alpha^n}{1-\alpha}\,|x_1 - x_0|.$$

**Bizonyításvázlat (5 lépés).**
- *1.* $f$ folytonos a kontrakcióból.
- *2.* $(x_n)$ Cauchy-sorozat: $|x_{n+1}-x_n| \leq \alpha^n |x_1-x_0|$, és $m>n$-re $|x_m-x_n| \leq \frac{\alpha^n}{1-\alpha}|x_1-x_0|$ (mértani-sor becslés).
- *3.* Cauchy-féle konvergenciakritérium $\Rightarrow$ $x^* := \lim x_n \in [a,b]$.
- *4.* $x_{n+1} = f(x_n)$ + $f$ folytonossága + átviteli elv $\Rightarrow$ $x^* = f(x^*)$.
- *5.* Egyértelműség: ha $x^{**}$ is fixpont, $|x^*-x^{**}| \leq \alpha\,|x^*-x^{**}|$ és $1-\alpha>0$ $\Rightarrow$ $x^*=x^{**}$.
- *3°* hibabecslés: a 2. lépés egyenlőtlenségében $m\to\infty$ határátmenet.

## Példa — $x = \cos x$

Egy pozitív valós gyök ($g(x) := x-\cos x$, $g(0)=-1<0$, $g(\pi/2)=\pi/2>0$, $g' = 1+\sin x > 0$ a $(0,\pi/2)$-n). A $[0,\pi/2]$-n $f(x) := \cos x$, de $\max|f'| = 1$ — **nem** kontrakció.

Szűkítés $[0,1]$-re: $f([0,1]) \subset [0,1]$, $\max_{[0,1]} |\sin| = \sin 1 \approx 0{,}8415 = \alpha < 1$ $\Rightarrow$ kontrakció. Banach: egyetlen fixpont, $x_{n+1} = \cos x_n$ konvergál hozzá, $|x_n - x^*| \leq \frac{\alpha^n}{1-\alpha}|x_1-x_0|$.

## Megjegyzések

- **Miért kell hibabecslés?** Adott pontossághoz előre megmondja, hány iteráció kell.
- **Miért több módszer?** Konvergenciasebesség, alkalmazhatósági feltételek különböznek (Newton kvadratikus, ha $f' \neq 0$; intervallumfelezés robusztus, de lassú; fixpont-iteráció kontrakciós feltételhez kötött).
- **Általánosítások:** Banach messze túlmutat $\mathbb{R}\to\mathbb{R}$-en — teljes metrikus terekre érvényes; lineáris és nemlineáris egyenletrendszerek, differenciálegyenletek közelítő megoldásánál is alapeszköz.

## Kapocs

- [[concepts/nummodi/banach-fixponttetel-rn]] — a tétel mátrixiterációkra alkalmazva (Numerikus módszerek)
- [[concepts/nummodi/iteracios-modszerek-ler]] — Jacobi/Gauss–Seidel mint speciális kontrakciók
- [[concepts/analii/kozeptertekek]] — Lagrange-tétel: a $C^1$ + $|f'|<1$ kontrakciós kritérium háttere
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — Heine-tétel jellegű kompaktsági argumentumok (folytonosság $\Rightarrow$ fixpont létezés)
- [[concepts/analii/improprius-integral]] — az ea12 témája, a félév lezárását adja az ea13 mellett
