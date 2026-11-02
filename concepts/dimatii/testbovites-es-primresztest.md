---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Testbővítés, prímrészteszt és a bővítés foka

Ha a $K$ test részteste az $F$ testnek, akkor $F$ a $K$ bővítése ($F : K$), és $F$ vektortér $K$ fölött; a bővítés foka ennek dimenziója. Minden test prímrészteste $\mathbb{Z}_p$-vel vagy $\mathbb{Q}$-val izomorf, a karakterisztikától függően.

## Tartalom

### Résztest, bővítés

**Definíció.** Legyen $F$ tetszőleges test. $K$ az $F$ **résztestje**, ha $K \subseteq F$ és $K$ maga is testet alkot az $F$ műveleteivel. Jelölés: $F : K$; ekkor $F$ a $K$ **bővítése**. Ha $K \neq F$, akkor $K$ **valódi résztest**, $F$ **valódi bővítés**.

**Észrevétel.** Ha $K$ részteste $F$-nek, akkor $F$ és $K$ karakterisztikája megegyezik. Véges test karakterisztikája prímszám.

### Prímtest és prímrészteszt

**Definíció.** Egy test **prímtest**, ha nincs valódi résztestje.

Résztestek metszete résztest, ezért az $F$ összes résztestének metszete az $F$ legszűkebb résztestje; ennek nincs valódi résztestje, tehát prímtest. Ez az $F$ **prímrészteste** (a diákban $\mathbb{F}_p$).

- Test prímrészteste prímtest.
- Ha $F$ a $K$ bővítése, akkor prímrésztesteik megegyeznek.

**Tétel (prímrésztestek).** Tetszőleges $F$ test prímrészteste izomorf $\mathbb{Z}_p$-vel, ha $\operatorname{char}(F) = p$, és $\mathbb{Q}$-val, ha $\operatorname{char}(F) = 0$.

*Bizonyítás.* Legyen $e$ az $F$ egységeleme.

- $\operatorname{char}(F) = p$: a prímrészteszt additív csoportjának elemei $e^n$ (azaz $n\cdot e$) alakúak, vagyis $\mathbb{F}_p = \{0 = e^0, e^1, \dots, e^{p-1}\}$, és az $e^k \mapsto 1^k$ megfeleltetés izomorfizmus $\mathbb{Z}_p$-re.
- $\operatorname{char}(F) = 0$: legyen $R = \{ke/(le) \mid k, l \in \mathbb{Z},\ l \neq 0\}$, ahol $ke = e + \dots + e$. A $k/l \mapsto ke/(le)$ leképezés izomorfizmus $\mathbb{Q}$ és $R$ között, így $R$ is test, résztest $F$-ben. Mivel $e \in \mathbb{F}_p$, $R$ elemei is $\mathbb{F}_p$-ben vannak, azaz $R \subseteq \mathbb{F}_p$; $\mathbb{F}_p$ legszűkebb volta miatt $\mathbb{F}_p = R \cong \mathbb{Q}$. $\square$

**Következmény.** Minden $p$ karakterisztikájú test $\mathbb{Z}_p$ bővítése, és minden nullkarakterisztikájú test $\mathbb{Q}$ bővítése.

### Vektortér-szerkezet és a bővítés foka

Ha $K$ részteste $F$-nek, akkor $F$ vektortér $K$ fölött: a $K \times F \to F$ külső művelet (az $F$-beli szorzás megszorítása) kielégíti a vektortér-axiómákat ($a(v+w) = av + aw$, $(a+b)v = av + bv$, $(ab)v = a(bv)$, $1\cdot v = v$).

**Definíció.** Ha $F$ mint $K$ fölötti vektortér nem véges dimenziós, a bővítés **végtelen**, különben **véges**. Az $F : K$ **bővítés foka** az $F$ $K$ fölötti vektortérként vett dimenziója, jelben $[F : K]$.

**Tétel (fokszámtétel).** Ha $M : L$ és $L : K$ véges testbővítés, akkor $M : K$ is véges, és
$$[M : K] = [M : L]\,[L : K].$$

**Tétel.** Tetszőleges $K$ test véges bővítése algebrai $K$ fölött (lásd [[concepts/dimatii/algebrai-elem-es-minimalpolinom]]).

## Kapocs

- [[concepts/dimatii/test]] — a résztest és a bővítés alapfogalma
- [[concepts/dimatii/veges-testek]] — véges testek karakterisztikája és elemszáma; a prímrészteszt $\mathbb{Z}_p$
- [[concepts/dimatii/algebrai-elem-es-minimalpolinom]] — algebrai elem és bővítés
- [[concepts/dimatii/egyszeru-testbovites]] — a $K(\alpha)$ bővítés szerkezete
- [[concepts/dimatii/nullosztomentes-gyuru]] — a karakterisztika fogalma
