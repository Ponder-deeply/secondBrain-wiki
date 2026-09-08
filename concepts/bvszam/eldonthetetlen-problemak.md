---
tags:
  - concept
sources:
  - szelmJegyzet.pdf
  - 08.md
  - 08.md
derivation: source
updated: 2026-08-05
---

# Eldönthetetlen problémák

Az eldönthetetlen problémák olyan eldöntési problémák (formális nyelvek), amelyek nincsenek $\mathrm{R}$-ben: nem létezik őket eldöntő, minden bemeneten megálló Turing-gép. A bizonyítások kiindulópontja az $L_u$ eldönthetetlensége, onnan visszavezetésekkel terjed tovább.

## A visszavezetés mint bizonyítási eszköz

Ha egy ismerten eldönthetetlen $L_1$ problémát sikerül [[concepts/bvszam/visszavezetes|visszavezetni]] egy $L_2$ problémára ($L_1 \leq L_2$), akkor $L_2$ is eldönthetetlen — különben $L_1$-et is el tudnánk dönteni, ami ellentmondás. Formálisan (2.18–2.19. tétel): ha $L_1 \leq L_2$, akkor
- $L_1 \notin \mathrm{R} \Rightarrow L_2 \notin \mathrm{R}$,
- $L_1 \notin \mathrm{RE} \Rightarrow L_2 \notin \mathrm{RE}$.

## Turing-gépekkel kapcsolatos eldönthetetlen problémák

| Probléma | Jelölés | Besorolás |
|---|---|---|
| Univerzális nyelv | $L_u = \{\langle M,w\rangle \mid w \in L(M)\}$ | $\mathrm{RE} \setminus \mathrm{R}$ |
| Megállási probléma | $L_h = \{\langle M,w\rangle \mid M \text{ megáll } w\text{-n}\}$ | $\mathrm{RE} \setminus \mathrm{R}$ |
| Nemüres nyelv | $L_{\neg\emptyset} = \{\langle M\rangle \mid L(M) \neq \emptyset\}$ | $\mathrm{RE} \setminus \mathrm{R}$ |
| Üres nyelv | $L_\emptyset = \{\langle M\rangle \mid L(M) = \emptyset\}$ | $\notin \mathrm{RE}$ |
| Ekvivalencia | $L_{EQ} = \{\langle M_1,M_2\rangle \mid M_1, M_2 \text{ ekvivalens}\}$ | $\notin \mathrm{RE}$ |

### $L_{\neg\emptyset} \in \mathrm{RE} \setminus \mathrm{R}$

- **$L_{\neg\emptyset} \notin \mathrm{R}$:** visszavezetés $L_u \leq L_{\neg\emptyset}$. Adott $\langle M, w \rangle$-hez konstruáljuk az $M'$ gépet, amely tetszőleges $u$ bemeneten ellenőrzi, hogy $u = w$-e; ha nem, elutasít, ha igen, $M$-et szimulálja $w$-n. Ekkor $L(M') \neq \emptyset \iff w \in L(M)$, azaz $\langle M' \rangle \in L_{\neg\emptyset} \iff \langle M, w \rangle \in L_u$.
- **$L_{\neg\emptyset} \in \mathrm{RE}$:** egy $M'$ kétszalagos gép a második szalagon tárolt $i$ számlálóval ciklikusan szimulálja a bemeneti $M$ első $i$ lépését az $w_1, \ldots, w_i$ szavakon (a szavak felsorolása mellett); ha valamelyiken $M$ elfogadó állapotba lép, $M'$ elfogad.

### $L_\emptyset \notin \mathrm{RE}$, $L_{EQ} \notin \mathrm{RE}$

$L_\emptyset = \overline{L_{\neg\emptyset}}$. Mivel $L_{\neg\emptyset} \in \mathrm{RE} \setminus \mathrm{R}$ és RE nem zárt komplementerre, $L_\emptyset \notin \mathrm{RE}$ (és így persze $\notin \mathrm{R}$). Az $L_\emptyset$ az $L_{EQ}$ speciális esete (rögzítsük $M_2$-t egy semmit el nem fogadó gépre), ezért ha $P_1$ ($= L_\emptyset$) speciális esete a $P_2$ ($= L_{EQ}$) problémának, akkor $P_1 \notin \mathrm{RE} \Rightarrow P_2 \notin \mathrm{RE}$. Tehát $L_{EQ} \notin \mathrm{RE}$.

## Rice tétele

Minden Turing-gépekkel kapcsolatos **nemtriviális** kérdés eldönthetetlen: ha $\mathcal{P} \subseteq \mathrm{RE}$ a felismert nyelv egy nemtriviális tulajdonsága, akkor $L_\mathcal{P} = \{\langle M\rangle \mid L(M) \in \mathcal{P}\} \notin \mathrm{R}$. Részletek: [[concepts/bvszam/rice-tetel|rice-tetel]]. Következményei (mind eldönthetetlen): üres nyelvet / véges nyelvet / környezetfüggetlen nyelvet ismer-e fel egy $M$ TG, illetve elfogadja-e az üres szót.

## Nem Turing-gépekről szóló eldönthetetlen problémák

- **Post megfelelkezési probléma (PMP):** dominósorozat-illesztés; $\mathrm{PMP} \notin \mathrm{R}$, az $L_u \leq \mathrm{MPMP} \leq \mathrm{PMP}$ láncon át. Részletek: [[concepts/bvszam/post-megfelelkezesi-problema|post-megfelelkezesi-problema]].
- **Környezetfüggetlen grammatikákkal kapcsolatos kérdések:** KF grammatika egyértelműsége; két KF nyelv metszetének üressége, egyenlősége, $\Gamma^*$-mal való egyenlősége, tartalmazása — mind eldönthetetlen, PMP-re visszavezetve. Részletek: [[concepts/bvszam/kornyezetfuggetlen-grammatika|kornyezetfuggetlen-grammatika]].
- **Elsőrendű logika:** egy formula érvényessége, kielégíthetősége, kielégíthetetlensége, illetve az $F \models \varphi$ következmény mind eldönthetetlen. Részletek: [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg|elsorendu-logika-eldonthetetlenseg]].

## Kapocs

- [[concepts/bvszam/univerzalis-turing-gep]] — $L_u$ konstrukciója és eldönthetetlensége
- [[concepts/bvszam/megallasi-problema]] — $L_h \in \mathrm{RE} \setminus \mathrm{R}$
- [[concepts/bvszam/rice-tetel]] — nemtriviális tulajdonságok eldönthetetlensége
- [[concepts/bvszam/post-megfelelkezesi-problema]] — PMP / dominóprobléma
- [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg]] — érvényesség, kielégíthetőség
- [[concepts/bvszam/visszavezetes]] — many-one visszavezetés, 2.18–2.19. tétel
- [[concepts/bvszam/r-re-nyelvek]] — R, RE, co-RE osztályok
