---
tags: [concept]
sources: [1.-bevezetés.md]
derivation: source
updated: 2026-04-07
---

# Homomorfizmus

A homomorfizmus két ábécé feletti szavak halmaza között értelmezett, konkatenációt megőrző leképezés; segítségével az egyik nyelv képe egy másik ábécé fölé vihető.

## Tartalom

### Definíció

Legyen $V_1$ és $V_2$ két ábécé. A $h : V_1^* \to V_2^*$ leképezés **homomorfizmus**, ha:
1. Minden szóra pontosan egy kép van (egyértelmű).
2. $h(uv) = h(u)h(v)$ minden $u, v \in V_1^*$-ra.

**Következmény:** $h(\varepsilon) = \varepsilon$, és $h$ teljesen meghatározott az ábécé betűin felvett értékekből:
$$h(a_1 a_2 \cdots a_n) = h(a_1) h(a_2) \cdots h(a_n)$$

### ε-mentes homomorfizmus

$h$ **ε-mentes**, ha minden $u \in V_1^+$-ra $h(u) \neq \varepsilon$ (azaz egyetlen nemüres szót sem képez).

### Homomorf kép

Az $L \subseteq V_1^*$ nyelv **$h$-homomorf képe**: $h(L) = \{h(u) \mid u \in L\}$.

> **Példa:** $V_1 = \{a,b\}$, $V_2 = \{b,c\}$, $h(a) = cc$, $h(b) = cbb$, $L = \{a^n b a^n \mid n \in \mathbb{N}\}$
> → $h(L) = \{c^{2n+1} b^2 c^{2n} \mid n \in \mathbb{N}\}$

## Kapocs

- [[concepts/bvszam/formalis-nyelvek]] — nyelvi műveletek általában
- [[concepts/bvszam/chomsky-hierarchia]] — a homomorf képek megőrizhetik vagy csökkenthetik a típust
