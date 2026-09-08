---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Homotóp görbék

Két görbe $G$-ben homotóp, ha a tartományon belül folytonosan átdeformálható egymásba; a nullhomotóp zárt görbe egyetlen pontra húzható össze.

## Tartalom

### Közös kezdő- és végpontú homotóp görbék

**Definíció.** Legyen $G \subset \mathbb{R}^p$, és $\gamma_0, \gamma_1 : [0,1] \to G$ közös kezdő- és végpontú folytonos görbék, tehát $\gamma_0(0) = \gamma_1(0)$ és $\gamma_0(1) = \gamma_1(1)$.

A $\gamma_0$ és a $\gamma_1$ görbe $G$-ben **homotóp** egymással, ha folytonosan átdeformálhatók egymásba, vagyis létezik olyan $H : [0,1]\times[0,1] \to G$ folytonos függvény, amelyre

- **(a)** bármely $t \in [0,1]$-re $H(t,0) = \gamma_0(t)$ és $H(t,1) = \gamma_1(t)$;
- **(b)** bármely $u \in [0,1]$-re $H(0,u) = \gamma_0(0) = \gamma_1(0)$ és $H(1,u) = \gamma_0(1) = \gamma_1(1)$.

Szemléletesen: rögzített $u$ mellett $t \mapsto H(t,u)$ az „$u$-adik" görbe. Az (a) tulajdonság szerint a $0$-adik görbe $\gamma_0$, az $1$-edik $\gamma_1$; a (b) azt követeli meg, hogy a közbülső görbék kezdő- és végpontja is ugyanaz maradjon.

Döntő, hogy $H$ értékei **végig $G$-ben** vannak: a deformáció nem léphet ki a tartományból. Éppen ezért lesz a homotópia a tartomány alakjának — nem a görbéknek — a jellemzője.

### Homotóp zárt görbék

**Definíció.** Legyen $\gamma_0, \gamma_1 : [0,1] \to G$ folytonos **zárt** görbék, tehát $\gamma_0(0) = \gamma_0(1)$ és $\gamma_1(0) = \gamma_1(1)$.

A két görbe $G$-ben **homotóp**, ha van olyan $H : [0,1]\times[0,1] \to G$ folytonos függvény, amelyre

- **(a)** bármely $t \in [0,1]$-re $H(t,0) = \gamma_0(t)$ és $H(t,1) = \gamma_1(t)$;
- **(b)** bármely $u \in [0,1]$-re $H(0,u) = H(1,u)$.

Itt a (b) tulajdonság azt követeli meg, hogy a közbülső görbék is **zártak** legyenek — a kezdő- és végpont mozoghat, csak egybe kell esnie.

### Nullhomotóp görbe

**Definíció.** Legyen $\gamma$ folytonos zárt görbe $G$-ben. A $\gamma$ görbe $G$-ben **nullhomotóp**, más néven **(egy) pontra (össze)húzható**, ha homotóp egy egypontú (konstans) görbével.

Ez a fogalom fordítja le a „a görbe nem fog körbe semmilyen lyukat" szemléletet a matematika nyelvére: a kilyukasztott síkban az origó körüli körvonal nem húzható össze, mert a deformáció közben át kellene haladnia a hiányzó ponton.

## Kapocs

- [[concepts/analiii/vonalintegral-homotop-gorbeken]] — a homotópia fő analízisbeli következménye: homotóp görbéken a vonalintegrál megegyezik.
- [[concepts/analiii/egyszeresen-osszefuggo-tartomany]] — az a tartományosztály, amelyben minden zárt görbe nullhomotóp.
- [[concepts/analiii/szakaszonkent-c1-gorbe]] — a görbe és az átparaméterezés fogalma; a homotópia ennél gyengébb, pusztán folytonossági követelmény.
- [[concepts/analiii/primitiv-fuggveny-csillagszeru-tartomanyon]] — a csillagszerűség az a geometriai feltétel, amelyet a homotópia topológiaira cserél.
