---
tags: [concept, dimatii/polinomok]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf]
derivation: source
updated: 2026-09-08
---

# Polinom algebrai deriváltja

Az algebrai deriválás tetszőleges gyűrű fölött, tisztán az együtthatókból, határérték nélkül definiált művelet, amely az analízisből ismert derivált formális szabályait teljesíti.

## Tartalom

### Definíció

Legyen $R$ gyűrű. Az $f(x) = f_nx^n + f_{n-1}x^{n-1} + \dots + f_2x^2 + f_1x + f_0 \in R[x]$ ($f_n \neq 0$) polinom **algebrai deriváltja** az

$$f'(x) = nf_nx^{n-1} + (n-1)f_{n-1}x^{n-2} + \dots + 2f_2x + f_1 \in R[x]$$

polinom.

Itt $kf_k = \underbrace{f_k + f_k + \dots + f_k}_{k \text{ db}}$ — erre azért van szükség, mert $k \in \mathbb{N}^+$, de általában $k \notin R$, tehát a $k$-val való szorzás nem $R$-beli művelet, hanem ismételt összeadás.

**Segédállítás.** Legyen $R$ gyűrű, $a, b \in R$ és $n \in \mathbb{N}^+$. Ekkor $(na)b = n(ab) = a(nb)$, hiszen

$$(a + a + \dots + a)b = ab + ab + \dots + ab = a(b + b + \dots + b).$$

### A deriválás tulajdonságai

**Állítás.** Ha $R$ egységelemes integritási tartomány, akkor az $f \mapsto f'$ algebrai deriválás rendelkezik a következő tulajdonságokkal:

1. konstans polinom deriváltja a nullpolinom;
2. az $x$ polinom deriváltja az egységelem;
3. $(f+g)' = f' + g'$ minden $f, g \in R[x]$ esetén (**additivitás**);
4. $(fg)' = f'g + fg'$ minden $f, g \in R[x]$ esetén (**szorzat differenciálási szabálya**).

**Megjegyzés (jellemzés).** Megfordítva: ha egy $R$ egységelemes integritási tartomány esetén egy $f \mapsto f'$, $R[x]$-et önmagába képező leképezés rendelkezik az előző négy tulajdonsággal, akkor az az algebrai deriválás. A négy tulajdonság tehát teljes jellemzést ad.

### A gyöktényező hatványainak deriváltja

**Állítás.** Ha $R$ egységelemes integritási tartomány, $c \in R$ és $n \in \mathbb{N}^+$, akkor

$$\big((x-c)^n\big)' = n(x-c)^{n-1}.$$

*Bizonyítás.* $n$ szerinti teljes indukció. $n = 1$ esetén $(x-c)' = 1 = 1\cdot(x-c)^0$. Tegyük fel, hogy $\big((x-c)^k\big)' = k(x-c)^{k-1}$. Ekkor a szorzatszabállyal

$$\big((x-c)^{k+1}\big)' = \big((x-c)^k(x-c)\big)' = k(x-c)^{k-1}(x-c) + (x-c)^k\cdot 1 = (k+1)(x-c)^k. \quad \square$$

### Karakterisztika és az $n\cdot r = 0$ feltétel

**Állítás.** Ha $R$ integritási tartomány, $\mathrm{char}(R) = p$, és $0 \neq r \in R$, akkor

$$n\cdot r = 0 \iff p \mid n.$$

Ez az állítás a multiplicitás és a derivált kapcsolatában döntő: pontosan akkor „vész el” egy tényező a deriváláskor, ha a karakterisztika osztja a multiplicitást.

## Kapocs

- [[concepts/dimatii/polinomgyuru]] — a deriválás $R[x]$-et önmagába képezi
- [[concepts/dimatii/gyok-multiplicitasa]] — a derivált fő alkalmazása: a többszörös gyökök felismerése
- [[concepts/dimatii/gyuru]] — a karakterisztika fogalma
