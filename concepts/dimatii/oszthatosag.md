---
tags: [concept, dimatii/elemi-szamelmelet]
sources: [DimatIIEa01.pdf]
derivation: source
updated: 2026-09-08
---

# Oszthatóság

Az egész számok körében az osztás nem mindig végezhető el maradék nélkül; az oszthatóság reláció pontosan azt rögzíti, mikor igen.

## Tartalom

**Definíció.** Az $a$ egész **osztja** a $b$ egészet — jelölés: $a \mid b$ —, ha létezik olyan $c$ egész, mellyel $a \cdot c = b$, azaz $b/a$ szintén egész.

Racionális számok körében az $a/b$ osztás mindig elvégezhető, és az eredmény is racionális. Egészek körében viszont nem: a hányados nem feltétlenül egész. Ez teszi az oszthatóságot érdemi relációvá.

**Példák.** $1 \mid 13$, mert $1 \cdot 13 = 13$; $1 \mid n$ minden $n$-re; $6 \mid 12$, mert $6 \cdot 2 = 12$; $-6 \mid 12$, mert $(-6)\cdot(-2) = 12$.

A definíció szó szerint kiterjeszthető más számkörökre is, például a **Gauss-egészekre**, $\{a + bi \,:\, a,b \in \mathbb{Z}\}$. Ott például $i \mid 13$, mert $i \cdot (-13i) = 13$, és $1 + i \mid 2$, mert $(1+i)(1-i) = 2$.

### Az oszthatóság tulajdonságai

Minden $a, b, c, \dots \in \mathbb{Z}$ esetén:

1. $a \mid a$ (reflexivitás);
2. $a \mid b$ és $b \mid c \Rightarrow a \mid c$ (tranzitivitás);
3. $a \mid b$ és $b \mid a \Rightarrow a = \pm b$;
4. $a \mid b$ és $a' \mid b' \Rightarrow aa' \mid bb'$;
5. $a \mid b \Rightarrow ac \mid bc$;
6. $ac \mid bc$ és $c \neq 0 \Rightarrow a \mid b$;
7. $a \mid b_1, \dots, a \mid b_k \Rightarrow a \mid c_1b_1 + \cdots + c_kb_k$ minden $c_1, \dots, c_k$ egész esetén;
8. $a \mid 0$, ugyanis $a \cdot 0 = 0$;
9. $0 \mid a \iff a = 0$;
10. $1 \mid a$ és $-1 \mid a$.

A 7. pont a leggyakrabban használt: **egy közös osztó az egész együtthatós lineáris kombinációt is osztja**. Erre épül az euklideszi algoritmus helyességének bizonyítása is.

**Példák.** $2 \mid 6$ és $6 \mid 12 \Rightarrow 2 \mid 12$; $2 \mid 4$ és $3 \mid 9 \Rightarrow 2\cdot 3 \mid 4 \cdot 9$; $3 \mid 6$ és $3 \mid 9 \Rightarrow 3 \mid 6c_1 + 9c_2$.

## Kapocs

- [[concepts/dimatii/egyseg-es-asszocialt]] — az oszthatóság szempontjából nem megkülönböztethető számok
- [[concepts/dimatii/maradekos-osztas]] — mi történik, ha az oszthatóság nem áll fenn
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — az oszthatósági rendezés szerinti „legnagyobb”
- [[concepts/dimatii/felbonthatatlan-es-prim]] — az oszthatóság alapján definiált két primitív fogalom
- [[concepts/dimatii/kongruencia]] — oszthatóság különbségekre megfogalmazva
