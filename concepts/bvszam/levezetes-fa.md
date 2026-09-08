---
tags: [concept]
sources: ["5.-környezetfüggetlen-gramm,-cnf,-cyk-pumpálási-lemma.md", szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Levezetési fa és egyértelműség

A levezetési fa a KF grammatika levezetéseinek gyökeres fa-reprezentációja; egyértelmű grammatikában minden szónak pontosan egy levezetési fája (és pontosan egy baloldali levezetése) van.

## Tartalom

### Levezetési fa definíciója

Egy $G = \langle N, T, P, S \rangle$ grammatika feletti **levezetési fa** gyökeres irányított fa, ahol:
- A gyökér címkéje $S$.
- Minden belső csúcs ($X$ címkéjű) gyerekeinek ($X_1, \ldots, X_m$) balról jobbra sorrendi felsorolása egy $X \to X_1 \cdots X_m \in P$ szabálynak felel meg.
- Minden levél $T \cup \{\varepsilon\}$-beli; az $\varepsilon$-nal jelölt csúcsnak nincs testvére.

**Határ:** a levélcímkék balról jobbra összefűzve alkotják a generált szót.

### Baloldali levezetés

Egy levezetés **baloldali**, ha minden lépésben az aktuális mondatforma **legbaloldalibb** nemterminálisát írjuk át.

> Minden levezetési fához pontosan **egy** baloldali levezetés tartozik (a topológikus sorrendek egyike).

### Egyértelmű grammatika

Egy $G$ KF grammatika **egyértelmű**, ha minden $L(G)$-beli szónak pontosan egy baloldali levezetése (és ezzel pontosan egy levezetési fája) van. Egy $L$ nyelvet **egyértelműnek** nevezünk, ha van olyan egyértelmű grammatika, amely $L$-et generálja.

**Nem egyértelmű grammatika (aritmetikai kifejezések):** a
$$G_{Ar} = (\{E\}, \{(, ), *, +, x, y, z\}, R, E), \quad E \to E + E \mid E * E \mid (E) \mid x \mid y \mid z$$
grammatikában az $x + y * z$ szónak két különböző baloldali levezetése van, amelyek más-más műveleti sorrendnek (jelentésnek) felelnek meg. $G_{Ar}$ tehát nem egyértelmű.

**Ekvivalens egyértelmű grammatika ugyanarra a nyelvre:** a precedenciát nemterminálisokba kódolva
$$E \to E + T \mid T, \quad T \to T * N \mid N, \quad N \to (E) \mid x \mid y \mid z$$
egyértelmű, és ugyanazt az $L_{Ar}$ nyelvet generálja.

> **Inherensen többértelmű nyelvek:** Nem minden KF nyelvhez adható egyértelmű grammatika. Például $L = \{a^n b^n c^m d^m \mid n, m \ge 1\} \cup \{a^n b^m c^m d^n \mid n, m \ge 1\}$ nem egyértelmű KF nyelv.

> **Eldönthetőség:** Egy tetszőleges CF grammatikáról algoritmikusan **nem dönthető el**, hogy egyértelmű-e (ld. [[concepts/bvszam/eldonthetetlen-problemak|eldonthetetlen-problemak]]).

## Kapocs

- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — KF grammatika alapja
- [[concepts/bvszam/chomsky-normalforma]] — CNF esetén a fa bináris
- [[concepts/bvszam/bar-hillel-lemma]] — a levezetési fa mélységéből adódik a pumpálás
- [[concepts/bvszam/generativ-grammatika]] — levezetés, mondatforma
- [[concepts/bvszam/eldonthetetlen-problemak]] — a CF egyértelműség eldönthetetlensége
