---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Egyszeresen összefüggő tartomány

Olyan összefüggő nyílt halmaz, amelyben minden zárt görbe nullhomotóp. Ez a végleges topológiai feltétel, amely mellett a rotációmentesség már elégséges a primitív függvény létezéséhez.

## Tartalom

### Definíció

**Definíció.** Legyen $G \subset \mathbb{R}^p$ összefüggő nyílt. A $G$ **egyszeresen összefüggő**, ha minden $G$-ben fekvő zárt görbe nullhomotóp, azaz $G$-n belül egy pontra összehúzható.

Szemléletesen: a tartománynak nincsenek olyan „lyukai", amelyeket egy hurok körülfoghatna.

### Példák

**Egyszeresen összefüggő tartományok:**

- $\mathbb{R}^p$;
- minden konvex tartomány;
- minden csillagszerű tartomány;
- $\mathbb{R}^3\setminus\{(0,0,0)\}$ — a **térben** egy pont kilyukasztása nem árt: a hurok kikerülheti a hiányzó pontot, és úgy húzódhat össze.

**Nem egyszeresen összefüggő tartományok:**

- $\mathbb{R}^2\setminus\{(0,0)\}$ — a kilyukasztott sík;
- $\mathbb{R}^2\setminus B((0,0),1)$ — a síkból kivágott zárt körlemez komplementere;
- $\mathbb{R}^3\setminus\{(t,t,t) : t \in \mathbb{R}\}$ — a térből kivett **egyenes**;
- $\mathbb{R}^3\setminus\{(\cos t, \sin t, 0) : t \in [0,2\pi]\}$ — a térből kivett **körvonal**.

A $\mathbb{R}^3\setminus\{pont\}$ és a $\mathbb{R}^3\setminus\{egyenes\}$ szembeállítása mutatja, hogy nem a kivett halmaz mérete, hanem a **kodimenziója** számít: egy $2$ kodimenziós akadály körül lehet hurkolni, egy $3$ kodimenziós körül nem.

### A fő tétel

**Tétel (a primitív függvény létezése egyszeresen összefüggő tartományon).** Legyen $G \subset \mathbb{R}^p$ egyszeresen összefüggő, nyílt, és $f : G \to \mathbb{R}^p$ **differenciálható** vektormező. Az $f$-nek akkor és csak akkor van primitív függvénye, ha $f$ rotációmentes.

**Bizonyítás.** A „csak akkor" irányt már tudjuk (a Jacobi-mátrix a primitív függvény Hesse-mátrixa, és a Young-tétel szerint szimmetrikus).

Fordítva: ha $f$ rotációmentes, akkor a Goursat-lemma következménye szerint $f$-nek **lokálisan** létezik primitív függvénye. A tartomány egyszeresen összefüggő, ezért $G$-ben minden zárt görbe — speciálisan minden zárt töröttvonal — nullhomotóp. A homotóp görbékről szóló tétel (c) pontja szerint tehát minden zárt töröttvonalon $0$ az $f$ vonalintegrálja, a konzervativitás ekvivalenciatétele szerint pedig ekkor van primitív függvénye.

### Az elmélet íve

A fejezet végén így áll össze a teljes kép differenciálható vektormezőkre:

| Feltétel a tartományra | Rotációmentesség elég? | Eszköz |
|---|---|---|
| tetszőleges összefüggő nyílt | nem (kilyukasztott sík) | ellenpélda |
| konvex | igen | Goursat-lemma + átlós felbontás |
| csillagszerű | igen | Goursat-lemma + a középpontból való felbontás |
| egyszeresen összefüggő | igen | homotópia + lokális primitív függvény |

A lokális feltétel (rotációmentesség) és a globális következtetés (primitív függvény létezése) közötti szakadékot tehát pontosan a tartomány topológiája hidalja át — és a kilyukasztott sík „szög" függvénye az a példa, ahol a híd leszakad.

## Kapocs

- [[concepts/analiii/homotop-gorbek]] — a nullhomotópia fogalma, amelyre a definíció épül.
- [[concepts/analiii/vonalintegral-homotop-gorbeken]] — a tétel bizonyításának fő eszköze.
- [[concepts/analiii/primitiv-fuggveny-csillagszeru-tartomanyon]] — a szűkebb, geometriai feltételekkel dolgozó előző lépcsőfok.
- [[concepts/analiii/rotaciomentes-vektormezo]] — a feltétel, amely itt válik elégségessé, és az ellenpélda, amely mutatja, hogy a topológia nélkülözhetetlen.
- [[concepts/analiii/konzervativ-vektormezo]] — a bizonyítás záró lépése.
