---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Részgyűrű és ideál

A részgyűrű a gyűrű műveletekre zárt, maga is gyűrűt alkotó részhalmaza; az ideál ennél erősebb: a gyűrű elemeivel való szorzásra is zárt, ezért szerinte mellékosztályokra bontható a gyűrű.

## Tartalom

### Részgyűrű

Az $R$ gyűrűben $S \subseteq R$ **részgyűrű**, ha az $R$-beli műveletek $S$-re való leszűkítésére nézve $S$ maga is gyűrűt alkot.

- Mivel $S \subseteq R$, műveleti zártság esetén az asszociativitás, a kommutativitás és a disztributivitás öröklődik.
- Csoportban $S$ részcsoport $\iff S \cdot S^{-1} \subseteq S$ (lásd [[concepts/dimatii/reszcsoport]]).
- Ennek megfelelően komplexusokkal felírva: $S$ részgyűrű $R$-ben $\iff$ $S - S \subseteq S$ és $S \cdot S \subseteq S$.

### Ideál

Legyen $R$ gyűrű, $\emptyset \ne I \subseteq R$. Az $I$ halmaz

- **balideál**, ha $I - I \subseteq I$ és $R \cdot I \subseteq I$;
- **jobbideál**, ha $I - I \subseteq I$ és $I \cdot R \subseteq I$;
- **ideál**, ha egyszerre bal- és jobbideál.

Észrevételek:

- bal-/jobbideálok, illetve ideálok metszete is bal-/jobbideál, illetve ideál;
- **kommutatív gyűrűben** a bal-, jobb- és kétoldali ideál fogalma egybeesik.

Elnevezések: **triviális ideál** a $\{0\}$ és az $R$; **valódi ideál** az $R$-től különböző ideál; **egyszerű gyűrű**, amelynek csak triviális ideáljai vannak.

### Generált ideál, főideál

Az $A \subseteq R$ halmaz **által generált ideál** $R$ összes, $A$-t tartalmazó ideáljának metszete; jele $(A)$ vagy $\langle A \rangle$. Ha $A = \{a\}$, akkor az **$a$ által generált főideálról** beszélünk, jele $(a)$ (bal és jobb oldali változata hasonlóan).

Ha $R$ integritási tartomány és $A = \{a_1, \dots, a_n\}$, akkor

$$\langle a_1, \dots, a_n \rangle = \Bigl\{ \sum_{i=1}^n r_i a_i \;\Big|\; r_1, \dots, r_n \in R \Bigr\},$$

vagyis $A$ elemeinek összes véges $R$ feletti lineáris kombinációja. Speciálisan $(a) = \langle a \rangle = \{ra \mid r \in R\}$: az $a$ összes többszöröséből áll.

**Főideálgyűrű**: olyan egységelemes integritási tartomány, amelyben minden ideál főideál.

### Mellékosztály

Legyen $I$ az $R$ gyűrű additív részcsoportja, és $a \sim b \iff a - b \in I$ ekvivalenciareláció $R$-en. Az $I + a$ ekvivalenciaosztály $R$-nek egy **$I$ szerinti mellékosztálya (maradékosztálya)**.

**Tétel (8.2.15).** Egy $R$ gyűrű egy $I$ ideál szerinti mellékosztályai a gyűrűnek mindkét művelettel kompatibilis osztályozását alkotják. Minden, mindkét művelettel kompatibilis osztályozás esetén a nulla osztálya ideál, és az osztályozás ezen ideál szerinti mellékosztályokból áll.

*Bizonyítás-váz (összeadás).* $(I; +)$ Abel-csoport, tehát normálosztó $R$ additív csoportjában, így a normálosztóra vonatkozó tétel (1) pontja szerint az osztályozás kompatibilis az összeadással, az osztályok összeadása pedig a komplexusszorzás (lásd [[concepts/dimatii/normaloszto-es-faktorcsoport]]).

## Kapocs

- [[concepts/dimatii/maximalis-es-primideal]] — maximális ideál, prímideál, a faktorgyűrű típusai
- [[concepts/dimatii/gyuru]] — az alapfogalom, amelyben részgyűrűt és ideált értelmezünk
- [[concepts/dimatii/reszcsoport]] — a részgyűrű additív része részcsoport
- [[concepts/dimatii/normaloszto-es-faktorcsoport]] — az ideál szerinti mellékosztályok az additív normálosztóra épülnek
- [[concepts/dimatii/integritasi-tartomany]] — a generált ideál leírása ilyen gyűrűben szerepel
- [[concepts/dimatii/homomorfizmustetel]] — a homomorfizmus magja
