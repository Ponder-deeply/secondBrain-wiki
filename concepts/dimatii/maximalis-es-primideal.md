---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Maximális ideál és prímideál

Egy ideál maximális, ha nincs nála bővebb valódi ideál; prímideál, ha a szorzatba tartozásból valamelyik tényezőbe tartozás következik. A faktorgyűrű szerkezete pontosan ezt tükrözi: $R/I$ test $\iff$ $I$ maximális, $R/I$ integritási tartomány $\iff$ $I$ prímideál.

## Tartalom

### Definíciók

**Maximális ideál (8.2.36).** Egy $R$ gyűrű egy $I$ *valódi* ideálját maximálisnak nevezzük, ha nincs nála bővebb valódi ideál, amely tartalmazza, azaz a valódi ideálok között a tartalmazásra nézve maximális.

**Prímideál.** $R$ egységelemes, kommutatív gyűrű. Egy $I$ ideál prímideál, ha $ab \in I$-ből $a \in I$ vagy $b \in I$ következik.

**Példák $\mathbb{Z}$-ben.**
1. $2\mathbb{Z}$ prímideál: $ab \in 2\mathbb{Z} \Rightarrow ab$ páros $\Rightarrow$ $a$ vagy $b$ páros.
2. $2\mathbb{Z}$ maximális is: ha $2\mathbb{Z} \subseteq I \subseteq \mathbb{Z}$ és van páratlan $a \in I$, akkor $1 \in I$ (az $a$ és a $2$ lineáris kombinációjaként), így $I = \mathbb{Z}$; különben $I = 2\mathbb{Z}$.
3. $49\mathbb{Z}$ nem maximális és nem prímideál: $49\mathbb{Z} \subset 7\mathbb{Z} \subset \mathbb{Z}$, és $7 \cdot 7 = 49 \in 49\mathbb{Z}$, de $7 \notin 49\mathbb{Z}$.

### Irreducibilitás és maximális ideál euklideszi gyűrűben

**Lemma.** Legyen $R$ euklideszi gyűrű, $a \in R^* \setminus U(R)$. Ekkor $\langle a \rangle$ maximális ideál $R$-ben $\iff$ $a$ felbonthatatlan $R$-ben.

*Bizonyítás.* ($\Rightarrow$, kontrapozícióval, bármely egységelemes integritási tartományban.) Ha $a$ felbontható, $a = bc$ ahol $b, c \in R^* \setminus U(R)$, akkor $\langle a \rangle \subset \langle b \rangle \subset R$ valódi tartalmazások, tehát $\langle a \rangle$ nem maximális.
($\Leftarrow$, indirekt.) Legyen $a$ felbonthatatlan, de $\langle a \rangle$ nem maximális: van $I$ ideál, amelyre $\langle a \rangle \subset I \subset R$ valódi tartalmazásokkal. $R$ főideálgyűrű (lásd [[concepts/dimatii/euklideszi-gyuru-egyertelmu-felbontas]]), így $I = \langle b \rangle$ valamilyen nem nulla, nem egység $b$-vel. Mivel $\langle a \rangle \subset \langle b \rangle$, $a$ többszöröse $b$-nek: $a = bc$. $c$ nem egység, mert akkor $\langle a \rangle = \langle b \rangle$ lenne. Így $a$ nem felbonthatatlan — ellentmondás. $\square$

### Faktorgyűrű és ideáltípusok

**Tétel.** $R$ kommutatív, egységelemes gyűrű, $I$ ideálja.

- **I.** $R/I$ akkor és csak akkor integritási tartomány, ha $I \ne R$ és $I$ prímideál.
- **II.** $R/I$ akkor és csak akkor test, ha $I$ maximális ideál.

*Bizonyítás I.* $R/I$ integritási tartomány $\iff$ nincs nullosztó $\iff$ $(I+a)(I+b) = I \Rightarrow I+a = I$ vagy $I+b = I$ (az $I$ az $R/I$ nulleleme, és $I + a = I \iff a \in I$), azaz $ab \in I \Rightarrow a \in I$ vagy $b \in I$.

*Bizonyítás II/1.* Legyen $I$ maximális és $I + a \in R/I$, $I + a \ne I$ (azaz $a \notin I$). Az $S = \{i + ax \mid i \in I,\ x \in R\}$ ideál: $S - S \subseteq S$, mert $i_1 + ax_1 - i_2 - ax_2 = (i_1 - i_2) + a(x_1 - x_2) \in S$, és $RS \subseteq S$, mert $ri + rax = ri + a(rx) \in S$. Továbbá $I \subset S$, mert $a \in S \setminus I$. $I$ maximális, ezért $S = R$, így az $e$ egységelem $e = i + ax$ alakú valamely $i \in I$, $x \in R$ elemekkel. Innen $I + e = I + i + ax = I + ax = (I+a)(I+x)$, tehát $I + a$ invertálható. $R/I$ kommutatív, egységelemes és minden nem nulla eleme invertálható, ezért test.

*Bizonyítás II/2.* Legyen $R/I$ test és $M$ olyan ideál, amely valódi módon tartalmazza $I$-t: van $a \in M \setminus I$. Mivel $R/I$ test, az $(I+a)(I+x) = (I+b)$ egyenlet bármely $b \in R$-re megoldható, azaz $I + ax = I + b$. Mivel $I \subset M$ és $a \in M$, $I + ax \subseteq M$, tehát $b \in M$ minden $b$-re, így $M = R$. Tehát $I$ maximális. $\square$

**Következmény.** Kommutatív, egységelemes gyűrűben minden maximális ideál prímideál. *Bizonyítás.* $I$ maximális $\Rightarrow$ $R/I$ test $\Rightarrow$ integritási tartomány $\Rightarrow$ (I. rész) $I$ prímideál.

**Lemma.** Legalább 2 elemű kommutatív egységelemes $R$ gyűrűnek akkor és csak akkor vannak csupán triviális ideáljai, ha test.
*Bizonyítás.* Ha $R$ nem test, van nem nulla, nem invertálható $a$; ennek többszörösei között nincs $e$, így $(a)$ nem triviális ideál. Ha $R$ test, $I \ne \{0\}$ ideál, $a \in I$, $a \ne 0$: létezik $a^{-1}$, és az ideál tulajdonsága miatt $e = a^{-1}a \in I$, így minden $b = be \in I$, tehát $I = R$. $\square$

## Kapocs

- [[concepts/dimatii/reszgyuru-es-idealok]] — az ideál fogalma, triviális ideálok
- [[concepts/dimatii/faktorgyuru]] — az $R/I$ szerkezet
- [[concepts/dimatii/foideal]] — főideál, főideálgyűrű
- [[concepts/dimatii/euklideszi-gyuru-egyertelmu-felbontas]] — euklideszi gyűrű főideálgyűrű
- [[concepts/dimatii/integritasi-tartomany]] — a nullosztómentesség
- [[concepts/dimatii/test]] — az $R/I$ test esete
- [[concepts/dimatii/hanyadostest]] — integritási tartomány testbe ágyazása
