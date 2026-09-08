---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.7.10. Tétel, 1.8. x), xii)–xvi) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# A kompaktság három ekvivalens megfogalmazása

Metrikus térben a sorozatos (Bolzano–Weierstrass-féle) kompaktság, a fedéses (Borel-féle) kompaktság és a „minden végtelen részhalmaznak van torlódási pontja" feltétel ugyanazt jelenti. A három megfogalmazás közti átjárás a kompaktsági bizonyítások fő technikája.

## Tartalom

### Sorozatos kompaktság

**Definíció.** Az $(X,\rho)$ metrikus tér $\emptyset\neq A \subset X$ halmaza **kompakt**, ha tetszőleges $(x_n):\mathbb{N}\to A$ sorozathoz létezik olyan $(\nu_n)$ indexsorozat, hogy az $(x_{\nu_n})$ részsorozat konvergens és $\lim(x_{\nu_n}) \in A$.

Minden véges halmaz kompakt: az $A$ végessége miatt van olyan $a \in A$ és $(\nu_n)$, hogy $x_{\nu_n}=a$ minden $n$-re.

### Nyílt lefedés

Ha $\Gamma\neq\emptyset$ és $T_\gamma \subset X$ ($\gamma\in\Gamma$) nyílt halmazok olyanok, hogy $A \subset \bigcup_{\gamma\in\Gamma}T_\gamma$, akkor a $\{T_\gamma : \gamma\in\Gamma\}$ halmazrendszer az $A$ egy **nyílt lefedése**. Ha van olyan véges $\Gamma_0\subset\Gamma$, amelyre $A \subset \bigcup_{\gamma\in\Gamma_0}T_\gamma$, akkor a lefedésből **kiválasztható véges lefedés**.

### A fő tétel

**Tétel.** Az $A \subset X$ halmaz akkor és csak akkor kompakt, ha minden nyílt lefedéséből kiválasztható véges lefedés.

**Lemma (Lebesgue-szám).** Ha $A$ kompakt, akkor tetszőleges $\{T_\gamma : \gamma\in\Gamma\}$ nyílt lefedéséhez van olyan $r>0$, hogy bármely $a \in A$ pontra egy alkalmas $\gamma$ indexszel $K_r(a) \subset T_\gamma$.

*A lemma bizonyítása.* Ha nem így lenne, akkor volna olyan lefedés, hogy minden $0<n\in\mathbb{N}$-hez van $x_n \in A$, amelyre $K_{1/n}(x_n)$ egyik $T_\gamma$-nak sem részhalmaza. Az $A$ kompaktsága miatt van olyan $(\nu_n)$, hogy $a := \lim(x_{\nu_n}) \in A$. Valamely $\gamma$-ra $a \in T_\gamma$, és $T_\gamma$ nyíltsága miatt $K_\sigma(a)\subset T_\gamma$ egy $\sigma>0$-val. Ha $t \in K_{1/\nu_n}(x_{\nu_n})$, akkor

$$\rho(t,a) \leq \rho(t,x_{\nu_n}) + \rho(x_{\nu_n},a) < \tfrac{1}{\nu_n}+\rho(x_{\nu_n},a) \to 0,$$

tehát elég nagy $n$-re $K_{1/\nu_n}(x_{\nu_n}) \subset K_\sigma(a) \subset T_\gamma$ — ellentmondás. $\blacksquare$

*A szükségesség.* Indirekt: tegyük fel, hogy egy nyílt lefedésből nem választható ki véges lefedés, és legyen $r$ a lemma szerinti szám. Ha $x_0 \in A$, akkor $A \not\subset K_r(x_0)$ (különben egyetlen $T_\gamma$ lefedné $A$-t), tehát van $x_1 \in A$ úgy, hogy $\rho(x_0,x_1)\geq r$; ugyanígy $A \not\subset K_r(x_0)\cup K_r(x_1)$, és így tovább. Teljes indukcióval olyan $(x_n):\mathbb{N}\to A$ sorozathoz jutunk, amelyre

$$\rho(x_n,x_m) \geq r \qquad (n\neq m).$$

Ennek nincs Cauchy-részsorozata, tehát konvergens részsorozata sem — ez ellentmond $A$ kompaktságának. $\blacksquare$

*Az elégségesség.* Legyen $(x_n):\mathbb{N}\to A$. Ha az $R_{(x_n)}$ értékkészlet véges, van konstans (tehát konvergens) részsorozat, és a határértéke $A$-ban van. Ha $B := R_{(x_n)}$ végtelen, előbb belátjuk, hogy $B$-nek van $A$-beli torlódási pontja. Ha nem lenne, minden $a \in A$-hoz volna $K(a)$ környezet, amelyre $\bigl(K(a)\setminus\{a\}\bigr)\cap B=\emptyset$. Ezek nyílt lefedését adják $A$-nak, így véges $A_0 \subset A$ mellett $A \subset \bigcup_{a\in A_0}K(a)$, tehát

$$B = B\cap A = \bigcup_{a\in A_0}\bigl(K(a)\cap B\bigr),$$

ahol minden tag legfeljebb egyelemű — $B$ véges volna. Van tehát $a \in B'\cap A$, és így minden $0<n$-hez választható $x_{\nu_n}$ úgy, hogy $\rho(x_{\nu_n},a)<1/n$ és $\nu_n<\nu_{n+1}$. Ekkor $(x_{\nu_n})$ konvergens és $\lim(x_{\nu_n})=a \in A$. $\blacksquare$

### A torlódási pontos jellemzés

**Tétel.** Az $A \subset X$ halmaz akkor és csak akkor kompakt, ha minden $B \subset A$ **végtelen** részhalmazára $B'\cap A \neq \emptyset$, azaz $B$-nek van $A$-beli torlódási pontja.

(Véges $A$ esetén nincs végtelen részhalmaz, így a feltétel automatikusan teljesül — összhangban azzal, hogy a véges halmazok kompaktak.)

### Összefoglalva

Metrikus térben az alábbi három állítás ekvivalens:

- az $A$ halmaz minden nyílt lefedéséből kiválasztható véges lefedés;
- az $A$ halmaz minden végtelen részhalmazának van $A$-beli torlódási pontja;
- tetszőleges $A$-beli sorozatnak van $A$-ban konvergens részsorozata.

**Borel-lefedési tétel.** Az $X:=\mathbb{R}$, $\rho(x,y):=|x-y|$, $A := [a,b]$ speciális eset: ha $\mathbb{R}$-beli nyílt halmazok együttesen lefedik az $[a,b]$ intervallumot, akkor közülük már véges sok is lefedi.

### Két öröklődési szabály

**Zárt részhalmaz.** Ha $A$ kompakt és $B \subset A$ zárt, akkor $B$ is kompakt. (Egy $B$-beli sorozatnak $A$ kompaktsága miatt van $A$-ban konvergáló részsorozata, és $B$ zártsága miatt a határérték $B$-ben van.)

**Egymásba skatulyázott kompaktok.** Ha $\emptyset \neq A_{n+1} \subset A_n$ ($n\in\mathbb{N}$) kompakt halmazok, akkor $\bigcap_{n=0}^\infty A_n$ nemüres és kompakt. Ez a [[concepts/analiii/cantor-metszettetel]] absztrakt változata: a Cantor-axióma korlátos zárt intervallumokra ennek speciális esete.

## Kapocs

- [[concepts/analiii/kompakt-halmazok]] — a fedéses definíció és a „kompakt $\Rightarrow$ korlátos és zárt" irány
- [[concepts/analiii/heine-borel-tetel]] — $\mathbb{R}^p$-ben a korlátos és zárt halmazok kompaktak
- [[concepts/analiii/cantor-metszettetel]] — a skatulyázott metszettétel konkrét alakja
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a torlódási pont és a derivált halmaz
- [[concepts/analiii/metrikus-terek-szorzata]] — kompaktság a szorzattérben
