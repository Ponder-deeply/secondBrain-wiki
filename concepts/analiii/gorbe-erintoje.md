---
tags: [concept]
sources: [12_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Görbe érintője

Egy sima elemi görbe adott pontbeli érintőegyenese a paraméterezés deriváltvektora által kifeszített, a ponton áthaladó egyenes; az érintő maga független a paraméterezés megválasztásától.

## Tartalom

### Egyszerű sima görbe

**Definíció.** A $\Gamma \subset \mathbb{R}^n$ halmaz **egyszerű sima görbe**, ha létezik olyan $\varphi \in C^1(I, \mathbb{R}^n)$ leképezés ($I = [a,b] \subset \mathbb{R}$ nemüres kompakt intervallum), hogy $\varphi : I \to \Gamma$ bijekció és $\varphi'(t) \neq \theta$ minden $t \in I$-re. A $\varphi$ leképezést a $\Gamma$ görbe **paraméterezésének** (paraméteres előállításának) nevezzük.

Ez a [[concepts/analiii/parameteres-gorbe]] lapon bevezetett, még csak folytonosságot feltételező görbefogalom finomítása: az injektivitás kizárja az önmetszéseket, a $\varphi'(t) \neq \theta$ feltétel pedig a "megtörés nélküli", sima befutást biztosítja.

**Megjegyzés (a paraméterezés nem egyértelmű).** A görbéknek nemcsak egy paraméterezése létezik. Ha $\varphi \in C^1(I, \mathbb{R}^n)$ a $\Gamma$ egy paraméterezése, $J \subset \mathbb{R}$ kompakt intervallum, és $\gamma : J \to I$ olyan folytonosan deriválható bijekció, amelynek a deriváltja sehol sem tűnik el, akkor $\varphi \circ \gamma \in C^1(J, \mathbb{R}^n)$ kölcsönösen egyértelmű leképezés $J$ és $\Gamma$ között, amelynek a deriváltja szintén nem nulla — következésképpen $\varphi \circ \gamma$ ugyanannak a $\Gamma$ görbének egy másik paraméterezése. Ez a [[concepts/analiii/szakaszonkent-c1-gorbe]] lapon tárgyalt átparaméterezés/megfordítás fogalmának a sima elemi görbékre szűkített, deriválhatósági feltételekkel élesített változata.

**Példák.**
- $\Gamma_1 := [a,b] := \{a + (b-a)t \mid 0 \le t \le 1\} \subset \mathbb{R}^n$ ($a, b \in \mathbb{R}^n$ különböző pontok) az $a, b$ pontokat összekötő **szakasz**.
- $\Gamma_2 := \{a + (b-a)t \mid t \in \mathbb{R}\} \subset \mathbb{R}^n$ az $a, b$ pontokon átmenő **egyenes**; $b - a$ az egyenes egy irányvektora.

### Az érintő definíciója

**Definíció.** Legyen $\Gamma \subset \mathbb{R}^n$ egy sima elemi görbe. Tegyük fel, hogy $\varphi \in C^1(I, \mathbb{R}^n)$ a $\Gamma$ egy paraméteres előállítása, és $b := \varphi(t_0) \in \Gamma$. A

$$\{\varphi'(t_0) \cdot t + \varphi(t_0) \mid t \in \mathbb{R}\} \subset \mathbb{R}^n$$

egyenest a $\Gamma$ görbe $b$ pontbeli **érintőjének** nevezzük.

Világos, hogy a $\varphi(t_0)$ pontbeli érintő "áthalad" a $\varphi(t_0)$ ponton, és $\varphi'(t_0)$ a szóban forgó érintő egy irányvektora.

**Az érintő független a paraméterezéstől.** Könnyen ellenőrizhető, hogy az érintő nem függ attól, melyik $\varphi$ paraméterezéssel írjuk le a $\Gamma$ görbét — csak a görbén (mint ponthalmazon) és a kiválasztott ponton múlik. Ez a fizikai szemléletnek is megfelel: ha $\varphi(t)$ egy tömegpont pályáját írja le, akkor $\varphi'(t_0)$ a $t_0$ időpillanatbeli sebességvektor, az érintő pedig az a pillanatnyi mozgásirány, amelyet a pálya alakja (és nem az időzítés) határoz meg.

## Kapocs

- [[concepts/analiii/parameteres-gorbe]] — az általánosabb, csak folytonosságot feltételező görbefogalom, amelynek az egyszerű sima görbe a finomítása
- [[concepts/analiii/szakaszonkent-c1-gorbe]] — a görbe fogalmának egy másik, integrálelméleti irányú finomítása: nyílt tartományban fekvő, szakaszonként $C^1$ görbe, átparaméterezéssel és megfordítással
- [[concepts/analiii/sikgorbe-megadasi-modok]] — a síkgörbék ($n=2$) megadásának különböző módjai, amelyeken az érintőfogalom alkalmazható
- [[concepts/analiii/jacobi-matrix]] — a deriváltfogalom többváltozós megfelelője, amelynek az $n$-dimenziós vektorértékű $\varphi'(t)$ derivált az $1$-változós speciális esete
