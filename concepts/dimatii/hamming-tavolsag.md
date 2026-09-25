---
tags: [concept, dimatii/hibakorlatozo-es-linearis-kodok]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Hamming-távolság

Két azonos hosszú szó eltérő pozícióinak száma; a hibakorlátozó kódolás alapvető metrikája.

## Tartalom

### Definíció

Legyen $A$ véges ábécé, továbbá $u, v \in A^n$. Ekkor $u$ és $v$ **Hamming-távolsága** az azonos pozícióban lévő különböző betűk száma:
$$d(u, v) = \left|\{ i : 1 \le i \le n \ \wedge\ u_i \ne v_i \}\right| .$$

**Példa.** $d(01110, 10101) = 4$, illetve $d(\text{ALMA}, \text{ANNA}) = 2$.

### Metrikatulajdonságok

**Állítás.** A Hamming-távolság rendelkezik a távolság szokásos tulajdonságaival, vagyis tetszőleges $u, v, w$-re:

1. $d(u,v) \ge 0$;
2. $d(u,v) = 0 \iff u = v$;
3. $d(u,v) = d(v,u)$ (szimmetria);
4. $d(u,v) \le d(u,w) + d(w,v)$ (háromszög-egyenlőtlenség).

*Bizonyítás.* 1), 2) és 3) nyilvánvaló. 4) Ha $u$ és $v$ eltér valamelyik pozícióban, akkor ott $u$ és $w$, illetve $w$ és $v$ közül legalább az egyik pár különbözik. $\square$

### A kód távolsága

Egy $K$ kód **távolsága** ($d(K)$) a különböző kódszópárok távolságainak minimuma.

**Példa (*).** Az
$$(0,0) \mapsto (0,0,0,0,0), \quad (0,1) \mapsto (0,1,1,1,0), \quad (1,0) \mapsto (1,0,1,0,1), \quad (1,1) \mapsto (1,1,0,1,1)$$
kód kódszavainak páronkénti távolságai 3, 4, 3, 4, 3, 3, tehát a kód távolsága 3. Erre a kódra a továbbiakban $(*)$-gal hivatkozunk.

A kód távolsága határozza meg, hány hibát tud jelezni és hányat tud javítani; ez a hibakorlátozó kódolás központi összefüggése.

## Kapocs

- [[concepts/dimatii/hibajelzes-es-hibajavitas]] — a kód távolsága és a hibajelző, illetve hibajavító képessége közötti kapcsolat
- [[concepts/dimatii/singleton-korlat]] — a távolság és a kód mérete közötti felső korlát
- [[concepts/dimatii/hamming-korlat]] — a hibajavító képességből adódó másik korlát
- [[concepts/dimatii/linearis-kod]] — lineáris kódnál a távolság a minimális súllyal egyenlő
