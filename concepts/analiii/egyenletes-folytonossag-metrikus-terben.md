---
tags: [concept]
sources: [SimonP-Anal2.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf]
references: ["Simon Péter: Analízis II., 2.6. Tétel és 2.1. iii) megjegyzés"]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Egyenletes folytonosság metrikus terekben

Egy leképezés egyenletesen folytonos, ha a $\delta$ csak $\varepsilon$-tól függ, a ponttól nem. Ez szigorúan erősebb a folytonosságnál, de kompakt értelmezési tartományon a kettő egybeesik (Heine-tétel).

## Tartalom

### A fogalom motivációja

Folytonos $f \in X \to Y$ esetén minden $a \in D_f$ és $\varepsilon > 0$ mellett van $\delta_a^{(\varepsilon)} > 0$, amellyel

$$\sigma\bigl(f(x),f(a)\bigr) < \varepsilon \qquad (x \in D_f,\ \rho(x,a) < \delta_a^{(\varepsilon)}).$$

A kérdés, hogy a $\delta$ választható-e $a$-tól függetlenül. Nem mindig: az $f(x) := 1/x$ ($0 < x \in \mathbb{R}$) függvényre az $x := a + \delta_a^{(\varepsilon)}/2$ választással (ha $a\varepsilon < 1$)

$$\frac{\delta_a^{(\varepsilon)}}{2xa} < \varepsilon \implies 0 < \delta_a^{(\varepsilon)} < \frac{2a^2\varepsilon}{1 - a\varepsilon} \to 0 \qquad (a \to 0),$$

tehát a nullához közeledve a jó $\delta$ kényszerűen nullához tart: adott $\varepsilon$-hoz nincs minden $a$-ra egyszerre jó $\delta$.

### Definíció

Az $f \in X \to Y$ függvény **egyenletesen folytonos**, ha minden $\varepsilon > 0$ számhoz létezik olyan $\delta > 0$, hogy

$$\sigma\bigl(f(x),f(t)\bigr) < \varepsilon \qquad (x,t \in D_f,\ \rho(x,t) < \delta).$$

Ekkor $f$ nyilván folytonos is; a fenti $1/x$ példa mutatja, hogy megfordítva nem igaz.

### Lipschitz-tulajdonság

Ha van olyan $q \ge 0$, hogy

$$\sigma\bigl(f(x),f(y)\bigr) \le q \cdot \rho(x,y) \qquad (x,y \in D_f),$$

akkor $f$ egyenletesen folytonos: adott $\varepsilon$-hoz minden $\delta$ megfelel, amelyre $q\delta < \varepsilon$. Ilyen például minden **kontrakció** ($q < 1$), tehát a [[concepts/analiii/banach-fixponttetel-metrikus-terben|Banach-fixponttétel]] leképezései, és minden [[concepts/analiii/korlatos-linearis-lekepezes|korlátos lineáris leképezés]] is (ott $q = \|f\|$).

### 2.6. Tétel (Heine)

**Tétel.** Ha az $f \in X \to Y$ függvény folytonos és $D_f$ kompakt, akkor $f$ egyenletesen folytonos.

*Bizonyítás (indirekt).* Tegyük fel, hogy valamilyen $\varepsilon > 0$ mellett minden $\delta > 0$-hoz vannak olyan $x,t \in D_f$ pontok, hogy $\rho(x,t) < \delta$, de $\sigma(f(x),f(t)) \ge \varepsilon$. A $\delta := 1/n$ választással kapunk $(x_n), (t_n) : \mathbb{N}\to D_f$ sorozatokat, amelyekre

$$\rho(x_n,t_n) < \frac1n, \qquad \sigma\bigl(f(x_n),f(t_n)\bigr) \ge \varepsilon.$$

A $D_f$ kompaktsága miatt van olyan $(\nu_n)$ indexsorozat, hogy $a := \lim(x_{\nu_n}) \in D_f$, majd ebből egy további $(\mu_n)$ kiválasztással $b := \lim(t_{\nu_{\mu_n}}) \in D_f$. Mivel $\rho(x_{\nu_{\mu_n}}, t_{\nu_{\mu_n}}) < 1/n$, a metrika folytonossága miatt

$$0 \le \rho(a,b) = \lim \rho(x_{\nu_{\mu_n}}, t_{\nu_{\mu_n}}) \le \lim \frac1n = 0,$$

tehát $a = b$. Az [[concepts/analiii/atviteli-elv-metrikus-terben|átviteli elv]] szerint ekkor

$$\lim \sigma\bigl(f(x_{\nu_{\mu_n}}), f(t_{\nu_{\mu_n}})\bigr) = \sigma\bigl(f(a),f(a)\bigr) = 0,$$

ami ellentmond a $\sigma(f(x_n),f(t_n)) \ge \varepsilon$ feltevésnek. $\blacksquare$

A **kétszeri részsorozat-kiválasztás** a bizonyítás kulcsa: egyetlen indexsorozat csak az egyik sorozatot teszi konvergenssé, a másikat egy második kiválasztással kell utolérni.

### Feladatok

**Módszer.** *Bizonyítás*: rögzített $\varepsilon$-ra a $|f(x)-f(t)|$-t felülről becsüljük a távolsággal ($\le C\|x-t\|$), és $\delta:=\varepsilon/C$. *Cáfolat* (nem egyenletes folytonosság): az állítás tagadása szerint elég $\varepsilon>0$-t és két sorozatot találni, amelyre $\|x_n-a_n\|\to0$, de $|f(x_n)-f(a_n)|\ge\varepsilon$. (Ez a cáfolat módszere, bizonyításra nem használható.) Kompakt halmazon [[concepts/analiii/weierstrass-tetel-kompakt-halmazon|folytonos]] függvény Heine szerint egyenletesen folytonos, ezért a hibát a nem kompakt tartomány szélén keressük.

**Munkapéldák.**

1. $f=2x+3y-5$ egyenletesen folytonos $\mathbb{R}^2$-en: $|f(x,y)-f(a,b)|\le2|x-a|+3|y-b|\le5\max\{|x-a|,|y-b|\}=5\|(x,y)-(a,b)\|_\infty<\varepsilon$, tehát $\delta=\varepsilon/5$ ($\|\cdot\|_1$-gyel $\delta=\varepsilon/3$ is jó).
2. $f(x)=\|x\|$ minden normált térben egyenletesen folytonos, $\delta=\varepsilon$: a fordított háromszög-egyenlőtlenség miatt $\bigl|\|x\|-\|t\|\bigr|\le\|x-t\|$. Így $\sqrt{x^2+y^2}$ egyenletesen folytonos $\mathbb{R}^2$-en.
3. $f=\sin\dfrac\pi{1-x^2-y^2}$ az $x^2+y^2<1$ nyílt egységkörön **nem** egyenletesen folytonos: $x_n=\sqrt{1-\frac1{1/2+2n}}$ (itt $\frac\pi{1-x_n^2}=\frac\pi2+2n\pi$, $f=1$) és $a_n=\sqrt{1-\frac1{2n}}$ ($\frac\pi{1-a_n^2}=2n\pi$, $f=0$). Mindkettő a $(-1,1)$-ben van, $|x_n-a_n|\to0$, de $|f(x_n,0)-f(a_n,0)|=1=:\varepsilon$. A zárt $\overline{K_R(0)}$ körlapon ($R<1$) viszont kompakt, így egyenletesen folytonos.
4. $f=\dfrac{\sin(x^2+y^2+e^{x^4})}{1+\operatorname{arctg}^2x}$ **nem** egyenletesen folytonos $\mathbb{R}^2$-en: az $x=0$ egyenesen $f(0,y)=\sin(1+y^2)$, és $y_n=\sqrt{\tfrac\pi2-1+2n\pi}$, $b_n=\sqrt{2n\pi-1}$ esetén $|y_n-b_n|\to0$, de $|f(0,y_n)-f(0,b_n)|=|1-0|=1$. Ötlet: az egyik változót rögzítve egy nem egyenletesen folytonos egyváltozós függvényt kapunk (mint $x^2$).

## Kapocs

- [[concepts/analiii/folytonossag-metrikus-terben]] — a gyengébb, pontonkénti fogalom
- [[concepts/analiii/kompakt-halmazok]] — a Heine-tétel feltétele
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a bizonyítás eszköze
- [[concepts/analiii/korlatos-linearis-lekepezes]] — Lipschitz-tulajdonságú, tehát egyenletesen folytonos leképezések
- [[concepts/analiii/halmaztol-vett-tavolsagfuggveny]] — a legfontosabb Lipschitz-példa metrikus térben
- [[concepts/analii/egyenletes-folytonossag]] — az egyváltozós eset
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
