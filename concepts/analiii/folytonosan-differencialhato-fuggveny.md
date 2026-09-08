---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 3.1. szakasz zárórésze"]
derivation: source
updated: 2026-09-07
---

# Folytonosan differenciálható függvény ($C^1$)

Az $f$ függvény folytonosan differenciálható egy pontban, ha annak egy egész környezetében differenciálható, és a gradiensei ott folytonosak. Ez ekvivalens azzal, hogy minden $\partial_k f_i$ parciális deriváltfüggvény folytonos a pontban.

## Tartalom

### A definíció

Legyen $f = (f_1, \dots, f_m) \in \mathbb{R}^n \to \mathbb{R}^m$. Azt mondjuk, hogy $f$ **folytonosan differenciálható** (vagy deriválható) az $a \in D_f$ pontban, ha

- van olyan $K(a) \subset D_f$ környezet, hogy minden $x \in K(a)$ helyen $f \in D\{x\}$, **és**
- minden $i = 1, \dots, m$ esetén a $\operatorname{grad} f_i$ függvény folytonos az $a$-ban.

Jelölés: $f \in C^1\{a\}$. Ha ez minden $a \in D_f$ pontban teljesül, akkor $f \in C^1$.

Vegyük észre, hogy a definíció **nem** pontbeli: a differenciálhatóságot egy egész környezetben megköveteli. Ez a pontbeli differenciálhatóságnál lényegesen erősebb feltétel.

### Ekvivalens jellemzés a parciális deriváltakkal

Mivel [[concepts/analiii/gradiens-parcialis-derivaltakbol|$\operatorname{grad} f_i = (\partial_1 f_i, \dots, \partial_n f_i)$]], és egy vektorértékű függvény folytonossága ekvivalens a koordinátafüggvényei folytonosságával, a második feltétel átírható:

$$f \in C^1\{a\} \iff \partial_k f_i \in C\{a\} \quad (i = 1, \dots, m;\ k = 1, \dots, n),$$

feltéve az első pont teljesülését. Fordítva: a [[concepts/analiii/differencialhatosag-elegseges-feltetele|3.1.5. Tétel]] szerint ha az összes $\partial_k f_i$ létezik egy $K(a)$ környezetben és folytonos ott, akkor $f$ automatikusan differenciálható a $K(a)$ minden pontjában — vagyis az első feltétel a másodikból már következik.

**Gyakorlati jelentés:** a $C^1$ osztályba tartozás ellenőrzése tisztán számolási feladat — kiszámítjuk a parciális deriváltakat, és megnézzük, folytonosak-e. Semmi határátmenetet nem kell kézzel elvégezni.

### Miért ez a természetes osztály

A többváltozós analízis erős tételei — az inverz- és implicitfüggvény-tétel, a helyettesítéses integrálás, a Young-tétel a vegyes parciális deriváltak felcserélhetőségéről — jellemzően nem a puszta differenciálhatóságot, hanem a $C^1$ (vagy $C^k$) feltételt követelik meg. Ennek oka a fenti definíció első pontja: a pontbeli differenciálhatóság csak egyetlen pontról mond valamit, míg a bizonyítások környezetbeli, egyenletes viselkedésre támaszkodnak.

## Kapocs

- [[concepts/analiii/differencialhatosag-elegseges-feltetele]] — az a tétel, amely a $C^1$ feltételt a differenciálhatósághoz köti.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a gradiens és a parciális deriváltak kapcsolata, amelyen az ekvivalens jellemzés alapul.
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — a koordinátánkénti visszavezetés ugyanezen a mintán.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — a $C^1$ helye a fogalmi láncban.
