---
tags: [concept, bigdata/gepi-tanulas-klaszterezes-es-dimenziocsokkentes]
sources: [BDAEM-2022-EA10.pptx]
derivation: source
updated: 2026-09-12
---

# Sajátvektor és sajátérték

A sajátvektor és sajátérték egy négyzetes mátrix azon jellemző irányait és
skálázási tényezőit írja le, amelyeket a mátrix lineáris transzformációként
alkalmazva nem forgat el, csak nyújt vagy zsugorít — ez adja a PCA
matematikai alapját.

## Tartalom

### Definíció

Egy $A$ négyzetes mátrixra $x$ ($x \ne 0$) sajátvektor és $\lambda$
sajátérték, ha:
$$Ax = \lambda x$$

- $A$: négyzetes mátrix
- $x$: sajátvektor (characteristic vector)
- $\lambda$: sajátérték (characteristic value)

A nullvektor sohasem lehet sajátvektor, de a $\lambda = 0$ érték lehet
sajátérték.

### A sajátértékek meghatározása

Az egyenlet átrendezhető:
$$Ax - \lambda x = 0 \quad\Rightarrow\quad (A - \lambda I)x = 0$$

Ha bevezetjük a $B = A - \lambda I$ mátrixot, akkor $Bx = 0$. Mivel $x$ nem
lehet a nullvektor, $B$-nek **nem szabad** invertálhatónak lennie — ha
invertálható lenne, abból $x = B^{-1} \cdot 0 = 0$ következne, ami ellentmond
annak, hogy $x$ sajátvektor. Tehát $x$ pontosan akkor sajátvektora $A$-nak, ha
$B$ szingluráris, azaz:
$$\det(A - \lambda I) = 0$$

Ez a *karakterisztikus egyenlet*, amelynek gyökei adják $A$ sajátértékeit.

### Multiplicitás

A karakterisztikus egyenlet gyökei ismétlődhetnek: ha
$\lambda_1 = \lambda_2 = \dots = \lambda_k$, akkor az adott sajátértéket
$k$-szoros multiplicitásúnak nevezzük.

## Kapocs

- [[concepts/bigdata/pca]] — a PCA a kovarianciamátrix sajátvektorait és
  sajátértékeit használja a főkomponensek (legnagyobb varianciájú irányok)
  meghatározására
- [[concepts/bigdata/kovariancia]] — a PCA-ban a sajátvektor/sajátérték-
  felbontást a kovarianciamátrixra alkalmazzuk
</content>
