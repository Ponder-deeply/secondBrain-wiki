---
tags: [concept]
sources: [12_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Síkgörbék ívhossza

A síkgörbe ívhossza a paraméteres ívhosszképlet $n=2$-re szűkített alakja; polárkoordinátás alakban megadott görbére a képlet $r(\varphi)$-vel és $r'(\varphi)$-vel fejezhető ki.

## Tartalom

### Rektifikálhatóság és ívhossz — a paraméteres eset

Legyen $\Gamma \subset \mathbb{R}^n$ sima elemi görbe, $\tau := \{a = t_0 < t_1 < \dots < t_m = b\}$ az $[a,b]$ paraméter-intervallum egy felosztása. A $\varphi(t_0), \varphi(t_1), \dots, \varphi(t_m)$ pontokat összekötő töröttvonalat $\Gamma$ **beírt töröttvonalának** nevezzük; ennek hossza

$$\ell_\varphi(\tau) = \sum_{i=1}^{m} \|\varphi(t_i) - \varphi(t_{i-1})\|.$$

**Definíció.** A $\Gamma$ görbe **rektifikálható**, ha $\ell(\Gamma) := \ell(\varphi) := \sup\{\ell_\varphi(\tau) \mid \tau \in \mathcal{F}[a,b]\} < +\infty$. Ekkor $\ell(\Gamma)$ a $\Gamma$ görbe **ívhossza**. Igazolható, hogy $\ell(\Gamma)$ független a $\Gamma$ paraméteres előállításától.

**Tétel.** Ha $\Gamma \subset \mathbb{R}^n$ sima görbe, $\varphi \in C^1([a,b], \mathbb{R}^n)$ egy paraméterezése, akkor $\Gamma$ rektifikálható, és

$$\ell(\Gamma) = \int_a^b \|\varphi'(t)\|\,\mathrm{d}t = \int_a^b \sqrt{\bigl(\varphi_1'(t)\bigr)^2 + \dots + \bigl(\varphi_n'(t)\bigr)^2}\,\mathrm{d}t.$$

Ez ugyanaz a képlet, mint a [[concepts/analiii/szakaszonkent-c1-gorbe]] lapon a $G$-ben fekvő szakaszonként $C^1$ görbe hosszára kimondott $\ell(\gamma) = \int_a^b |\dot\gamma(t)|\,\mathrm{d}t$ tétel — a beírt töröttvonalak szuprémumaként vett ívhosszfogalom mindkét tárgyalásban ugyanaz, csak a görbeosztály (sima elemi görbe, illetve nyílt tartományban fekvő szak.$C^1$ görbe) eltérő.

$n=2$-re, azaz síkgörbére ($\varphi = (\varphi_1, \varphi_2)$) a képlet:

$$\ell(\Gamma) = \int_a^b \|\varphi'(t)\|\,\mathrm{d}t = \int_a^b \sqrt{\bigl(\varphi_1'(t)\bigr)^2 + \bigl(\varphi_2'(t)\bigr)^2}\,\mathrm{d}t.$$

### Polárkoordinátás alakban megadott görbe ívhossza

**Tétel.** Tegyük fel, hogy $r : [a,b] \to [0,+\infty)$ folytonosan deriválható $[a,b]$-n. Ekkor az $r$ által [[concepts/analiii/sikgorbe-megadasi-modok|polárkoordinátás alakban megadott görbe]] rektifikálható, és az ívhossza:

$$\ell(\Gamma) = \int_a^b \sqrt{\bigl(r'(\varphi)\bigr)^2 + \bigl(r(\varphi)\bigr)^2}\,\mathrm{d}\varphi.$$

Valóban, $[a,b] \ni \varphi \mapsto \bigl(r(\varphi)\cos\varphi,\, r(\varphi)\sin\varphi\bigr)$ a görbe egy paraméterezése; ennek deriváltjára a szorzatszabály és $\cos^2\varphi+\sin^2\varphi=1$ alkalmazásával adódik a fenti alak a paraméteres képletből.

### Példa: a Bernoulli-lemniszkáta ívhossza

A [[concepts/analiii/sikgorbe-megadasi-modok]] lapon bevezetett lemniszkátára, $r(\varphi) = \sqrt{2}\,a\sqrt{\cos(2\varphi)}$, szimmetria okok miatt elég az első síknegyedbe eső résznek ($\varphi \in [0, \pi/4]$) az ívhosszát meghatározni, és azt néggyel szorozni:

$$\ell = 4\int_0^{\pi/4} \sqrt{\bigl(r(\varphi)\bigr)^2 + \bigl(r'(\varphi)\bigr)^2}\,\mathrm{d}\varphi = 4\int_0^{\pi/4} \sqrt{2a^2\cos(2\varphi) + 2a^2\cdot\frac{\sin^2(2\varphi)}{\cos(2\varphi)}}\,\mathrm{d}\varphi = \sqrt{2}\,a \cdot 4\int_0^{\pi/4} \frac{1}{\sqrt{\cos(2\varphi)}}\,\mathrm{d}\varphi.$$

Az integrandus primitív függvénye **nem elemi függvény** (elliptikus integrálra vezet), ezért az integrálnak csak közelítő értéke határozható meg:

$$\ell = 4\sqrt{2}\,a \int_0^{\pi/4} \frac{1}{\sqrt{\cos(2\varphi)}}\,\mathrm{d}\varphi \approx 7{,}416\dots \cdot a.$$

Ez szemlélteti, hogy egy görbe rektifikálhatósága és az ívhosszképlet léte nem garantálja, hogy az integrál zárt alakban kiszámítható — csak azt, hogy (numerikusan) közelíthető.

## Kapocs

- [[concepts/analiii/szakaszonkent-c1-gorbe]] — a $G \subset \mathbb{R}^p$ nyílt tartományban fekvő szakaszonként $C^1$ görbe ívhosszának ugyanilyen alakú képlete
- [[concepts/analiii/gorbe-erintoje]] — a sima elemi görbe és a paraméterezés fogalma, amelyre az ívhosszképlet épül
- [[concepts/analiii/sikgorbe-megadasi-modok]] — a polárkoordinátás alak és a Bernoulli-lemniszkáta példája
- [[concepts/analiii/polarkoordinatas-helyettesites]] — az $(x,y) = (r\cos\varphi, r\sin\varphi)$ leképezés mint területtranszformáció
- [[concepts/analii/ivhossz]] — az egyváltozós, függvénygrafikonra vonatkozó ívhosszfogalom, amelynek ez az általánosítása
