---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Logaritmikus tárbonyolultság

A logaritmikus tárral eldönthető problémák osztályai L és NL. Központi problémájuk az ELÉRHETŐSÉG, amely NL-teljes; legfontosabb eredmények: NL ⊆ P és az Immermann–Szelepcsényi tétel (NL = coNL).

## L és NL

$$\text{L} = \text{SPACE}(\log_2 n), \qquad \text{NL} = \text{NSPACE}(\log_2 n)$$

A logaritmikus tárfelhasználás nagyon hatékony. Mivel a bemenetet csak olvassuk (off-line TG), a $\log n$ tár pl. egy bemenetpozíció-mutatót tud tárolni.

**Logaritmikus tárral kiszámítható függvény:** olyan $f:\Sigma^*\to\Sigma^*$, amit egy legalább három szalagos, logaritmikus tárú off-line TG számol ki, amely az utolsó szalagra (kimenet) csak ír. Az ilyen gépeket **lyukszalagos gépeknek** is nevezzük; a tárfelhasználásba sem a bemenet, sem a kimenet mérete nem számít.

## Logaritmikus tárral való visszavezetés

**3.41. Definíció:** $L_1 \leq_l L_2$, ha van olyan logaritmikus tárral kiszámítható $f$ függvény, amellyel $L_1$ visszavezethető $L_2$-re. Az ehhez tartozó **C-teljesség / C-nehézség** a logaritmikus tárú visszavezetésekre vonatkozik.

**3.42. Tétel:** L és NL zártak a logaritmikus tárral való visszavezetésre.

A bizonyításnál nem alkalmazható a polinom idejű visszavezetéseknél használt egyszerű kompozíciós trükk (a két gép sorba kapcsolása nem biztos, hogy logaritmikus tárú). Helyette egy háromszalagos $M_1$ gép **a köztes szót nem tárolja**: bináris számlálóval követi, hányadik betűjét olvassa az $f(u)$ szónak, és valahányszor szükséges, újraszámolja azt a betűt.

**3.43. Következmény:** Ha $L$ NL-teljes és $L \in \text{L}$, akkor $\text{L} = \text{NL}$. (Sejtés: $\text{L} \subsetneq \text{NL}$.)

## ELÉRHETŐSÉG

Az ELÉRHETŐSÉG probléma: adott $G=(V,E)$ irányított gráf és $s,t \in V$, van-e út $s$-ből $t$-be.

**3.40. Tétel:** $\text{ELÉRHETŐSÉG} \in \text{SPACE}(\log^2 n)$ — Savitch ELÉR-algoritmusát alkalmazva.

**3.44. Tétel:** ELÉRHETŐSÉG NL-teljes.

- **$\in \text{NL}$:** Egy NTG a bemenetpozíciót (aktuális csúcs $u$, kezdetben $s$) és egy lépésszámlálót tárol $O(\log|V|)$ tárral; nemdeterminisztikusan választ egy $u$-ból elérhető $v$ csúcsot, $|V|$ lépésig.
- **NL-nehéz:** Tetszőleges $L \in \text{NL}$-re az $L$-t eldöntő $O(\log n)$ tárú NTG $M$ **konfigurációs gráfja** $G$ logaritmikus tárral megkonstruálható, és $u \in L \iff$ $G$-ben van út $c_{kezdő}$-ből $c_{elfogadó}$-ba.

## NL ⊆ P

**3.45. Következmény:** $\text{NL} \subseteq \text{P}$.

Egy $O(\log n)$ tárú NTG konfigurációs gráfja legfeljebb $p(n)=n^{2}\cdot n^{c\cdot\log n}$ csúcsú (polinom!), így az ELÉRHETŐSÉG ebben a gráfban polinom időben eldönthető. Innen $\text{NL} \subseteq \text{P}$.

## Immermann–Szelepcsényi tétel

**3.46. Tétel:** $\text{NL} = \text{coNL}$.

**Bizonyítás vázlata:** Megmutatjuk, hogy $\overline{\text{ELÉRHETŐSÉG}} \in \text{NL}$, azaz NL-es TG-pel eldönthető, hogy *nincs* út $s$-ből $t$-be. Az ötlet: az $s$-ből pontosan $i$ lépésben elérhető csúcsok $d_i$ számát induktívan kiszámítjuk ($d_0=1$); $d_{i+1}$ kiszámításához minden csúcsra nemdeterminisztikusan megsejtjük, hogy elérhető-e $\leq i$ lépésben, és a sejtést útkereséssel ellenőrizzük — közben számoljuk, hogy a $d_i$ elérhető csúcsot mind megtaláltuk-e. Végül a $d_{|V|}$ elérhető csúcs ismeretében eldönthető, hogy $t$ közöttük van-e. Mivel $\overline{\text{ELÉRHETŐSÉG}}$ így NL-ben van és (3.26. tétel) coNL-teljes, a 3.28. tétel miatt $\text{NL} = \text{coNL}$.

## 2SAT NL-teljes

**3.47. Tétel:** 2SAT NL-teljes.

- **$\in \text{NL}$:** $\overline{\text{2SAT}} \in \text{NL}$: a $\varphi$ implikációs gráfjában ($G_\varphi$ csúcsai a literálok, élei a klózokból adódó implikációk) $\varphi$ pontosan akkor kielégíthetetlen, ha van olyan kör, amely érint egy $x$ ítéletváltozót és $\neg x$-et is. Ez ELÉRHETŐSÉG-gel ellenőrizhető, így $\overline{\text{2SAT}} \in \text{NL}$, és 3.46. miatt $\text{2SAT} \in \text{NL}$.
- **NL-nehéz:** $\text{ELÉRHETŐSÉG} \leq_l \overline{\text{2SAT}}$: a $G,s,t$ bemenethez a $\varphi = (x\vee x)\bigwedge_{(u,v)\in E'}(\bar u\vee v)$ formula, ahol $s,t$ helyett $x,\neg x$ szerepel; $G$-ben van út $s$-ből $t$-be $\iff$ $\varphi$ kielégíthetetlen. A 3.26. és 3.46. tételekkel innen $\overline{\text{2SAT}}$, majd $\text{2SAT}$ NL-nehézsége adódik.

## Kapocs

- [[concepts/bvszam/tarbonyolultsag-pspace]] — SPACE/NSPACE, Savitch tétele, PSPACE-teljesség
- [[concepts/bvszam/2sat]] — 2SAT $\in$ P, implikációs gráf módszer
- [[concepts/bvszam/np-koztes-es-conp]] — coC osztályok; NL = coNL itt bizonyítva
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP; NL ⊆ P
- [[concepts/bvszam/nemdeterminisztikus-turing-gep]] — NTG, amelyen az NSPACE alapul
