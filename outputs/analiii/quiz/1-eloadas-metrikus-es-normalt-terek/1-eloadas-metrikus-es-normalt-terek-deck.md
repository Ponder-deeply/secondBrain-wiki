#flashcards/analiii/1-eloadas-metrikus-es-normalt-terek

## Mi a fordított háromszög-egyenlőtlenség metrikus térben, és hogyan kapjuk meg?
?
$\rho(x,y)\ge|\rho(x,z)-\rho(y,z)|$. A háromszög-egyenlőtlenség kétszeri felírásából kapjuk.
---

## Ha $(X,\rho)$ metrikus tér és $f:Y\to X$, mikor metrika $Y$-on a $\sigma(x,y)=\rho(f(x),f(y))$ függvény (visszahúzott metrika)?
?
Ha $f$ injektív (ennél többet, bijektivitást nem kell megkövetelni). Például $|f(x)-f(y)|$ metrika $\mathbb R$-en minden szigorúan monoton $f$-re.
---

## Miért nem metrika $\mathbb R$-en a $\rho(x,y)=(x-y)^2$ függvény?
?
Mert sérül a háromszög-egyenlőtlenség: $\rho(0,2)=4>1+1=\rho(0,1)+\rho(1,2)$.
---

## Milyen két tulajdonság jellemzi a normából származó metrikákat?
?
Az eltolásinvariancia és az, hogy $\rho(\lambda x,\lambda y)=|\lambda|\rho(x,y)$. Ez megfordítva is igaz. Például a diszkrét metrika ezért nem származik normából.
---

## Milyen alakú egy egydimenziós valós vektortér összes normája, és miért?
?
$\|x\|=\alpha|x|$ alakú, ahol $\alpha=\|1\|>0$. Ez a homogenitásból következik: $\|x\|=\|x\cdot1\|=|x|\,\|1\|$.
---

## Miért folytonos függvény a norma $X\to\mathbb R$?
?
Mert $\bigl|\|x\|-\|y\|\bigr|\le\|x-y\|$, azaz a norma 1-Lipschitz.
---

## Adja meg a $H$ halmaz lezártjának egyenértékű leírásait!
?
$\operatorname{cl}H=H\cup\partial H=H\cup H'$. Ez a legszűkebb $H$-t tartalmazó zárt halmaz, vagyis a $H$-t tartalmazó zárt halmazok metszete. Elemei az érintkezési pontok: azok a $b$ pontok, amelyek minden $K(b)$ környezetére $K(b)\cap H\neq\emptyset$.
---

## Melyek az $A\subset X$ altér, $(A,\rho|_{A\times A})$ nyílt halmazai?
?
Pontosan az $U\cap A$ alakú halmazok, ahol $U$ nyílt $X$-ben. Ennek oka, hogy $K^A_r(a)=K_r(a)\cap A$.
---
