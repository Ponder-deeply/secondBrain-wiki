---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.2. xv)–xviii) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Félmetrika és félmetrikus tér

A félmetrika a metrika azon gyengítése, amely a $\rho(x,y)=0 \Rightarrow x=y$ következtetést elejti: különböző pontok távolsága is lehet nulla. A természetes példa a Riemann-integrálható függvények $\int_a^b|f-g|$ „távolsága"; a hiányzó axióma faktorizálással pótolható.

## Tartalom

### Motiváció: az integrálos távolság nem metrika

A $(C[a,b], \rho_1)$ tér mintájára megpróbálhatnánk a Riemann-integrálható $f,g \in R[a,b]$ függvények távolságát is a

$$\rho(f,g) := \int_a^b |f-g|$$

integrállal mérni. Ez azonban **nem metrika**: az

$$f(x) := 1, \qquad g(x) := \begin{cases} 1 & (a < x \leq b)\\ 0 & (x=a)\end{cases}$$

függvényekre $\rho(f,g)=0$, holott $f \neq g$. A metrika többi axiómája viszont teljesül — pontosan egyetlen implikáció hiányzik.

### Definíció

Legyen $X \neq \emptyset$. A $\rho : X^2 \to [0,+\infty)$ függvény **félmetrika**, ha minden $x,y,z \in X$ esetén

- $\rho(x,x) = 0$;
- $\rho(x,y) = \rho(y,x)$;
- $\rho(x,y) \leq \rho(x,z) + \rho(z,y)$.

Az $(X,\rho)$ párt **félmetrikus térnek** nevezzük. A metrikától tehát csak a $\rho(x,y)=0 \Rightarrow x=y$ kikötés hiányzik.

**További példa.** A számsorozatok $X := \mathbb{N}\to\mathbb{K}$ halmazán rögzített $N \in \mathbb{N}$ mellett

$$\bigl((x_n),(y_n)\bigr) \mapsto \frac{|x_N - y_N|}{1+|x_N-y_N|}$$

félmetrika: csak az $N$-edik tagot „látja".

### Faktorizálás: félmetrikus térből metrikus tér

Legyen $(X,\rho)$ félmetrikus tér. Mondjuk azt, hogy $x$ **ekvivalens** $y$-nal, ha $\rho(x,y)=0$; a félmetrika axiómáiból azonnal adódik, hogy

$$r := \{(x,y) \in X^2 : \rho(x,y)=0\}$$

ekvivalenciareláció. Az $x$ osztálya $r_x := \{y \in X : (x,y) \in r\}$.

**Állítás.** Bármely $x,y \in X$ és $u \in r_x$, $v \in r_y$ esetén $\rho(x,y) = \rho(u,v)$ — a távolság tehát az osztályokon is jól definiált. Így az

$$A := \{r_x : x \in X\}, \qquad \sigma(r_x, r_y) := \rho(x,y)$$

jelölésekkel $(A,\sigma)$ **metrikus tér**.

Ez a konstrukció az, amely az $R[a,b]$ példában a $\{f : \int_a^b |f| = 0\}$ altérrel való faktorizálást jelenti.

### Félmetrikák szuprémumából metrika

**Állítás.** Legyen $I \neq \emptyset$ indexhalmaz, és minden $\alpha \in I$ mellett $(X,\rho_\alpha)$ félmetrikus tér. Tegyük fel, hogy

- $\sup\{\rho_\alpha(x,y) : \alpha \in I\} < +\infty$ minden $x,y \in X$-re, és
- a $\rho_\alpha(x,y)=0$ egyenlőség minden $\alpha \in I$-re csak $x=y$ esetén teljesül.

Ekkor $\rho(x,y) := \sup\{\rho_\alpha(x,y) : \alpha \in I\}$ **metrika** $X$-en.

Speciális esetként adódik, hogy a számsorozatok halmazán

$$\bigl((x_n),(y_n)\bigr) \mapsto \sup\Bigl\{\frac{|x_n-y_n|}{1+|x_n-y_n|} : n \in \mathbb{N}\Bigr\}$$

metrika: a fenti „$N$-edik tagot néző" félmetrikák szuprémuma.

## Kapocs

- [[concepts/analiii/metrikus-ter]] — a teljes axiómarendszer, amelyből egy implikáció hiányzik
- [[concepts/analiii/metrikabol-uj-metrika]] — a $\rho/(1+\rho)$ transzformáció, amit a szuprémumos példa használ
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — az $R[a,b]$ tér faktorizálása ott is felmerül
- [[concepts/analii/integralhato-fuggvenyek]] — a Riemann-integrálhatóság, ami a motiváló példát adja
