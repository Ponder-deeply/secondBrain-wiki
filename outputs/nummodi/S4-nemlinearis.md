---
tags: [synthesis]
sources: [tetel-25-nemlinearis-1.md, tetel-26-nemlinearis-2.md, tetel-27-nemlinearis-3.md, tetel-28-polinom-gyok.md]
updated: 2026-06-09
---

# S4 – Nemlineáris egyenletek

Minden gyökkeresés ugyanaz a két ötlet: az $f(x)=0$ egyenletet $x=\varphi(x)$ **fixpont-iterációvá** írjuk át, és a gyakorlati módszerek a $\varphi$-t **linearizálással** állítják elő. A négy tételt egyetlen skála köti össze — a **konvergenciarend** $p$ —, amelynek elméleti hátterét a Banach-fixponttétel és a magasabb-rend tétel adja (felezés $p=1$, húr $p=1$, szelő $p\approx1{,}618$, Newton $p=2$).

## A közös váz

**Fixpont-átírás.** Az $f(x)=0$ egyenlethez választunk olyan $\varphi$-t, hogy
$$f(x)=0 \iff x=\varphi(x),$$
pl. $\varphi(x)=x-f(x)$. A megoldás $x^*=\varphi(x^*)$ a $\varphi$ **fixpontja**, és az $x_{k+1}=\varphi(x_k)$ iterációval keressük.

**Kontrakció.** $\varphi$ kontrakció $[a,b]$-n, ha $\exists q\in(0,1)$:
$$|\varphi(x)-\varphi(y)|\le q\,|x-y|.$$
**Elégséges feltétel** (Lagrange-középérték-tételből): ha $\varphi\in C^1$ és $q:=\max_{[a,b]}|\varphi'|<1$, akkor kontrakció.

**Létezés/egyértelműség — három réteg, egyre erősebb:**

| Tétel | Feltétel | Mit ad |
|---|---|---|
| **Bolzano** | $f\in C[a,b]$, $f(a)f(b)<0$ | gyök **létezik** $(a,b)$-ben |
| **Brouwer** | $\varphi:[a,b]\to[a,b]$ folytonos | fixpont **létezik** (de nem egyértelmű) |
| **Banach** | $\varphi:[a,b]\to[a,b]$ kontrakció ($q$) | **egyetlen** fixpont + iteráció konvergál + **hibabecslés** |

Banach hibabecslése:
$$|x_k-x^*|\le q^k|x_0-x^*|,\qquad |x_k-x^*|\le\frac{q^k}{1-q}\,|x_1-x_0|.$$

**Konvergenciarend.** Az $x_k\to x^*$ sorozat **$p$-edrendben** konvergens, ha
$$\lim_{k\to\infty}\frac{|x_{k+1}-x^*|}{|x_k-x^*|^p}=c\in(0,\infty)$$
($p=1$ esetén $c<1$ kell). $p=1$ lineáris, $1<p$ szuperlineáris, $p=2$ kvadratikus. A Banach-iteráció $|x_{k+1}-x^*|\le q|x_k-x^*|$ miatt **legalább elsőrendű** ($c\le q$).

**Magasabb-rend tétele.** Ha $\varphi\in C^p$ az $x^*$ körül és
$$\varphi'(x^*)=\varphi''(x^*)=\cdots=\varphi^{(p-1)}(x^*)=0,\qquad \varphi^{(p)}(x^*)\ne0,$$
akkor az iteráció **pontosan $p$-edrendű**, $c=\dfrac{|\varphi^{(p)}(x^*)|}{p!}$. Ez a kulcs: a magasabb rendhez az első deriváltaknak el kell tűnniük a fixpontban. Egyszerű iterációnál ($\varphi'(x^*)\ne0$) a konvergencia csak lineáris; a Newton azért kvadratikus, mert nála $\varphi'(x^*)=0$.

## A módszerek egy skálán

A **linearizálás** közös elve: a Newton minden lépésben az $f$-et az aktuális ponti **érintővel** (elsőfokú Taylor) helyettesíti, és e lineáris feladat zérushelyét veszi. A húr/szelő ugyanezt csinálja, csak az érintő meredekségét **véges differenciával** közelíti; a felezés nem linearizál, hanem Bolzano-alapon felez.

| Módszer | Iterációs képlet | $f'$ kell? | Rend $p$ | Megjegyzés |
|---|---|---|---|---|
| **Intervallumfelezés** | $c_k=\frac{x_k+y_k}{2}$, az előjelet tartó fél marad | nem | $1$ | garantáltan konvergens (Bolzano); hiba $\le\frac{b-a}{2^{k+1}}$ |
| **Húrmódszer** | $x_{k+1}=x_k-f(x_k)\frac{x_k-x_s}{f(x_k)-f(x_s)}$, $x_s$ **rögzített** ellentétes előjelű végpont | nem | $1$ | zárólási tulajdonság megmarad, egyoldali közelítés |
| **Szelőmódszer** | $x_{k+1}=x_k-f(x_k)\frac{x_k-x_{k-1}}{f(x_k)-f(x_{k-1})}$, a **két legutóbbi** pont | nem | $\frac{1+\sqrt5}{2}\approx1{,}618$ | Newton véges differenciával; szuperlineáris |
| **Newton (1-vált.)** | $x_{k+1}=x_k-\frac{f(x_k)}{f'(x_k)}$ | igen | $2$ | érintő zérushelye; egyszerű gyökre kvadratikus |
| **Newton (több-vált.)** | $J_F(x^{(k)})\,\Delta x=-F(x^{(k)})$, majd $x^{(k+1)}=x^{(k)}+\Delta x$ | igen ($J_F$) | $2$ | minden lépésben egy **LER** megoldása |

A többváltozós eset visszakapcsol a direkt megoldókhoz: lépésenként egy $J_F\,\Delta x=-F$ **lineáris egyenletrendszert** kell megoldani (LU/Gauss). $n=1$-re $J_F=f'$ skalár, és visszakapjuk a skalár Newton-t. (Broyden: $J_F$-et csak ritkán számítjuk újra, rangegyrendű frissítéssel.)

**Newton monoton konvergenciája (konvex eset).** Ha $f',f''>0$ és a kezdőpontot a gyöknek azon az oldalán választjuk, ahol $f\cdot f''>0$ (pl. $x_0=b$ esetén $f(b)>0$), akkor $x^*\le\cdots\le x_{k+1}\le x_k\le x_0$, monoton csökkenve.

## Polinomok (T28)

Legyen $p(x)=a_nx^n+\cdots+a_0$, $a_n\ne0$.

**Gyökbecslés.** Minden komplex gyökre $|z|<R$, ahol
$$R=1+\max_{0\le k\le n-1}\left|\frac{a_k}{a_n}\right|.$$
Ha $a_0\ne0$, a reciprok-polinomra alkalmazva alsó korlát is adódik:
$$r=\frac{1}{1+\dfrac{\max_{1\le k\le n}|a_k|}{|a_0|}},\qquad r<|z|<R$$
(körgyűrű). Így a gyökkereső iterációkat (Newton) nem a vakvilágba indítjuk: a $|z|<R$ tartomány adja az értelmes kezdő-régiót.

**Horner-séma — $p(x_0)$ kiértékelése $\mathcal{O}(n)$-ben** (naiv $\mathcal{O}(n^2)$ helyett). A beágyazott zárójelezésből:
$$b_n:=a_n,\qquad b_k:=b_{k+1}x_0+a_k,\qquad p(x_0)=b_0.$$
A $b_n,\dots,b_1$ együtthatók egyúttal a $q(x)=\dfrac{p(x)-p(x_0)}{x-x_0}$ hányados együtthatói: $p(x)=(x-x_0)q(x)+b_0$.

**Deriváltak ismételt Hornerrel.** A $p(x)=(x-x_0)q(x)+b_0$ azonosságot deriválva $p'(x_0)=q(x_0)$ — vagyis a Horner **újrafuttatása** a $b$-együtthatókon adja $p'(x_0)$-t. A menetet ismételve a Taylor-eltolás együtthatóit kapjuk:
$$p^{(j)}(x_0)=j!\,t_j,$$
ahol $t_j$ a $j$-edik menet végértéke. Ez a **polinomos Newton-lépés alaptéglája**: egy gyökkereső Newton-iterációhoz $p(x_k)$ és $p'(x_k)$ kell, és mindkettő egy-egy $\mathcal{O}(n)$ Horner-menet.

## Tétel-delták

Mi az egyetlen új réteg tételenként:

- **T25 (elméleti motor).** A fixpont-keretrendszer maga: $f=0\to x=\varphi(x)$, kontrakció, a Bolzano/Brouwer/Banach **háromrétegű** létezés-egyértelműség, a konvergenciarend definíciója és a **magasabb-rend tétel** ($\varphi^{(j)}(x^*)=0$). Ez adja a nyelvet a többi tételhez.
- **T26 (derivált nélküli módszerek + szelő rendje).** Húr és szelő mint a Newton derivált nélküli rokona; az új tartalom a **szelő = Newton véges differenciával** levezetés és a rendek skálája (húr $1$, szelő $1{,}618$, Newton $2$).
- **T27 (robusztusság + linearizálás + többváltozós).** Az **intervallumfelezés** garantált konvergenciája és hibabecslése; a Newton **monoton** konvergenciája konvex esetben; és a **többváltozós Newton** ($J_F\Delta x=-F$), ahol minden lépés egy LER — a linearizálás kifejezett megjelenése.
- **T28 (polinom-specialitás).** Gyökök **körgyűrűben** ($r<|z|<R$, explicit korlátok); a **Horner** $\mathcal{O}(n)$ kiértékelés és az **ismételt Horner** a deriváltakra — a polinomos Newton hatékony alaplépése.

## Felmondható tételmondatok

- **Bolzano.** $f\in C[a,b]$, $f(a)f(b)<0$ $\Rightarrow$ $\exists x^*\in(a,b):f(x^*)=0$.
- **Brouwer ($[a,b]$).** $\varphi:[a,b]\to[a,b]$ folytonos $\Rightarrow$ $\exists x^*\in[a,b]:\varphi(x^*)=x^*$ (nem feltétlen egyértelmű).
- **Banach.** $\varphi:[a,b]\to[a,b]$ kontrakció $q$-val $\Rightarrow$ (1) **egyetlen** $x^*$ fixpont; (2) minden $x_0$-ból $x_{k+1}=\varphi(x_k)\to x^*$; (3) $|x_k-x^*|\le q^k|x_0-x^*|\le\frac{q^k}{1-q}|x_1-x_0|$.
- **Kontrakció elégséges feltétele.** $\varphi\in C^1[a,b]$, $\max_{[a,b]}|\varphi'|=q<1$ $\Rightarrow$ $\varphi$ kontrakció $q$-val.
- **Magasabb-rend tétele.** $\varphi'(x^*)=\cdots=\varphi^{(p-1)}(x^*)=0$, $\varphi^{(p)}(x^*)\ne0$ $\Rightarrow$ az iteráció pontosan $p$-edrendű.
- **Newton lokális kvadratikus konvergencia.** $f\in C^2$, $x^*$ egyszerű gyök ($f'(x^*)\ne0$) $\Rightarrow$ $\exists\delta$: $x_0\in[x^*\!-\!\delta,x^*\!+\!\delta]$-ból a Newton **másodrendben** konvergál, $c=\frac{|f''(x^*)|}{2|f'(x^*)|}$.
- **Szelőmódszer rendje.** $p=\frac{1+\sqrt5}{2}\approx1{,}618$ (aranymetszés).
- **Polinom gyök felső korlátja.** Minden gyökre $|z|<R=1+\max_{0\le k\le n-1}|a_k/a_n|$.

## Bizonyítás-magok

- **Brouwer Bolzanóból.** $h(x):=\varphi(x)-x$. Mivel $\varphi(a),\varphi(b)\in[a,b]$: $h(a)\ge0$, $h(b)\le0$. Ha valamelyik $=0$, kész; különben $h(a)h(b)<0$, és Bolzano $h$-ra ad zérushelyet $=$ fixpontot.
- **Kontrakció Lagrange-ból.** $\varphi(x)-\varphi(y)=\varphi'(\xi)(x-y)$, abszolútérték + $|\varphi'(\xi)|\le q$ $\Rightarrow$ $|\varphi(x)-\varphi(y)|\le q|x-y|$.
- **Magasabb-rend tétele (T25, Taylor-bizonyítás).** Feltétel: $\varphi\in C^p$ az $x^*$ körül, $\varphi'(x^*)=\cdots=\varphi^{(p-1)}(x^*)=0$, $\varphi^{(p)}(x^*)\ne0$. Írjuk fel $\varphi$ Taylor-sorát $x^*$ körül $x_k$-ban, Lagrange-maradéktaggal (valamely $\xi_k$ az $x_k$ és $x^*$ között):
  $$x_{k+1}=\varphi(x_k)=\varphi(x^*)+\sum_{j=1}^{p-1}\frac{\varphi^{(j)}(x^*)}{j!}(x_k-x^*)^j+\frac{\varphi^{(p)}(\xi_k)}{p!}(x_k-x^*)^p.$$
  A feltétel szerint $\varphi(x^*)=x^*$ és az első $p-1$ derivált eltűnik, így marad
  $$x_{k+1}-x^*=\frac{\varphi^{(p)}(\xi_k)}{p!}(x_k-x^*)^p.$$
  Osztva $(x_k-x^*)^p$-nel, és mivel $x_k\to x^*\Rightarrow\xi_k\to x^*$ ($\varphi^{(p)}$ folytonos):
  $$\frac{|x_{k+1}-x^*|}{|x_k-x^*|^p}=\frac{|\varphi^{(p)}(\xi_k)|}{p!}\xrightarrow{k\to\infty}\frac{|\varphi^{(p)}(x^*)|}{p!}=:c>0,$$
  ami éppen a pontosan $p$-edrendű konvergencia definíciója. $\blacksquare$
- **Newton kvadratikus.** $\varphi=x-f/f'$ $\Rightarrow$ $\varphi'=\frac{f f''}{(f')^2}$, és $f(x^*)=0$ miatt $\varphi'(x^*)=0$; mivel $\varphi''(x^*)=\frac{f''(x^*)}{f'(x^*)}\ne0$, a magasabb-rend tétele $p=2$-t ad.
- **Newton monoton konvergenciája (T27, konvex eset).** Feltétel: $f\in C^2[a,b]$, $f(a)<0<f(b)$, $f'>0$, $f''>0$; kezdőpont $x_0\in[x^*,b]$. A gyök egyértelmű, mert $f$ szigorúan monoton. Indukcióval igazoljuk, hogy a sorozat $x^*$ felett marad és csökken.
  - *Alsó korlát ($x_{k+1}\ge x^*$).* Taylor $x_k$ körül $x^*$-ban, Lagrange-maradékkal ($\xi$ az $x^*$ és $x_k$ között):
    $$0=f(x^*)=f(x_k)+f'(x_k)(x^*-x_k)+\tfrac12 f''(\xi)(x^*-x_k)^2.$$
    Átrendezve, $f'(x_k)>0$-val osztva, és felismerve a Newton-lépést:
    $$x^*=x_k-\frac{f(x_k)}{f'(x_k)}-\frac{f''(\xi)}{2f'(x_k)}(x^*-x_k)^2=x_{k+1}-\underbrace{\frac{f''(\xi)}{2f'(x_k)}(x^*-x_k)^2}_{\ge\,0}.$$
    Mivel $f''>0$ és $f'>0$, az utolsó tag $\ge0$, ezért $x^*\le x_{k+1}$. Az $x_0\ge x^*$ kezdőfeltétel mellett ez minden $k$-ra $x_k\ge x^*$-ot ad.
  - *Monoton csökkenés ($x_{k+1}\le x_k$).* $x_k\ge x^*$ és $f$ növő $\Rightarrow$ $f(x_k)\ge f(x^*)=0$, továbbá $f'(x_k)>0$, ezért
    $$x_{k+1}-x_k=-\frac{f(x_k)}{f'(x_k)}\le0.$$
  - *Konvergencia.* A $(x_k)$ monoton csökkenő és alulról korlátos ($x^*$) $\Rightarrow$ konvergens; $\bar x:=\lim x_k$. A folytonosság miatt $\bar x=\bar x-f(\bar x)/f'(\bar x)$, ahonnan $f(\bar x)=0$, azaz $\bar x=x^*$. $\blacksquare$
- **Szelő = Newton véges differenciával.** $f'(x_k)\approx\frac{f(x_k)-f(x_{k-1})}{x_k-x_{k-1}}$ a Newton-képletbe helyettesítve adja a szelő-iterációt.
- **Többváltozós Newton elsőfokú Taylorból.** $F(x^{(k)}+\Delta x)\approx F(x^{(k)})+J_F(x^{(k)})\Delta x\overset{!}{=}0$ $\Rightarrow$ $J_F\Delta x=-F$, majd $x^{(k+1)}=x^{(k)}+\Delta x$. $n=1$-re $f'\Delta x=-f$.
- **Polinom-gyök $R$ (felső korlát).** $a_nz^n=-\sum_{k<n}a_kz^k$, háromszög-egyenlőtlenség + mértani sor $\sum_{k<n}|z|^k<\frac{|z|^n}{|z|-1}$ ($|z|>1$); $|z|^n$-nel osztva $|z|-1<\frac{\max|a_k|}{|a_n|}$, azaz $|z|<R$ (indirekt ellentmondás).
- **Polinom-gyök $r$ (alsó korlát, reciprok-polinom trükk).** Tegyük fel $a_0\ne0$. A $y=1/z$ helyettesítéssel vezessük be a reciprok-polinomot
  $$Q(y)=a_0y^n+a_1y^{n-1}+\cdots+a_n,$$
  amelyre $p(z)=0\iff Q(1/z)=0$ (számolással: $Q(1/z)=p(z)/z^n$), tehát $Q$ gyökei éppen $p$ gyökeinek reciprokai. Alkalmazzuk a felső korlátot $Q$-ra (vezető együttható $a_0$, a többi $a_1,\dots,a_n$): minden $Q$-gyök $y=1/z$-re
  $$\frac1{|z|}=|y|<1+\frac{\max_{1\le k\le n}|a_k|}{|a_0|}=\frac1r.$$
  Reciprokot véve $|z|>r$. A két korláttal együtt minden gyök az $r<|z|<R$ nyílt körgyűrűben fekszik. $\blacksquare$
- **Horner helyessége.** Indukcióval $b_k=a_nx_0^{n-k}+\cdots+a_k$ a felülről $k$-ig vett részpolinom értéke; $k=0$-ra ez $p(x_0)$. A deriváltakra: $p=(x-x_0)q+b_0$ deriválva $p'(x_0)=q(x_0)$, a menet ismétlése a Taylor-együtthatókat ($p^{(j)}(x_0)=j!\,t_j$) adja.

## Kapcsolódó oldalak

- [[tetel-25-nemlinearis-1]] — fixpont, kontrakció, Bolzano/Brouwer/Banach, magasabb-rend tétel
- [[tetel-26-nemlinearis-2]] — húr, szelő, szelő rendje, Newton mint összehasonlítási alap
- [[tetel-27-nemlinearis-3]] — felezés, Newton monoton konvergencia, többváltozós Newton (LER)
- [[tetel-28-polinom-gyok]] — gyökbecslés körgyűrű, Horner és deriváltjai
