---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Tárbonyolultság és PSPACE-teljesség

A tárbonyolultság a probléma eldöntéséhez szükséges memória nagyságát méri. Savitch tétele szerint a nemdeterminizmus tárban csak négyzetes árat jelent, és léteznek a PSPACE osztályra teljes problémák, pl. a QSAT.

## Off-line Turing-gép

A tárbonyolultságot **off-line Turing-gépen** vizsgáljuk: ez egy többszalagos TG, amely a bemenetet tartalmazó szalagot csak olvashatja, a többi (munka)szalagra írhat is. A **tárigénybe csak a munkaszalagokon felhasznált terület** számít be.

Ez teszi értelmessé a **szublineáris** tárbonyolultságot (a bemenet hosszát nem számoljuk a tárba). Szublineáris *idő*bonyolultságnak nincs gyakorlati jelentősége, mert akkor a gép a bemenetet sem olvassa végig.

A tár — az idővel szemben — **újrafelhasználható**.

## Tárbonyolultsági osztályok

$$\text{SPACE}(f(n)) = \{L \mid L \text{ eldönthető } O(f(n)) \text{ tárigényű determinisztikus TG-pel}\}$$
$$\text{NSPACE}(f(n)) = \{L \mid L \text{ eldönthető } O(f(n)) \text{ tárigényű nemdeterminisztikus TG-pel}\}$$

Ezekből:
$$\text{PSPACE} = \bigcup_{k>0} \text{SPACE}(n^k), \qquad \text{NPSPACE} = \bigcup_{k>0} \text{NSPACE}(n^k)$$
$$\text{L} = \text{SPACE}(\log_2 n), \qquad \text{NL} = \text{NSPACE}(\log_2 n)$$

## Savitch tétele

**3.33. Tétel (Savitch):** Ha $f(n) \geq \log n$, akkor $\text{NSPACE}(f(n)) \subseteq \text{SPACE}(f^2(n))$.

Azaz a determinisztikus TG-ek a tárbonyolultság **négyzetes** romlása árán szimulálni tudják a (legalább logaritmikus tárú) nemdeterminisztikus TG-eket.

**Bizonyítás vázlata:** Egy $O(f(n))$ tárú NTG $M$ konfigurációi a $w$ bemeneten egy $C_w$ **konfigurációs gráfot** alkotnak; $C_w$ mérete $2^{O(f(n))}$. Az $M$-nek (alkalmas $M'$-re cserélve) pontosan egy $c_{elfogadó}$ konfigurációja van. A $w$ elfogadása ekvivalens azzal, hogy $C_w$-ben van út $c_{kezdő}$-ből $c_{elfogadó}$-ba. Definiáljuk az $\text{ELÉR}(c_1,c_2,i,t)$ predikátumot: igaz, ha van legfeljebb $t$ hosszú út $c_1$-ből $c_2$-be, csupa legfeljebb $i$ méretű konfiguráción át. Rekurzió: középső konfiguráció keresésével
$$\text{ELÉR}(c_1,c_2,i,t) \iff \exists c:\ \text{ELÉR}(c_1,c,i,\lceil t/2\rceil) \wedge \text{ELÉR}(c,c_2,i,\lceil t/2\rceil).$$
A rekurzió mélysége $\log_2 2^{O(f(n))} = O(f(n))$, minden szinten $O(f(n))$ tár kell, így összesen $O(f^2(n))$. $M'$ minden $i=1,2,\dots$ méretkorlátra ellenőrzi az $\text{ELÉR}(c_{kezdő},c_{elfogadó},i,2^{di})$ értékét.

**3.34. Következmény:** $\text{PSPACE} = \text{NPSPACE}$ (a polinom négyzete is polinom).

## QSAT — az első PSPACE-teljes probléma

A **PSPACE-teljesség** itt: polinom idejű visszavezetésekre nézve teljesség.

Egy **teljesen kvantifikált Boole-formula (TKBF)** olyan formula, amelyben minden ítéletváltozó univerzális ($\forall$) vagy egzisztenciális ($\exists$) kvantorral kötött, ráadásul minden kvantor a formula elején áll, hatóköre a formula végéig tart.

$$\text{QSAT} = \{\langle\varphi\rangle \mid \varphi \text{ igaz teljesen kvantifikált Boole-formula}\}$$

**3.37. Tétel:** QSAT PSPACE-teljes.

- **QSAT $\in$ PSPACE:** Az $\text{ÉRTÉK}(\varphi)$ függvény rekurzív kiszámítása (3. algoritmus): $\varphi = Qx\psi$ esetén kiszámoljuk a $\psi^i$ (minden $x$ igaz) és $\psi^h$ (minden $x$ hamis) értékét, majd $Q$ szerint kombináljuk. A rekurzió mélysége a változók száma, minden szinten egy igazságérték tárolódik → lineáris tár.
- **QSAT PSPACE-nehéz:** Tetszőleges $L \in \text{PSPACE}$-re, $L$-t eldöntő $n^k$ tárú $M$ TG-hez egy $\varphi$ TKBF-et konstruálunk úgy, hogy $w \in L(M) \iff \langle\varphi\rangle \in \text{QSAT}$. A konfigurációkat **konfiguráció-azonosító halmazok** (KH) változócsoportjaival reprezentáljuk. A $\varphi_{C,D,t}$ formula azt fejezi ki, hogy $M$ el tud jutni $c$-ből $d$-be legfeljebb $t$ lépésben — Savitch ötletével felezve, de a középső konfigurációt **univerzális kvantorral** osztjuk, hogy a formula mérete ne duplázódjon, így polinom méretű maradjon:
$$\varphi_{C,D,t} = \exists M\,\forall C_1\forall C_2\big((C_1{=}C \wedge C_2{=}M) \vee (C_1{=}M \wedge C_2{=}D) \to \varphi_{C_1,C_2,\lceil t/2\rceil}\big).$$

QSAT akkor is PSPACE-teljes marad, ha a kvantorok alternálnak, az első és utolsó kvantor $\exists$, és a kvantormentes rész KNF — ez **kétszemélyes játékként** is felfogható.

## FÖLDRAJZI JÁTÉK

**3.38. Definíció:** Adott egy $G$ irányított gráf és egy $p$ csúcsa. Két játékos $p$-ből kiindulva felváltva jelöli meg $G$ még meg nem jelölt csúcsait, mindig az utoljára megjelölt csúcsból elérhető csúcsok közül választva. Az veszít, aki nem tud további csúcsot megjelölni. (Eredetileg: városnevek mondogatása az utolsó betű szerint.)

**3.39. Tétel:** FÖLDRAJZI JÁTÉK PSPACE-teljes.

A PSPACE-nehézséget a $\text{QSAT} \leq_p \text{FÖLDRAJZI JÁTÉK}$ visszavezetés adja: a $\varphi = \exists x_1\forall x_2\exists x_3\dots\exists x_k\psi$ TKBF-hez egy $G_\varphi$ gráfot építünk, amelyben minden változóhoz egy rombusz-részgráf tartozik (az első játékos a páratlan, a második a páros indexű változók értékét választja), a KNF klózainak pedig külön csúcsok felelnek meg. Az első játékosnak pontosan akkor van nyerő stratégiája, ha $\langle\varphi\rangle \in \text{QSAT}$.

## Kapocs

- [[concepts/bvszam/logaritmikus-tarbonyolultsag]] — L, NL, ELÉRHETŐSÉG, NL-teljesség
- [[concepts/bvszam/np-koztes-es-conp]] — coNP; NPSPACE = coNPSPACE Savitch nyomán
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP, idő- és tárbonyolultság viszonya
- [[concepts/bvszam/ksat-es-3sat]] — SAT/3SAT; a QSAT a SAT kvantoros általánosítása
- [[concepts/bvszam/nemdeterminisztikus-turing-gep]] — NTG, amelyen az NSPACE alapul
- [[concepts/bvszam/tobb-szalagos-turing-gep]] — többszalagos TG, az off-line TG alapja
