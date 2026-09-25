---
tags: [concept, dimatii/forraskodolas]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# Entrópia

Egy üzenetforrás által kibocsátott üzenetek átlagos információtartalma, amely csak az üzenetek eloszlásától függ, a tartalmuktól nem.

## Tartalom

A kommunikáció során információt hordozó adatokat viszünk át egy csatornán keresztül az információforrástól, az adótól az információ címzettjéhez, a vevőhöz. Az információ átvitele térben és időben egyaránt történhet: telefonáláskor a térbeli, adathordozóra rögzítéskor és későbbi visszaolvasáskor az időbeli dimenzió a domináns. Az információ új ismeret; Shannon nyomán az általa megszüntetett bizonytalansággal mérjük.

### Gyakoriság és egyedi információtartalom

Tegyük fel, hogy egy információforrás összesen $n$ üzenetet bocsát ki, és az összes ténylegesen előforduló különböző üzenet $a_1, a_2, \dots, a_k$. Ha az $a_j$ üzenet $m_j$-szer fordul elő, akkor a **gyakorisága** $m_j$, a **relatív gyakorisága** pedig
$$p_j = \frac{m_j}{n} > 0 .$$
A $p_1, p_2, \dots, p_k$ szám $k$-ast az üzenetek **eloszlásának** nevezzük; erre $\sum_{j=1}^k p_j = 1$.

Az $a_j$ üzenet **egyedi információtartalma**
$$I_j = -\log_r p_j ,$$
ahol az $r > 1$ valós szám az **információ egységét** határozza meg. Ha $r = 2$, akkor az információ egysége a **bit**.

### Az entrópia definíciója

Az üzenetforrás által kibocsátott üzenetek átlagos információtartalma a forrás **entrópiája**:
$$H_r(p_1, p_2, \dots, p_k) = -\sum_{j=1}^k p_j \log_r p_j .$$

Ez csak az üzenetek eloszlásától függ, a tartalmuktól nem. Általánosabban **eloszlásnak** nevezünk minden olyan $p_1, \dots, p_k$ pozitív valós számokból álló sorozatot, amelyre $\sum_{j=1}^k p_j = 1$; ennek entrópiája ugyanezzel a képlettel adódik.

### Az entrópia felső korlátja

**Tétel.** Bármilyen eloszláshoz tartozó entrópiára
$$H_r(p_1, p_2, \dots, p_k) \le \log_r k ,$$
és egyenlőség pontosan akkor teljesül, ha $p_1 = p_2 = \dots = p_k = \frac{1}{k}$.

*Bizonyítás.* $r > 1$ esetén a $-\log_r(x)$ függvény szigorúan konvex, ezért alkalmazható a Jensen-egyenlőtlenség a $q_j = \frac{1}{p_j}$ választással:
$$-H_r(p_1, \dots, p_k) = \sum_{j=1}^k p_j \log_r p_j = \sum_{j=1}^k p_j\left(-\log_r \frac{1}{p_j}\right) \ge -\log_r\left(\sum_{j=1}^k p_j \frac{1}{p_j}\right) = -\log_r k . \qquad \square$$

Az entrópia tehát akkor maximális, amikor a forrás minden üzenete egyformán valószínű: ekkor a legnagyobb az a bizonytalanság, amit egy üzenet megszüntet.

### A felhasznált konvexitás

Egy $f : I \to \mathbb{R}$ függvény **konvex** az $I \subset \mathbb{R}$ intervallumon, ha bármely $x_1, x_2 \in I$ és $0 \le t \le 1$ esetén
$$f(tx_1 + (1-t)x_2) \le t f(x_1) + (1-t) f(x_2),$$
és **szigorúan konvex**, ha egyenlőség csak $t = 0$ vagy $t = 1$ esetén lehetséges.

**Jensen-egyenlőtlenség.** Legyen $p_1, p_2, \dots, p_k$ egy eloszlás, $f$ pedig szigorúan konvex függvény az $I \subset \mathbb{R}$ intervallumon. Ekkor $q_1, q_2, \dots, q_k \in I$ esetén
$$f\left(\sum_{j=1}^k p_j q_j\right) \le \sum_{j=1}^k p_j f(q_j),$$
és egyenlőség pontosan akkor áll fenn, ha $q_1 = q_2 = \dots = q_k$.

## Kapocs

- [[concepts/dimatii/shannon-tetel-zajmentes-csatornara]] — az entrópia a felbontható betűnkénti kódok átlagos szóhosszának alsó korlátja
- [[concepts/dimatii/optimalis-kod]] — az átlagos szóhossz, amelyet az entrópia korlátoz
- [[concepts/dimatii/huffman-kod]] — a példáiban az entrópiát az elért átlagos szóhosszal vetjük össze
- [[concepts/dimatii/betunkenti-kodolas]] — a kódolás kerete, amelyben az entrópia korlátként megjelenik
