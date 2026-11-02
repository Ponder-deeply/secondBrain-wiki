---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf, dm2gy11.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
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

### Feladattípusok és módszerek: távolság, súly, gömb (2024. 11. sorozat)

*Példa.* A $00\mapsto00000$, $01\mapsto01110$, $10\mapsto10101$, $11\mapsto11011$ kód esetén:

- $d(01110,10101)=4$ (a négy eltérő helyet kell megszámolni);
- a páronkénti távolságok $3,3,4,4,3,3$, tehát a **kód távolsága** $3$ (a legkisebb *páronkénti* távolság, nem a legkisebb szóhossz-eltérés);
- a $11011$ súlya $4$; a **kód súlya** a nem nulla kódszavak súlyának minimuma, $3$ — a kód lineáris ($01110+10101=11011$), ezért a súly és a távolság egyezik; lineáris kódnál $d=\min\{w(v):v\neq0\}$;
- a $00000$-tól legfeljebb $1$ távolságra levő $\mathbb{Z}_2^5$-beli szavak: $00000,10000,01000,00100,00010,00001$ (a gömb $1+5=6$ szó);
- az $01000$ szó távolsága a kódszavaktól $1,2,4,3$, így minimális távolságú dekódolással $00000$-ra, azaz a $00$ üzenetre dekódoljuk.

**Pakolási feladat.** A hat hosszú, pontosan három $1$-est tartalmazó bináris szavak közül hányat lehet kiválasztani úgy, hogy páronként legalább $3$ legyen a távolságuk? Két ilyen szó távolsága páros ($2(3-\text{átfedés})$), így a feltétel legalább $4$ távolságot jelent, azaz az átfedés legfeljebb $1$; a legtöbb ilyen szó $4$ (teljes kereséssel ellenőrizve).

**Tipikus hibák.** A kód távolságát a nulla szó távolságaként számolni nemlineáris kódnál; a súlyt és a távolságot felcserélni; a gömb méretét $q$-áris kódnál $1+n$ helyett $1+n(q-1)$-re kell cserélni.

## Kapocs

- [[concepts/dimatii/hibajelzes-es-hibajavitas]] — a kód távolsága és a hibajelző, illetve hibajavító képessége közötti kapcsolat
- [[concepts/dimatii/singleton-korlat]] — a távolság és a kód mérete közötti felső korlát
- [[concepts/dimatii/hamming-korlat]] — a hibajavító képességből adódó másik korlát
- [[concepts/dimatii/linearis-kod]] — lineáris kódnál a távolság a minimális súllyal egyenlő
- [[concepts/dimatii/singleton-korlat]] — az MDS-tulajdonság ellenőrzése
