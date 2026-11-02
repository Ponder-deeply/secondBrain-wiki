---
tags: [concept]
sources: [DimatIIEa04.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Csoport és Abel-csoport

Olyan egységelemes félcsoport, amelyben minden elemnek van inverze; ha a művelet ráadásul kommutatív, Abel-csoportról beszélünk.

## Tartalom

### Elem inverze

Legyen $(G; *)$ egységelemes félcsoport $e$ egységelemmel. A $g \in G$ elem **inverze** az a $g^{-1} \in G$ elem, amelyre

$$g * g^{-1} = g^{-1} * g = e.$$

Egy elemnek nem feltétlenül létezik inverze, de ha létezik, akkor **egyértelmű** — a bizonyításhoz a művelet asszociativitása kell.

### Csoport

Ha egy $(G; *)$ egységelemes félcsoportban minden $g \in G$ elemnek létezik inverze, akkor $(G; *)$ **csoport**.

### Abel-csoport

Ha egy $(G; *)$ csoportban a $*$ csoportművelet **kommutatív**, akkor $(G; *)$ **Abel-csoport**.

$\mathbb{Z}$ a legszűkebb olyan (Abel-)csoport, amely tartalmazza $\mathbb{N}$-et; $\mathbb{Z}$ meg is konstruálható $\mathbb{N}$-ből: az $(r, s) \sim (p, q)$ reláció, ha $r + q = p + s$, ekvivalenciareláció, és az osztályai épp az egész számok.

### A csoport ekvivalens definíciói

A $(H, \cdot)$ félcsoport **csoport**, ha (a tétel szerint a négy definíció ekvivalens):

- **I.** van bal oldali egységelem $e_b$, és minden $a$-nak van erre vonatkozó balinverze: $a_b a = e_b$;
- **II.** van egységelem $e$, és minden $a$-nak van inverze: $a^{-1}a = aa^{-1} = e$;
- **III.** minden $a, b$-re egyértelműen létezik az $ax = b$ és az $ya = b$ egyenlet megoldása;
- **IV.** a művelet invertálható: minden $a, b$-re megoldható $ax = b$ és $ya = b$ (nem követeljük meg az egyértelműséget).

*Bizonyítás vázlata.* I. $\Rightarrow$ II.: ha $b$ az $a_b$ balinverze, akkor $ba_b a a_b = (ba_b)aa_b = e_b a a_b = aa_b$, másrészt $= b(a_b a)a_b = b e_b a_b = ba_b = e_b$; így $aa_b = e_b$, azaz $a_b$ kétoldali inverz. Továbbá $aa^{-1}a = (aa^{-1})a = e_b a = a$ és $= a(a^{-1}a) = ae_b$, tehát $ae_b = a$: $e_b$ jobb oldali egységelem is. II. $\Rightarrow$ III.: ha $ax_0 = b$, akkor balról $a^{-1}$-gyel szorozva $x_0 = a^{-1}b$, és ez valóban megoldás: $a(a^{-1}b) = b$; $ya = b$ hasonló. III. $\Rightarrow$ IV. nyilvánvaló. IV. $\Rightarrow$ I.: az $ya = a$ megoldása $e_b$; tetszőleges $b$-re $ax = b$ egy megoldása $x_0$, és $e_b b = e_b(ax_0) = (e_b a)x_0 = ax_0 = b$, tehát $e_b$ bal egységelem; $ya = e_b$ megoldása adja a balinverzet.

A szemléletes tanulság: csoportban az $ax = b$ típusú egyenletek mindig egyértelműen oldhatók, ezért a művelet reguláris (egyszerűsíthető).

### Regularitás és a szorzat inverze

**Következmény.** Csoportban a művelet **reguláris**. *Bizonyítás:* ha $ac = bc = d$, akkor az $yc = d$ egyenlet megoldása egyértelmű, és $a$, $b$ is megoldás, tehát $a = b$; a másik oldali regularitás hasonlóan látható be.

**Szorzat inverze:** $(ab)^{-1} = b^{-1}a^{-1}$, hiszen $(b^{-1}a^{-1})ab = b^{-1}(a^{-1}a)b = b^{-1}b = e$.

**Pitfall:** az, hogy $ax = b$ és $ya = b$ minden $a,b$-re egyértelműen megoldható (a szorzótábla minden sorában és oszlopában minden elem pontosan egyszer szerepel), önmagában még nem elég a csoporthoz. A $H = \{a,b,c\}$ struktúra, melynek táblája (sorok: bal tényező)

| $\cdot$ | a | b | c |
|---|---|---|---|
| a | b | a | c |
| b | a | c | b |
| c | c | b | a |

invertálható és egyértelműen oldható, de nincs egységeleme és nincs inverze. Ennek oka, hogy a művelet **nem asszociatív**: $(ab)c = ac = c$, de $a(bc) = ab = a$.

### Nevezetes példák (Farkas-diák)

- Az $n$-edik komplex egységgyökök a szorzással Abel-csoportot alkotnak; ugyanígy az összes $p^n$-edik egységgyök ($n = 1,2,\dots$, $p$ prím) — ez a $Z(p^\infty)$ **Prüfer-csoport** —, és az összes egységgyök, valamint az egységnyi abszolút értékű komplex számok.
- A $Q = \{\pm 1, \pm i, \pm j, \pm k\}$ kvaterniócsoport a kvaterniószorzással **nem kommutatív** csoport.
- A **Klein-féle csoport** $\{e,a,b,c\}$ táblája: $e$ egységelem, $a^2 = b^2 = c^2 = e$, $ab = c$, $bc = a$, $ca = b$ (kommutatív). Részcsoportjai kapcsán lásd [[concepts/dimatii/reszcsoport]].

### Példák

- $(\mathbb{Q}; +)$ Abel-csoport $0$ egységelemmel.
- $(\mathbb{Q}^*; \cdot)$ Abel-csoport $1$ egységelemmel, ahol $\mathbb{Q}^* = \mathbb{Q} \setminus \{0\}$.
- $(\mathbb{Z}_m; +)$ Abel-csoport $\overline{0}$ egységelemmel.
- $(\mathbb{Z}_p^*; \cdot)$ Abel-csoport $\overline{1}$ egységelemmel ($p$ prím).
- $\{M \in \mathbb{C}^{k \times k} : \det M \ne 0\}$ a mátrixszorzással csoport az egységmátrixszal mint egységelemmel, de $k > 1$ esetén **nem** Abel.
- Az $X \to X$ bijektív függvények a kompozícióval csoportot alkotnak, egységeleme az $\mathrm{id}_X : x \mapsto x$ identikus leképezés.

A $(\mathbb{Z}_p^*; \cdot)$ csoport ciklikus is: a benne található generátor a [[concepts/dimatii/primitiv-gyok]] lapon szerepel.

### Feladattípusok és módszerek (gyakorlati feladatsor, 2020 ősz, 6. sor)

Egy $(H,\circ)$ pár csoport-e? Ellenőrzési lánc: művelet → asszociatív → egységelem → inverz ([[concepts/dimatii/muvelet]], [[concepts/dimatii/felcsoport-es-monoid]]). A feladatsor példáiban egyik vizsgált szerkezet sem csoport: a $(\mathbb{Q}, \tfrac{a+b}{2})$ és az $(\mathbb{R}\setminus\{0\}, \div)$ nem asszociatív, a $\max$-félcsoportnak nincs egységeleme, a $(\mathbb{Z}, \tfrac{a+b}{2})$ nem is művelet. Ezzel szemben $(S,+)$ minden Abel-csoportja a zérógyűrű additív csoportja (lásd [[concepts/dimatii/gyuru]]).

## Kapocs

- [[concepts/dimatii/felcsoport-es-monoid]] — a kiindulási struktúra, amelyhez az inverzek hozzáadódnak
- [[concepts/dimatii/algebrai-struktura]] — a fogalmi keret
- [[concepts/dimatii/gyuru]] — a gyűrű additív része definíció szerint Abel-csoport
- [[concepts/dimatii/test]] — a nemnulla elemek a szorzásra csoportot alkotnak
- [[concepts/dimatii/primitiv-gyok]] — $\mathbb{Z}_p^*$ ciklikussága
- [[concepts/dimatii/reszcsoport]] — részcsoport, komplexus, generátum
- [[concepts/dimatii/ciklikus-csoport]] — egy elem által generált csoport
- [[concepts/dimatii/elem-rendje]] — a csoport és az elem rendje
