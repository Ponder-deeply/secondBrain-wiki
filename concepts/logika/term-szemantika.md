---
tags: [concept, logika/elsorendu-logika-szemantika]
sources: [Elsőrendű_logika_szemantika.pdf]
derivation: source
updated: 2026-09-08
---

# Term szemantikája

Egy $t$ term $I$ interpretáció és $\kappa$ változókiértékelés melletti $|t|^{I,\kappa}$ helyettesítési értéke szerkezeti rekurzióval van definiálva: a term felépítése szerint konstansra, változóra, illetve összetett termre esik szét.

## Tartalom

### A kiértékelés két lépése

Egy formula (és a benne szereplő termek) jelentésének megállapítása két lépésben történik:

1. Kiválasztunk egy, a nyelvvel azonos szignatúrájú interpretáló struktúrát — ez az $I$ [[concepts/logika/elsorendu-interpretacio]].
2. A nem kötött (szabad) individuumváltozókat kiértékeljük egy $\kappa$ [[concepts/logika/valtozokiertekeles]] segítségével, és ez alapján kiszámítjuk a kifejezések helyettesítési értékét.

### Formális definíció

A $t$ term $I,\kappa$ melletti $|t|^{I,\kappa}$ helyettesítési értéke a term felépítése szerinti rekurzióval:

1. Ha $c$ konstansszimbólum, akkor $|c|^{I,\kappa}$ az $U$-beli $c^I$ elem (az interpretáció adja meg, $\kappa$-tól független).
2. Ha $x$ individuumváltozó, akkor $|x|^{I,\kappa}$ a $\kappa(x) \in U$ elem.
3. Ha a term összetett, $f(t_1, t_2, \dots, t_n)$ alakú, akkor
$$|f(t_1, t_2, \dots, t_n)|^{I,\kappa} = f^I\big(|t_1|^{I,\kappa}, |t_2|^{I,\kappa}, \dots, |t_n|^{I,\kappa}\big).$$

Vagyis az összetett term értéke: az $I$ interpretáció szerinti $f^I$ művelet alkalmazva a résztermek (rekurzívan kiszámított) értékeire.

### Példa

Legyen az interpretáló struktúra leíró nyelve $S = \mathbb{N}(=, <, >;\ 0, 1, +, *)$, ahol $a \mapsto 0$, $b \mapsto 1$, $f_1 \mapsto {+}$, $f_2 \mapsto {*}$ (lásd [[concepts/logika/elsorendu-interpretacio]] példáját). A $t = f_1(x, f_2(x, y))$ term értéke:

$$|t|^{I,\kappa} = |f_1|^I\big(|x|^{I,\kappa},\ |f_2(x,y)|^{I,\kappa}\big) = +(x, *(x, y)) = x + x*y.$$

Konkrét $\kappa$-kra: $\kappa_1(x)=1,\kappa_1(y)=1 \Rightarrow |t| = 2$; $\kappa_2(x)=2,\kappa_2(y)=3 \Rightarrow |t| = 8$.

A term szemantikájára épül a formulák szemantikája: egy $P(t_1,\dots,t_n)$ atomi formula pontosan akkor igaz $I,\kappa$ mellett, ha a résztermek kiértékelt értékeiből álló $n$-es benne van a $P^I$ reláció igazhalmazában — lásd [[concepts/logika/szemantikus-tulajdonsagok]].

## Kapocs

- [[concepts/logika/elsorendu-interpretacio]] — a struktúra, amely a függvényszimbólumokat konkrét műveletekhez rendeli
- [[concepts/logika/valtozokiertekeles]] — $\kappa$, amely a szabad változók értékét adja
- [[concepts/logika/szemantikus-tulajdonsagok]] — a term szemantikájára épülő formula-szemantika és a hozzá kötődő tulajdonságok
- [[concepts/logika/term]] — a term mint szintaktikai fogalom
