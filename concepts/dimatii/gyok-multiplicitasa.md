---
tags: [concept]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy08.pdf, dm2gy08_Polinomok.pdf, dm2gy09_Polinomok.pdf, dm2gy11_Polinomok.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
---

# Gyök multiplicitása

Egy gyök multiplicitása az a legnagyobb kitevő, amellyel a gyöktényező még kiemelhető; a derivált a multiplicitást — a karakterisztika által megengedett mértékben — pontosan eggyel csökkenti.

## Tartalom

### Definíció

Legyen $R$ egységelemes integritási tartomány, $0 \neq f \in R[x]$ és $n \in \mathbb{N}^+$. Azt mondjuk, hogy $c \in R$ az $f$ egy **$n$-szeres gyöke**, ha

$$(x-c)^n \mid f, \qquad (x-c)^{n+1} \nmid f.$$

Ekkor $c$ **multiplicitása** $n$.

**Megjegyzés.** A definíció azzal ekvivalens, hogy $f(x) = (x-c)^ng(x)$, ahol $c$ **nem** gyöke $g$-nek.

### A derivált és a multiplicitás

**Tétel.** Legyen $R$ egységelemes integritási tartomány, $f \in R[x]$, $n \in \mathbb{N}^+$, és legyen $c \in R$ az $f$ egy $n$-szeres gyöke. Ekkor $c$ az $f'$-nek legalább $(n-1)$-szeres gyöke, és ha $\mathrm{char}(R) \nmid n$, akkor **pontosan** $(n-1)$-szeres gyöke.

*Bizonyítás.* Legyen $f(x) = (x-c)^ng(x)$, ahol $c$ nem gyöke $g$-nek. A szorzatszabállyal

$$f'(x) = n(x-c)^{n-1}g(x) + (x-c)^ng'(x) = (x-c)^{n-1}\big(ng(x) + (x-c)g'(x)\big).$$

Tehát $c$ valóban legalább $(n-1)$-szeres gyöke $f'$-nek. Pontosan $(n-1)$-szeres akkor lesz, ha $c$ nem gyöke a zárójeles tényezőnek:

$$ng(c) + (c-c)g'(c) = ng(c) + 0\cdot g'(c) = ng(c).$$

Ez pedig teljesül, ha $\mathrm{char}(R) \nmid n$, hiszen ekkor $g(c) \neq 0$ miatt $ng(c) \neq 0$. $\square$

### Ellenpélda: amikor a karakterisztika osztja a multiplicitást

Legyen $f(x) = x^4 - x \in \mathbb{Z}_3[x]$. Ekkor $1$ a $3$-szoros gyöke $f$-nek, mert

$$f(x) = x(x^3-1) \overset{\mathbb{Z}_3}{=} x(x^3 - 3x^2 + 3x - 1) = x(x-1)^3.$$

A derivált viszont

$$f'(x) = 4x^3 - 1 \overset{\mathbb{Z}_3}{=} x^3 - 3x^2 + 3x - 1 = (x-1)^3,$$

tehát $1$ **továbbra is** $3$-szoros gyöke $f'$-nek: a multiplicitás nem csökkent, mert $\mathrm{char}(\mathbb{Z}_3) = 3 \mid 3$.

### Farkas-diák kiegészítése

Jelölés: $(x-c)^n \,\|\, f(x)$ jelenti, hogy $(x-c)^n \mid f$ és $(x-c)^{n+1} \nmid f$. A tétel bizonyításában $f = (x-c)^n g$, $f' = (x-c)^{n-1}\big((x-c)g' + ng\big)$, és a zárójeles tényező $c$-ben $ng(c) = g(c) + \ldots + g(c)$ ($n$ tag); ez $\mathrm{char}(R) \nmid n$ esetén sosem $0$. A megfordítás nem igaz: $f = x^n + 1$, $f' = nx^{n-1}$ esetén $0$ az $f'$-nek $(n-1)$-szeres gyöke, $f$-nek viszont nem gyöke.

### Feladattípusok és módszerek: többszörös gyökök keresése (gyakorlati feladatsorok, 8. hét)

**Módszer A: ismételt Horner-osztás.** Ha $f(c)=0$, osszuk $x-c$-vel; a hányadosnak megint megnézzük $c$-nél az értékét, és ezt ismételjük, amíg a maradék nem $0$. A sikeres osztások száma a multiplicitás. *Példa:* $x^5-5x^4+7x^3-2x^2+4x-8\in\mathbb{Z}[x]$, $c=2$: a sorok $1,-3,1,0,4\mid0$; $1,-1,-1,-2\mid0$; $1,1,1\mid0$; $1,3\mid7\ne0$ — tehát a $2$ **háromszoros** gyök, $f=(x-2)^3(x^2+x+1)$.

**Módszer B: $f$ és $f'$ közös gyökei.** A többszörös gyökök az $\mathrm{lnko}(f,f')$ gyökei (ha a karakterisztika nem osztja a multiplicitást). Gyakorlás:

- $\mathbb{Q}$ fölött $x^4+3x^3+4x^2+3x+1=(x+1)^2(x^2+x+1)$: $-1$ kétszeres gyök.
- $\mathbb{Q}$ fölött $x^5+2x^4+x^3+x^2+2x+1=(x+1)^3(x^2-x+1)$: $-1$ háromszoros gyök.
- $\mathbb{Z}_3$ fölött $x^5+x^4+1=(x-1)^2(x^3-x+1)$: $1$ kétszeres gyök (a harmadfokú tényezőnek nincs gyöke).
- $\mathbb{Z}_3$ fölött $x^6+x^5+x^2+2=(x+1)^3(x^3+x^2-1)$: $-1\equiv2$ háromszoros gyök.
- $\mathbb{Z}_3$ fölött $x^8+x^7+x^6+x^5+2x^4+2x^3+x^2=x^2(x-1)^3(x^3+x^2+x-1)$: $0$ kétszeres, $1$ háromszoros gyök.

**Tipikus hiba (karakterisztika):** $\mathbb{Z}_3$ fölött egy háromszoros gyök a deriváltnak is legalább háromszoros gyöke (pl. $((x+1)^3)'=3(x+1)^2=0$), ezért az „$f'$-ben eggyel kisebb a multiplicitás” szabály nem használható; az $\mathrm{lnko}(f,f')$ itt túl nagy lehet — ilyenkor a Horner-osztás (A) a megbízható módszer. Lásd az ellenpéldát fent.

**Típus: paraméter a multiplicitáshoz.** „$-1$ legalább kétszeres gyöke $x^5-ax^2-ax+1\in\mathbb{R}[x]$-nek” $\Leftrightarrow f(-1)=0$ és $f'(-1)=0$ ($\mathbb{R}$ fölött $\mathrm{char}=0$). $f(-1)=-1-a+a+1=0$ minden $a$-ra; $f'(x)=5x^4-2ax-a$, $f'(-1)=5+a=0$, tehát $a=-5$ (ellenőrzés: $x^5+5x^2+5x+1$ értéke $-1$-nél $0$).

### Feladattípusok és módszerek: $\mathbb{C}[x]$ többszörös gyökei és az „egyszeres gyökű társ” (2020. 9. és 11. feladatsor)

**Típus 1: többszörös gyökök $\mathbb{C}[x]$-ben.** Számoljuk ki $d=\mathrm{lnko}(f,f')$-t ($\mathbb{C}$ fölött $\mathrm{char}=0$, így az $f'$-ben eggyel kisebb a multiplicitás); $d$ gyökei $f$ többszörös gyökei, multiplicitásuk $d$-ben eggyel kisebb, mint $f$-ben. Példák (az algoritmussal számolva):

- $f=x^6-6x^4-4x^3+9x^2+12x+4$: $d=x^4+x^3-3x^2-5x-2=(x+1)^3(x-2)$, így $f=(x+1)^4(x-2)^2$.
- $f=x^5-10x^3-20x^2-15x-4$: $d=x^3+3x^2+3x+1=(x+1)^3$, így $f=(x+1)^4(x-4)$.

**Típus 2: egyszeres gyökű polinom ugyanazokkal a gyökökkel.** $f/d$-nek ugyanazok a gyökei, mint $f$-nek, de mind egyszeres. Példák: $f=x^6-15x^4+8x^3+51x^2-72x+27$: $d=x^3+x^2-5x+3=(x-1)^2(x+3)$, $f/d=x^3-x^2-9x+9=(x-1)(x-3)(x+3)$ (tehát $f=(x-1)^3(x+3)^2(x-3)$); $f=x^5-6x^4+16x^3-24x^2+20x-8$: $d=x^2-2x+2$, $f/d=x^3-4x^2+6x-4=(x-2)(x^2-2x+2)$, és $f=(x-2)(x^2-2x+2)^2$ (a $1\pm i$ kétszeres gyök).

**Típus 3: racionális többszörös gyökök $\mathbb{Z}[x]$-ben.** $4x^6-8x^5-3x^4-11x^3+18x^2+28x+8$: racionális gyökjelöltek $\pm\{1,2,4,8\}/\{1,2,4\}$; a Horner-táblás ismételt osztás a $2$ és a $-\tfrac12$ kétszeres gyöknek találja, és $f=(x-2)^2(2x+1)^2(x^2+x+2)$, ahol az utolsó tényezőnek nincs valós gyöke (diszkrimináns $-7$). Lásd [[concepts/dimatii/racionalis-gyokteszt]].

**Tipikus hibák.** A $d$ gyökeit „a többszörös gyökök multiplicitásaként” olvasni (a $d$-beli kitevő eggyel kisebb); a $-\tfrac12$ gyöknél a $2x+1$ tényezőt $x+\tfrac12$-ként felírva a főegyüttható $4=2^2$ elveszik.

## Kapocs

- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — az egyszeres gyök és a gyöktényező kiemelése
- [[concepts/dimatii/polinom-algebrai-derivaltja]] — a tétel eszköze
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a gyöktényező-hatványok kiemelésének technikai alapja
