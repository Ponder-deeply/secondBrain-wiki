---
tags: [concept, bigdata/ajanlorendszerek]
sources: [BDAEM-2022-EA11.pdf]
references: ["Y. Koren, R. Bell, C. Volinsky. Matrix factorization techniques for recommender systems. Computer, 42(8):30-37, 2009."]
derivation: source
updated: 2026-09-12
---

# Mátrixfaktorizáció ajánlórendszerekben

Modellalapú, dimenziócsökkentésen alapuló kollaboratív szűrési módszer, amely a
felhasználó–elem értékelési mátrixot két alacsony rangú mátrix szorzataként
közelíti, ezzel rejtett (latens) faktorokban ragadva meg a felhasználók és
elemek közti hasonlóságot.

## Tartalom

### A Netflix Prize és az RMSE proxy-metrika

A forrás a Netflix Prize versenyt hozza fel motivációként: a valódi cél a
**magas minőségű ajánlás**, de ez közvetlenül nehezen mérhető, ezért a verseny
egy **proxy-kérdést** használt — az előrejelzett értékelés pontossága, mérve a
gyök-átlagos négyzetes hibával (RMSE):

$$\mathrm{RMSE} = \sqrt{\frac{1}{n}\sum_{j=1}^{n}(y_j-\hat y_j)^2}$$

A verseny tétje 1 millió dollár volt a kiinduló Cinematch-rendszerhez képest
10%-os RMSE-javításért. A forrás tanulsága: „nagyon egyszerű 'elfogadható'
ajánlásokat produkálni, és rendkívül nehéz ezeket tovább javítani” — az
első, egyszerű modellek (Random, Average, Cinematch) és a győztes megoldás
közötti RMSE-különbség viszonylag kicsi volt.

### SVD (szinguláris érték felbontás) mint kiindulópont

A szinguláris érték felbontás egy $X$ mátrixot ($n\times m$, pl. $n$
felhasználó, $m$ elem) három tényezőre bont:

$$X_{[n\times m]} = U_{[n\times r]}\, S_{[r\times r]}\, (V_{[m\times r]})^T$$

ahol $U$ az $n\times r$ felhasználó-faktor mátrix, $S$ az $r\times r$
diagonális mátrix (az egyes rejtett faktorok "erőssége", $r$ a mátrix rangja),
$V$ pedig az $m\times r$ elem-faktor mátrix. A **csonkolt SVD** ($A_k$) az
adatok legjobb alacsony rangú közelítése Frobenius-norma szerint:

$$\|A - A_k\|_F = \min_{\mathrm{rank}(B)=k} \|A-B\|_F$$

Az SVD hasznos zajszűrésre, vizualizációra és a mögöttes struktúra
feltárására — ez a **csökkentett dimenziójú tér**, ami a legfontosabb aspektust
ragadja meg és a többit figyelmen kívül hagyja (vö. főkomponens-elemzés).

### Az SVD problémája hiányzó értékekkel

A klasszikus SVD teljes bemeneti mátrixot feltételez — minden bejegyzést
ismertnek és figyelembe vettnek tekint. Az ajánlórendszerek mátrixa viszont
jellemzően nagyrészt hiányos (a felhasználók csak az elemek töredékét
értékelik). Heurisztikák a hiányzó értékek előzetes kitöltésére (pl. az elem
átlagértékelésével, vagy egyszerűen nullával) torzítást visznek a modellbe.

### Mátrixkiegészítés (matrix completion)

A **mátrixkiegészítés** technikái elkerülik a hiányzó bejegyzések előzetes
kitöltésének szükségességét azzal, hogy kizárólag a ténylegesen megfigyelt
értékelésekre alapozva optimalizálnak — ez tekinthető az SVD egy
alkalmazásfüggő optimalizálási kritérium szerinti becslésének/közelítésének.
A Netflix Prize is azt igazolta, hogy ez a legjobb egymodelles megközelítés
a kollaboratív szűrésre.

A kiegészítést egy $R \approx P \times Q$ faktorizáció hajtja végre: minden
felhasználóhoz és minden elemhez egy rejtett faktorvektort ($p_i$, illetve
$q_j$) rendelünk, és a hiányzó bejegyzéseket ezek skalárszorzatával
becsüljük:

$$r_{ij} \approx p_i q_j$$

### Latens faktormodellek (Koren et al., 2009)

Egy $r=1$ rejtett faktor esetén a módszer minden filmhez és minden
felhasználóhoz egyetlen számot rendel (pl. "komoly ↔ escapista" vagy
"nőknek szóló ↔ férfiaknak szóló" tengely mentén), és ezek szorzata adja az
előrejelzett értékelést. A forrás egy 3 felhasználós (Anni, Bob, Charlie), 3
filmes (Avatar, The Matrix, Up) példán mutatja be, hogyan tanulhatók meg a
faktorok úgy, hogy szorzatuk minél jobban közelítse a megfigyelt
értékeléseket, majd a tanult faktorokkal a hiányzó cellák (a példában
`?`-lel jelölve) is kitölthetők.

#### A veszteségfüggvény fokozatos bővítése

A forrás lépésről lépésre bővíti a minimalizálandó célfüggvényt:

1. **Alapváltozat** — csak a megfigyelt $(i,j)\in\Omega$ párokra vett
   négyzetes hiba:
   $$\min_{Q,P} \sum_{(i,j)\in\Omega} \left(v_{ij} - [Q^T P]_{ij}\right)^2$$
2. **Torzítással (bias)** — a globális átlag ($\mu$), valamint a
   felhasználó- ($u_i$) és elem-specifikus ($m_j$) torzítás hozzáadásával:
   $$\min_{Q,P,u,m} \sum_{(i,j)\in\Omega} \left(v_{ij} - \mu - u_i - m_j -
   [Q^T P]_{ij}\right)^2$$
3. **Regularizációval** — a paraméterek normájának büntetésével a túltanulás
   ellen:
   $$+\ \lambda\left(\|Q\|+\|P\|+\|u\|+\|m\|\right)$$

A forrás megjegyzi, hogy a valós rendszerek (pl. a Netflix Prize győztes
megoldása) ezen felül időbeli dinamikát (temporal dynamics) és implicit
visszajelzést is bevonnak a modellbe, ezekkel tovább csökkentve az RMSE-t.

### Optimalizálás sztochasztikus gradiens módszerrel (SGD)

A $\Theta = \{P, Q\}$ paramétereket a veszteségfüggvény ($L$) minimumát kereső
**sztochasztikus gradiens módszerrel** (stochastic gradient descent) tanuljuk:
egy kezdőpontból ($\Theta^0$) indulva, minden egyes tanítópontra iteratív
frissítést végzünk:

$$\Theta_{n+1} \leftarrow \Theta_n - \eta \frac{\partial L}{\partial \Theta}$$

ahol $\eta$ a tanulási ráta (learning rate). Az egyes bejegyzésekre vett
négyzetes hiba

$$L_{ij}(P,Q) = (r_{ij} - p_i q_j)^2$$

alapján az SGD az $\varepsilon_{ij} = r_{ij} - p_i q_j$ hibát felhasználva
frissíti iteratívan a $p_i$ és $q_j$ faktorvektorokat.

## Kapocs

- [[concepts/bigdata/ajanlorendszerek-alapjai]] — a mátrixfaktorizáció helye a
  memória-/modellalapú kollaboratív szűrés taxonómiájában
- [[concepts/bigdata/felhasznalo-alapu-kollaborativ-szures]] — a memóriaalapú
  módszer, amelynek ritkasági és skálázhatósági problémáira a
  mátrixfaktorizáció modellalapú választ ad
- [[concepts/bigdata/elem-alapu-kollaborativ-szures]] — a másik memóriaalapú
  szomszédsági módszer, ugyanazon értékelési mátrixon
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a modellalapú kollaboratív
  szűrés a gépi tanulás keretrendszerébe illeszkedik (veszteségfüggvény,
  regularizáció, gradiens módszer)
