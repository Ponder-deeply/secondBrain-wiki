---
tags: [concept]
sources: [01_ea_An3_2025_osz.pdf]
derivation: source
updated: 2026-09-14
---

# Paraméteres görbe

Egy $\Gamma \subset \mathbb{R}^m$ halmaz görbe, ha előáll egy $[a,b] \to \mathbb{R}^m$ folytonos függvény értékkészleteként; a függvény a görbe egy paraméterezése. Ez az általános, még differenciálhatóságot nem feltételező görbefogalom, amelyre a későbbi fejezetek (ívhossz, vonalintegrál) ráépülnek.

## Tartalom

### Definíció

Legyen $f \in \mathbb{R} \to \mathbb{R}^m$ ($1 < m \in \mathbb{N}$) függvény, azaz valós változós, vektorértékű: $f(t) = (f_1(t), f_2(t), \dots, f_m(t)) \in \mathbb{R}^m$ ($t \in [a,b]$), ahol az $f_i : [a,b] \to \mathbb{R}$ **koordinátafüggvények** mindegyike folytonos.

**Definíció.** Egy $\Gamma \subset \mathbb{R}^m$ halmazt **görbének** nevezünk, ha létezik olyan $f : [a,b] \to \mathbb{R}^m$ függvény, amelynek az értékkészlete $\Gamma$. Ekkor $f$-et a $\Gamma$ görbe egy (paraméteres) **paraméterezésének** nevezzük.

- $m = 2$ esetén **síkgörbéről**, $m = 3$ esetén **térgörbéről** beszélünk.
- Fizikai szemléltetésben minden pontszerű test (tömegpont) $t \in [a,b]$ időpillanatbeli helyvektorát $f(t)$ írja le; ekkor $\Gamma$ a mozgó pont **pályagörbéje**.
- Ugyanaz a $\Gamma$ ponthalmaz **több, lényegesen különböző paraméterezéssel** is előállítható — a görbe a leképezés, a paraméterezés csak az egyik lehetséges befutási módja.

### Példák

- **Síkbeli egyenes.** $u, v \in \mathbb{R}^2$, $v \neq \theta$ esetén a $\Gamma_{u,v} := \{u + t\cdot v \mid t \in \mathbb{R}\}$ egyenes paraméterezése $f(t) := (u_1 + t\cdot v_1,\, u_2 + t\cdot v_2)$.
- **Félkörív.** $f(t) := (\cos t, \sin t)$ ($t \in [0,\pi]$), illetve ugyanennek a görbének egy másik paraméterezése $g(x) := (x, \sqrt{1-x^2})$ ($x \in [-1,1]$).
- **Kardioid.** $f(t) := (2\cos t - \cos 2t,\, 2\sin t - \sin 2t)$ ($t \in [0, 2\pi]$).
- **Arkhimédészi spirális.** $f(t) := (t\cos t,\, t\sin t)$ ($t \geq 0$).
- **Csavarvonal (helix).** Az $a$ sugarú hengerre írható, $m$ menetemelkedésű térgörbe: $f(t) := \bigl(a\cos t,\, a\sin t,\, \frac{m}{2\pi} t\bigr)$ ($t \in \mathbb{R}$).

### Kapcsolódás a többváltozós függvényekhez

A görbe az $\mathbb{R} \to \mathbb{R}^m$ (vektorértékű) függvények speciális esete. Az általánosabb $f \in \mathbb{R}^n \to \mathbb{R}^m$ ($1 < n, m$) leképezéseket **vektor-vektor függvényeknek** hívjuk; ezek is koordinátafüggvényekkel írhatók fel. Az $n$-változós, skalárértékű ($m=1$) esetben két nevezetes ponthalmazt szokás vizsgálni: az $f : H \to \mathbb{R}$ ($H \subset \mathbb{R}^n$) **grafikonja** az $\{(x_1,\dots,x_n,f(x_1,\dots,x_n)) : x \in H\} \subset \mathbb{R}^{n+1}$ halmaz, a **szintvonala** (nívóvonala) pedig egy adott $c$ értékhez tartozó $\{x \in D_f : f(x) = c\}$ halmaz — ez utóbbi a [[concepts/analiii/nivofelulet-es-gradiens]] lapon tárgyalt nívófelület speciális ($n=2$) esete.

## Kapocs

- [[concepts/analiii/szakaszonkent-c1-gorbe]] — a görbefogalom finomítása: nyílt tartományban fekvő, szakaszonként folytonosan differenciálható görbe, a vonalintegrál elméletének alapja
- [[concepts/analiii/nivofelulet-es-gradiens]] — a szintvonal/nívófelület mint speciális ponthalmaz $n$ változós skalármezőre
- [[concepts/analiii/skalarmezo-es-vektormezo]] — a görbe menti integrálás alapszókincse, amely erre a görbefogalomra épül
- [[concepts/analiii/metrikus-ter]] — a $\Gamma$ görbe az $\mathbb{R}^m$ euklideszi (és így metrikus) terében fekvő ponthalmaz
