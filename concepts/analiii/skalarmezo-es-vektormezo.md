---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Skalármező és vektormező

Egy $G \subset \mathbb{R}^p$ nyílt halmazon értelmezett szám értékű, illetve vektor értékű függvények elnevezése; a vonalintegrál és a primitív függvény elméletének alapszókincse.

## Tartalom

### Definíció

Legyen $G \subset \mathbb{R}^p$ nyílt halmaz (a továbbiakban rendszerint összefüggő is). Ekkor

- a $G \to \mathbb{R}$ függvényeket **skalármezőnek**,
- a $G \to \mathbb{R}^p$ függvényeket **vektormezőnek**

nevezzük.

A szokásos simasági jelzőket ezekre is használjuk: *folytonos skalármező*, *kétszer differenciálható vektormező*, *nyolcszor folytonosan differenciálható skalármező* és így tovább.

Lényeges, hogy a vektormező **ugyanabba** az $\mathbb{R}^p$-be képez, ahonnan az értelmezési tartománya való: az $f(x)$ értéket az $x$ pontbeli elmozdulásvektorokkal skalárisan szorozzuk majd, ezért kell a két dimenziónak megegyeznie.

### A fizikai kép

A fogalompár a mechanikai munka precíz megfogalmazásából nőtt ki. Tegyük fel, hogy egy domboldalon az $A$ pontból csúszik a $B$ pontba egy $m$ tömegű test. Minden $x$ pontban van egy $g(x)$ **gravitációs térerősség**, tehát a test súlya $m\cdot g(x)$. A $g$ vektor értékű: nemcsak a nagysága, még az **iránya** sem állandó, hiszen a test repülhetne akár a Nap, a Föld és a Hold között is. Az utat kicsi darabokra vágva a mező által végzett munka közelítőleg

$$\sum \bigl\langle m\cdot g(x); \Delta x\bigr\rangle,$$

ahol $\langle \mathbf{a}; \mathbf{b}\rangle$ az $\mathbf{a}$ és $\mathbf{b}$ skaláris szorzata. (A skalárszorzat azt fejezi ki, hogy csak az elmozdulás **irányába** eső erőkomponens végez munkát.)

Minden $x$ ponthoz hozzárendelhető egy $V(x)$ szám, a pontbeli **gravitációs potenciál**; a test helyzeti energiája $m\cdot V(x)$, a lecsúszás közben végzett munka pedig a kettő különbsége, $m\bigl(V(A) - V(B)\bigr)$. Az $m$-mel osztva:

$$\sum \bigl\langle g(x); \Delta x\bigr\rangle = V(A) - V(B).$$

### Három függvénytípus egyszerre

Érdemes tudatosítani, hogy a fenti képben **háromféle** függvény szerepel, és a fejezet minden tétele ezek viszonyáról szól:

| Függvény | Típusa | Példa |
|---|---|---|
| $g(x)$ | vektormező, $G \to \mathbb{R}^p$ | gravitációs térerősség |
| $V(x)$ | skalármező, $G \to \mathbb{R}$ | potenciálfüggvény |
| $t \mapsto x(t)$ | görbe, $[a,b] \to G$ | a lecsúszó test hely–idő függvénye |

A vonalintegrál a vektormezőt integrálja a görbén; a Newton–Leibniz-formula ezt a skalármező végpontbeli értékkülönbségével fejezi ki.

## Kapocs

- [[concepts/analiii/szakaszonkent-c1-gorbe]] — a harmadik szereplő, a görbe fogalma.
- [[concepts/analiii/valos-vonalintegral]] — a $\sum \langle g(x); \Delta x\rangle$ összegek határértéke.
- [[concepts/analiii/vektormezo-primitiv-fuggvenye]] — a $V$ potenciálfüggvény precíz fogalma.
