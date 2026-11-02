---
tags: [concept]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_Polinomok.pdf, dm2gy07.pdf, dm2gy07_Polinomok.pdf, dm2gy08.pdf, dm2gy09.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Polinomok maradékos osztása

Egységelemes integritási tartomány fölött egy polinom egyértelműen elosztható maradékosan egy olyan polinommal, amelynek főegyütthatója egység — a maradék foka az osztóénál kisebb.

## Tartalom

### A tétel

**Tétel.** Legyen $R$ egységelemes integritási tartomány, $f, g \in R[x]$, és tegyük fel, hogy $g$ főegyütthatója egység $R$-ben. Ekkor **egyértelműen léteznek** olyan $q, r \in R[x]$ polinomok, melyekre

$$f = qg + r, \qquad \deg(r) < \deg(g).$$

A $q$ polinom a maradékos osztás **hányadospolinomja**, az $r$ polinom az osztási **maradékpolinom**. A tétel az $f$ polinom $g$-vel való maradékos elosztásának egyértelmű elvégezhetőségét mondja ki.

A főegyütthatóra tett kikötés lényeges: az eljárás minden lépésben az osztó főegyütthatójával kell osztani. Test fölött ez automatikusan teljesül minden nem-nulla $g$-re, mert testben minden nem-nulla elem egység.

### Létezés

$f$ foka szerinti teljes indukció. Ha $\deg(f) < \deg(g)$, akkor $q = 0$ és $r = f$ megfelelő előállítás.

Legyen $\deg(f) = n$, $f$ főegyütthatója $f_n$, $g$ főegyütthatója $g_k$, és $n \ge k$. Legyen

$$f^*(x) = f(x) - f_n g_k^{-1} g(x) x^{n-k}.$$

Ekkor $\deg(f^*) < \deg(f)$ (a főtagok kiejtik egymást), így az indukciós feltevés használható $f^*$-ra: léteznek $q^*, r^* \in R[x]$, amikre $f^* = q^*g + r^*$. Ebből

$$f(x) = f^*(x) + f_n g_k^{-1} g(x) x^{n-k} = q^*(x)g(x) + r^*(x) + f_ng_k^{-1}g(x)x^{n-k},$$

vagyis $q = q^* + f_n g_k^{-1} x^{n-k}$ és $r = r^*$ jó választás.

### Egyértelműség

Tekintsük $f$ két megfelelő előállítását: $f = qg + r = q^*g + r^*$. Ebből

$$g(q - q^*) = r^* - r.$$

Ha a bal oldal nem $0$, akkor foka legalább $k = \deg(g)$, de a jobb oldal foka legfeljebb $k-1$. Ez csak úgy lehetséges, ha $0 = g(q-q^*) = r^* - r$, és így $q = q^*$ és $r = r^*$. $\square$

### Farkas-diák kiegészítése

A diák ugyanezt az indukciós bizonyítást $n = \deg f$ szerint adja: ha $f = 0$ vagy $n < k$, akkor $q = 0$, $r = f$; ha $n = k = 0$, akkor $r = 0$, $q = a_n b_k^{-1}$; különben $f_1 = f - g a_n b_k^{-1} x^{n-k}$-ra az indukciós feltevést alkalmazva $q = a_n b_k^{-1} x^{n-k} + q_1$, $r = r_1$ (ha $f_1 = 0$, akkor $r = 0$). **Következmény:** ha $R$ test és $f \in R[x]^*$, a $\varphi(f) = \deg(f)$ függvénnyel $R[x]$ euklideszi gyűrű.

### Feladattípusok és módszerek (gyakorlati feladatsorok, 6–8. hét)

**Típus: „osszuk el maradékosan $\mathbb{Q}$, $\mathbb{Z}$, $\mathbb{Z}_7$, $\mathbb{Z}_6$ fölött, ha lehet”.** Az osztás akkor végezhető el, ha $g$ **főegyütthatója egység** az adott gyűrűben (osztani kell vele). Így $g=3x^2-2x+1$ esetén $\mathbb{Q}$-ban és $\mathbb{Z}_7$-ben lehet ($3$ egység), $\mathbb{Z}$-ben és $\mathbb{Z}_6$-ban nem (a $3$ nem egység; $\mathbb{Z}_6$-ban nullosztó). Példák:

- $f=42x^4-7x^3+13x^2+43x-12$, $g=x^2-x+1$ (főegyüttható $1$, tehát minden gyűrűben lehet): $f=(42x^2+35x+6)g+(14x-18)$ $\mathbb{Z}$ fölött; modulo $7$ és $6$ redukálni kell.
- $f=x^3-3x^2-x-1$, $g=3x^2-2x+1$: $\mathbb{Q}$ fölött $q=\tfrac13x-\tfrac79$, $r=-\tfrac{26}{9}x-\tfrac29$; $\mathbb{Z}_7$ fölött $q=5x$ ($=-2x$), $r=x-1$.
- $f=x^3+x^2+3x+2$, $g=2x^2+4$ $\mathbb{Z}_7$ fölött: $q=4x+4$ ($=-3x-3$), $r=x$ (ellenőrzés: $(2x^2+4)(4x+4)\equiv x^3+x^2+2x+2$, és $+x$ adja $f$-et).

**Menet:** a hányados főtagját a főegyütthatók hányadosa adja, kivonás, ismétlés, amíg a maradék foka kisebb $\deg g$-nél. Ha $\deg f<\deg g$, a hányados $0$, a maradék $f$.

**Típus: paraméterek osztáshoz.** $x^3+px+q$ osztható $x^2+mx-1$-gyel $\mathbb{C}$ fölött: $x^3+px+q=(x^2+mx-1)(x-m)+(p+m^2+1)x+(q-m)$, tehát $m$ szabadon választható, és $p=-(m^2+1)$, $q=m$. — $x^4+3x^2+ax+b$ osztható $x^2-2ax+2$-vel: az osztás maradéka $(8a^3-a)x+(b-2-8a^2)$, ennek eltűnése $a(8a^2-1)=0$, $b=2+8a^2$. $\mathbb{Q}$ fölött csak $a=0$, $b=2$; $\mathbb{R}$ és $\mathbb{C}$ fölött még $a=\pm\tfrac{\sqrt2}{4}$, $b=3$.

### Feladattípusok és módszerek: számolás $\mathbb{Z}_p[x]$-ben modulo $m(x)$ (2024. 9. sorozat)

Cél: egy polinomkifejezést redukálni egy rögzített $m$ polinom szerint, azaz a $\mathbb{Z}_p[x]/(m)$ gyűrűben (testben, ha $m$ irreducibilis) számolni. Módszer: (i) az együtthatókat minden lépésben $\bmod\ p$ redukáljuk; (ii) $m$-mel való osztást **minél később, de mindig a fok csökkentésére** végezzük — részeredményeket is lehet redukálni, mert a maradékosztályok között a műveletek reprezentánsfüggetlenek; (iii) $\mathbb{Z}_p$-ben $(u+v)^p = u^p+v^p$, így pl. $(f-g)^3 = f^3 - g^3$ $\mathbb{Z}_3$ fölött és $(f-g)^8 = f^8 - g^8$ $\mathbb{Z}_2$ fölött.

*Példa* ($\mathbb{Z}_3[x]$, $m = x^2+2x+2$, $f = x^2+2$, $g = 2x^2+4x+1 = 2x^2+x+1$, $h = x^3+x+4 = x^3+x+1$):

- $(f+g)^2 \bmod m$: $f+g = 3x^2+x+3 = x$, így $x^2 = m - 2x - 2 \equiv x+1$;
- $g\cdot h \bmod m$: $g = 2x^2+4x+4 = 2m$, tehát $g \equiv 0$ és a szorzat $0$ — érdemes először megnézni, hogy valamelyik tényező nem többszöröse-e $m$-nek;
- $(f-g)(g-h)(f-h) \bmod m = 2x+1$;
- $(f-g)^3 \bmod m = 2x+1$.

*Példa* ($\mathbb{Z}_5[x]$, $m = x^3+1$, $f=x^2+x+1$, $g=3x^2+4x+1$, $h=x^3+x+4$): $(f+g)^2 \equiv x^2+4x+4$; $fg+gh+fh \equiv 4x+1$; $(f-g)(g-h)(f-h) \equiv x+3$.

*Példa* ($\mathbb{Z}_2[x]$, $m = x^3+x+1$, $f=x^5+x+1$, $g=x^5+x^2+1$, $h=x^3+x$): $(f+g)^2 \equiv x$; $fg+gh+fh \equiv x^2+1$; $(f-g)(g-h)(f-h) \equiv x^2+1$; $(f-g)^8 \equiv x^2+x$.

**Tipikus hibák.** Az együtthatók $\bmod\ p$ redukálásának kihagyása (a $-2x-2$ nem $x+1$ $\mathbb{Z}_3$ fölött, amíg nem redukáltuk); $\mathbb{Z}_2$-ben a $-1 = 1$ miatt az előjelek elnézése; az $m$ főegyütthatójának figyelmen kívül hagyása nem főpolinom $m$-nél. A multiplikatív inverzek számításához lásd [[concepts/dimatii/veges-testek]].

## Kapocs

- [[concepts/dimatii/polinom-foka]] — a maradék fokára tett kikötés az egyértelműség kulcsa
- [[concepts/dimatii/integritasi-tartomany]] — a tétel feltétele
- [[concepts/dimatii/horner-elrendezes]] — az $(x-c)$-vel való maradékos osztás gyakorlati elvégzése
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a tétel közvetlen következményei
- [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]] — a maradékos osztásra épülő eljárás
- [[concepts/dimatii/lagrange-interpolacio]] — további $\mathbb{Z}_p[x]$ feladattípus: interpoláció
