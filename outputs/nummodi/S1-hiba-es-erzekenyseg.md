---
tags: [synthesis]
sources: [tetel-01-lebegopont.md, tetel-02-hibaszamitas.md, tetel-13-matrixnormak-1.md, tetel-14-matrixnormak-2.md, tetel-15-frobenius-norma.md, tetel-16-ler-erzekenysege-jobboldal.md, tetel-17-ler-erzekenysege-matrix.md]
updated: 2026-06-09
---

# S1 – Hiba és érzékenység

Egyetlen szál fűzi össze a hét tételt: **a pontatlanság mérése a bittől a rendszerig — a relatív hiba és annak felerősödése.** Ugyanaz a kérdés tér vissza három egyre magasabb szinten: mekkora *erősítési faktorral* terjed tovább egy kis relatív hiba, és mikor robban fel.

## A közös váz

A vezérfonal: **mindig a relatív hibát mérjük, és mindig az a kérdés, mekkora faktor szorozza fel.** A faktor neve szintenként más, de a jelenség egy.

### Mikro szint (T01–02): a gépi szám és a művelet-hibaterjedés

A számítógép csak véges, diszkrét gépi számhalmazból ($M$) tud ábrázolni. Az `fl` kerekítő függvény a legközelebbi gépi számra kerekít, és a belőle adódó **relatív** hiba egyenletesen korlátos:

$$\frac{|x - \mathrm{fl}(x)|}{|x|} \leq \frac{1}{2}\varepsilon_1 = \varepsilon, \qquad \varepsilon_1 = 2^{1-t},$$

ahol $\varepsilon$ a **kerekítési egység**. Ez a relatív hiba forrása a legalsó szinten — minden egyes szám betöltése legfeljebb $\varepsilon$ relatív hibát hoz be.

A hibák a műveleteken keresztül terjednek. A relatív hibára nézve:

- **szorzás / osztás:** $\delta(xy),\ \delta(x/y) \leq \delta x + \delta y$ — a relatív hiba csak *összeadódik*, ezért nem veszélyes;
- **összeadás / kivonás:** $\delta(x\pm y) \leq \dfrac{|x|\,\delta x + |y|\,\delta y}{|x\pm y|}$ — a nevezőben $|x\pm y|$ áll.

**A kulcsjelenség: a katasztrofális törlés.** Ha $x \approx y$, akkor $|x-y| \to 0$, a nevező nullához tart, és a relatív hiba *korlátlanul felrobban*, miközben az abszolút hiba nem nő. A kis nevező = a relatív hiba erősítése.

### Eszköz szint (T13–15): a norma mint a vektorhiba mérőszáma

Egy vektor relatív hibájához mérőszám kell — ez a **norma**. A vektornorma 4 axiómát teljesít (nemnegatív, definit, pozitív homogén, szubadditív). A **mátrixnorma** ezekhez hozzáteszi az 5. axiómát:

$$\|AB\| \leq \|A\|\,\|B\| \quad \text{(szubmultiplikativitás)}.$$

A legfontosabb mátrixnormák **indukáltak** egy vektornormából:

$$\|A\| := \sup_{x \neq 0} \frac{\|Ax\|_v}{\|x\|_v} = \max_{\|y\|_v=1}\|Ay\|_v,$$

amiből azonnal adódik az **illeszkedés**: $\|Ax\|_v \leq \|A\|\,\|x\|_v$ — a mátrix mint leképezés legfeljebb $\|A\|$-szorosára nyújt. Minden indukált normára $\|I\| = 1$. Explicit alakok:

$$\|A\|_1 = \max_j \sum_i |a_{ij}|\ \text{(max oszlopösszeg)},\quad \|A\|_\infty = \max_i \sum_j |a_{ij}|\ \text{(max sorösszeg)},\quad \|A\|_2 = \sqrt{\rho(A^TA)}\ \text{(spektrálnorma)}.$$

A **Frobenius-norma** $\|A\|_F = \sqrt{\sum a_{ij}^2} = \sqrt{\mathrm{tr}(A^TA)}$ szintén mátrixnorma, de **nem indukált** (mert $\|I\|_F = \sqrt{n} \neq 1$); viszont *illeszkedik* a 2-normához: $\|Ax\|_2 \leq \|A\|_F\,\|x\|_2$.

### Makró szint (T16–17): a kondíciószám mint erősítési faktor

Az $Ax = b$ rendszer egészén a relatív hiba erősítési faktora a **kondíciószám**:

$$\kappa(A) = \mathrm{cond}(A) = \|A\|\,\|A^{-1}\|.$$

**Jobboldal-perturbáció** ($A(x+\Delta x) = b + \Delta b$, tehát $A\Delta x = \Delta b$). A megoldás relatív hibája kétoldalt becsült:

$$\frac{1}{\kappa(A)}\,\frac{\|\Delta b\|}{\|b\|} \;\leq\; \frac{\|\Delta x\|}{\|x\|} \;\leq\; \kappa(A)\,\frac{\|\Delta b\|}{\|b\|}.$$

**Mátrix-perturbáció** ($(A+\Delta A)(x+\Delta x) = b$). Ha $\kappa(A)\cdot\delta A < 1$:

$$\frac{\|\Delta x\|}{\|x\|} \;\leq\; \frac{\kappa(A)}{1 - \kappa(A)\,\delta A}\,\delta A, \qquad \delta A = \frac{\|\Delta A\|}{\|A\|}.$$

Az utóbbi a **Neumann-lemmán** áll: ha $\|M\| < 1$, akkor $(I+M)$ invertálható és $\|(I+M)^{-1}\| \leq \dfrac{1}{1-\|M\|}$.

A $\kappa$ tulajdonságai: $\kappa(A) \geq 1$, $\kappa(I) = 1$, $\kappa(\alpha A) = \kappa(A)$ ($\alpha \neq 0$), $\kappa(A^{-1}) = \kappa(A)$.

### A nagy összekötés

A **katasztrofális törlés** (mikro) és a **rossz kondíció** (makró) **ugyanaz a jelenség**. Mikro szinten a $\delta(x-y)$ nevezője $|x-y| \to 0$; makró szinten a $\kappa(A) = \|A\|\|A^{-1}\|$ robban fel, ahogy $A$ közel szinguláris ($\|A^{-1}\| \to \infty$). Mindkét esetben **kis „nevező" / közel-szinguláris szerkezet → a relatív hiba korlátlan felerősödése.** Az eszköz szint (norma) éppen az a nyelv, amin a mikro skalár-relatívhibát a makró rendszerszintre emeljük.

## Tétel-delták

Mit tesz hozzá *pontosan* az egyes tétel a vázhoz:

| Tétel | Az egyetlen új dolog (delta) |
|-------|------------------------------|
| **T01** Lebegőpont | A gépi számhalmaz szerkezete: $x = \pm m\beta^e$, $m_1 \neq 0$; a számok **nem egyenletesen** állnak ($\delta(k) = 2^{k-t}$), de a **relatív** felbontás állandó ($\varepsilon_1 = 2^{1-t}$). Innen jön az $\varepsilon$ kerekítési egység. |
| **T02** Hibaszámítás | Abszolút vs. relatív hiba + a 4 alapművelet hibakorlátai. Delta: szorzás/osztás $\delta x+\delta y$ (biztonságos), kivonás nevezője $|x-y|$ → **törlési hiba**. |
| **T13** Mátrixnorma I. | A norma-hierarchia (vektor 4 + mátrix 5. axióma), az indukált norma sup-definíciója és a **teljes bizonyítás, hogy az indukált norma mind az 5 axiómát teljesíti** + a három explicit képlet. |
| **T14** Mátrixnorma II. | Az **illeszkedés** önálló fogalma + az $\|A\|_\infty = \max_i\sum_j|a_{ij}|$ képlet **kétirányú bizonyítása** (felső korlát + előjel-vektoros élesség). |
| **T15** Frobenius | A Frobenius-norma definíciója; delta: **nem indukált** ($\|I\|_F=\sqrt n$), de **illeszkedik a 2-normához**; $\|A\|_F^2 = \mathrm{tr}(A^TA) = \sum_i\lambda_i(A^TA)$. |
| **T16** LER, jobboldal | A $\kappa(A)=\|A\|\|A^{-1}\|$ definíció + a **kétoldali** jobboldal-perturbációs becslés ($1/\kappa \le \delta x/\delta b \le \kappa$) + a $\kappa$ négy tulajdonsága bizonyítással. |
| **T17** LER, mátrix | A **mátrix-perturbációs** becslés $\dfrac{\kappa}{1-\kappa\delta A}\delta A$ + a **Neumann-lemma** mint a bizonyítás motorja és a $\kappa\delta A<1$ invertálhatósági feltétel. |

## Felmondható tételmondatok

Szó szerint kérhető, precíz állítások (feltételekkel, bizonyítás nélkül):

1. **fl relatív hibakorlátja.** Ha $|x| \leq M_\infty$, akkor $\dfrac{|x-\mathrm{fl}(x)|}{|x|} \leq \dfrac{1}{2}\varepsilon_1 = \varepsilon$, ahol $\varepsilon_1 = 2^{1-t}$ a gépi epszilon.
2. **Alapműveletek relatív hibakorlátai.** $\delta(xy) \leq \delta x + \delta y$, $\delta(x/y) \leq \delta x + \delta y$, $\delta(x\pm y) \leq \dfrac{|x|\delta x + |y|\delta y}{|x\pm y|}$. (Kivonásnál $|x-y|\to 0$ → törlési hiba.)
3. **Norma-axiómák.** Vektornorma: nemnegatív, definit ($\|x\|=0 \iff x=0$), pozitív homogén, szubadditív. Mátrixnorma: ugyanezek + szubmultiplikativitás $\|AB\| \leq \|A\|\|B\|$.
4. **Indukált norma 5 axiómája.** Tétel: tetszőleges vektornormából indukált $\|A\| = \sup_{x\neq 0}\|Ax\|_v/\|x\|_v$ mind az 5 mátrixnorma-axiómát teljesíti.
5. **Illeszkedés.** Indukált normára $\|Ax\|_v \leq \|A\|\,\|x\|_v$ minden $x$-re; és $\|I\| = 1$.
6. **Explicit normák.** $\|A\|_1 = \max_j\sum_i|a_{ij}|$, $\|A\|_\infty = \max_i\sum_j|a_{ij}|$, $\|A\|_2 = \sqrt{\rho(A^TA)}$.
7. **Frobenius.** $\|A\|_F = \sqrt{\sum_{i,j}a_{ij}^2} = \sqrt{\mathrm{tr}(A^TA)}$; **nem indukált** ($\|I\|_F = \sqrt n$), de illeszkedik a 2-normához ($\|Ax\|_2 \leq \|A\|_F\|x\|_2$).
8. **Jobboldal-perturbáció.** $A$ invertálható, $b\neq 0$: $\dfrac{1}{\kappa(A)}\dfrac{\|\Delta b\|}{\|b\|} \leq \dfrac{\|\Delta x\|}{\|x\|} \leq \kappa(A)\dfrac{\|\Delta b\|}{\|b\|}$.
9. **Mátrix-perturbáció.** Ha $\kappa(A)\delta A < 1$: $\dfrac{\|\Delta x\|}{\|x\|} \leq \dfrac{\kappa(A)}{1-\kappa(A)\delta A}\delta A$.
10. **Neumann-lemma.** Ha $\|M\| < 1$ indukált normában, akkor $(I+M)$ invertálható és $\|(I+M)^{-1}\| \leq \dfrac{1}{1-\|M\|}$.
11. **$\kappa$ tulajdonságai.** $\kappa(A) = \|A\|\|A^{-1}\| \geq 1$; $\kappa(I) = 1$; $\kappa(\alpha A) = \kappa(A)$ ($\alpha\neq 0$); $\kappa(A^{-1}) = \kappa(A)$.

## Bizonyítás-magok

A nemtriviális levezetések csontváza (kulcslépés, nem a teljes):

- **Szorzás relatív hibája = $\delta x + \delta y$.** $\tilde x\tilde y - xy = \tilde y(\tilde x - x) + x(\tilde y - y)$, háromszög-egyenlőtlenség adja $\Delta(xy) \leq |y|\Delta x + |x|\Delta y$, majd $|xy|$-nal osztva: $\delta(xy) \leq \Delta x/|x| + \Delta y/|y| = \delta x + \delta y$.
- **$\|A\|_\infty = \max_i\sum_j|a_{ij}|$.** *Felső korlát:* $|(Ax)_i| \leq \sum_j|a_{ij}||x_j| \leq \|x\|_\infty\,r_i \leq R\|x\|_\infty$. *Élesség:* a maximális sor $i^*$-ban $x^*_j = \mathrm{sgn}(a_{i^*j})$ választással $(Ax^*)_{i^*} = \sum_j|a_{i^*j}| = R$, $\|x^*\|_\infty = 1$, tehát $\|A\|_\infty \geq R$.
- **Frobenius nem indukált.** Indukált normára $\|I\| = \sup\|x\|_v/\|x\|_v = 1$, de $\|I\|_F = \sqrt{\sum\delta_{ij}^2} = \sqrt n \neq 1$ ($n>1$) → ellentmondás.
- **$\kappa(A) \geq 1$.** $1 = \|I\| = \|A\,A^{-1}\| \leq \|A\|\,\|A^{-1}\| = \kappa(A)$ — a szubmultiplikativitásból és $\|I\|=1$-ből.
- **Mátrix-perturbáció Neumann-lemmával.** Kivonás: $(A+\Delta A)\Delta x = -\Delta A\,x$, faktorálás: $A(I + A^{-1}\Delta A)\Delta x = -\Delta A\,x$. Mivel $\|A^{-1}\Delta A\| < 1$, a Neumann-lemma alapján $\Delta x = -(I+A^{-1}\Delta A)^{-1}A^{-1}\Delta A\,x$; normát véve a lemmát és $\kappa = \|A\|\|A^{-1}\|$-t behelyettesítve adódik a becslés.

- **T13 — Az indukált norma mind az 5 mátrixnorma-axiómát teljesíti** (TELJES). Jelölje $\|A\| = \sup_{x\neq 0}\|Ax\|_v/\|x\|_v$ az indukált, $\|\cdot\|_v$ az indukáló vektornormát. Az illeszkedés ($\|Ax\|_v \le \|A\|\,\|x\|_v$ minden $x$-re) a definícióból azonnal jön, ezt használjuk.
  - **(1) Nemnegatívság.** Minden $x\neq 0$-ra $\|Ax\|_v \ge 0$ és $\|x\|_v > 0$, így a hányados $\ge 0$, a szuprémumuk is: $\|A\| = \sup_{x\neq 0}\frac{\|Ax\|_v}{\|x\|_v} \ge 0$.
  - **(2) Definitség (mindkét irány).** *(⇒)* Ha $A = 0$, akkor $Ax = 0$ minden $x$-re, így minden hányados $0$, tehát $\|0\| = 0$. *(⇐)* Ha $\|A\| = 0$, akkor minden $x\neq 0$-ra $\frac{\|Ax\|_v}{\|x\|_v} \le \|A\| = 0$, vagyis $\|Ax\|_v = 0$; a vektornorma definitsége miatt $Ax = 0$. Ez minden $x\in\mathbb{R}^n$-re igaz (az $x=0$ triviális), így $A = 0$.
  - **(3) Pozitív homogenitás.** $\|\lambda A\| = \sup_{x\neq 0}\frac{\|\lambda Ax\|_v}{\|x\|_v} = \sup_{x\neq 0}\frac{|\lambda|\,\|Ax\|_v}{\|x\|_v} = |\lambda|\sup_{x\neq 0}\frac{\|Ax\|_v}{\|x\|_v} = |\lambda|\,\|A\|$ (a $|\lambda|$ kihúzható a vektornorma homogenitása és a szuprémum elé).
  - **(4) Háromszög-egyenlőtlenség.** A vektornorma szubadditivitásából minden $x$-re $\|(A+B)x\|_v = \|Ax + Bx\|_v \le \|Ax\|_v + \|Bx\|_v$. Osztva $\|x\|_v > 0$-val és szuprémumot véve: $\|A+B\| = \sup_{x\neq 0}\frac{\|(A+B)x\|_v}{\|x\|_v} \le \sup_{x\neq 0}\frac{\|Ax\|_v}{\|x\|_v} + \sup_{x\neq 0}\frac{\|Bx\|_v}{\|x\|_v} = \|A\| + \|B\|$ (a $\sup(f+g)\le\sup f+\sup g$ becslés).
  - **(5) Szubmultiplikativitás (a kulcs).** Legyen $A\in\mathbb{R}^{p\times m}$, $B\in\mathbb{R}^{m\times n}$, $x\neq 0$. Az illeszkedést **kétszer** alkalmazva: $$\|ABx\|_v = \|A(Bx)\|_v \;\overset{(1.)}{\le}\; \|A\|\,\|Bx\|_v \;\overset{(2.)}{\le}\; \|A\|\,\|B\|\,\|x\|_v.$$ Az 1. lépésben $Bx$ vektort nyújtja $A$ (illeszkedés $A$-ra), a 2.-ban $\|Bx\|_v \le \|B\|\,\|x\|_v$ (illeszkedés $B$-re). Osztva $\|x\|_v$-vel és szuprémumot véve $x\neq 0$-ra: $$\|AB\| = \sup_{x\neq 0}\frac{\|ABx\|_v}{\|x\|_v} \le \|A\|\,\|B\|. \qquad\square$$ *(Következmény: $\|I\| = \sup_{x\neq 0}\|x\|_v/\|x\|_v = 1$.)*

- **T01 — A gépi számok nem egyenletes elhelyezkedése** (LEVEZETÉS). Rögzítsünk egy $k$ kitevőt; a $[2^{k-1}, 2^k)$ intervallumon az $x = 2^k\cdot m$, $m = \sum_{i=1}^t m_i 2^{-i}$ alakú számokat nézzük ($m_1 = 1$ rögzített).
  - **Szomszédos távolság.** A mantissza utolsó (t-edik) bitjének súlya $2^{-t}$; ezt a $2^k$ skálázza, így két szomszédos gépi szám távolsága ezen a kitevőn $$\delta(k) = 2^k\cdot 2^{-t} = 2^{k-t}.$$ Ez az intervallumon belül **állandó** (csak $k$-tól függ).
  - **Konzisztencia-ellenőrzés (számolás).** Egy $k$ kitevőn $2^{t-1}$ pozitív gépi szám van: $m_1 = 1$ rögzített, a maradék $t-1$ bit szabad → $2^{t-1}$ kombináció. Ezek $\delta(k)$ lépésekkel fedik le a $2^{k-1}$ hosszú intervallumot, és valóban $$2^{t-1}\cdot 2^{k-t} = 2^{(t-1)+(k-t)} = 2^{k-1} = \text{az intervallum hossza}. \checkmark$$
  - **Exponenciális ritkulás + állandó relatív felbontás.** A kitevőt eggyel növelve $\delta(k+1) = 2^{(k+1)-t} = 2\,\delta(k)$: a szomszédsági távolság megduplázódik, vagyis nagy $|x|$-nél a gépi számok exponenciálisan ritkulnak (a 0 közelében sűrűk). Az **abszolút** felbontás tehát nem egyenletes. A **relatív** felbontás viszont állandó: $\delta(k)$ az intervallum hosszához ($2^{k-1}$) viszonyítva $\frac{2^{k-t}}{2^{k-1}} = 2^{1-t}$, függetlenül $k$-tól — ez éppen a gépi epszilon $\varepsilon_1 = 2^{1-t}$, és innen ered az egyenletes $\frac{|x-\mathrm{fl}(x)|}{|x|} \le \tfrac12\varepsilon_1 = \varepsilon$ kerekítési korlát.

## Kapcsolódó oldalak

- [[concepts/nummodi/hibameroek-es-hibaterjedes]] — abszolút/relatív hiba, hibaterjedés alapjai
- [[concepts/nummodi/matrixnormak]] — mátrixnorma-axiómák, indukált normák, Frobenius
- [[concepts/nummodi/kondicioszam]] — kondíciószám definíció és tulajdonságok
- [[concepts/nummodi/ler-erzekenysege]] — perturbációs becslések teljes bizonyítása, Neumann-lemma
