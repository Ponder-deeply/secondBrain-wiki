---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.2. vii), 1.4. v), 1.6. vii), 1.8. vi)–vii), xiv) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Metrikus, normált és euklideszi terek szorzata

Két metrikus tér Descartes-szorzatán ugyanaz a $p$-paraméteres képlet ad metrikát, amely $\mathbb{K}^n$-ben a $\rho_p$ metrikákat: a $(\mathbb{K}^n,\rho_p)$ terek nem mások, mint $\mathbb{K}$ $n$-szeres szorzatai. A szorzattér minden lényeges tulajdonsága — konvergencia, Cauchy-tulajdonság, teljesség, kompaktság — **koordinátánként** dől el.

## Tartalom

### A szorzatmetrika

Legyenek $(X,\rho)$, $(Y,\sigma)$ metrikus terek és $0 < p \in \mathbb{R}\cup\{\infty\}$. Az $X\times Y$-beli $(x,y)$, $(u,v)$ elemekre

$$(\rho\times\sigma)\bigl((x,y),(u,v)\bigr) := \begin{cases}\rho^p(x,u)+\sigma^p(y,v) & (0<p\leq 1)\\[2pt] \bigl(\rho^p(x,u)+\sigma^p(y,v)\bigr)^{1/p} & (1<p\in\mathbb{R})\\[2pt] \max\{\rho(x,u),\sigma(y,v)\} & (p=\infty).\end{cases}$$

Ekkor $(X\times Y, \rho\times\sigma)$ metrikus tér. A definíció értelemszerűen kiterjed véges sok tényezőre.

**A $\mathbb{K}^n$ mint szorzat.** Az

$$X := Y := \dots := \mathbb{K}, \qquad \rho(a,b) := \sigma(a,b) := \dots := |a-b|$$

választással pontosan a $(\mathbb{K}^n, \rho_p)$ terek adódnak.

A metrikavolta $p=1,2,\infty$ esetén közvetlenül ellenőrizhető. Egyéb $p$-kre csak a háromszög-egyenlőtlenség bonyolult: $0<p<1$ mellett az $(1+x)^p \leq 1+x^p$ becslésen, $p \geq 1$ mellett a Hölder-egyenlőtlenségen múlik a $q := \frac{p}{p-1}$ konjugált kitevővel (a $p=2$ eset a Cauchy–Bunyakovszkij-egyenlőtlenség).

### Szorzatnorma és szorzat-skalárszorzat

Ha $(X,\|\cdot\|_X)$, $(Y,\|\cdot\|_Y)$ normált terek, akkor az $X\times Y$ Descartes-szorzat a koordinátánkénti műveletekkel lineáris tér, és

$$\|(x,y)\|_{X\times Y} := \begin{cases}\bigl(\|x\|_X^p + \|y\|_Y^p\bigr)^{1/p} & (1\leq p<+\infty)\\[2pt] \max\{\|x\|_X,\|y\|_Y\} & (p=+\infty)\end{cases}$$

**szorzatnorma**. A $(\mathbb{K}^n, \|\cdot\|_p)$ terek ennek is speciális esetei ($X=Y=\dots=\mathbb{K}$, $\|a\|=|a|$).

Euklideszi terekre ugyanez a

$$\bigl\langle (x,y),(u,v)\bigr\rangle := \langle x,u\rangle_X + \langle y,v\rangle_Y$$

definícióval megy: $(X\times Y, \langle\cdot,\cdot\rangle)$ euklideszi tér, és a $(\mathbb{K}^n,\langle\cdot,\cdot\rangle)$ tér az $\langle a,b\rangle := a\overline b$ tényezőkből adódik.

### Minden koordinátánként dől el

**Állítás (konvergencia).** Az $\bigl((x_n,y_n)\bigr) : \mathbb{N}\to X\times Y$ sorozat akkor és csak akkor konvergens, ha $(x_n)$ és $(y_n)$ is az; és ekkor $\lim(x_n,y_n) = \bigl(\lim(x_n), \lim(y_n)\bigr)$.

**Állítás (Cauchy-tulajdonság és teljesség).** Az $\bigl((x_n,y_n)\bigr)$ sorozat akkor és csak akkor Cauchy-sorozat, ha $(x_n)$ és $(y_n)$ is az. Következésképpen a szorzattér **akkor és csak akkor teljes, ha mindkét tényező teljes**.

**Állítás (kompaktság).**

- Ha $A \subset X$ és $B \subset Y$ kompakt, akkor $A\times B$ kompakt a $\rho\times\sigma$ metrikában.
- Ha $U \subset X\times Y$ kompakt, akkor az $U^{(1)}$, $U^{(2)}$ vetületei is kompaktak.
- Speciálisan $(\mathbb{K}^s,\rho_p)$-ben minden kompakt halmaz minden vetülete kompakt számhalmaz, és kompakt $A_i \subset \mathbb{K}$ halmazok $A_1\times\dots\times A_s$ szorzata kompakt.

*Az első bizonyítása.* Ha $(z_n) = (x_n,y_n) : \mathbb{N}\to A\times B$, akkor $A$ kompaktsága miatt van olyan $(\nu_n)$ indexsorozat, hogy $a := \lim(x_{\nu_n}) \in A$; $B$ kompaktsága miatt ebből tovább válogatva van $(\mu_n)$, amellyel $b := \lim(y_{\nu_{\mu_n}}) \in B$. Mivel $a = \lim(x_{\nu_{\mu_n}})$ is igaz, ezért $\lim(z_{\nu_{\mu_n}}) = (a,b) \in A\times B$. $\blacksquare$

### A szorzattopológia szigorúan bővebb

**Vetület.** Ha $U \subset X\times Y$, akkor a vetületei

$$U^{(1)} := \{x \in X : \exists y \in Y,\ (x,y)\in U\}, \qquad U^{(2)} := \{z \in Y : \exists t \in X,\ (t,z)\in U\}.$$

**Állítás.** $\mathcal{T}_\rho(X)\times\mathcal{T}_\sigma(Y) \subset \mathcal{T}_{\rho\times\sigma}(X\times Y)$: nyílt halmazok Descartes-szorzata nyílt a szorzatmetrikában. Nyílt halmaz vetületei pedig nyíltak.

**A tartalmazás szigorú.** $\mathbb{R}^2\setminus\{(0,0)\}$ nyílt a $\rho_2$ metrikában, de nem áll elő $A\times B$ alakban: mivel $(0,1),(1,0) \in \mathbb{R}^2\setminus\{(0,0)\}$, szükségszerűen $0 \in A$ és $0 \in B$ lenne, tehát $(0,0) \in A\times B$ — ellentmondás.

Fordítva, a vetületek nyíltságából sem következik a halmaz nyíltsága: az

$$U := \{(x,y)\in\mathbb{R}^2 : 1 \leq x^2+y^2 < 4\}$$

halmaz nem nyílt, de $U^{(1)}=U^{(2)}=(-2,2)$ igen. Ennek hátterében az az egyszerű tény áll, hogy általában $U \neq U^{(1)}\times U^{(2)}$.

**Geometriai kép.** A $(\mathbb{K}^s,\rho_\infty)$ térben a környezet éppen a koordinátánkénti környezetek szorzata:

$$K_r(a) = K_r(a_1)\times\dots\times K_r(a_s) \qquad \bigl(a=(a_1,\dots,a_s), \ r>0\bigr),$$

azaz $\mathbb{R}^2$-ben nyílt négyzet — szemben a $\rho_1$-beli rombusszal és a $\rho_2$-beli körlemezzel.

## Kapocs

- [[concepts/analiii/metrikus-ter]] — a szorzatkonstrukció bemenete
- [[concepts/analiii/normalt-vektorter]] — a $\|\cdot\|_p$ normák mint szorzatnormák
- [[concepts/analiii/skalaris-szorzat-ter]] — euklideszi terek szorzata
- [[concepts/analiii/ekvivalens-metrikak]] — a különböző $p$-hez tartozó szorzatmetrikák $p\geq 1$-re ekvivalensek
- [[concepts/analiii/koordinatafuggvenyek-folytonossaga]] — a projekciók és a szorzattér folytonossági oldala
- [[concepts/analiii/kompaktsag-ekvivalens-jellemzesei]] — a sorozatos kompaktság, amit a bizonyítás használ
