---
tags: [concept]
sources: [1.-bevezetés.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Ábécé, szavak és műveletek

Az ábécé, a szó és a rajtuk értelmezett műveletek (konkatenáció, hatványozás, tükrörkép) a formális nyelvek elméletének legalsó szintű alapfogalmai.

## Tartalom

### Ábécé és szavak

- **Ábécé** ($\Sigma$, néhány forrásban $V$): véges, nemüres szimbólumhalmaz; elemei a **betűk**. A formális nyelvi ábécé betűi tetszőleges szimbólumok lehetnek.
- **Szó** ($\Sigma$ felett): a $\Sigma$ betűinek tetszőleges véges sorozata; jelölés $u = t_1 \cdots t_n$, hossza $l(u) = |u| = n$.
- **Üres szó**: $\varepsilon$, $l(\varepsilon) = 0$.
- $\Sigma^*$: az összes $\Sigma$ feletti szó halmaza (beleértve $\varepsilon$-t).
- $\Sigma^+ = \Sigma^* \setminus \{\varepsilon\}$: nemüres szavak halmaza.
- **Betűszámláló:** $a \in \Sigma$ esetén $l_a(u)$ az $u$-beli $a$ betűk száma.
- A szavak kanonikális rendezése: **hosszlexikografikus (shortlex) sorrend**.

> A jegyzet (Gazdag) az ábécét $\Sigma$-val jelöli. A [[concepts/bvszam/generativ-grammatika|grammatikáknál]] $V$ a nemterminálisok ábécéjét jelöli — ne keverjük össze.

### Konkatenáció

Ha $u = s_1 \cdots s_n$ és $v = t_1 \cdots t_k$, akkor $uv = s_1 \cdots s_n t_1 \cdots t_k$.

- $|uv| = |u| + |v|$
- Asszociatív, de általában **nem kommutatív**
- Egységelem: $\varepsilon$
- $V^*$ konkatenációra zárt (monoid)

### Hatványozás

$u^0 := \varepsilon$, $u^i := u \cdot u^{i-1}$. Tulajdonság: $u^{n+k} = u^n u^k$.

### Tükrörkép

Az $u = a_1 \cdots a_n$ szó **tükörképe**: $u^{-1} = a_n \cdots a_1$.

- $(uv)^{-1} = v^{-1} u^{-1}$
- Ha $u = u^{-1}$, az $u$ **palindróma**.

### Részszó, prefix, suffix

- $u$ **részszava** $v$-nek, ha $v = xuy$ valamely $x,y \in V^*$-ra.
- Ha $x = \varepsilon$: **prefix**; ha $y = \varepsilon$: **suffix**.
- Valódi prefix/suffix: $\varepsilon$-tól és magától az egész szótól különböző.

## Kapocs

- [[concepts/bvszam/formalis-nyelvek]] — szavak halmazai, nyelvi műveletek
- [[concepts/bvszam/generativ-grammatika]] — szavak generálása szabályokkal
