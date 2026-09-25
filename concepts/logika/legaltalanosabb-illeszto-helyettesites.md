---
tags: [concept, logika/rezolucio-elsorendu-logika]
sources: [Rezolúció_II.pdf]
references: [Tk. 273. o.]
derivation: source
updated: 2026-09-08
---

# Legáltalánosabb illesztő helyettesítés

A legáltalánosabb illesztő helyettesítés (unifikáció) egy olyan helyettesítés, amely azonos predikátumszimbólumú atomi formulák egy halmazát szintaktikailag azonossá teszi, és amelyből minden más illesztő helyettesítés egy további helyettesítéssel előáll; ez teszi lehetővé, hogy az elsőrendű rezolúció két literált a lehető legkevesebb megkötéssel egyesítsen.

## Tartalom

### Összeférhetetlenségi halmaz

Legyen $W$ azonos predikátumszimbólumot tartalmazó atomi formulák legalább kételemű véges halmaza. Vizsgáljuk $W$ elemeit szimbólumonként, párhuzamosan, balról jobbra haladva, és álljunk meg annál az első szimbólumnál, amelyik $W$ nem minden atomi formulájában egyforma. Emeljük ki $W$ minden atomi formulájából azt a résztermet, amely az ezen a pozíción lévő szimbólummal kezdődik. E résztermek $D$ halmaza $W$ **összeférhetetlenségi halmaza**.

### Az algoritmus

Legyen $W$ a vizsgált atomi formulahalmaz.

1. $k := 0$, $W_k := W$, $\sigma_k := \varepsilon$ (az üres helyettesítés).
2. Ha $W_k$ egyelemű, a legáltalánosabb illesztő helyettesítés $\sigma_k$. Stop.
3. $D_k$ (összeférhetetlenségi halmaz) megszerkesztése.
4. Ha van $D_k$-ban olyan $x_k$ változó és $t_k$ term, hogy $x_k$ nem fordul elő $t_k$-ban, folytatás az 5. lépéssel. Egyébként nincs illesztő helyettesítés — Stop.
5. $\sigma_{k+1} := \sigma_k(x_k \| t_k)$, $W_{k+1} := \{A(x_k \| t_k) \mid A \in W_k\}$. (Megjegyzés: $W_{k+1} = \{A\sigma_{k+1} \mid A \in W\}$.)
6. $k := k+1$, ugrás a 2. lépésre.

A 4. lépés feltétele az ún. *occurs check*: ha $x_k$ előfordulna $t_k$-ban, a helyettesítés végtelen termet eredményezne, ezért ilyenkor nincs illesztő helyettesítés.

### Példa — sikeres unifikáció

$W = \{Q(f(a), g(x)),\ Q(y,y)\}$

1. $k=0$, $W_0 = W$, $\sigma_0 = \varepsilon$.
2. $W_0$ nem egyelemű.
3. $D_0 = \{f(a), y\}$.
4. $x_0 = y$, $t_0 = f(a)$ — $y$ nem fordul elő $f(a)$-ban.
5. $\sigma_1 = (y \| f(a))$, $W_1 = W_0(y \| f(a)) = \{Q(f(a), g(x)),\ Q(f(a), f(a))\}$.
6. $k := 1$.
2. $W_1$ nem egyelemű.
3. $D_1 = \{g(x), f(a)\}$.
4. $D_1$-ben nincs változó — **sikertelen**: $Q(f(a), g(x))$ és $Q(y,y)$ nem unifikálható.

### Faktor és bináris rezolvens az illesztő helyettesítéssel

Az illesztő helyettesítés két alkalmazása az elsőrendű rezolúcióban:

- **Faktor:** ha egy elsőrendű klózban legalább két azonos alapú, egyformán negált literál illeszthető, és $\sigma$ a legáltalánosabb illesztő helyettesítés, akkor a klóz $\sigma$-val kapott példánya a klóz **faktora**. Példa: $\forall x \forall y (P(x) \vee P(f(y)) \vee \lnot Q(x))$ faktora $\sigma = (x \| f(y))$ helyettesítéssel $\forall x \forall y (P(f(y)) \vee \lnot Q(f(y)))$.
- **Bináris rezolvens:** ha $C_1, C_2$ változóidegen elsőrendű klózok magjai $C_1 = C_1' \vee L_1$, $C_2 = C_2' \vee \lnot L_2$ alakúak, és $L_1, L_2$ egy $\sigma$ legáltalánosabb illesztő helyettesítéssel illeszthetők, akkor $C_1, C_2$ **bináris rezolvense** a $C_1'\sigma \vee C_2'\sigma$ magú elsőrendű klóz. $C_1, C_2$ a **szülő klózok**.

E két fogalom együtt vezet az [[concepts/logika/elsorendu-rezolucio|elsőrendű rezolvens]] fogalmához.

## Kapocs

- [[concepts/logika/term]] — a termek, amelyeken az illesztő helyettesítés dolgozik
- [[concepts/logika/elsorendu-kloz]] — a klózok, amelyek literáljait az illesztő helyettesítés unifikálja
- [[concepts/logika/elsorendu-rezolucio]] — a faktor és a bináris rezolvens felhasználása az elsőrendű rezolvens definíciójában
