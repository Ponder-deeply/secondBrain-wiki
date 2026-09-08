---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.6. Tétel és 2.1. iii) megjegyzés"]
derivation: source
updated: 2026-09-07
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

## Kapocs

- [[concepts/analiii/folytonossag-metrikus-terben]] — a gyengébb, pontonkénti fogalom
- [[concepts/analiii/kompakt-halmazok]] — a Heine-tétel feltétele
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a bizonyítás eszköze
- [[concepts/analiii/korlatos-linearis-lekepezes]] — Lipschitz-tulajdonságú, tehát egyenletesen folytonos leképezések
- [[concepts/analiii/halmaztol-vett-tavolsagfuggveny]] — a legfontosabb Lipschitz-példa metrikus térben
- [[concepts/analii/egyenletes-folytonossag]] — az egyváltozós eset
