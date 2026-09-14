---
tags: [concept]
sources: [SimonP-Anal2.pdf, 06_ea_An3_2022_tavasz.pdf, 07_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.3.2. és 4.3.4. Tétel"]
derivation: source
updated: 2026-09-14
---

# Többváltozós Taylor-formula

A Taylor-polinom hibája kétféleképpen írható le: Lagrange-féle maradéktaggal (egy közbülső pont deriváltjaival) és Peano-féle maradéktaggal ($o(\|h\|^s)$ nagyságrenddel) — az utóbbi az, amit a szélsőérték-elmélet használ.

## Tartalom

### Lagrange-maradéktag

Ha $f \in \mathbb{R}^n \to \mathbb{R}$, $f \in D^{s+1}$, akkor bármely $[a,b] \subset D_f$ szakaszhoz van olyan $c \in [a,b]$, hogy

$$f(b) = T_{a,s}f(b) + \sum_{i\in\mathbb{N}^n,\,|i|=s+1} \frac{\partial^i f(c)}{i!}\cdot (b-a)^i.$$

Az összeget **Lagrange-féle maradéktagnak** nevezzük.

**A bizonyítás sémája — visszavezetés egy változóra.** Legyen $h := b - a$ és $F(t) := f(a + th)$. A $g(t) := a + th$ függvény triviálisan $D^{s+1}$-beli, ezért a [[concepts/analiii/lancszabaly|láncszabály]] többszöri alkalmazásával $F = f \circ g \in D^{s+1}$, és $[0,1] \subset D_F$. Az egyváltozós Taylor-formulát $F$-re alkalmazva egy $\xi \in (0,1)$ hellyel

$$f(b) = F(1) = \sum_{k=0}^s \frac{F^{(k)}(0)}{k!} + \frac{F^{(s+1)}(\xi)}{(s+1)!}.$$

Már csak a

$$\frac{F^{(k)}(t)}{k!} = \sum_{|i| = k} \frac{\partial^i f(a+th)}{i!}\cdot h^i$$

azonosság kell, ami $k$ szerinti indukcióval, minden lépésben a láncszabállyal adódik; ekkor $c := a + \xi h$ megfelel. **Ez a szakasz módszertani magva:** a többváltozós állítást a szakasz paraméterezésével egyváltozós állítássá tesszük.

### Peano-maradéktag

Ha csak $f \in D^s\{a\}$ teljesül **egyetlen pontban** (nem $D^{s+1}$ egy környezetben), akkor van olyan $\eta \in \mathbb{R}^n \to \mathbb{R}$, $\lim_0 \eta = 0$ függvény, amellyel

$$f(a+h) - f(a) = \sum_{k=1}^s \sum_{|i|=k} \frac{\partial^i f(a)}{i!}h^i + \eta(h)\cdot\|h\|^s \qquad (a + h \in D_f),$$

azaz másképp írva

$$\frac{f(x) - T_{a,s}f(x)}{\|x-a\|^s} \to 0 \qquad (\|x - a\| \to 0).$$

Az $s = 1$ eset pontosan az $f \in D\{a\}$ definíció; az általános eset $s$ szerinti indukció.

**Az indukciós lépés vázlata.** $f \in C^s\{a\}$ mellett minden $|i| = s$ multiindexre $\partial^i f(a+h) = \partial^i f(a) + \varepsilon_i(h)$, ahol $\varepsilon_i(h) \to 0$ ($h \to \theta_n$) — ez maga a $D\{a\}$ feltétel az $s-1$-edrendű deriváltakra. Az $(s-1)$-edrendű Lagrange-maradéktagos formulát felírva egy $\nu \in (0,1)$-gyel, majd a maradéktagba behelyettesítve $\partial^i f(a+\nu h) = \partial^i f(a) + \varepsilon_i(\nu h)$-t, a $\eta(h) := \sum_{|i|=s} \frac{\varepsilon_i(\nu h)}{i!}\cdot\frac{h^i}{\|h\|^s}$ függvényre $|\eta(h)| \le M \cdot \sum_{|i|=s}\frac{|\varepsilon_i(\nu h)|}{i!} \to 0$ adódik, ahol $M$ a $\frac{h^i}{\|h\|^s}$ hányadosok korlátja (pl. $\|\cdot\|_\infty$ normában $M=1$).

**Miért ez a hasznosabb.** Kevesebbet tesz fel (egy pontban $D^s$, nem egy környezetben $D^{s+1}$), és a hibát nagyságrendben adja meg, nem egy ismeretlen $c$ pont deriváltjaival. Az $s = 2$ eset

$$f(a+h) - f(a) = \langle \operatorname{grad} f(a), h\rangle + \tfrac12 Q^f_a(h) + \eta(h)\|h\|^2$$

az a formula, amelyre a [[concepts/analiii/lokalis-szelsoertek-feltetelei|szélsőérték-feltételek]] mindhárom bizonyítása épül.

### Alkalmazás: hibabecslés

A Lagrange-alak konkrét numerikus becslést ad: ha az $(s+1)$-edrendű parciális deriváltak korlátosak a szakaszon, a maradéktag $\|b-a\|^{s+1}$ nagyságrendű. Ez a többváltozós közelítő számítások alapja.

## Kapocs

- [[concepts/analiii/tobbvaltozos-taylor-polinom]] — a $T_{a,s}f$ definíciója és a multiindexes jelölés.
- [[concepts/analiii/lagrange-kozepertektetel-tobbvaltozos]] — az $s = 0$ speciális eset.
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — a Peano-alak fő alkalmazása.
- [[concepts/analiii/hesse-matrix]] — a másodrendű tag.
- [[concepts/analiii/lancszabaly]] — a bizonyítás eszköze.
- [[concepts/analii/taylor-formula-maradektag]] — az egyváltozós eredeti, amelyre a bizonyítás visszavezet.
