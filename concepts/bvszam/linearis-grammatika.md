---
tags: [concept]
sources: [2.-lingram-és-regexp.md]
derivation: source
updated: 2026-04-07
---

# Lineáris grammatika

A lineáris grammatika a környezetfüggetlen grammatika azon speciális esete, amelynek minden szabályában legfeljebb egy nemterminális szerepel a jobb oldalon; a jobb-lineáris grammatikák pontosan a reguláris grammatikákat fedik le.

## Tartalom

### Definíció

Egy $G = \langle N, T, S, R \rangle$ KF grammatika **lineáris**, ha minden szabálya vagy:
- $A \to u$ ($u \in T^*$), vagy
- $A \to u_1 B u_2$ ($A, B \in N$, $u_1, u_2 \in T^*$).

**Bal-lineáris**: minden $A \to u_1 B u_2$ szabályban $u_1 = \varepsilon$ (a nemterminális balra kerül).

**Jobb-lineáris**: minden $A \to u_1 B u_2$ szabályban $u_2 = \varepsilon$ (a nemterminális jobbra kerül). Ez egyenértékű a 3-as típusú (reguláris) grammatikával.

> **Példák:**
> - $S \to aSb \mid \varepsilon$ — lineáris, de nem bal- és nem jobb-lineáris
> - $S \to Saa \mid b$ — bal-lineáris
> - $S \to aS \mid bbS \mid c$ — jobb-lineáris

### Bal-lineáris ↔ jobb-lineáris ekvivalencia

> **Tétel:** Minden bal-lineáris grammatikához van ekvivalens jobb-lineáris grammatika (és viszont), tehát minden bal-lineáris grammatika reguláris nyelvet generál.

**Bizonyítás ötlete:** Ha $G$ bal-lineáris, konstruálunk $G'$ jobb-lineáris grammatikát az $R'$ szabályhalmazzal:
1. $S \to u \in R' \iff S \to u \in R$
2. $S \to u A_k \in R' \iff A_k \to u \in R$
3. $A_j \to u A_k \in R' \iff A_k \to A_j u \in R$
4. $A_j \to u \in R' \iff S \to A_j u \in R$

### $\mathcal{L}_3$ zártsága tükrözésre

Minden jobb-lineáris grammatikából bal-lineáris grammatika kapható az $A \to u$ és $A \to uB$ szabályok helyett $A \to u^{-1}$ és $A \to B u^{-1}$ szabályokkal. Ebből következik, hogy $\mathcal{L}_3$ zárt a tükrözésre, és minden reguláris nyelv bal-lineáris grammatikával is generálható.

## Kapocs

- [[concepts/bvszam/chomsky-hierarchia]] — a 3-as típus definíciója
- [[concepts/bvszam/regularis-normalforma]] — 3-as típusú normálalak
- [[concepts/bvszam/regularis-kifejezesek]] — a reguláris nyelvek leírásának másik eszköze
