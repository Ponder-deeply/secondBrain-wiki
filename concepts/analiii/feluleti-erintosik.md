---
tags: [concept]
sources: [13_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Felület pontbeli érintősíkja

Egy $\mathbb{R}^3$-beli felület egy szabályos pontjában az összes ott átmenő [[concepts/analiii/feluleti-gorbe|felületi görbe]] érintője közös síkba esik; ezt a síkot nevezzük a felület adott pontbeli érintősíkjának, és a paraméterezéstől függetlenül van értelme.

## Tartalom

### Definíció felületi görbék érintőiből

Legyen $\mathcal{F}\subset\mathbb{R}^3$ egyszerű sima felületdarab, $F:\mathbb{I}^2\to\mathcal{F}$ egy folytonosan deriválható paraméterezése (l. [[concepts/analiii/parameteres-felulet]]), $(u_0,v_0)\in\mathbb{I}^2$ rögzített és $P_0:=F(u_0,v_0)=(x_0,y_0,z_0)$ a megfelelő felületi pont. Minden $P_0$-on átmenő reguláris felületi görbe érintője a $\partial_uF(u_0,v_0)$, $\partial_vF(u_0,v_0)$ lineárisan független vektorokkal párhuzamos síkban fekszik (l. [[concepts/analiii/feluleti-gorbe]] a levezetésért) — ezt a síkot nevezzük a felület $P_0$ **pontbeli érintősíkjának**.

**Igazolható, hogy az érintősík definíciója nem függ a felület paraméterezésétől.**

### Normálvektor és a sík egyenlete

A $P_0$-beli érintősík egy bázisa a lineárisan független $\partial_uF(u_0,v_0)$, $\partial_vF(u_0,v_0)\in\mathbb{R}^3$ vektorpár, a sík egy normálvektora tehát ezek vektoriális szorzata (l. [[concepts/analiii/parameteres-felulet]] a $\mathbf{n}$ definíciójáért):

$$\mathbf{n}(u_0,v_0) = \frac{\partial_uF(u_0,v_0)\times\partial_vF(u_0,v_0)}{|\partial_uF(u_0,v_0)\times\partial_vF(u_0,v_0)|}.$$

Az érintősík egyenlete ($\mathbf{x}:=(x,y,z)$ jelöléssel):

$$0 = \bigl\langle \mathbf{x}-F(u_0,v_0),\ \mathbf{n}(u_0,v_0)\bigr\rangle = \det\begin{bmatrix} x-x_0 & y-y_0 & z-z_0 \\[2pt] \partial_uF_1(u_0,v_0) & \partial_uF_2(u_0,v_0) & \partial_uF_3(u_0,v_0) \\[2pt] \partial_vF_1(u_0,v_0) & \partial_vF_2(u_0,v_0) & \partial_vF_3(u_0,v_0) \end{bmatrix}.$$

### Explicit és implicit alak

Ha a felület $z=g(x,y)$ ($g\in\mathbb{R}^2\to\mathbb{R}$, $g\in C^1$) *explicit alakban*, illetve $G(x,y,z)=0$ ($G\in\mathbb{R}^3\to\mathbb{R}$, $G\in C^1$) *implicit alakban* van megadva (l. [[concepts/analiii/parameteres-felulet]]), akkor a $P_0=(x_0,y_0,z_0)$ pontbeli érintősík normálvektora, illetve egyenlete:

$$\mathbf{n}(P_0) = \bigl(g_x'(x_0,y_0),\,g_y'(x_0,y_0),\,-1\bigr), \qquad z-z_0 = g_x'(x_0,y_0)(x-x_0) + g_y'(x_0,y_0)(y-y_0);$$

illetve

$$\mathbf{n}(P_0) = \bigl(G_x'(P_0),\,G_y'(P_0),\,G_z'(P_0)\bigr), \qquad G_x'(P_0)(x-x_0) + G_y'(P_0)(y-y_0) + G_z'(P_0)(z-z_0) = 0.$$

Az explicit eset pontosan a [[concepts/analiii/fuggvenygrafikon-erintosikja|függvénygrafikon érintősíkja]] lapon tárgyalt speciális eset, ahol az érintősík léte a $g$ totális differenciálhatóságával esik egybe. Az implicit alak $\mathbf{n}(P_0)=\operatorname{grad}G(P_0)$ normálvektora ugyanaz a [[concepts/analiii/nivofelulet-es-gradiens|nívófelület-gradiens merőlegesség]], amelyet a $G(x,y,z)=0$ nívófelület ír le.

## Kapocs

- [[concepts/analiii/feluleti-gorbe]] — a felületi görbék érintői feszítik ki az érintősíkot
- [[concepts/analiii/parameteres-felulet]] — a paraméterezés, a normálvektor $\mathbf{n}$ és a felület megadási módjai
- [[concepts/analiii/fuggvenygrafikon-erintosikja]] — az explicit (függvénygrafikonos) eset mint speciális eset
- [[concepts/analiii/nivofelulet-es-gradiens]] — az implicit alak normálvektora mint gradiens
- [[concepts/analiii/sikvektorok-keresztszorzata]] — a vektoriális szorzat, amellyel a normálvektor számolódik
