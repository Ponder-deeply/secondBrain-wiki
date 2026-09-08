---
tags: [concept]
sources: [08.md]
derivation: source
updated: 2026-04-09
---

# Kiszámítható szófüggvény

A kiszámítható szófüggvény a döntési problémák általánosítása: az algoritmus tetszőleges kimeneti szót számít ki (nem csupán igen/nem választ). Ez alapozza meg a [[concepts/bvszam/visszavezetes|visszavezetés]] fogalmát.

## Definíció — TG mint szófüggvény-kiszámító

Az $M = \langle Q, \Sigma, \Delta, \delta, q_0, q_i, q_n \rangle$ TG **kiszámítja** az $f : \Sigma^* \to \Delta^*$ szófüggvényt, ha minden $u \in \Sigma^*$-ra megáll, és megálláskor $f(u)$ olvasható az utolsó szalagon.

**Megjegyzés:** A definíció értelmében $q_i$ és $q_n$ megkülönböztetése felesleges — elegendő egyetlen megállási állapot. (Ezért szokás $q_n$-t zárójelbe írva jelölni.)

## Definíció — kiszámítható függvény

Az $f : \Sigma^* \to \Delta^*$ szófüggvény **kiszámítható**, ha létezik olyan Turing gép, amely kiszámítja. Ez pontosan a Church–Turing tézis értelmében vett algoritmikusan kiszámítható függvény.

## Példa

$$f(u) = ub \quad (u \in \{a, b\}^*)$$

Megvalósítás: a fej jobbra halad a bemenet végéig, majd $b$-t ír és megáll.

## Kapocs

- [[concepts/bvszam/turing-gep]] — TG formális definíciója
- [[concepts/bvszam/visszavezetes]] — $L_1 \leq L_2$ fogalma kiszámítható $f$ segítségével
- [[concepts/bvszam/r-re-nyelvek]] — R és RE osztályok
