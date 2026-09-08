---
tags: [concept]
sources: [1.-bevezetés.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Generatív grammatika

A generatív (átírási szabályrendszerre épülő) grammatika egy szintetizáló eszköz, amely szabályok alkalmazásával szavakat állít elő; az általa generált szavak összessége alkotja a grammatika nyelvét. Noam Chomsky vezette be 1956-ban a természetes nyelvek szintaxisának modellezésére.

## Tartalom

### Definíció

Egy $G = (V, \Sigma, R, S)$ rendszer **(generatív) grammatika**, ahol:
- $V$ a **nemterminálisok** ábécéje,
- $\Sigma$ a **terminálisok** ábécéje (feltesszük, hogy $V \cap \Sigma = \emptyset$),
- $S \in V$ egy kitüntetett szimbólum, a **kezdőszimbólum**,
- $R$ az $u \to v$ alakú **átírási szabályok** (röviden szabályok) véges halmaza, ahol $u, v \in (V \cup \Sigma)^*$ és $u$-ban van legalább egy nemterminális.

Ha egy grammatikának az $\alpha$ bal oldalú szabályai $\alpha \to \beta_1, \ldots, \alpha \to \beta_n$ ($n \ge 2$), ezt gyakran $\alpha \to \beta_1 \mid \ldots \mid \beta_n$ alakban írjuk. A szabályok megadásának egyik elterjedt metanyelve a **Backus–Naur-forma (BNF)**, amelyet John Backus vezetett be 1959-ben az ALGOL leírására.

### Levezetés

Legyen $G = (V, \Sigma, R, S)$ grammatika és $u, v \in (V \cup \Sigma)^*$. A $v$ **egy lépésben levezethető** $u$-ból (jele $u \Rightarrow_G v$), ha $u = \alpha\gamma\beta$ és $v = \alpha\gamma'\beta$ valamely $\alpha, \beta, \gamma, \gamma' \in (V \cup \Sigma)^*$-ra úgy, hogy $\gamma \to \gamma' \in R$. Az így kapott relációt **közvetlen levezetési relációnak** nevezzük; egyértelmű $G$ esetén az index elhagyható.

A $G$ által meghatározott **levezetési reláció** $\Rightarrow_G^*$ a $\Rightarrow_G$ reláció reflexív, tranzitív lezártja: $u \Rightarrow^* v$ pontosan akkor, ha vannak olyan $n \ge 0$ és $w_0, \ldots, w_n \in (V \cup \Sigma)^*$ szavak, hogy $u = w_0$, minden $0 \le i \le n-1$-re $w_i \Rightarrow w_{i+1}$, és $w_n = v$.

Az $S$-ből levezethető szavakat **mondatformáknak** nevezzük.

### Generált nyelv

A $G$ által **generált nyelv** azon $\Sigma^*$-beli szavak halmaza, amelyek a kezdőszimbólumból levezethetők:

$$L(G) = \{u \in \Sigma^* \mid S \Rightarrow_G^* u\}$$

Kizárólag terminálisokból álló, a kezdőszimbólumból levezethető szavak halmaza.

### Ekvivalens grammatikák

- **Ekvivalens grammatikák**: ha $L(G_1) = L(G_2)$.
- **Gyengén ekvivalens**: ha $L(G_1)$ és $L(G_2)$ legfeljebb az üres szóban különböznek.

### Normálforma: álterminálisok bevezetése

Minden grammatikához van ekvivalens és azonos típusú $G'$, amelynek szabályaiban a bal oldalon csak nemterminálisok szerepelnek. Ötlet: minden $a \in \Sigma$ terminálishoz bevezetünk egy $\bar{a} \in V$ álterminálisát, és hozzávesszük az $\bar{a} \to a$ szabályokat.

## Kapocs

- [[concepts/bvszam/chomsky-hierarchia]] — a grammatikák típusainak osztályozása
- [[concepts/bvszam/formalis-nyelvek]] — a generált nyelv fogalma
- [[concepts/bvszam/linearis-grammatika]] — speciális 3-as típusú grammatikák
