---
tags: [concept, logika/elsorendu-logika-szemantika]
sources: [Elsőrendű_logika_szemantika.pdf]
derivation: source
updated: 2026-09-08
---

# Elsőrendű interpretáció

Egy $L[V_\nu]$ elsőrendű logikai nyelv interpretációja egy, a nyelvvel azonos szignatúrájú $\langle U, R, M, K \rangle$ matematikai struktúra: az interpretáció a nyelv logikán kívüli szimbólumaihoz rendel konkrét relációkat, műveleteket és elemeket.

## Tartalom

### Az interpretáló struktúra

Az $L$ nyelv egy $I$ interpretációjának megadása két, egyenértékű megfogalmazásban:

- kiválasztunk egy, a nyelvvel **azonos szignatúrájú** $\langle U, R, M, K\rangle$ matematikai struktúrát;
- vagy: megadunk egy $U$ halmazt (az **univerzumot**), és ezen definiálunk egy $R$ reláció-, egy $M$ művelet- és egy $K$ konstanshalmazt, amelyek szignatúrája megegyezik a $Pr$, $Fn$, $Cnst$ szimbólumhalmazok szignatúrájával.

Az interpretáció formálisan egy $I = \langle I_{Srt}, I_{Pr}, I_{Fn}, I_{Cnst}\rangle$ függvénynégyes:

- $I_{Srt} : \pi \mapsto U_\pi$ — a fajták interpretációja. Ha $Srt$ egyelemű, akkor az $U$ univerzum **egyfajtájú** elemekből áll; a továbbiakban végig ilyen, egyfajtájú struktúrákkal és egyfajtájú nyelvvel dolgozunk.
- $I_{Pr} : P \mapsto P^I$, ahol $P^I$ a struktúra $R$ halmazának egy eleme (egy $U$ feletti reláció);
- $I_{Fn} : f \mapsto f^I$, ahol $f^I$ az $M$ halmaz egy eleme (egy $U$ feletti művelet);
- $I_{Cnst} : c \mapsto c^I$, ahol $c^I$ a $K$ halmaz egy eleme (egy $U$-beli kitüntetett elem).

### Az interpretáló struktúra leíró nyelve

Ha az interpretáló struktúrának **van leíró nyelve**, és azt fel is használjuk, akkor a szimbólumok interpretációja ennek a nyelvnek a jeleivel írható le: $P_i^I = R_i$ neve és $f_k^I = o_k$ neve. Ha a struktúrának nincs leíró nyelve, vagy nem akarjuk használni, akkor közvetlenül a relációkat és műveleteket feleltetjük meg: $P_i = P_i^I$, $f_k = f_k^I$.

**Példa.** Legyen az $L$ nyelv $L = (=, P_1, P_2; a, b, f_1, f_2)$, szignatúrája $(2,2,2;\,0,0,2,2)$; az interpretáló struktúra leíró nyelve $S = \mathbb{N}(=, <, >;\, 0, 1, +, *)$, ugyanezzel a szignatúrával. Ekkor

$$I_{Pr}: \quad {=} \mapsto {=}, \qquad P_1 \mapsto {<}, \qquad P_2 \mapsto {>},$$
$$I_{Fn}: \quad a \mapsto 0, \qquad b \mapsto 1, \qquad f_1 \mapsto +, \qquad f_2 \mapsto {*}.$$

Konstansszimbólum itt nincs: $a$ és $b$ két darab **nullaváltozós függvényszimbólum**, így $I_{Cnst}$ üres.

### A lehetséges interpretáló struktúrák száma

Legyenek az $L$ nyelv szignatúrája szerint $(r_1, \dots, r_n; s_1, \dots, s_k)$ a predikátum-, illetve függvényszimbólumok aritásai, és legyen $|U| = M$. Hány különböző ilyen szignatúrájú struktúra létezik $U$ felett?

- Egy $r_j$ változós reláció az $U^{r_j}$ halmaz egy részhalmaza, tehát $2^{M^{r_j}}$ féleképp adható meg;
- egy $s_t$ változós művelet egy $U^{s_t} \to U$ függvény, tehát $M^{M^{s_t}}$ féleképp.

Az összes definiálható struktúra száma a kettő szorzata:

$$\left(\prod_{j=1}^{n} 2^{M^{r_j}}\right) \cdot \prod_{t=1}^{k} M^{M^{s_t}}.$$

**Alsó becslés.** Ha csak a relációk számát nézzük: egy $n$ változós reláció az $U^n$ ($|U^n| = M^n$ elemű) halmaz egy részhalmazának kijelölése, így a lehetséges $n$ változós relációk száma $|\mathcal{P}(U^n)|$. Ha $U$ megszámlálhatóan végtelen, ez már **kontinuum számosságú** — több, mint megszámlálhatóan végtelen —, tehát algoritmikusan nem kezelhető. Ez a szám a magyarázata annak, hogy a [[concepts/logika/szemantikus-tulajdonsagok]] szemantikai úton való eldöntése miért reménytelen: a vizsgálathoz *az összes* interpretáló struktúrára szükség lenne.

## Kapocs

- [[concepts/logika/matematikai-struktura]] — az interpretáló struktúra maga
- [[concepts/logika/leiro-nyelv-es-szignatura]] — a szignatúra, amelynek meg kell egyeznie
- [[concepts/logika/valtozokiertekeles]] — az interpretáció mellé kell egy $\kappa$ is
- [[concepts/logika/term-szemantika]] — az interpretáció első felhasználása
- [[concepts/logika/elsorendu-szemantikus-fa]] — az összes interpretáció szisztematikus előállítása
- [[concepts/bvszam/elsorendu-logika]] — tömör összefoglaló ugyanerről a szelmJegyzet felől
