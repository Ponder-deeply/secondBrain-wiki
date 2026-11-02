---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf, dm2gy11.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Hamming-kód

1-hibajavító perfekt lineáris kód, amelynek ellenőrző mátrixát az összes nem-nulla oszlopvektor alkotja; a szindróma közvetlenül megmutatja a hibás pozíciót.

## Tartalom

### Definíció

Az 1-hibajavító perfekt lineáris kódot **Hamming-kódnak** nevezzük. (Perfekt kód: olyan kód, amelyre a Hamming-korlát egyenlőséggel teljesül.)

### Konstrukció

Ha egy olyan bináris kódot készítünk, amelyre a $\mathbf{H}$ ellenőrző mátrix oszlopainak a különböző nemnulla, $r$ hosszú vektorokat választjuk, akkor egy 1-hibajavító kódot kapunk: nincs $\mathbf{H}$-nak 1, se 2 lineárisan összefüggő oszlopa, tehát a kód távolsága legalább 3.

Ekkor a Hamming-korlát alakja:
$$2^k (1 + n) \le 2^n .$$
Egyenlőség esetén $n = 2^{\,n-k} - 1$, és pont ennyi $n-k$ hosszú, nemnulla vektor van.

$n = 2^r - 1$ esetén $k = n - \log(n+1)$, így a megfelelő $(n,k)$ párok:

| $n$ | 3 | 7 | 15 | 31 | 63 | 127 | $\cdots$ |
|---|---|---|---|---|---|---|---|
| $k$ | 1 | 4 | 11 | 26 | 57 | 120 | $\cdots$ |

### Dekódolás

Ha csak 1 hiba van, akkor a hibavektornak csak egy koordinátája 1, a többi 0, így a szindróma az ellenőrző mátrix valamely oszlopa lesz. Ennek az oszlopnak megfelelő koordinátája hibás az üzenetben — a javítás tehát egyetlen táblázatkeresés.

### Példa

$n = 7$, $k = 4$:
$$\mathbf{H} = \begin{pmatrix} 1 & 0 & 1 & 1 & 1 & 0 & 0 \\ 1 & 1 & 0 & 1 & 0 & 1 & 0 \\ 1 & 1 & 1 & 0 & 0 & 0 & 1 \end{pmatrix}, \qquad \mathbf{G} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \\ 1 & 0 & 1 & 1 \\ 1 & 1 & 0 & 1 \\ 1 & 1 & 1 & 0 \end{pmatrix}.$$

$v = (1,1,0,0,1,1,1)^T$ esetén $\mathbf{H}v = (0,1,1)^T = s$, ami a $\mathbf{H}$ 2. oszlopa, így a 2. koordináta romlott el; az elküldött kódszó $c = (1,0,0,0,1,1,1)^T$.

### Gyakorlati változatok

A $[7,4]$-es Hamming-kódot egy paritásbittel kiegészítve kapjuk a teletextnél használt kódolást. A $[15,11]$-es Hamming-kódot egy paritásbittel kiegészítve a műholdas műsorszórásnál (DBS) használják.

### Feladattípus: „kérdezz-felelek” játék mint kódolási feladat (2024. 11. sorozat)

Alice egy számot gondol $1$ és $16$ között ($16=2^4$ lehetőség), Bob előre leírt (nem adaptív) igen/nem kérdéseket tesz fel. A kérdések válaszsorozata egy bináris kódszó, a számhoz rendelt kódolás $n$ hosszú, $16$ kódszóval; a hibák az átvitel hibái. A kódelméleti átfogalmazás (a lap nem ad megoldást; a következők a távolság–képesség összefüggésből és a $[7,4,3]$ kód ismeretéből következnek):

- Alice igazat mond: $d=1$ elég, $4$ kérdés (a szám bináris jegyei).
- Egy válasz *kimarad* (törlés, a hely ismert): $d=2$ kell, $5$ kérdés (paritásbit); két kimaradt válasz: $d=3$, és a $[7,4,3]$ Hamming-kód $7$ kérdést ad ($16$ kódszóhoz $6$ kérdés nem elég, mert $A(6,3)=8<16$).
- Cecile *hazudhat* (feltéve, hogy a kérdések itt is előre rögzítettek; az adaptív, Ulam-féle játék más számokat adhat): legfeljebb $t$ hazugság esetén $d=2t+1$ kell. $t=1$: $d=3$, a Hamming-kód $7$ kérdéssel megoldja; a $d=3$, $16$ kódszavas kód hossza $7$-nél kisebb nem lehet ($A(6,3)=8$). $t=2$: $d=5$, $11$ kérdés kell ($A(10,5)=12<16\le A(11,5)=24$).

**Tipikus hiba.** A hazugságot és a kimaradást összekeverni: kimaradásnál (törlés) $d=t+1$ elég, hazugságnál $d=2t+1$ kell, mert a hiba helye ismeretlen.

## Kapocs

- [[concepts/dimatii/hamming-korlat]] — a perfektség definíciója, amelyet a kód teljesít
- [[concepts/dimatii/ellenorzo-matrix]] — a konstrukció közvetlenül az oszlopok megválasztása
- [[concepts/dimatii/szindroma-dekodolas]] — a dekódolás általános elve, itt különösen egyszerű alakban
- [[concepts/dimatii/linearis-kod]] — a kódcsalád, amelybe tartozik
