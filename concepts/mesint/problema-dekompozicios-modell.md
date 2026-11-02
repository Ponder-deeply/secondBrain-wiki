---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Probléma-dekompozíciós modell

A dekompozíció során a problémát részproblémákra bontjuk, majd azokat tovább részletezzük, amíg nyilvánvalóan megoldható (egyszerű) problémákhoz nem jutunk; a reprezentáció ÉS/VAGY gráf.

## Tartalom

Sok esetben egy problémát többféleképpen is fel lehet bontani részproblémákra. Az egy bontást szimbolizáló élköteg a **hiperél**: egy csúcsból kiinduló, ÉS kapcsolatban levő élek, amelyek egy dekompozíciós lépést jelentenek; a különböző bontások VAGY kapcsolatban állnak.

**A modellhez meg kell adni:**

- a feladat részproblémáinak általános leírását,
- a kiinduló problémát,
- az egyszerű problémákat, amelyekről könnyen eldönthető, hogy megoldhatók-e vagy sem,
- a dekomponáló műveleteket: $D: probléma\to probléma^+$, $D(p)=\langle p_1,\dots,p_n\rangle$.

**ÉS/VAGY gráf megfeleltetés:**

| Dekompozíciós modell | ÉS/VAGY gráf |
| --- | --- |
| részprobléma | csúcs |
| dekomponáló művelet hatása egy problémára | irányított hiperél |
| művelet költsége | hiperél költsége |
| kiinduló probléma | startcsúcs |
| megoldható (egyszerű) probléma | célcsúcs |
| dekompozíciós folyamat | hiperút |
| megoldás | a megoldás-gráfból olvasható ki |

Egy problémára véges sok művelet alkalmazható (véges kifokú gráf), és a műveletek költségének van alsó pozitív korlátja ($\delta$).

**Példák.**

- *Dominó.* Általános leírás: $2^n\times 2^n$-es tábla egy foglalt mezővel. Kiinduló probléma: $8\times 8$-as tábla egy foglalt mezővel. Egyszerű probléma: $2\times 2$-es tábla egy foglalt mezővel. Dekomponáló operátor: a táblát 4 egyenlő részre osztja, és középre elhelyez egy L alakú dominót úgy, hogy az ne fedje le a foglalt mezőt tartalmazó részt; így mind a négy rész egy-egy foglalt mezős (a dominó egy mezője foglaltnak számít) kisebb tábla. A megoldás: az ÉS/VAGY fa egyben megoldásgráf is, hiperélei és levélcsúcsai mutatják az L alakú elemek elhelyezését.
- *Integrálszámítás.* Általános leírás: szintaktikusan helyes kifejezés vagy műveleti jel. Kiinduló probléma: adott integrálkifejezés. Egyszerű probléma: integráljel nélküli kifejezés. Dekomponáló operátorok: integrálási szabályok (összeg, konstans kiemelése, parciális integrálás stb.). Megoldás: a megoldásgráf leveleiben tárolt szimbólumokat balról jobbra összeolvasva kapjuk az eredeti kifejezés primitív függvényét.
- *Hanoi tornyai* ([[concepts/mesint/hanoi-tornyai]]). Általános leírás: $H(n, i\to j, k)$: $n$ korongot viszünk át az $i$. rúdról a $j$. rúdra a $k$. rúd segítségével. Kiinduló probléma: $H(3, 3\to 1, 2)$. Egyszerű probléma: $H(1, i\to j, k)$ (eldönthető, hogy megoldható-e). Dekomponálás: $H(n,i\to j,k) \rightsquigarrow \langle H(n-1,i\to k,j),\ H(1,i\to j,k),\ H(n-1,k\to j,i)\rangle$. A lépéssorozat a reprezentációs fa (egyben megoldásgráf) leveleiből olvasható ki balról jobbra.

## Kapocs

- [[concepts/mesint/es-vagy-grafok]] — a dekompozíció gráfreprezentációja.
- [[concepts/mesint/hiperut]] — a dekompozíciós folyamat és a megoldás hiperút.
- [[concepts/mesint/utkereses-es-vagy-grafban]] — a megoldás megkeresése ÉS/VAGY gráfban.
- [[concepts/mesint/problema-redukcios-modell]] — az állapottér-alapú, halmazokkal dolgozó modell.
- [[concepts/mesint/hanoi-tornyai]] — az állapottér-megoldás ugyanarra a feladatra.
- [[concepts/mesint/allapotter-vs-problemater]] — a modellek közti választás.
