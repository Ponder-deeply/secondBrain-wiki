---
tags: [concept]
sources: [DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Teljes maradékrendszer

Minden maradékosztályból pontosan egy reprezentáns — a modulo $m$ számolás „névsora”.

## Tartalom

**Definíció.** Egy rögzített $m$ modulus esetén, ha minden maradékosztályból pontosan egy elemet kiveszünk, akkor az így kapott számok **teljes maradékrendszert** alkotnak modulo $m$.

**Példa.** $\{33, -5, 11, -11, -8\}$ teljes maradékrendszer modulo $5$ (a maradékok rendre $3, 0, 1, 4, 2$).

Gyakori választások teljes maradékrendszerre:

- **legkisebb nemnegatív maradékok:** $\{0, 1, \dots, m-1\}$;
- **legkisebb abszolútértékű maradékok:**
  $$\left\{0, \pm 1, \dots, \pm\tfrac{m-1}{2}\right\}, \ \text{ha } 2 \nmid m; \qquad \left\{0, \pm 1, \dots, \pm\tfrac{m-2}{2}, \tfrac{m}{2}\right\}, \ \text{ha } 2 \mid m.$$

Egy teljes maradékrendszer mérete mindig $m$.

### Eltolás és szorzás megőrzi

**Lemma.** Legyen $m > 1$ egész, $a_1, a_2, \dots, a_m$ teljes maradékrendszer modulo $m$. Ekkor minden $a, b$ egészre, melyre $(a,m) = 1$, az
$$a\cdot a_1 + b,\ a\cdot a_2 + b,\ \dots,\ a\cdot a_m + b$$
számok szintén teljes maradékrendszert alkotnak.

**Bizonyítás.** $i \neq j$ esetén $aa_i + b \equiv aa_j + b \pmod m \iff aa_i \equiv aa_j \pmod m$. Mivel $(a,m) = 1$, a [[concepts/dimatii/kongruencia]] egyszerűsítési szabálya szerint $a$-val egyszerűsíthetünk: $a_i \equiv a_j \pmod m$, ami ellentmondás. Tehát a felsorolt $m$ szám páronként inkongruens, így teljes maradékrendszert alkot. $\square$

Ez a lemma a [[concepts/dimatii/euler-fermat-tetel]] bizonyításának kulcsa; ugyanez a gondolat működik a [[concepts/dimatii/redukalt-maradekrendszer]]re is.

**Megjegyzés (Farkas-diák).** A lemma a diák „omnibusz” tétele: $\{a_i\}$ TMR, $\{b_j\}$ RMR modulo $m$, $(c,m)=1$, $d\in\mathbb{Z}$ $\Rightarrow$ $\{ca_i + d\}$ TMR és $\{cb_j\}$ RMR. Bizonyítás indirekt: ha $ca_i + d \equiv ca_j + d$, akkor $(c,m)=1$ miatt $a_i \equiv a_j$, ellentmondás, és pontosan $m$ elem van; az RMR-nél $(c,m)=1$ és $(b_i,m)=1 \Rightarrow (cb_i,m)=1$.

## Kapocs

- [[concepts/dimatii/maradekosztaly]] — a reprezentált objektumok
- [[concepts/dimatii/redukalt-maradekrendszer]] — a relatív prím osztályokra szűkített változat
- [[concepts/dimatii/kongruencia]] — az egyszerűsítési szabály
- [[concepts/dimatii/euler-fermat-tetel]] — a lemma alkalmazása
