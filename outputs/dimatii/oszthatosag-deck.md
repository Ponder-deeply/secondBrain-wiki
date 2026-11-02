`button-fc-review` | `button-fc-cram`

#flashcards/dimatii/oszthatosag

## Mi az oszthatóság ($a \mid b$) definíciója az egész számok körében?
?
Az $a$ egész **osztja** a $b$ egészet ($a \mid b$), ha létezik olyan $c \in \mathbb{Z}$, hogy
$$a \cdot c = b,$$
azaz $b/a$ is egész.
---

## Miért érdemi reláció az oszthatóság $\mathbb{Z}$-ben, és miért nem $\mathbb{Q}$-ban?
?
$\mathbb{Q}$-ban az $a/b$ osztás ($b \neq 0$) mindig elvégezhető, és az eredmény racionális, így ott minden nem nulla szám oszt mindent. $\mathbb{Z}$-ben a hányados nem feltétlenül egész, ezért az $a \mid b$ állítás valódi információt hordoz.
---

## Mit mond az oszthatóság lineáris kombinációs tulajdonsága, és mire épül rá?
?
Ha $a \mid b_1, \dots, a \mid b_k$, akkor minden $c_1, \dots, c_k \in \mathbb{Z}$ esetén
$$a \mid c_1b_1 + \cdots + c_kb_k.$$
Azaz egy közös osztó az egész együtthatós lineáris kombinációt is osztja. Erre épül az euklideszi algoritmus helyességének bizonyítása.
---

## Mi következik $\mathbb{Z}$-ben abból, hogy $a \mid b$ és $b \mid a$?
?
$a = \pm b$. Az oszthatóság tehát nem antiszimmetrikus: csak asszociáltság erejéig határozza meg a számot (reflexív és tranzitív, azaz kvázirendezés).
---

## Mit mondhatunk a $0$-ról az oszthatóság szempontjából?
?
- $a \mid 0$ minden $a$-ra, mert $a \cdot 0 = 0$;
- $0 \mid a \iff a = 0$.
---

## Milyen feltétellel egyszerűsíthető egy oszthatóság: $ac \mid bc \Rightarrow a \mid b$?
?
Ha $c \neq 0$. Megfordítva feltétel nélkül igaz: $a \mid b \Rightarrow ac \mid bc$. Továbbá $a \mid b$ és $a' \mid b'$ esetén $aa' \mid bb'$.
---

## Mi az egység definíciója, és melyek az egységek $\mathbb{Z}$-ben?
?
Egy szám **egység**, ha bármely másik számnak osztója. $\mathbb{Z}$-ben pontosan két egység van: $1$ és $-1$.
---

## Miért csak $\pm 1$ az egység $\mathbb{Z}$-ben?
?
Ha $\varepsilon$ egység, akkor $\varepsilon \mid 1$, azaz $1 = \varepsilon q$ valamely $q \in \mathbb{Z}$-re. Mivel nem nulla egészekre $|\varepsilon| \geq 1$ és $|q| \geq 1$, a szorzat abszolút értéke csak úgy lehet $1$, ha $|\varepsilon| = 1$, azaz $\varepsilon = \pm 1$.
---

## Mondj egy $\pm 1$-től különböző egységet a Gauss-egészek ($\{a+bi : a,b \in \mathbb{Z}\}$) körében, és indokold!
?
$i$ egység, mert minden Gauss-egészt oszt:
$$a + bi = i\,(b - ai).$$
---

## Mikor asszociált két szám, és hogyan fogalmazható ez meg oszthatósággal?
?
$a$ és $b$ **asszociált**, ha egymás egységszeresei. Ekvivalensen: $a \mid b$ és $b \mid a$. (Az oszthatóság mint kvázirendezés szimmetrikus magja.)
---

## Mik egy szám triviális osztói?
?
Az **asszociáltjai** és az **egységek**. $\mathbb{Z}$-ben $n$ triviális osztói: $\pm 1$ és $\pm n$.
---

## Mi a felbonthatatlan (irreducibilis) elem definíciója?
?
Egy **nem nulla, nem egység** $t$ szám felbonthatatlan, ha a triviális osztóin kívül nincs más osztója. Ekvivalensen:
$$t = ab \;\Rightarrow\; a \text{ vagy } b \text{ egység.}$$
---

## Mi a prímelem (prímszám) definíciója?
?
Egy **nem nulla, nem egység** $p$ szám prím, ha
$$p \mid ab \;\Rightarrow\; p \mid a \ \text{ vagy } \ p \mid b.$$
---

## Miben tér el a felbonthatatlanság a prímtulajdonságtól?
?
A **felbonthatatlanság** a szám *osztóiról* szól (nincs nemtriviális szorzatfelbontása), a **prímtulajdonság** a szám *osztási viselkedéséről* (ha szorzatot oszt, valamelyik tényezőt osztja). $\mathbb{Z}$-ben a kettő egybeesik, általában nem: a prím mindig felbonthatatlan, fordítva nem feltétlenül.
---
<!--SR:!2026-09-29,3,250-->

## Miért nem prím és miért nem felbonthatatlan a $6$?
?
- Nem felbonthatatlan: $6 = 2 \cdot 3$, és egyik tényező sem egység.
- Nem prím: $6 \mid 2 \cdot 3$, de $6 \nmid 2$ és $6 \nmid 3$.
---

## Miért felbonthatatlan minden prím?
?
Legyen $p$ prím, $p = ab$. Ekkor $p \mid ab$, így például $p \mid a$, azaz $a = pk$. Behelyettesítve $a = pk = a(bk)$, és $a \neq 0$ miatt $bk = 1$, tehát $b$ egység. (Minden integritási tartományban igaz.)
---

## Hogyan bizonyítjuk, hogy $\mathbb{Z}$-ben minden felbonthatatlan szám prím?
?
Legyen $p$ felbonthatatlan, $p \mid ab$, és tegyük fel, hogy $p \nmid b$. Ekkor $p$ és $b$ relatív prímek (közös osztójuk csak triviális osztója lehet $p$-nek, $p$ asszociáltjai pedig nem osztják $b$-t), így a bővített euklideszi algoritmus ad $x, y$ egészeket, hogy
$$px + by = 1.$$
$a$-val szorozva $pax + aby = a$. $p$ osztja a bal oldal mindkét tagját ($p \mid pax$, $p \mid ab$), tehát $p \mid a$.
---

## Hol nem igaz, hogy minden felbonthatatlan elem prím?
?
Például a $\{a + bi\sqrt{5} : a, b \in \mathbb{Z}\}$ számkörben. A *prím $\Rightarrow$ felbonthatatlan* irány minden integritási tartományban igaz, a megfordítás $\mathbb{Z}$-ben a bővített euklideszi algoritmuson múlik.
---

## Mi a legnagyobb közös osztó definíciója?
?
$d = (a,b)$ az $a$ és $b$ legnagyobb közös osztója, ha
$$d \mid a,\quad d \mid b, \qquad \text{és} \qquad c \mid a,\ c \mid b \;\Rightarrow\; c \mid d.$$
Azaz közös osztó, és minden közös osztónak többszöröse.
---

## Miért nem egyértelmű a legnagyobb közös osztó, és milyen konvencióval tesszük azzá?
?
A „legnagyobb” az **oszthatósági** rendezésre utal, nem a szokásosra, ezért $(a,b)$ csak asszociáltság erejéig egyértelmű: például $12$ és $9$ legnagyobb közös osztója $3$ és $-3$ is. Konvenció: $(a,b)$ a **pozitív** legnagyobb közös osztót jelöli.
---

## Mi a legkisebb közös többszörös definíciója?
?
$m = [a,b]$ az $a$ és $b$ legkisebb közös többszöröse, ha
$$a \mid m,\quad b \mid m, \qquad \text{és} \qquad a \mid c,\ b \mid c \;\Rightarrow\; m \mid c.$$
Csak asszociáltság erejéig egyértelmű; $[a,b]$ a pozitívat jelöli.
---

## Mikor relatív prím két egész szám?
?
Ha $(a,b) = 1$, azaz közös osztóik csak az egységek ($\pm 1$).
---

## Hogyan számolható több szám legnagyobb közös osztója?
?
Páronkénti lépésekben:
$$(a_1, a_2, \dots, a_n) = \big((\dots(a_1,a_2),\dots,a_{n-1}), a_n\big),$$
és ez bármely $a_1, \dots, a_n$ egészekre létezik.
---

## Hogyan viselkedik a legnagyobb közös osztó, ha mindkét számot ugyanazzal a $c$-vel szorozzuk?
?
$$(ca, cb) = c\,(a,b)$$
(asszociáltság erejéig; pozitív lnko-konvencióval $c > 0$ esetén szó szerint).
---

## Hogyan számolható $(m,n)$ és $[m,n]$ a kanonikus alakból?
?
Közös prímeken felírva $n = \prod p_i^{\alpha_i}$, $m = \prod p_i^{\beta_i}$ ($\alpha_i, \beta_i \geq 0$):
$$(m,n) = \prod_{i=1}^{\ell} p_i^{\min\{\alpha_i,\beta_i\}}, \qquad [m,n] = \prod_{i=1}^{\ell} p_i^{\max\{\alpha_i,\beta_i\}}.$$
---

## Mi az összefüggés $(m,n)$, $[m,n]$ és $mn$ között, és miért igaz?
?
$$(m,n)\cdot[m,n] = m\cdot n \qquad (m, n > 0).$$
Kanonikus alakból: a kitevőkre $\min\{\alpha,\beta\} + \max\{\alpha,\beta\} = \alpha + \beta$. Haszna: $[m,n] = mn/(m,n)$ prímfelbontás nélkül, euklideszi algoritmussal számolható.
---

## Mit mond a maradékos osztás tétele?
?
Tetszőleges $a$ és $b \neq 0$ egészekhez **egyértelműen** léteznek $q, r$ egészek, hogy
$$a = bq + r, \qquad 0 \leq r < |b|.$$
Jelölés: $a \bmod b = r$.
---

## Miért egyértelmű a maradékos osztás?
?
Ha $a = bq + r = bq^* + r^*$ (mindkét maradék $[0, |b|)$-ben), akkor
$$b(q - q^*) = r^* - r.$$
A jobb oldalra $|r^* - r| < |b|$, a bal oldal pedig $b$ többszöröse, így csak $0$ lehet: $q = q^*$, $r = r^*$.
---

## Mennyi $-123 \bmod 10$, és miért nem $-3$?
?
$-123 \bmod 10 = 7$, mert $-123 = 10 \cdot (-13) + 7$. A maradék definíció szerint mindig nemnegatív: $0 \leq r < |b|$.
---

## Hogyan működik az euklideszi algoritmus, és mi az eredménye?
?
Ismételt maradékos osztás, mindig az osztót a maradékkal osztva:
$$a = bq_1 + r_1,\quad b = r_1q_2 + r_2,\quad r_1 = r_2q_3 + r_3,\ \dots,\quad r_{n-1} = r_nq_{n+1}.$$
Az **utolsó nem nulla maradék** a legnagyobb közös osztó: $(a,b) = r_n$. (Ha valamelyik szám $0$, az lnko a másik.)
---

## Miért áll meg véges sok lépésben az euklideszi algoritmus?
?
A maradékokra $|b| > r_1 > r_2 > \dots \geq 0$, ez szigorúan csökkenő nemnegatív egész sorozat, tehát véges.
---
<!--SR:!2026-09-29,3,250-->

## Miért közös osztója $a$-nak és $b$-nek az euklideszi algoritmus utolsó nem nulla maradéka, $r_n$?
?
Alulról felfelé: $r_n \mid r_{n-1}$, ezért $r_n \mid r_{n-1}q_n + r_n = r_{n-2}$, és így tovább visszafelé a sorokon, míg $r_n \mid b$, majd $r_n \mid a$.
---

## Miért osztja az euklideszi algoritmus $r_n$ maradékát $a$ és $b$ minden közös osztója?
?
Felülről lefelé, a lineáris kombinációs tulajdonsággal: ha $c \mid a$ és $c \mid b$, akkor $c \mid a - bq_1 = r_1$, majd $c \mid b - r_1q_2 = r_2$, …, végül $c \mid r_{n-2} - r_{n-1}q_n = r_n$.
---

## Mi az euklideszi algoritmus rekurzív alakja?
?
Legyen $a \neq 0$. Ha $b = 0$, akkor $(a,b) = a$; ha $b \neq 0$, akkor
$$(a,b) = \big(|b|,\ a \bmod |b|\big).$$
Például $(172,62) \to (62,48) \to (48,14) \to (14,6) \to (6,2) \to (2,0)$, tehát $(172,62) = 2$.
---

## Mi az euklideszi algoritmus egyik fontos elméleti következménye a legnagyobb közös osztóra?
?
Bármely két egész számnak **létezik** legnagyobb közös osztója — az algoritmus ezt konstruktívan igazolja (a definícióból a létezés nem magától értetődő).
---

## Mit állít a bővített euklideszi algoritmus tétele?
?
Minden $a, b$ egészhez léteznek $x, y$ egészek, hogy
$$(a,b) = xa + yb,$$
azaz az lnko előáll a két szám egész együtthatós lineáris kombinációjaként.
---

## Milyen rekurzióval számolja a bővített euklideszi algoritmus az $x, y$ együtthatókat?
?
Az euklideszi algoritmus $q_i$ hányadosaival ($r_{i-2} = r_{i-1}q_i + r_i$):
$$x_{-1} = 1,\ x_0 = 0,\qquad x_i = x_{i-2} - q_ix_{i-1},$$
$$y_{-1} = 0,\ y_0 = 1,\qquad y_i = y_{i-2} - q_iy_{i-1}.$$
Indukcióval $x_ia + y_ib = r_i$, így $x_na + y_nb = r_n = (a,b)$.
---

## Írd fel $(172, 62)$-t $172x + 62y$ alakban!
?
Az euklideszi algoritmus maradékai $48, 14, 6, 2, 0$, hányadosai $2, 1, 3, 2, 3$; az együtthatók $(x_i, y_i)$: $(1,-2), (-1,3), (4,-11), (-9,25)$. Tehát
$$(172,62) = 2 = 172\cdot(-9) + 62 \cdot 25.$$
---

## Mire használjuk a bővített euklideszi algoritmust a kurzusban?
?
- *felbonthatatlan $\Rightarrow$ prím* bizonyítása $\mathbb{Z}$-ben;
- lineáris kongruencia és lineáris diofantikus egyenlet megoldása;
- a kínai maradéktétel konstruktív bizonyítása;
- multiplikatív inverz keresése $\mathbb{Z}_m$-ben.
---

## Mit állít a számelmélet alaptétele?
?
Minden **nem nulla, nem egység** egész szám **sorrendtől és asszociáltaktól eltekintve** egyértelműen felírható prímszámok szorzataként.
---

## Hogyan bizonyítjuk a számelmélet alaptételében a felbontás létezését?
?
Indukcióval (elég nemnegatív számokra). $n = 2, 3$ prím. Ha $n$ prím, kész. Ha nem, akkor $n$ nemtriviálisan szorzatra bomlik, $n = ab$ kisebb tényezőkkel, amelyek az indukciós feltevés szerint már felírhatók prímek szorzataként.
---

## Hogyan bizonyítjuk a számelmélet alaptételében a felbontás egyértelműségét?
?
Indukcióval. Legyen $n = p_1\cdots p_k = q_1\cdots q_\ell$ (prímek). $p_1$ osztja a jobb oldalt, és a **prímtulajdonság** miatt osztja valamelyik $q_j$-t; mivel $q_j$ felbonthatatlan, $p_1$ és $q_j$ asszociáltak, átrendezéssel $p_1 = q_1$. Egyszerűsítve $p_2\cdots p_k = q_2 \cdots q_\ell$, ami az indukciós feltevés szerint egyértelmű.
---

## Miért múlik a számelmélet alaptételének egyértelműsége azon, hogy $\mathbb{Z}$-ben a felbonthatatlan elemek prímek?
?
Az egyértelműség bizonyítása a **prímtulajdonságot** használja ($p_1 \mid q_1\cdots q_\ell \Rightarrow p_1 \mid q_j$). A létezés csak felbonthatatlan tényezőket ad; hogy ezek prímek is, az a bővített euklideszi algoritmusból következik. Ahol a két fogalom elválik (pl. $\{a + bi\sqrt5\}$), ott az egyértelműség elbukhat.
---

## Mi egy nem nulla egész szám kanonikus alakja?
?
$$n = \pm p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_\ell^{\alpha_\ell} = \pm\prod_{i=1}^{\ell}p_i^{\alpha_i},$$
ahol $p_1, \dots, p_\ell$ különböző **pozitív** prímek és $\alpha_1, \dots, \alpha_\ell$ **pozitív** egészek.
---

## Hogyan számolható az osztók száma, $\tau(n)$, a kanonikus alakból?
?
Ha $n = p_1^{\alpha_1}\cdots p_\ell^{\alpha_\ell}$ ($n > 1$), akkor
$$\tau(n) = (\alpha_1 + 1)(\alpha_2 + 1)\cdots(\alpha_\ell + 1).$$
Például $\tau(96) = \tau(2^5 \cdot 3) = 6 \cdot 2 = 12$.
---

## Miért $(\alpha_1+1)\cdots(\alpha_\ell+1)$ az $n = p_1^{\alpha_1}\cdots p_\ell^{\alpha_\ell}$ pozitív osztóinak száma?
?
A pozitív osztók pontosan a $d = p_1^{\beta_1}\cdots p_\ell^{\beta_\ell}$ alakú számok, $\beta_i \in \{0, 1, \dots, \alpha_i\}$. A számelmélet alaptételének egyértelműsége miatt különböző kitevőrendszerek különböző osztókat adnak, és minden $\beta_i$ pontosan $\alpha_i + 1$ féleképpen választható.
---

## Hogyan bizonyította Euklidész, hogy végtelen sok prím van?
?
Indirekt: ha csak $p_1, \dots, p_k$ prímek léteznének, legyen
$$n = p_1 p_2 \cdots p_k + 1.$$
$n$ egyik $p_i$-vel sem osztható (mindegyikkel osztva $1$ a maradék), de a számelmélet alaptétele szerint van prímtényezője — ez egy újabb prím, ellentmondás.
---

## Mit mond Dirichlet tétele a prímekről?
?
Ha $a, d$ egészek, $d > 0$ és $(a,d) = 1$, akkor végtelen sok prím van az $a$ és $d$ által meghatározott (relatív prím kezdőtagú és differenciájú) számtani sorozatban. Azaz a prímek minden olyan számtani sorozatban végtelen sokan vannak, amelyben egyáltalán lehetnek.
---

## Mit mond a prímszámtétel?
?
Az $x$-ig lévő prímek száma aszimptotikusan
$$\frac{x}{\ln x},$$
azaz az $x$-ig lévő számoknak nagyjából $1/\ln x$ hányada prím. (Pl. $1000$-ig $168$ prím van, $1000/\ln 1000 \approx 145$.)
---

## Hogyan működik Eratoszthenész szitája $n$-ig?
?
1. Soroljuk fel az egészeket $2$-től $n$-ig.
2. A legkisebb ki nem húzott szám prím; húzzuk ki a valódi többszöröseit.
3. Ismételjük a következő ki nem húzott számmal, amíg az $\leq \sqrt{n}$.
<br>
A végén a ki nem húzott számok pontosan az $n$-ig terjedő prímek.
---

## Miért elég Eratoszthenész szitájában $\sqrt{n}$-ig szitálni?
?
Ha $m \leq n$ összetett, $m = ab$ nemtriviálisan, akkor $a$ és $b$ közül a kisebbik $\leq \sqrt{m} \leq \sqrt{n}$, így $m$-nek van $\sqrt{n}$-nél nem nagyobb prímosztója, és azzal már kihúztuk.
---
