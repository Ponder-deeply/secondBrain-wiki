`button-fc-review` | `button-fc-cram`

#flashcards/analiii/vizsgatetelek-bizonyitassal


## **1. tétel.** Vektorsorozatok és koordinátasorozataik konvergenciája közötti kapcsolat — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $p \in \mathbb{N}$, $\mathbf{a}_n = (a_{n,1},\dots,a_{n,p})^\top \in \mathbb{R}^p$ és $\mathbf{b} = (b_1,\dots,b_p)^\top \in \mathbb{R}^p$. Ekkor
$$\mathbf{a}_n \to \mathbf{b} \quad \Longleftrightarrow \quad a_{n,i} \to b_i \ \text{ minden } 1 \le i \le p \text{ esetén.}$$
**A bizonyítás szerkezete.** Két, egymással szemközti egyenlőtlenség. Lefelé: egy koordináta eltérése sosem nagyobb a vektor hosszánál — ez adja a ($\Rightarrow$) irányt rendőrelvvel. Felfelé: a vektor hossza a $p$ darab koordinátaeltérés maximumával becsülhető ($\sqrt p$ szorzóval) — ez adja a ($\Leftarrow$) irányt, ahol a **végességet** használjuk ki: $p$ darab küszöbindex maximuma még küszöbindex.
<br>
**Bizonyítás.** Minden $1 \le i \le p$ és minden $\mathbf{x} \in \mathbb{R}^p$ esetén
$$|x_i| \ \le\ \sqrt{x_1^2 + \dots + x_p^2} \ = \ |\mathbf{x}| \ $$$$ \le\ \sqrt{p}\cdot\max_{1\le j\le p}|x_j| . \tag{$\ast$}$$
Az első egyenlőtlenség azért áll, mert a gyök alatt csak nemnegatív tagokat hagyunk el; a második azért, mert minden tagot a maximumával becsülünk felülről. Alkalmazzuk $(\ast)$-ot az $\mathbf{x} := \mathbf{a}_n - \mathbf{b}$ vektorra.
<br>
($\Rightarrow$) Tegyük fel, hogy $\mathbf{a}_n \to \mathbf{b}$, azaz $|\mathbf{a}_n - \mathbf{b}| \to 0$. Rögzített $i$-re $(\ast)$ bal oldala szerint
$$0 \le |a_{n,i} - b_i| \le |\mathbf{a}_n - \mathbf{b}| \to 0,$$
tehát a rendőrelv szerint $|a_{n,i} - b_i| \to 0$, azaz $a_{n,i} \to b_i$.
<br>
($\Leftarrow$) Tegyük fel, hogy minden $i$-re $a_{n,i} \to b_i$, és legyen $\varepsilon > 0$. Ekkor minden $i$-hez van olyan $n_i$ küszöbindex, hogy $n > n_i$ esetén $|a_{n,i} - b_i| < \varepsilon/\sqrt p$. Mivel **véges** sok indexről van szó, az $n_0 := \max\{n_1,\dots,n_p\}$ szám létezik, és $n > n_0$ esetén $(\ast)$ jobb oldala szerint
$$|\mathbf{a}_n - \mathbf{b}| \le \sqrt p \cdot \max_i |a_{n,i} - b_i| < \sqrt p \cdot \frac{\varepsilon}{\sqrt p} = \varepsilon .$$
Tehát $\mathbf{a}_n \to \mathbf{b}$. $\blacksquare$
<br>
**Következmény.** A vektorsorozatok konvergenciája $p$ darab számsorozat konvergenciájára esik szét: innen öröklődik $\mathbb{R}^p$-be a Bolzano–Weierstrass-tétel, a Cauchy-kritérium (azaz $\mathbb{R}^p$ teljessége) és a koordinátánkénti folytonosság-jellemzés.
---

## **2. tétel.** A $\bigl(C[a,b], \|\cdot\|_\infty\bigr)$ tér teljes normált tér — mondd ki és bizonyítsd.
?
**Állítás.** Az $[a,b]$ ($a<b$) intervallumon folytonos valós függvények $C[a,b]$ vektortere a
$$\|f\|_\infty := \max_{x \in [a,b]} |f(x)|$$
maximumnormával **normált tér**, és ez a normált tér **teljes** (azaz Banach-tér).
<br>
**A bizonyítás szerkezete.** Három lépés. (i) A norma egyáltalán jóldefiniált: a maximum létezik, mert $|f|$ folytonos kompakt intervallumon (Weierstrass). (ii) A teljességhez egy Cauchy-sorozatból **először pontonként** gyártunk határfüggvényt — ezt $\mathbb{R}$ teljessége adja —, majd a Cauchy-feltételben $m \to \infty$ határátmenettel megmutatjuk, hogy a konvergencia **egyenletes**. (iii) Végül a határfüggvénynek benne kell lennie a térben: ez pontosan az „egyenletes limesz folytonos" tétel.
<br>
**Bizonyítás.**
<br>
*(i) Normált tér.* $f \in C[a,b]$ esetén $|f|$ folytonos a kompakt $[a,b]$-n, így Weierstrass tétele szerint felveszi a maximumát — a $\|f\|_\infty$ tehát létező, véges szám. A normaaxiómák: $\|f\|_\infty \ge 0$ nyilvánvaló, és $\|f\|_\infty = 0$ pontosan akkor, ha $|f(x)| = 0$ minden $x$-re, azaz $f \equiv 0$; $\|cf\|_\infty = \max |c||f| = |c|\,\|f\|_\infty$; végül minden $x$-re $|f(x)+g(x)| \le |f(x)|+|g(x)| \le \|f\|_\infty + \|g\|_\infty$, és a bal oldal maximumát véve $\|f+g\|_\infty \le \|f\|_\infty + \|g\|_\infty$.
<br>
*(ii) Pontonkénti limesz, majd egyenletes konvergencia.* Legyen $(f_n) \subset C[a,b]$ Cauchy-sorozat:
$$\forall \varepsilon > 0\ \ \exists n_0\ \ \forall n,m > n_0: \qquad \|f_n - f_m\|_\infty = \max_{x\in[a,b]} |f_n(x) - f_m(x)| < \varepsilon. \tag{1}$$
Rögzítsünk egy $x \in [a,b]$ pontot. Mivel $|f_n(x) - f_m(x)| \le \|f_n - f_m\|_\infty$, az $(f_n(x))$ **számsorozat** Cauchy-tulajdonságú, tehát $\mathbb{R}$ teljessége miatt konvergens. Legyen
$$g(x) := \lim_{n\to\infty} f_n(x) \qquad (x \in [a,b]),$$
azaz $f_n \to g$ pontonként. Most rögzítsünk egy $n > n_0$ indexet és egy $x \in [a,b]$ pontot. Az (1) szerint minden $m > n_0$-ra $|f_n(x) - f_m(x)| < \varepsilon$; itt $m \to \infty$ határátmenettel (a $\lim f_m(x) = g(x)$ miatt, és mert a gyenge egyenlőtlenség öröklődik a limeszre)
$$|f_n(x) - g(x)| \le \varepsilon .$$
Ez **minden** $x \in [a,b]$-re egyszerre igaz, ugyanazzal az $n_0$-lal, tehát $\sup_{x}|f_n(x)-g(x)| \le \varepsilon$ minden $n > n_0$ esetén. Vagyis $f_n \to g$ **egyenletesen**.
<br>
*(iii) A limesz a térben van.* Folytonos függvények egyenletes limesze folytonos, tehát $g \in C[a,b]$. Ekkor a $\|f_n - g\|_\infty$ maximum már létezik, és a fentiek szerint $\|f_n - g\|_\infty \le \varepsilon$ minden $n > n_0$-ra, azaz $f_n \to g$ a $\|\cdot\|_\infty$ normában. Minden Cauchy-sorozat konvergens, tehát a tér teljes. $\blacksquare$
<br>
**Következmény.** $\bigl(C[a,b],\|\cdot\|_\infty\bigr)$ Banach-tér, ezért érvényes benne a Banach-féle fixponttétel és a Baire-kategóriatétel. Ellentétben az $\|\cdot\|_1$ normával: $\bigl(C[-1,1],\|\cdot\|_1\bigr)$ **nem** teljes.
---

## **3. tétel.** $\mathbb{R}^n$-ben ($n \ge 1$) bármely két norma ekvivalens — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $n \ge 1$. Bármely $\|\cdot\|$ norma $\mathbb{R}^n$-en ekvivalens az $|\cdot|$ euklideszi normával, azaz léteznek olyan $c_1, c_2 > 0$ konstansok, hogy
$$c_1 |x| \le \|x\| \le c_2 |x| \qquad (x \in \mathbb{R}^n).$$
Mivel az ekvivalencia ekvivalenciareláció, ebből következik, hogy **bármely két** norma ekvivalens egymással.
<br>
**A bizonyítás szerkezete.** Elég az euklideszi normához képest becsülni, mert az ekvivalencia tranzitív. A **felső** becslés puszta számolás: a háromszög-egyenlőtlenség és a homogenitás a bázisra bontásból azonnal kiadja, konstansnak az $\|e_i\|$ értékek összegével. Az **alsó** becslés indirekt: ha nincs jó $c_1$, akkor az $\frac1n$ sorozat mentén gyártható egy euklideszi egységvektorokból álló sorozat, amelynek $\|\cdot\|$-normája nullához tart. Ezen a ponton lép be a **Bolzano–Weierstrass-tétel** (véges dimenzió!): kiválasztunk egy konvergens részsorozatot, a limesz euklideszi normája $1$, tehát nem nullvektor, így $\|y\| > 0$ — de a már bizonyított felső becslés miatt $\|y\|$ mégis nullához becsülhető. Ellentmondás.
<br>
**Bizonyítás.**
<br>
*Felső becslés.* Legyenek $e_1,\dots,e_n$ a koordináta-egységvektorok, és $x = \sum_{i=1}^n x_i e_i$. A háromszög-egyenlőtlenség és a homogenitás szerint
$$\|x\| \le \sum_{i=1}^n \|x_i e_i\| = \sum_{i=1}^n |x_i|\,\|e_i\| \le \Bigl(\max_i |x_i|\Bigr)\sum_{i=1}^n \|e_i\| \le \Bigl(\sum_{i=1}^n \|e_i\|\Bigr)\cdot |x| ,$$
hiszen $\max_i |x_i| \le |x|$. Tehát $c_2 := \sum_{i=1}^n \|e_i\| > 0$ megfelelő. (Ebből egyúttal az is kiolvasható, hogy $\|\cdot\|$ **folytonos** az euklideszi metrikában: $\bigl|\,\|u\|-\|v\|\,\bigr| \le \|u-v\| \le c_2|u-v|$.)
<br>
*Alsó becslés — indirekt.* Tegyük fel, hogy nincs megfelelő $c_1 > 0$. Akkor speciálisan egyik $c_1 = \frac1k$ ($k \in \mathbb{N}$) sem jó, azaz minden $k$-hoz van olyan $x_k \in \mathbb{R}^n$, amelyre
$$\|x_k\| < \tfrac1k\,|x_k| .$$
Ez az $x_k$ nem lehet a nullvektor (mert arra mindkét oldal $0$), így $|x_k| > 0$, és az $x_k / |x_k|$ helyettesítéssel — mindkét oldal pozitív homogén — feltehető, hogy $|x_k| = 1$, és ekkor
$$\|x_k\| < \tfrac1k . \tag{2}$$
Az $(x_k)$ sorozat az euklideszi normában korlátos, ezért a Bolzano–Weierstrass-tétel szerint van konvergens részsorozata: $x_{k_j} \to y$ euklideszi értelemben. Az euklideszi norma folytonossága miatt $|y| = \lim_j |x_{k_j}| = 1$, tehát $y \ne 0$, így a norma definíciója szerint $\|y\| > 0$.
<br>
Másfelől a felső becslés és a háromszög-egyenlőtlenség alapján, (2)-t is használva,
$$0 < \|y\| \le \|x_{k_j}\| + \|y - x_{k_j}\| < \frac{1}{k_j} + c_2\,|y - x_{k_j}| \xrightarrow[j\to\infty]{} 0 + 0 = 0 ,$$
ami ellentmondás. Tehát létezik jó $c_1 > 0$. $\blacksquare$
<br>
**Következmény.** Véges dimenzióban a konvergencia, a Cauchy-tulajdonság, a korlátosság és maga a topológia (nyílt, zárt, belső, határ) **normafüggetlen** — ezért nem kell soha megmondani, melyik normával dolgozunk $\mathbb{R}^n$-ben. Végtelen dimenzióban ez elromlik: $C[0,1]$-en $\|\cdot\|_1 \not\sim \|\cdot\|_\infty$.
---

## **4. tétel.** Zárt halmazok jellemzése a torlódási pontokkal — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $(M,d)$ metrikus tér és $H \subset M$. Jelölje $H'$ a $H$ torlódási pontjainak halmazát (a **derivált halmazt**). Ekkor
$$H \text{ zárt} \quad \Longleftrightarrow \quad H' \subset H,$$
azaz a $H$ pontosan akkor zárt, ha minden torlódási pontját tartalmazza.
<br>
*(Emlékeztető: $\alpha \in M$ torlódási pontja $H$-nak, ha minden $r>0$ esetén $\bigl|B(\alpha,r)\cap H\bigr| = \infty$; $H$ zárt, ha $M\setminus H$ nyílt.)*
<br>
**A bizonyítás szerkezete.** Mindkét irány a komplementer nyíltságán keresztül megy. ($\Rightarrow$) kontrapozícióval: ha egy torlódási pont kimaradna $H$-ból, akkor a nyílt komplementerben benne volna egy egész gömbjével együtt, az viszont üresen metszené $H$-t — ellentmondás a „végtelen sok pont" feltétellel. ($\Leftarrow$) a komplementer minden pontjáról megmutatja, hogy belső pont; itt az egyetlen technikai lépés, hogy a „nem torlódási pont" csak **véges** metszetet ad, és egy $H$-n kívüli pont körül ez a véges ponthalmaz egy kisebb sugárral kiküszöbölhető.
<br>
**Bizonyítás.**
<br>
($\Rightarrow$) Legyen $H$ zárt, és legyen $\alpha \in H'$. Indirekt tegyük fel, hogy $\alpha \notin H$. Ekkor $\alpha \in M \setminus H$, ami a zártság miatt nyílt, tehát $\alpha$ belső pontja: van olyan $r > 0$, hogy
$$B(\alpha, r) \subset M \setminus H, \qquad \text{azaz} \qquad B(\alpha,r) \cap H = \emptyset .$$
Ez viszont ellentmond annak, hogy $\alpha$ torlódási pont, hiszen akkor $\bigl|B(\alpha,r)\cap H\bigr| = \infty$ volna. Tehát $\alpha \in H$, azaz $H' \subset H$.
<br>
($\Leftarrow$) Tegyük fel, hogy $H' \subset H$, és mutassuk meg, hogy $M \setminus H$ nyílt. Legyen $\alpha \in M \setminus H$ tetszőleges. Mivel $\alpha \notin H$ és $H' \subset H$, ezért $\alpha \notin H'$, azaz $\alpha$ **nem** torlódási pontja $H$-nak: van olyan $r > 0$, hogy az
$$F := B(\alpha, r) \cap H$$
halmaz **véges**. Két eset:
<br>
- Ha $F = \emptyset$, akkor $B(\alpha,r) \subset M\setminus H$, kész.
- Ha $F \ne \emptyset$, akkor $\alpha \notin F$ (hiszen $\alpha \notin H$), tehát $d(\alpha, x) > 0$ minden $x \in F$-re. Mivel $F$ véges, a
$$\rho := \min\Bigl\{ r,\ \min_{x \in F} d(\alpha, x)\Bigr\}$$
szám létezik és **pozitív** (véges sok pozitív szám minimuma pozitív — itt használjuk ki a végességet). Erre a $\rho$-ra $B(\alpha,\rho) \subset B(\alpha,r)$, és $B(\alpha,\rho)$ egyetlen $F$-beli pontot sem tartalmaz, tehát
$$B(\alpha,\rho) \cap H = B(\alpha,\rho) \cap F = \emptyset, \qquad \text{azaz} \qquad B(\alpha,\rho) \subset M \setminus H .$$
Mindkét esetben $\alpha$ belső pontja $M\setminus H$-nak. Mivel $\alpha$ tetszőleges volt, $M\setminus H$ nyílt, tehát $H$ zárt. $\blacksquare$
<br>
**Következmény.** $\operatorname{cl} H = H \cup H'$ a legszűkebb $H$-t tartalmazó zárt halmaz, és $H$ pontosan akkor zárt, ha $H = \operatorname{cl}H$. Speciálisan minden véges halmaz zárt, hiszen nincs torlódási pontja.
---

## **5. tétel.** Zárt halmazok jellemzése sorozatokkal — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $(M,d)$ metrikus tér és $H \subset M$. Ekkor
$$H \text{ zárt} \quad \Longleftrightarrow \quad \text{minden } (x_n) \subset H \text{ konvergens sorozatra } \lim x_n \in H,$$
azaz a $H$ pontosan akkor zárt, ha a benne haladó konvergens sorozatok limesze is $H$-beli.
<br>
**A bizonyítás szerkezete.** ($\Rightarrow$) indirekt: ha a limesz kimaradna, egy körülötte fekvő, $H$-t üresen metsző gömböt kapnánk a nyílt komplementerből, ebbe viszont a konvergencia miatt a sorozat majdnem minden tagja beleesne — de azok $H$-ban vannak. ($\Leftarrow$) szintén indirekt, és ez a lényegi irány: ha $M\setminus H$ nem volna nyílt, akkor volna olyan $\alpha \notin H$ pont, amely körül **minden** gömb belemetsz $H$-ba; az $r = \frac1n$ sugarakkal ebből **sorozatot építünk**, amely $H$-ban halad és $\alpha$-hoz tart, tehát a feltevés szerint $\alpha \in H$ — ellentmondás.
<br>
**Bizonyítás.**
<br>
($\Rightarrow$) Legyen $H$ zárt, $(x_n) \subset H$, és $x_n \to b$. Indirekt tegyük fel, hogy $b \notin H$. Ekkor $b \in M \setminus H$, ami nyílt, tehát van olyan $r > 0$, hogy $B(b,r) \subset M \setminus H$. Másfelől a konvergencia definíciója szerint ehhez az $r$-hez van olyan $n_0$, hogy $n > n_0$ esetén $d(x_n, b) < r$, azaz $x_n \in B(b,r) \subset M\setminus H$. Ez ellentmond annak, hogy $x_n \in H$. Tehát $b \in H$.
<br>
($\Leftarrow$) Tegyük fel, hogy minden $H$-beli konvergens sorozat limesze $H$-ban van. Indirekt tegyük fel, hogy $H$ nem zárt, azaz $M \setminus H$ **nem** nyílt: van olyan $\alpha \in M\setminus H$, amely nem belső pontja $M\setminus H$-nak. Ez azt jelenti, hogy **semelyik** $r>0$ sugárra sem áll fenn $B(\alpha,r)\subset M\setminus H$, vagyis
$$\forall r > 0: \qquad B(\alpha, r) \cap H \ne \emptyset .$$
Alkalmazzuk ezt az $r := \frac1n$ ($n \in \mathbb{N}$) sugarakra, és válasszunk minden $n$-re egy
$$x_n \in B\bigl(\alpha, \tfrac1n\bigr) \cap H$$
pontot. Az így kapott $(x_n)$ sorozat $H$-ban halad, és
$$0 \le d(x_n, \alpha) < \tfrac1n \longrightarrow 0,$$
tehát a rendőrelv szerint $x_n \to \alpha$. A feltevés szerint ekkor $\alpha \in H$ — ez viszont ellentmond az $\alpha \in M\setminus H$ választásnak. Tehát $M\setminus H$ mégis nyílt, azaz $H$ zárt. $\blacksquare$
<br>
**Következmény.** Ez az a jellemzés, amellyel a zártság a gyakorlatban ellenőrizhető: elég sorozatokkal számolni, gömbökkel nem kell. Innen adódik például, hogy $\mathbb{R}^p$-ben minden kompakt halmaz zárt, és hogy folytonos függvény esetén a zárt halmaz ősképe zárt.
---

## **6. tétel.** A derivált mátrix egyértelmű — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $f \in \mathbb{R}^n \to \mathbb{R}^m$ és $a \in \operatorname{int} D_f$. Ha $f$ differenciálható $a$-ban, akkor a definícióban szereplő $L \in \mathcal{L}(\mathbb{R}^n,\mathbb{R}^m)$ korlátos lineáris leképezés **egyértelmű**. (Emlékeztető: $f \in D\{a\}$, ha van olyan $L$ és olyan $\eta$, hogy $f(a+h)-f(a) = L(h) + \eta(h)\|h\|$, ahol $\eta(h)\to 0$, ha $\|h\|\to 0$.) Ezt az egyetlen $L$-t nevezzük $f'(a)$-nak.
<br>
**A bizonyítás szerkezete.** Tegyük fel, hogy két jelölt van, és vonjuk ki egymásból a két előállítást: a különbségük, $L^\ast := L - \tilde L$ lineáris leképezésre azt kapjuk, hogy $\|L^\ast(h)\| / \|h\| \to 0$. A trükk ezután: $h$-t **nem** tetszőleges irányból közelítjük nullához, hanem az $h := t e_i$ sugár mentén. A linearitás és a homogenitás miatt ez a hányados ilyenkor a **$t$-től független** $\|L^\ast(e_i)\|$ számmá egyszerűsödik — egy konstans pedig csak úgy tarthat nullához, ha maga nulla. Tehát $L^\ast$ minden bázisvektort nullába visz, így linearitás miatt azonosan nulla.
<br>
**Bizonyítás.** Tegyük fel, hogy $L$ és $\tilde L$ is megfelel a definíciónak, $\eta$, illetve $\tilde\eta$ hibafüggvénnyel. Dolgozzunk a $\|\cdot\|_\infty$ normával (ez nem megszorítás: $\mathbb{R}^n$-ben és $\mathbb{R}^m$-ben minden norma ekvivalens). Elég kis $\|h\|_\infty$ mellett
$$f(a+h)-f(a) = L(h) + \eta(h)\|h\|_\infty = \tilde L(h) + \tilde\eta(h)\|h\|_\infty .$$
Legyen $L^\ast := L - \tilde L$; ez lineáris. A két előállítás különbségéből
$$L^\ast(h) = \bigl(\tilde\eta(h) - \eta(h)\bigr)\cdot \|h\|_\infty ,$$
azaz minden $h \ne 0$-ra
$$\frac{\|L^\ast(h)\|_\infty}{\|h\|_\infty} = \|\tilde\eta(h)-\eta(h)\|_\infty \le \|\tilde\eta(h)\|_\infty + \|\eta(h)\|_\infty \xrightarrow[\|h\|_\infty \to 0]{} 0 . \tag{3}$$
Rögzítsünk egy $i \in \{1,\dots,n\}$ indexet, és válasszuk speciálisan $h := t e_i$-t, ahol $e_i$ az $i$-edik egységvektor és $t \ne 0$ valós. Ekkor $\|t e_i\|_\infty = |t|$, és $L^\ast$ linearitása (homogenitása) miatt $L^\ast(te_i) = t\,L^\ast(e_i)$, tehát
$$\frac{\|L^\ast(te_i)\|_\infty}{\|te_i\|_\infty} = \frac{|t|\cdot\|L^\ast(e_i)\|_\infty}{|t|} = \|L^\ast(e_i)\|_\infty .$$
Ez a mennyiség **nem függ $t$-től**, a (3) szerint viszont nullához tart, amikor $t \to 0$. Egy konstans sorozat határértéke önmaga, tehát
$$\|L^\ast(e_i)\|_\infty = 0, \qquad \text{azaz} \qquad L^\ast(e_i) = 0 \qquad (i = 1,\dots,n).$$
Végül tetszőleges $x = \sum_{i=1}^n x_i e_i \in \mathbb{R}^n$ esetén a linearitás miatt
$$L^\ast(x) = \sum_{i=1}^n x_i L^\ast(e_i) = 0,$$
tehát $L^\ast \equiv 0$, azaz $L = \tilde L$. $\blacksquare$
<br>
**Következmény.** Az $f'(a)$ jelölés jogos: a derivált **objektum**, nem választás kérdése. Ezért beszélhetünk a Jacobi-mátrixról mint $f'(a)$ egyetlen mátrixáról, és ezért lehet a deriváltat bármilyen kényelmes úton (parciális deriváltakkal, láncszabállyal) kiszámolni — bárhogy kapjuk meg, ugyanazt kapjuk.
---

## **7. tétel.** Vektorértékű függvények és koordinátafüggvényeik differenciálhatósága közötti kapcsolat — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $n, m \ge 1$, $f = (f_1,\dots,f_m) \in \mathbb{R}^n \to \mathbb{R}^m$ és $a \in \operatorname{int}D_f$. Ekkor
$$f \in D\{a\} \quad \Longleftrightarrow \quad f_i \in D\{a\} \ \text{ minden } i = 1,\dots,m \text{ esetén},$$
és ilyenkor a Jacobi-mátrix sorai a koordinátafüggvények gradiensei:
$$f'(a) = \begin{pmatrix} \operatorname{grad}f_1(a) \\ \vdots \\ \operatorname{grad}f_m(a)\end{pmatrix} \in \mathbb{R}^{m\times n}.$$
**A bizonyítás szerkezete.** Az egész tétel egyetlen észrevételen múlik: a differenciálhatóság definíciójában szereplő **vektoregyenlőség koordinátánként kiolvasható**, és a hibatag $\eta(h) \to 0$ feltétele éppen az $m$ darab $\eta_i(h)\to 0$ feltétellel ekvivalens (ez a konvergencia koordinátánkénti jellemzése $\mathbb{R}^m$-ben). Oda-vissza ugyanaz az egy sor; a különbség csak az, hogy melyik irányban olvassuk. Az egyértelműség a végén azért kell, hogy az összerakott $A$ mátrixot valóban $f'(a)$-nak nevezhessük.
<br>
**Bizonyítás.** Használjuk $\mathbb{R}^n$-ben a $\|\cdot\|_2$ normát.
<br>
($\Rightarrow$) Legyen $f \in D\{a\}$, és jelölje $A_1,\dots,A_m \in \mathbb{R}^n$ az $f'(a)$ mátrix sorvektorait. Ekkor alkalmas $\eta = (\eta_1,\dots,\eta_m)$ függvénnyel, amelyre $\eta(h)\to 0$ ($\|h\|_2\to 0$),
$$f(a+h)-f(a) = f'(a)h + \eta(h)\|h\|_2 = \bigl(\langle A_1,h\rangle,\dots,\langle A_m,h\rangle\bigr) + \bigl(\eta_1(h)\|h\|_2,\dots,\eta_m(h)\|h\|_2\bigr),$$
hiszen a mátrix-vektor szorzat $i$-edik koordinátája éppen az $i$-edik sor és $h$ skalárszorzata. Két vektor akkor és csak akkor egyenlő, ha minden koordinátájuk egyenlő, tehát minden $i$-re
$$f_i(a+h) - f_i(a) = \langle A_i, h\rangle + \eta_i(h)\cdot\|h\|_2 .$$
Mivel $\eta(h)\to 0$ $\mathbb{R}^m$-ben ekvivalens azzal, hogy $\eta_i(h)\to 0$ minden $i$-re, ez pontosan az $f_i$ differenciálhatóságának definíciója az $\langle A_i,\cdot\rangle$ lineáris funkcionállal. Tehát $f_i \in D\{a\}$ és $\operatorname{grad}f_i(a) = A_i$.
<br>
($\Leftarrow$) Tegyük fel, hogy minden $i$-re $f_i \in D\{a\}$, azaz alkalmas $\eta_i(h)\to 0$ függvényekkel
$$f_i(a+h)-f_i(a) = \langle \operatorname{grad}f_i(a), h\rangle + \eta_i(h)\|h\|_2 \qquad (i=1,\dots,m).$$
Legyen
$$A := \begin{pmatrix}\operatorname{grad}f_1(a)\\ \vdots \\ \operatorname{grad}f_m(a)\end{pmatrix} \in \mathbb{R}^{m\times n}, \qquad \eta := (\eta_1,\dots,\eta_m).$$
Az $m$ darab skaláregyenlőség egyetlen vektoregyenlőséggé áll össze:
$$f(a+h)-f(a) = Ah + \eta(h)\cdot\|h\|_2 ,$$
ahol $\eta(h)\to 0$, mert minden koordinátája nullához tart. $A$ lineáris (és véges dimenzióban automatikusan korlátos) leképezés, tehát $f \in D\{a\}$; a **derivált egyértelműsége** miatt pedig $f'(a) = A$. $\blacksquare$
<br>
**Következmény.** A vektorértékű eset maradéktalanul visszavezethető $m$ darab skalárértékű függvényre — elég tehát a $\operatorname{grad}$ szerkezetét ismerni a Jacobi-mátrix felírásához. Figyelem: ez a koordinátánkénti visszavezetés a **differenciálhatóságra** (és a folytonosságra) működik; a parciális deriválhatóság önmagában semelyik esetben nem elég.
---

## **8. tétel.** Parciális deriváltakkal kifejezett elégséges feltétel a totális deriválhatóságra — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $n \ge 1$, $h \in \mathbb{R}^n \to \mathbb{R}$ és $a \in \operatorname{int}D_h$. Tegyük fel, hogy valamely rögzített $i \in \{1,\dots,n\}$ indexre:
<br>
1. alkalmas $r>0$ mellett $K_r(a) \subset D_h$, és minden $x \in K_r(a)$-ban léteznek a $\partial_j h(x)$ parciális deriváltak ($j \ne i$);
2. mindegyik $\partial_j h$ ($j\ne i$) parciális deriváltfüggvény **folytonos** $a$-ban;
3. létezik a $\partial_i h(a)$ parciális derivált.
<br>
Ekkor $h \in D\{a\}$, és $h'(a) = \operatorname{grad}h(a) = \bigl(\partial_1h(a),\dots,\partial_nh(a)\bigr)$.
<br>
A feltétel aszimmetriája lényeges: **egyetlen** kitüntetett változónál elég a puszta pontbeli parciális deriválhatóság, a többinél kell a környezetbeli létezés és a pontbeli folytonosság.
<br>
**A bizonyítás szerkezete.** Három gondolat. (i) A $h(a+x)-h(a)$ megváltozást **teleszkópikus összegre** bontjuk: olyan lépések sorozatára, amelyek mindegyikében csak **egy** koordináta változik. (ii) A kitüntetett $i$-edik lépést a $\partial_ih(a)$ **definíciója** kezeli; az összes többi lépésre az egyváltozós **Lagrange-középértéktétel** alkalmazható — ehhez kell a parciális deriváltak létezése az egész $K_r(a)$-n, nem csak $a$-ban. (iii) A Lagrange-tétel közbülső helyeken vett parciális deriváltakat ad; ezeket a **folytonosság** cseréli ki az $a$-beli értékekre, kis hibával. A hiba pont az, ami a differenciálhatóság definíciójának $\eta(x)$-e.
<br>
**Bizonyítás.** Feltehető $n \ge 2$ (az $n=1$ eset triviális) és — a koordináták átszámozásával — $i = 1$. $\mathbb{R}^n$-ben a $\|\cdot\|_\infty$ normát használjuk. Legyen $x \in \mathbb{R}^n$, $\|x\|_\infty < r$, és bontsuk fel a megváltozást úgy, hogy egyszerre egy koordinátát kapcsolunk be:
$$h(a+x)-h(a) = \underbrace{\bigl[h(a_1+x_1,a_2,\dots,a_n) - h(a)\bigr]}_{\text{csak az 1. koordináta változik}} + \sum_{i=2}^{n}\bigl[h(P_i) - h(P_{i-1})\bigr],$$
ahol $P_i := (a_1+x_1,\dots,a_i+x_i,a_{i+1},\dots,a_n)$, azaz a $P_{i-1} \to P_i$ lépésben csak az $i$-edik koordináta változik, $a_i$-ről $a_i+x_i$-re.
<br>
*Az első tag.* A $\partial_1h(a)$ parciális derivált létezik, ami definíció szerint azt jelenti, hogy alkalmas $\omega(t)\to 0$ ($t\to0$), $\omega(0)=0$ függvénnyel
$$h(a_1+x_1,a_2,\dots,a_n) - h(a) = \partial_1h(a)\cdot x_1 + \omega(x_1)\cdot x_1 .$$
*A többi tag.* Rögzített $i \ge 2$ mellett a
$$t \ \longmapsto\ h(a_1+x_1,\dots,a_{i-1}+x_{i-1},\, t,\, a_{i+1},\dots,a_n)$$
egyváltozós függvény az $a_i$ és $a_i+x_i$ közötti zárt szakaszon differenciálható (ez éppen az 1. feltétel: a szakasz $K_r(a)$-ban fekszik, hiszen $\|\cdot\|_\infty$ mellett minden $P$ közbülső pont $\|P-a\|_\infty \le \|x\|_\infty < r$), deriváltja pedig $\partial_ih$ az adott helyen. A Lagrange-középértéktétel szerint van olyan $\xi_i$ az $a_i$ és $a_i+x_i$ között, hogy
$$h(P_i)-h(P_{i-1}) = \partial_ih(a_{x,i})\cdot x_i, \qquad a_{x,i} := (a_1+x_1,\dots,a_{i-1}+x_{i-1},\,\xi_i,\,a_{i+1},\dots,a_n).$$
*Összerakás.* A két rész összege, az $A := \operatorname{grad}h(a)$ jelöléssel:
$$h(a+x)-h(a) = \sum_{i=1}^n \partial_ih(a)x_i \ +\ \omega(x_1)x_1 \ +\ \sum_{i=2}^n\bigl(\partial_ih(a_{x,i}) - \partial_ih(a)\bigr)x_i = \langle A,x\rangle + \langle \varphi(x),x\rangle,$$
ahol
$$\varphi(x) := \Bigl(\omega(x_1),\ \partial_2h(a_{x,2})-\partial_2h(a),\ \dots,\ \partial_nh(a_{x,n})-\partial_nh(a)\Bigr).$$
*A hibatag nullához tart.* Legyen $\varepsilon>0$. A $\partial_ih \in C\{a\}$ feltétel ($i\ge2$) szerint van olyan $0<\delta<r$, hogy $\|z-a\|_\infty<\delta$ esetén $|\partial_ih(z)-\partial_ih(a)|<\varepsilon$ minden $i \ge 2$-re; $\omega(t)\to 0$ miatt $\delta$ úgy is választható, hogy $|t|<\delta$ esetén $|\omega(t)|<\varepsilon$. A közbülső pontokra $\|a_{x,i}-a\|_\infty \le \|x\|_\infty$, tehát $\|x\|_\infty<\delta$ már elég ahhoz, hogy **minden** koordinátában teljesüljön a becslés, azaz $\|\varphi(x)\|_\infty < \varepsilon$. Tehát $\varphi(x)\to 0$, ha $\|x\|_\infty \to 0$.
<br>
*A definíció alakjára hozás.* Legyen
$$\eta(x) := \Bigl\langle \varphi(x),\ \frac{x}{\|x\|_\infty}\Bigr\rangle \quad (x \ne 0), \qquad \eta(0):=0 .$$
Ezzel $\langle\varphi(x),x\rangle = \eta(x)\cdot\|x\|_\infty$, azaz
$$h(a+x)-h(a) = \langle A,x\rangle + \eta(x)\cdot\|x\|_\infty,$$
és a Cauchy–Bunyakovszkij-egyenlőtlenség szerint
$$|\eta(x)| \le \|\varphi(x)\|_2\cdot\Bigl\|\frac{x}{\|x\|_\infty}\Bigr\|_2 \le \bigl(\sqrt n\,\|\varphi(x)\|_\infty\bigr)\cdot\sqrt n = n\,\|\varphi(x)\|_\infty \longrightarrow 0 .$$
Tehát $h \in D\{a\}$ és $h'(a) = A = \operatorname{grad}h(a)$. $\blacksquare$
<br>
**Következmény.** Ha $h$ minden parciális deriváltja létezik egy környezetben és folytonos $a$-ban (azaz $h \in C^1\{a\}$), akkor $h \in D\{a\}$ — ez a gyakorlatban használt kritérium, hiszen a parciális deriváltak kiszámolhatók. A megfordítás **nem** igaz: a differenciálhatóságból nem következik a parciális deriváltak folytonossága.
---

## **9. tétel.** Az összetett függvény deriválási szabálya (láncszabály) — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $g \in \mathbb{R}^n\to\mathbb{R}^m$, $f \in \mathbb{R}^m\to\mathbb{R}^s$, továbbá $a \in \operatorname{int}D_g$ olyan, hogy $b := g(a) \in \operatorname{int}D_f$, valamint $g \in D\{a\}$ és $f \in D\{b\}$. Ekkor $f\circ g \in D\{a\}$, és
$$(f\circ g)'(a) = f'(g(a))\cdot g'(a) .$$
A jobb oldal $\mathbb{R}^{s\times m}$ és $\mathbb{R}^{m\times n}$ mátrixok szorzata, azaz $\mathbb{R}^{s\times n}$-beli — pontosan az a típus, amit egy $\mathbb{R}^n\to\mathbb{R}^s$ függvény deriváltjától várunk. A mátrixszorzás nem kommutatív: **a sorrend kötött.**
<br>
**A bizonyítás szerkezete.** Egyetlen behelyettesítés, majd három becslés. A $g$ megváltozását, $y(x) := g(a+x)-g(a)$-t, beírjuk az $f$ differenciálhatóságának definíciójába. A kapott kifejezésben a fő tag azonnal $f'(b)g'(a)x$; a maradékot három darabra bontjuk: (i) $f'(b)\eta(x)$ — a mátrix operátornormájával becsülhető, ezért nullához tart; (ii) $y(x)\to 0$ (hiszen $g$ differenciálható, tehát folytonos $a$-ban), így $\tilde\eta(y(x))\to 0$ — **ehhez kell**, hogy $\tilde\eta$-t folytonossá tegyük $0$-ban az $\tilde\eta(0):=0$ megállapodással; (iii) az $\|y(x)\|/\|x\|$ hányados **korlátos**. Egy nullsorozat és egy korlátos sorozat szorzata nullsorozat — kész.
<br>
**Bizonyítás.** A differenciálhatóság definíciója szerint alkalmas $\eta$, $\tilde\eta$ függvényekkel (és az $\eta(0) := 0$, $\tilde\eta(0):=0$ megállapodással, ami megengedett)
$$g(a+x)-g(a) = g'(a)x + \eta(x)\|x\|, \qquad \eta(x)\to 0 \ (\|x\|\to0), \tag{4}$$
$$f(b+y)-f(b) = f'(b)y + \tilde\eta(y)\|y\|, \qquad \tilde\eta(y)\to 0 \ (\|y\|\to0). \tag{5}$$
*Értelmezési tartomány.* Mivel $g \in D\{a\}$, $g$ folytonos $a$-ban, és $b \in \operatorname{int}D_f$, ezért van olyan $\delta>0$, hogy $K_\delta(b)\subset D_f$, és van olyan $r>0$, hogy $K_r(a)\subset D_g$ és $g[K_r(a)] \subset K_\delta(b)$. Tehát $K_r(a) \subset D_{f\circ g}$, azaz $a \in \operatorname{int}D_{f\circ g}$ — a tétel állítása értelmes.
<br>
*A behelyettesítés.* Legyen $\|x\| < r$ és
$$y(x) := g(a+x) - g(a) \overset{(4)}{=} g'(a)x + \eta(x)\|x\| .$$
Ekkor $g(a+x) = b + y(x)$, így (5)-öt $y := y(x)$-szel alkalmazva
$$(f\circ g)(a+x) - (f\circ g)(a) = f\bigl(b+y(x)\bigr)-f(b) = f'(b)\,y(x) + \tilde\eta\bigl(y(x)\bigr)\cdot\|y(x)\| .$$
Az $y(x)$ helyére (4)-et beírva, és $f'(b)$ linearitását használva:
$$(f\circ g)(a+x)-(f\circ g)(a) = \underbrace{f'(b)g'(a)\,x}_{\text{fő tag}} \ +\ \underbrace{f'(b)\eta(x)\|x\| + \tilde\eta(y(x))\|y(x)\|}_{=:\ R(x)} .$$
Azt kell belátni, hogy $\|R(x)\|/\|x\| \to 0$, ha $\|x\|\to 0$ — akkor ugyanis az $\eta^\ast(x) := R(x)/\|x\|$ ($x\ne0$), $\eta^\ast(0):=0$ választással a definíció teljesül az $A := f'(b)g'(a)$ leképezéssel, és a derivált egyértelműsége miatt $(f\circ g)'(a) = A$.
<br>
*(i)* Az $f'(b)$ mátrix operátornormáját $q := \|f'(b)\|$-val jelölve
$$\frac{\|f'(b)\eta(x)\|x\|\,\|}{\|x\|} = \|f'(b)\eta(x)\| \le q\,\|\eta(x)\| \longrightarrow 0 .$$
*(iii)* Legyen $Q := \|g'(a)\|$ az operátornorma. A (4) szerint $x \ne 0$ esetén
$$\frac{\|y(x)\|}{\|x\|} \le \frac{\|g'(a)x\|}{\|x\|} + \|\eta(x)\| \le Q + \|\eta(x)\| \le Q+1 \tag{6}$$
elég kis $\|x\|$-re (hiszen $\|\eta(x)\|\to0$). A hányados tehát **korlátos**; egyúttal $\|y(x)\| \le (Q+1)\|x\| \to 0$, azaz $y(x)\to 0$.
<br>
*(ii)* Mivel $y(x)\to 0$ és $\tilde\eta(y)\to 0$ ($\|y\|\to0$), $\tilde\eta(0)=0$, ezért $\tilde\eta(y(x)) \to 0$. Így (6)-ot is használva
$$\frac{\|\tilde\eta(y(x))\|y(x)\|\,\|}{\|x\|} = \|\tilde\eta(y(x))\|\cdot\frac{\|y(x)\|}{\|x\|} \le (Q+1)\cdot\|\tilde\eta(y(x))\| \longrightarrow 0 .$$
A két becslést összeadva $\|R(x)\|/\|x\| \to 0$, tehát $f\circ g \in D\{a\}$ és $(f\circ g)'(a) = f'(g(a))g'(a)$. $\blacksquare$
<br>
**Következmény.** Parciális deriváltakkal kiírva $\partial_k(f\circ g)(a) = \sum_{j} \partial_jf(g(a))\cdot\partial_kg_j(a)$ — a szokásos $\frac{\partial f}{\partial x_k} = \sum_j \frac{\partial f}{\partial y_j}\frac{\partial y_j}{\partial x_k}$ formula. Egysoros folyománya az iránymenti derivált képlete, $\partial_ef(a) = f'(a)e$, valamint a szorzat- és hányadosszabály.
---

## **10. tétel.** Young tétele — mondd ki és bizonyítsd.
?
**Állítás.** Legyen $n \ge 2$, $f \in \mathbb{R}^n\to\mathbb{R}$, $a \in \operatorname{int}D_f$, $s \ge 2$ és $f \in C^s\{a\}$. Ekkor tetszőleges $k_1,\dots,k_s \in \{1,\dots,n\}$ indexekre és azok bármely $j_1,\dots,j_s$ permutációjára
$$\partial_{k_1\dots k_s}f(a) = \partial_{j_1\dots j_s}f(a),$$
azaz a magasabbrendű parciális deriváltak értéke **nem függ a deriválás sorrendjétől**.
<br>
**A bizonyítás szerkezete.** Minden permutáció előáll szomszédos cserék szorzataként, és minden szomszédos csere csak két egymást követő deriválást érint — ezért teljes indukcióval elég az $s=2$, $n=2$ eset, azaz $\partial_{12}f(a)=\partial_{21}f(a)$. Ehhez bevezetjük a **szimmetrikus másodrendű differenciát**, $\Delta(u,v)$-t: ez a négy sarokpontos kifejezés úgy is felbontható, hogy előbb $u$, utóbb $v$ szerint olvassuk, és fordítva is. Mindkét olvasatban Lagrange-középértéktétel + a $\partial_if$ függvény $a$-beli differenciálhatósága adja, hogy $\Delta(t,t)/t^2$ az egyik, illetve a másik vegyes deriválthoz tart. Egy határérték egyértelmű, tehát a kettő egyenlő.
<br>
**Bizonyítás.** Elég az $n=2$, $s=2$ eset (jelölés: $a = (a_1,a_2)$, $\partial_{12} := \partial_2\partial_1$). Legyen $r>0$ olyan, hogy $K_r(a)\subset D_f$, és $\partial_1f$, $\partial_2f$ létezzen $K_r(a)$-n, továbbá legyen mindkettő differenciálható $a$-ban (ezt jelenti $f \in D^2\{a\}$). Vezessük be $|u|,|v|<r/2$ mellett a **szimmetrikus differenciát**:
$$\Delta(u,v) := f(a_1+u,\,a_2+v) - f(a_1+u,\,a_2) - f(a_1,\,a_2+v) + f(a_1,a_2).$$
*Első olvasat — $u$ szerint.* Rögzített $v$ mellett legyen $\varphi(t) := f(a_1+t,a_2+v)-f(a_1+t,a_2)$. Ekkor $\Delta(u,v)=\varphi(u)-\varphi(0)$, és $\varphi$ differenciálható a $0$ és $u$ közötti szakaszon, $\varphi'(t)=\partial_1f(a_1+t,a_2+v)-\partial_1f(a_1+t,a_2)$. A Lagrange-középértéktétel szerint van olyan $\xi$ a $0$ és $u$ között, hogy
$$\Delta(u,v) = u\cdot\bigl[\partial_1f(a_1+\xi,\,a_2+v)-\partial_1f(a_1+\xi,\,a_2)\bigr].$$
Mivel $\partial_1f$ differenciálható $a$-ban, a $G := \operatorname{grad}(\partial_1f)(a) = \bigl(\partial_{11}f(a),\ \partial_{12}f(a)\bigr)$ jelöléssel alkalmas $\varepsilon(\cdot)\to0$, $\varepsilon(0)=0$ függvénnyel
$$\partial_1f(a+w) = \partial_1f(a) + \langle G,w\rangle + \varepsilon(w)\|w\|_\infty .$$
Ezt a $w_1 := (\xi,v)$ és $w_2 := (\xi,0)$ vektorokra alkalmazva, a $\partial_1 f(a)$ és a $\langle G, \cdot\rangle$ első komponense kiesik:
$$\partial_1f(a_1+\xi,a_2+v)-\partial_1f(a_1+\xi,a_2) = \partial_{12}f(a)\cdot v + \varepsilon(w_1)\|w_1\|_\infty - \varepsilon(w_2)\|w_2\|_\infty .$$
Válasszuk most $u = v = t \ne 0$-t. Ekkor $|\xi|\le|t|$, tehát $\|w_1\|_\infty \le |t|$ és $\|w_2\|_\infty\le|t|$, és
$$\frac{\Delta(t,t)}{t^2} = \partial_{12}f(a) + \frac{\varepsilon(w_1)\|w_1\|_\infty - \varepsilon(w_2)\|w_2\|_\infty}{t},$$
ahol a hibatag abszolút értéke $\le |\varepsilon(w_1)|+|\varepsilon(w_2)| \to 0$, ha $t\to0$ (hiszen $\|w_1\|_\infty,\|w_2\|_\infty \le |t| \to 0$). Tehát
$$\lim_{t\to0}\frac{\Delta(t,t)}{t^2} = \partial_{12}f(a).$$
*Második olvasat — $v$ szerint.* A $\Delta(u,v)$ kifejezés **szimmetrikus** a két változó szerepében: átcsoportosítva
$$\Delta(u,v) = \bigl[f(a_1+u,a_2+v)-f(a_1,a_2+v)\bigr] - \bigl[f(a_1+u,a_2)-f(a_1,a_2)\bigr] = \psi(v)-\psi(0),$$
ahol $\psi(t) := f(a_1+u,a_2+t)-f(a_1,a_2+t)$. Ugyanaz a gondolatmenet — Lagrange-középértéktétel $\psi$-re, majd a $\partial_2f$ $a$-beli differenciálhatósága — $u=v=t$ mellett azt adja, hogy
$$\lim_{t\to0}\frac{\Delta(t,t)}{t^2} = \partial_{21}f(a).$$
*Összevetés.* Ugyanannak a $\Delta(t,t)/t^2$ kifejezésnek a határértékéről van szó, a határérték pedig egyértelmű, tehát
$$\partial_{12}f(a) = \partial_{21}f(a). \qquad \blacksquare$$
Az általános $s$, $n$ esetet ebből $s$ szerinti teljes indukció adja: bármely permutáció előáll szomszédos transzpozíciók szorzataként, és egy szomszédos csere éppen a fenti kétváltozós állítás a megfelelő belső deriváltfüggvényre alkalmazva.
<br>
**A feltétel nem hagyható el.** Az
$$f(x,y) := \begin{cases} xy\dfrac{x^2-y^2}{x^2+y^2} & (x^2+y^2\ne0)\\[4pt] 0 & (x=y=0)\end{cases}$$
függvényre a vegyes másodrendű parciális deriváltak **léteznek** az origóban, mégis $\partial_{12}f(0,0) = -1 \ne 1 = \partial_{21}f(0,0)$.
<br>
**Következmény.** A Hesse-mátrix szimmetrikus (enélkül nem volna kvadratikus alak a második derivált), a multiindexes $\partial^\alpha f$ jelölés jóldefiniált, és a $\partial_if_j = \partial_jf_i$ rotációmentesség szükséges feltétele primitív függvény létezésének.
---
