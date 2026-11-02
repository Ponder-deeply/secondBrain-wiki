---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Felbontási test

Egy $K$ feletti $f$ polinom felbontási teste a $K$ legszűkebb olyan bővítése, amelyben $f$-nek multiplicitással számolva pontosan $\deg f$ gyöke van; létezik, és izomorfizmus erejéig egyértelmű.

## Tartalom

### Kiindulás

Ha $\alpha$ gyöke az $f \in K[x]$ irreducibilis polinomnak, akkor az $f$ szerinti faktorgyűrűben az $[x]$ maradékosztály is gyöke $f$-nek: $f([x]) = [a_0] + [a_1][x] + \dots + [a_n][x]^n = [f] = [0]$. A $K(\alpha)$ egyszerű algebrai bővítés tehát épp az $f$ egy gyökének hozzávételével keletkezik (lásd [[concepts/dimatii/egyszeru-testbovites]]).

**Példa.** $f(x) = x^2 + x + 2 \in \mathbb{Z}_3[x]$: $f(0) = -1$, $f(1) = 1$, $f(-1) = -1$, így nincs gyöke, másodfokú lévén irreducibilis. Legyen $u = [x]$ az $f$ egy gyöke; $\mathbb{Z}_3/\langle f \rangle = \mathbb{Z}_3(u)$ bázisa $\{1, u\}$, elemei $0, 1, 2, u, u+1, u+2, 2u, 2u+1, 2u+2$. Itt $2u+2$ is gyöke $f$-nek:

$$f(2u+2) = 4u^2 + 8u + 4 + 2u + 2 + 2 = 4(u^2+u+2) + 6u = 0.$$

A bővítést $2u+2$-vel végezve algebrai szempontból ugyanazt a testet kapjuk.

### Egyszerű bővítések izomorfiája

**Tétel.** Ha $\alpha$ és $\beta$ gyöke a $K$ felett irreducibilis $f \in K[x]$ polinomnak, akkor $K(\alpha) \cong K(\beta)$; az izomorfizmus $\alpha$-t $\beta$-ba viszi, $K$ elemeit fixen hagyja.

### Definíció

Legyen $K$ test, $f \in K[x]$, $\deg f = n > 0$. $K$-nak az a legszűkebb bővítése, amelyben $f$-nek multiplicitással számolva pontosan $n$ gyöke van, az $f$ polinom **$K$ feletti felbontási teste**.

### Létezés és egyértelműség

**Tétel.** Legyen $K$ test, $f \in K[x]$, $\deg f = n > 0$. Létezik $f$-nek $K$ feletti felbontási teste, és bármely két ilyen izomorf azon leképezés mellett, amely $K$ elemeit önmagukba, $f$ gyökeit egymásba képezi. (A diák ezt az előző kettő — az izomorfiatétel és a gyökhozzávétel — következményeként mondja ki; bizonyítást nem ad.)

**Következmény.** Test feletti polinom felbontási teste izomorfizmustól eltekintve egyértelműen létezik.

### Alkalmazás

A véges testek tárgyalásában az $x^q - x$ felbontási teste adja a $q$ elemű testet; lásd [[concepts/dimatii/veges-testek-szerkezete]].

## Kapocs

- [[concepts/dimatii/egyszeru-testbovites]] — a felbontási test egyszerű bővítések iterálásával áll elő
- [[concepts/dimatii/testbovites-es-primresztest]] — a bővítés fogalma, fokszámtétel
- [[concepts/dimatii/algebrai-elem-es-minimalpolinom]] — az irreducibilis polinom mint minimálpolinom
- [[concepts/dimatii/irreducibilis-polinom]] — a bővítés bemenete
- [[concepts/dimatii/veges-testek-szerkezete]] — a $q$ elemű test mint $x^q-x$ felbontási teste
- [[concepts/dimatii/veges-testek]] — a faktorgyűrűs konstrukció
