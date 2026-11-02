---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: comparison
element: air
updated: 2026-10-12
---

# Nevezetes gráfkereső algoritmusok

Az általános gráfkereső algoritmus az $f$ kiértékelő függvény megválasztásával konkretizálódik: nem-informált (mélységi, szélességi, egyenletes) és heurisztikus (előre tekintő, A, A*, A^c, B, B', A**) keresések adódnak.

## Tartalom

### Osztályozás

- **Nem-informált:** mélységi (MGK), szélességi (SZGK), egyenletes (EGK) gráfkeresés.
- **Heurisztikus:** előre tekintő (mohó, best-first); A, A*, A^c; B, B', A**.

A másodlagos vezérlési stratégiák, az úgynevezett tie-breaking rule-ok (egyenlőséget feloldó szabályok) a nem-informált gráfkereséseknél is tartalmazhatnak heurisztikákat.

### Nem-informált algoritmusok

| Algoritmus | Definíció | Eredmények |
|---|---|---|
| Mélységi gráfkeresés (MGK) | $f = -g$, $c(n,m)=1$ | végtelen gráfokban csak mélységi korláttal garantál megoldást; ugyanúgy mélységi stratégiát használ, mint a visszalépéses keresés |
| Szélességi gráfkeresés (SZGK) | $f = g$, $c(n,m)=1$ | optimális (legrövidebb) megoldást ad, ha van (még végtelen $\delta$-gráfban is); kiterjesztéskor ismeri az odavezető legrövidebb utat (legfeljebb egyszer terjeszti ki) |
| Egyenletes gráfkeresés (EGK) | $f = g$ | optimális (legolcsóbb) megoldást ad, ha van (még végtelen $\delta$-gráfban is); kiterjesztéskor ismeri az odavezető legolcsóbb utat (legfeljebb egyszer terjeszti ki); hasonlít Dijkstra legrövidebb utak algoritmusára |

### Heurisztikus algoritmusok

| Algoritmus | Definíció | Eredmények |
|---|---|---|
| Előre tekintő gráfkeresés | $f = h$ | nincs említhető extra tulajdonsága |
| A algoritmus | $f = g+h$ és $h \ge 0$ | megoldást ad, ha van megoldás (még végtelen $\delta$-gráfban is) |
| A* algoritmus | $f = g+h$, $h \ge 0$ és $h \le h^*$ | optimális megoldást ad, ha van (még végtelen $\delta$-gráfban is) |
| A^c algoritmus | $f = g+h$, $h \ge 0$, $h \le h^*$ és $h(n)-h(m) \le c(n,m)$ | optimális megoldást ad, ha van; kiterjesztéskor ismeri az odavezető legolcsóbb utat (legfeljebb egyszer terjeszti ki) |

Az egyenletes gráfkeresés az $f = g+0$ speciális eset (nulla heurisztikával az $A^c$-ből).

A $B$, $B'$ és $A^{**}$ algoritmusokat a diasor későbbi része tárgyalja (lásd [[concepts/mesint/b-algoritmus]]).

## Kapocs

- [[concepts/mesint/altalanos-grafkereso]] — a keretalgoritmus, amelynek ezek példányai
- [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]] — a $h$-tulajdonságok, amelyek az A/A*/A^c-t megkülönböztetik
- [[concepts/mesint/melysegi-es-szelessegi-grafkereses]] — MGK és SZGK részletesen
- [[concepts/mesint/elore-tekinto-grafkereses]] — az $f=h$ keresés
- [[concepts/mesint/a-algoritmus]] — az A algoritmus
- [[concepts/mesint/a-csillag-algoritmus]] — az A* algoritmus
- [[concepts/mesint/visszalepeses-kereses]] — a mélységi stratégia rokona
- [[subjects/mesint]] — tárgyi hub
