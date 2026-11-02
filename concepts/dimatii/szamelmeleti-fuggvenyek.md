---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Számelméleti függvények

A pozitív egészeken értelmezett, komplex értékű függvények; fontos osztályuk az additív és a multiplikatív függvények, amelyeket a kanonikus alak prímhatványokra bontva számol ki.

## Tartalom

**Definíció.** Számelméleti függvény minden $f : \mathbb{N}^+ \to \mathbb{C}$ leképezés. Legyen $m, n \in \mathbb{N}^+$ és $(m,n) = 1$. Az $f$ függvény

- **additív**, ha $f(mn) = f(m) + f(n)$;
- **multiplikatív**, ha $f(mn) = f(m)f(n)$;
- **totálisan (teljesen) additív**, illetve **totálisan (teljesen) multiplikatív**, ha a fenti összefüggések $(m,n) \neq 1$ esetén is fennállnak.

**Észrevételek.** Additív $f$-re $f(1) = 0$; multiplikatív, nem azonosan $0$ $f$-re $f(1) = 1$.

**Tétel (6.3.2).** Legyen $n$ kanonikus alakja $p_1^{\alpha_1}\cdots p_k^{\alpha_k}$. Ekkor

1. additív $f$-re $f(n) = f(p_1^{\alpha_1}) + \dots + f(p_k^{\alpha_k})$;
2. multiplikatív $f$-re $f(n) = f(p_1^{\alpha_1})\cdots f(p_k^{\alpha_k})$;
3. totálisan additív $f$-re $f(n) = \alpha_1 f(p_1) + \dots + \alpha_k f(p_k)$;
4. totálisan multiplikatív $f$-re $f(n) = f(p_1)^{\alpha_1}\cdots f(p_k)^{\alpha_k}$.

A tétel azt jelenti, hogy multiplikatív függvényt elég a prímhatványokon ismerni.

### Példák

1. **Möbius-függvény** (multiplikatív): $\mu(n) = 0$, ha $n$-nek van prímnégyzet osztója; $\mu(n) = (-1)^k$, ha $n$ pontosan $k$ különböző prím szorzata.
2. $\nu(n)$, az $n$ **prímosztóinak száma** (additív).
3. Az 1. és 2. **nem totális**: $0 = \mu(4) \neq \mu(2)^2 = 1$, illetve $1 = \nu(4) \neq 2\nu(2) = 2$.
4. Az azonosan $0$ függvény totálisan additív és totálisan multiplikatív is.
5. Az $n \mapsto n^a$ totálisan multiplikatív, bármely valós $a$-ra.
6. Az $n \mapsto \log_a n$ totálisan additív, bármely $a > 0$ valós számra.
7. Az [[concepts/dimatii/euler-fi-fuggveny]] multiplikatív (nem totálisan: $\varphi(4) = 2 \neq \varphi(2)^2 = 1$); a bizonyítás ugyanott.

A diasor ebben a részben a $\varphi$ és a Möbius-függvény mellett nem tárgyalja külön a $\tau$ és a $\sigma$ függvényt; az osztók számának kanonikus alakból számolását lásd [[concepts/dimatii/osztok-szama]].

## Kapocs

- [[concepts/dimatii/euler-fi-fuggveny]] — a legfontosabb multiplikatív függvény, bizonyítással
- [[concepts/dimatii/osztok-szama]] — kanonikus alakból számolható függvény
- [[concepts/dimatii/szamelmelet-alaptetele]] — a kanonikus alak léte és egyértelműsége
