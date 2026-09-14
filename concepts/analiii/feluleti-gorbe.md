---
tags: [concept]
sources: [13_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Felületi görbe

Egy $\mathcal{F}\subset\mathbb{R}^3$ felület egy $F:\mathbb{I}^2\to\mathcal{F}$ paraméterezésében fekvő síkgörbe $F$ általi képe — a felületen futó görbe, amelynek érintője (ha létezik) a felület érintősíkjának meghatározásához szükséges.

## Tartalom

### Definíció

Legyen $\mathcal{F}\subset\mathbb{R}^3$ felület, $F:\mathbb{I}^2\to\mathcal{F}$ ennek egy paraméterezése (l. [[concepts/analiii/parameteres-felulet]]), és legyen $\gamma := (\gamma_1,\gamma_2):[a,b]\to\mathbb{I}^2$ egy $\mathbb{I}^2$-ben fekvő egyszerű sima [[concepts/analiii/parameteres-gorbe|síkgörbe]] paraméterezése. Az $F$ által létesített kép

$$\phi := F\circ\gamma : [a,b]\to\mathcal{F}$$

egy **felületi görbe** egy paraméteres előállítása: a paramétertartományban futó $\gamma$ görbét $F$ "ülteti át" a felületre.

### Érintővektor

Ha $F$ folytonosan deriválható a $(u_0,v_0):=\gamma(t)$ pont körül, akkor a láncszabály szerint a $\phi$ felületi görbe érintőjének iránya a $t\in[a,b]$ pontban

$$\phi'(t) = F'(\gamma(t))\cdot\gamma'(t) = \gamma_1'(t)\cdot\partial_uF(\gamma(t)) + \gamma_2'(t)\cdot\partial_vF(\gamma(t)) \in \mathbb{R}^3.$$

Az érintő tehát mindig benne van az $F(\gamma(t))$ pontban átfektetett, a $\partial_uF(w)$, $\partial_vF(w)$ ($w=\gamma(t)$) lineárisan független vektorokkal (a paraméterezés parciális deriváltjaival) párhuzamos síkban — ez a megfigyelés vezet a felület egy pontbeli [[concepts/analiii/feluleti-erintosik|érintősíkjának]] definíciójához: mivel a $\gamma$ görbe tetszőleges volt, a $P_0=F(u_0,v_0)$ ponton átmenő *összes* reguláris felületi görbe érintője ugyanabban a síkban fekszik.

## Kapocs

- [[concepts/analiii/parameteres-felulet]] — a felület, amelyen a felületi görbe fut, és amelynek paraméterezéséből az érintővektor számolódik
- [[concepts/analiii/feluleti-erintosik]] — a felület pontbeli érintősíkja, amelyet a felületi görbék érintői feszítenek ki
- [[concepts/analiii/parameteres-gorbe]] — a paramétertartományban futó síkgörbe, amelynek $F$ általi képe a felületi görbe
- [[concepts/analiii/lancszabaly]] — a $\phi'(t)=F'(\gamma(t))\cdot\gamma'(t)$ képlet forrása
