---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-12
---

# A keresőgráf korrektsége

A keresőgráf korrekt, ha minden csúcsára a $\pi$ szülőpointer és a $g$ költség konzisztens egymással, és a $\pi$ által kijelölt $start \to m$ út optimális a keresőgráfban. Az [[concepts/mesint/altalanos-grafkereso]] ezt az invariánst próbálja fenntartani, de olcsóbb út megtalálásakor ideiglenesen sérülhet.

## Tartalom

### A $\pi$ és $g$ függvények

- $\pi: N \to N$ — **szülőre visszamutató pointer**. $\pi(m)$ az $m$ csúcs egy ismert szülője, $\pi(start) = nil$.
  - $\pi$ egy $start$ gyökerű irányított feszítőfát jelöl ki $G$-n, és segít kiolvasni a megoldási utat terminálás után.
  - Jó lenne, ha egy $m$ csúcs felfedezésekor $\pi(m)$ a $G$-beli **optimális** $start \to m$ utat mutatná.
- $g: N \to \mathbb{R}$ — **költségfüggvény**. $g(m) = c^{\alpha}(start,m)$ egy már megtalált $\alpha \in \{start \to m\}$ út költsége.
  - Jó lenne, ha $g(m)$ a $\pi$ által mutatott $start \to m$ út költségét adná.

### Korrektség

$G$ **korrekt**, ha minden csúcsa korrekt. Az $m \in G$ csúcs **korrekt**, ha

- $g(m)$ és $\pi(m)$ **konzisztens**: $g(m) = c^{\pi}(start,m)$, és
- $\pi(m)$ $G$-ben **optimális**: $c^{\pi}(start,m) = \min_{\alpha \in \{start \to m\} \cap G} c^{\alpha}(start,m)$.

### Karbantartás egy csúcs előállításakor

Kezdetben $\pi(start) := nil$, $g(start) := 0$. Az $n$ csúcs kiterjesztése után minden $m \in \Gamma(n)$ csúcsra:

1. **$m$ új csúcs** ($m \notin G$): $\pi(m) := n$, $g(m) := g(n)+c(n,m)$, $OPEN := OPEN \cup \{m\}$.
2. **$m$ régi csúcs, olcsóbb utat találtunk** ($m \in G$ és $g(n)+c(n,m) < g(m)$): $\pi(m) := n$, $g(m) := g(n)+c(n,m)$.
3. **$m$ régi csúcs, nem találtunk olcsóbb utat** ($g(n)+c(n,m) \ge g(m)$): SKIP.

### Miért romolhat el mégis a korrektség

A 2. eset után $m$ korrekt lesz, de az $m$-ből már korábban továbbvezető utakon a leszármazottak (a diaábra példájában $k$ és $l$, $g(k)=g(l)=5$) **inkorrektek** maradnak, mert $g$-jük a régi, drágább úton alapul. Az $m$ csúcs kiterjesztése ráadásul újra sorra kerülhet. Három lehetőség az olcsóbb úton újra megtalált $m$ leszármazottaival:

1. járjuk be és javítsuk ki a pointereiket és költségeiket;
2. kerüljük el egy jó kiértékelő függvénnyel, hogy ilyen történjen (lásd [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]], csökkenő kiértékelő függvény);
3. az $m$ csúcsot helyezzük vissza $OPEN$ halmazba (az algoritmus 9. sora ezt teszi: $OPEN := OPEN \cup \{m\}$).

## Kapocs

- [[concepts/mesint/altalanos-grafkereso]] — az algoritmus, amely ezt az invariánst karbantartja
- [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]] — csökkenő $f$ mellett a korrektség automatikusan helyreáll
- [[concepts/mesint/a-algoritmus]] — heurisztikus keresések, ahol a visszahelyezés valós probléma
- [[subjects/mesint]] — tárgyi hub
