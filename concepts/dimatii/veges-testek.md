---
tags: [concept]
sources: [DimatIIEa07.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy09.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Véges testek

Minden $p$ prím és $n$ pozitív egész esetén létezik $p^n$ elemű test, amit a $\mathbb{Z}_p[x]$ polinomgyűrűnek egy $n$-ed fokú irreducibilis polinom szerinti maradékosztályaiként állítunk elő; véges test elemszáma mindig prímhatvány, és az azonos elemszámú testek izomorfak.

## Tartalom

### A konstrukció

Tekintsük valamely $p$ prímre a $\mathbb{Z}_p$ testet, továbbá egy $f(x) \in \mathbb{Z}_p[x]$ felbonthatatlan főpolinomot. Vezessük be a

$$g(x) \equiv h(x) \pmod{f(x)}, \quad \text{ha} \quad f(x) \mid \big(g(x) - h(x)\big)$$

relációt. Ez ekvivalenciareláció, ezért meghatároz egy osztályozást $\mathbb{Z}_p[x]$-en.

### Az osztályok száma

Minden osztálynak van $\deg(f)$-nél alacsonyabb fokú **reprezentánsa** (osszuk el maradékosan az osztály bármely elemét $f$-fel), és ha $\deg(g), \deg(h) < \deg(f)$, továbbá $g$ és $h$ ugyanabban az osztályban van, akkor egyenlőek (különbségük foka kisebb $\deg(f)$-nél, de osztható $f$-fel, tehát nulla).

Tehát $\deg(f) = n$ esetén bijekciót létesíthetünk az $n$-nél kisebb fokú polinomok és az osztályok között — így **$p^n$ darab osztály van** (mindegyik együttható $p$-féle lehet).

### A műveletek

Az osztályok között a természetes módon értelmezhetjük a műveleteket: az $n$-nél alacsonyabb fokú reprezentánsokkal végezzük őket, és ha a szorzat foka nem kisebb, mint $n$, akkor az $f(x)$-szel vett osztási maradékot vesszük.

**Multiplikatív inverz.** Ha $f \nmid g$, akkor a bővített euklideszi algoritmus alapján léteznek $u, v$ polinomok, amelyekre

$$d(x) = u(x)f(x) + v(x)g(x).$$

Mivel $f(x)$ felbonthatatlan, ezért $d(x) = d$ konstans polinom, így $\frac{v(x)}{d}$ multiplikatív inverze lesz $g(x)$-nek.

**Tétel.** Az ekvivalenciaosztályok halmaza a rajta értelmezett összeadással és szorzással **testet alkot**.

### Következmények

- **Tetszőleges $p$ prím és $n$ pozitív egész esetén létezik $p^n$ elemű test**, mert létezik $n$-ed fokú felbonthatatlan polinom $\mathbb{Z}_p$-ben.
- **Véges test elemszáma prímhatvány**, továbbá az azonos elemszámú testek **izomorfak** — ezért beszélhetünk *a* $q$ elemű testről, jelölése $\mathbb{F}_q$.

### Példa: $\mathbb{F}_9 = \mathbb{Z}_3[x]/(x^2+1)$

Tekintsük az $x^2 + 1 \in \mathbb{Z}_3[x]$ felbonthatatlan polinomot (nincs gyöke $\mathbb{Z}_3$-ban: $0^2+1 = 1$, $(\pm1)^2+1 = 2$, és másodfokú lévén ez elég az irreducibilitáshoz). A legfeljebb elsőfokú polinomok, azaz a kilenc osztály reprezentánsai:

$$0,\ 1,\ 2,\ x,\ x+1,\ x+2,\ 2x,\ 2x+1,\ 2x+2.$$

Az összeadás komponensenként, $\mathbb{Z}_3$-ban történik, például

$$(2x+2) + (x+1) = 3x + 3 \overset{\mathbb{Z}_3}{=} x.$$

A szorzásnál a szorzat után $x^2+1$-gyel maradékosan osztunk, például

$$(2x+2)(2x+1) = 4x^2 + 6x + 2 \overset{\mathbb{Z}_3}{=} x^2 + 2 = (x^2+1) + 1 \equiv 1.$$

Vagyis $2x+2$ és $2x+1$ egymás multiplikatív inverzei $\mathbb{F}_9$-ben.

### Karakterisztika és prímrészteszt

Véges test karakterisztikája prímszám, és prímrészteszte izomorf $\mathbb{Z}_p$-vel; lásd [[concepts/dimatii/testbovites-es-primresztest]]. A fenti konstrukció a $\mathbb{Z}_p$ egyszerű bővítése az $f$ gyökével ([[concepts/dimatii/egyszeru-testbovites]]).

### Feladattípusok és módszerek: műveletek $\mathbb{F}_9$, $\mathbb{F}_{27}$, $\mathbb{F}_{125}$ testekben (2024. 9. sorozat)

**Műveleti táblák $\mathbb{F}_9$-ben.** $f=x^2+2x+2\in\mathbb{Z}_3[x]$ irreducibilis (nincs gyöke: $f(0)=2$, $f(1)=5=2$, $f(2)=10=1$). Elemek: $0,1,2,x,x+1,x+2,2x,2x+1,2x+2$. Az összeadás komponensenként $\bmod\ 3$. A szorzáshoz a $x^2\equiv -2x-2=x+1$ szabály kell; legkényelmesebb a **primitív elem hatványtáblája**: $x$ itt generátor ($\mathbb{F}_9^*$ ciklikus, rendje 8):

$x^1=x,\ x^2=x+1,\ x^3=2x+1,\ x^4=2,\ x^5=2x,\ x^6=2x+2,\ x^7=x+2,\ x^8=1.$

Ebből szorzás: kitevők összeadása $\bmod\ 8$ (pl. $(x+1)(2x+2)=x^2\cdot x^6=x^8=1$), inverz: $x^{-k}=x^{8-k}$. A teljes szorzótábla soraiból néhány: $x\cdot x=x+1$, $x\cdot(x+1)=2x+1$, $(x+1)(x+2)=x^2x^7=x^9=x$. A táblázatot érdemes a hatványtáblából felírni, nem soronként számolni.

*Gyökök $\mathbb{F}_9$-ben.* $z^2+z+2=0$: a kilenc elem behelyettesítésével (vagy a hatványtáblával) a megoldások $z=x+2$ és $z=2x$ (Viète-ellenőrzés: összegük $(x+2)+2x=3x+2=2=-1$, szorzatuk $(x+2)\cdot2x=2x^2+4x\equiv2(x+1)+x=3x+2=2$, ami a konstans tag). Másodfokú egyenletnek testben legfeljebb két gyöke van, itt kettő is van, bár $\mathbb{Z}_3$-ban nincs.

**Számolás $\mathbb{F}_{125}=\mathbb{Z}_5[x]/(x^3+x+1)$-ben.** $a=x$, $b=x^2+1$, $c=4x+1$ esetén (maradékos osztással $x^3\equiv -x-1$, inverzek a bővített euklideszi algoritmussal): $abc=x+4$; $(a+b+c)^2=3x^2+4x+4$; $a^{-1}=4x^2+4$ (ellenőrzés: $x(4x^2+4)=4x^3+4x\equiv 4(-1)=1$); $b^{-1}=4x$; $c^{-1}=2x^2+2x+4$; $a/b=4x^2$; $(b+c)^{-1}=x+1$; $(a+b)/(b+c)=2x^2+x$.

**Számolás $\mathbb{F}_{27}=\mathbb{Z}_3[x]/(x^3+x^2+2)$-ben** ($x^3+x^2+2$ gyökmentes harmadfokú, tehát irreducibilis). $a=x^2$, $b=x^2+2$, $c=2x+1$: $abc=2x^2+2x+2$; $(a+b+c)^2=x+1$; $a^{-1}=x+1$ ($x^2(x+1)=x^3+x^2=-2=1$); $b^{-1}=2x^2+2x+2$; $c^{-1}=x^2+2x+2$; $a/b=2x^2+2x$; $(b+c)^{-1}=x^2+1$; $(a+b)/(b+c)=2x$.

**Az inverz keresése** két módon: (i) bővített euklideszi algoritmus $g$ és $f$ között ($ug+vf=1\Rightarrow g^{-1}=u$, lásd [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]]); (ii) próbálgatás: az $x^2\equiv\ldots$ szabállyal felírt szorzat $=1$ egyenletrendszer az $u$ együtthatóira. A hányados $a/b=a\cdot b^{-1}$.

**Tipikus hibák.** Az $x^n$-t nem redukálni az $f$-fel való osztással (a $\mathbb{F}_{125}$-ben a szorzat foka akár 4); a $\mathbb{Z}_p$-beli együtthatók redukálásának kihagyása; reducibilis modulust használni (ekkor a gyűrű nem test, a nullosztóknak nincs inverze); az $\mathbb{F}_9$ és a $\mathbb{Z}_9$ összekeverése.

## Kapocs

- [[concepts/dimatii/veges-testek-szerkezete]] — elemszám, $a^q=a$, $x^q-x$ felbontási teste, egyértelműség, résztestek, ciklikus $\mathbb{F}_q^*$
- [[concepts/dimatii/felbontasi-test]] — a felbontási test fogalma
- [[concepts/dimatii/irreducibilis-polinom]] — a konstrukció bemenete: felbonthatatlan főpolinom
- [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]] — a multiplikatív inverz kiszámítása
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a műveletek elvégzésének technikai alapja
- [[concepts/dimatii/test]] — az eredményül kapott struktúra
- [[concepts/dimatii/gyuru]] — a faktorizált polinomgyűrű
- [[concepts/dimatii/testbovites-es-primresztest]] — résztest, bővítés, prímrészteszt
- [[concepts/dimatii/egyszeru-testbovites]] — $K[x]/\langle f \rangle$ mint a gyökkel való bővítés
