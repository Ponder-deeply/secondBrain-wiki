---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Szakaszonként folytonosan differenciálható görbe

A $G$-ben fekvő görbe fogalma, az átparaméterezés és a megfordítás, a szakaszonként $C^1$ osztály és a görbe hossza — a vonalintegrál elméletének geometriai alapfogalmai.

## Tartalom

### Görbe egy tartományban

Legyen $G \subset \mathbb{R}^p$ nyílt halmaz. Az $[a,b] \to G$ függvényeket **$G$-ben fekvő görbéknek** hívjuk; az $[a,b]$ intervallum a görbe **paraméter-intervalluma**. Kizárólag **folytonos** görbékkel dolgozunk.

A $\gamma : [a,b] \to G$ görbe **differenciálható**, ha az $(a,b)$ pontjaiban differenciálható, a végpontokban pedig féloldalról differenciálható.

A paramétert szeretjük $t$-vel jelölni, mintha az időt jelentené; a $t$ szerinti deriváltakat (sebességvektor, gyorsulásvektor) pedig pontokkal: $\gamma'$ helyett $\dot\gamma$, $\gamma''$ helyett $\ddot\gamma$.

Fontos, hogy a görbe **a leképezés**, nem pusztán a képhalmaz: az irány és a befutás módja hozzátartozik.

### Szakaszonként $C^1$

**Definíció.** A $\gamma : [a,b] \to G$ görbe **szakaszonként folytonosan differenciálható**, rövidítve **szak.$C^1$**, ha véges sok folytonosan differenciálható görbe egymás után fűzése, vagyis vannak olyan

$$a_0 = a < a_1 < \dots < a_n = b$$

számok, hogy minden $i = 1,2,\dots,n$ esetén $\gamma|_{[a_{i-1},a_i]}$ folytonosan differenciálható.

**Megjegyzés.** Minden **töröttvonal** szakaszonként folytonosan differenciálható görbe, ha a szakaszokat lineárisan paraméterezzük. Ez teszi lehetővé, hogy a primitív függvény létezésének feltételei között a szak.$C^1$ görbéket és a töröttvonalakat egymással helyettesítsük.

### Átparaméterezés és megfordítás

Legyen $\gamma : [a,b] \to G$ és $\varphi : [c,d] \to [a,b]$ bijekció.

- Ha $\varphi$ **szigorúan monoton növő**, akkor $\gamma \circ \varphi : [c,d] \to G$ a $\gamma$ egy **átparaméterezése**.
- Ha $\varphi$ **szigorúan monoton csökkenő**, akkor $\gamma \circ \varphi : [c,d] \to G$ a $\gamma$ egy **megfordítása**.

Az átparaméterezés ugyanazt az utat járja be, csak más ütemben; a megfordítás visszafelé futja be.

### A görbe hossza

**Definíció.** A $\gamma : [a,b] \to G$ **görbe hossza** a beírt töröttvonalak hosszának szuprémuma:

$$\ell(\gamma) = \sup\left\{\sum_{i=1}^{n}\bigl|\gamma(t_i) - \gamma(t_{i-1})\bigr| \;:\; a = t_0 < t_1 < \dots < t_n = b\right\}.$$

Ha ez véges, a görbe **rektifikálható**.

**Trivialitás.** Az átparaméterezés és a megfordítás nem változtatja meg a görbe hosszát — a definícióban szereplő halmaz ugyanaz marad, csak a felosztások címkézése változik.

**Tétel (szakaszonként $C^1$ görbe hossza).** Ha $\gamma : [a,b] \to G$ szak.$C^1$, akkor

$$\ell(\gamma) = \int_{t=a}^{b} \bigl|\dot\gamma(t)\bigr|\,\mathrm{d}t.$$

(Az előző félév anyaga.) Szemléletesen: a hossz a **sebesség nagyságának** időintegrálja.

## Kapocs

- [[concepts/analii/ivhossz]] — az egyváltozós ívhossz, ahol a görbe egy $f : [a,b] \to \mathbb{R}$ függvény **grafikonja**, és a beírt töröttvonalak szuprémuma $\int_a^b \sqrt{1 + f'^2}$. A mostani fogalom ennek általánosítása: a görbe már tetszőleges $\mathbb{R}^p$-beli paraméterezett út, a $\sqrt{1+f'^2}$ helyére pedig a $|\dot\gamma|$ sebességnagyság lép — a grafikon esete a $\gamma(t) = (t, f(t))$ paraméterezés.
- [[concepts/analiii/valos-vonalintegral]] — a szak.$C^1$ osztály éppen az, amelyen a vonalintegrál létezik és kiszámítható.
- [[concepts/analiii/skalarmezo-es-vektormezo]] — a görbe mentén integrált mező fogalma.
- [[concepts/analiii/homotop-gorbek]] — a görbék folytonos átdeformálása.
