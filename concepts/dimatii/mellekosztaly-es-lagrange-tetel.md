---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Mellékosztály, index és Lagrange-tétel

Egy részcsoport szerinti mellékosztályok a csoport elemeinek osztályozását adják; ebből következik, hogy véges csoportban a részcsoport rendje osztja a csoport rendjét (Lagrange-tétel).

## Tartalom

### Az ekvivalenciareláció

Legyen $G$ csoport, $H \le G$, és legyen $a \sim b$, ha $ab^{-1} \in H$ valamely $a, b \in G$-re. Ez **ekvivalenciareláció**:

1. reflexív: $aa^{-1} = e \in H$, mert $H$ csoport;
2. szimmetrikus: $ab^{-1} \in H \Rightarrow (ab^{-1})^{-1} = ba^{-1} \in H$;
3. tranzitív: $ab^{-1} \in H$ és $bc^{-1} \in H \Rightarrow ab^{-1}bc^{-1} = ac^{-1} \in H$.

**Lemma.** Az $a \in G$ elem ekvivalenciaosztálya a $Ha$ mellékosztály. *Bizonyítás.* Ha $b \in Ha$, akkor $b = ha$ egy $h \in H$-ra, így $ba^{-1} = h$, és $ab^{-1} = h^{-1} \in H$, azaz $a \sim b$. Fordítva, ha $a \sim b$, akkor $ab^{-1} = h \in H$, tehát $ba^{-1} = h^{-1}$, és $b = h^{-1}a \in Ha$.

Másik bevezetés: $a \sim b$, ha $b^{-1}a \in H$; ekkor az osztályok az $aH$ alakú halmazok.

### Definíció

Legyen $G$ csoport, $H \le G$, $a \in G$. A $G$ csoport $H$ részcsoportja szerinti

- **bal oldali mellékosztálya** az $aH = \{ak \mid k \in H\}$ komplexus,
- **jobb oldali mellékosztálya** a $Ha$ komplexus.

Ha minden $aH$ / $Ha$-ból kiveszünk egy reprezentáns elemet, $H$ **bal / jobb oldali reprezentánsrendszerét** kapjuk.

A mellékosztályok a csoport elemeinek **osztályozását** adják, így két mellékosztály vagy megegyezik, vagy diszjunkt.

### Index

A $Ha \mapsto (Ha)^{-1} = a^{-1}H$ leképezés bijekció a jobb és a bal oldali mellékosztályok halmaza között, ezért a $G$ tetszőleges részcsoportja szerinti különböző bal és jobb oldali mellékosztályok száma megegyezik.

**Definíció.** A $H$ szerinti mellékosztályok halmazának számossága **$H$ indexe $G$-ben**, jelölése $|G : H|$ vagy $[G : H]$. Az index végtelen is lehet.

### Lagrange-tétel

**Tétel.** Legyen $G$ véges csoport és $H \le G$. $H$ rendjének és $G$-beli indexének szorzata egyenlő $G$ rendjével: $|G| = |H| \cdot |G : H|$.

*Bizonyítás.* $|G| = \sum_{r \in R} |rH|$, ahol $R$ a $H$ egy bal oldali reprezentánsrendszere. A $\varphi(h) = ah$ leképezés bijekció $H$ és $aH$ között: szürjektív, mert $aH$ minden eleme $ah$ alakú; injektív, mert $ah_1 = ah_2$-ből a regularitás miatt $h_1 = h_2$. Így $|rH| = |H|$ minden $r$-re, és $|G| = |H| \cdot |R| = |H| \cdot |G : H|$.

### Következmények

1. Véges csoportban az elem rendje osztója a csoport rendjének (lásd [[concepts/dimatii/elem-rendje]]).
2. **Prímszámrendű csoport ciklikus.** Ha $|G| = p$ prím, van $a \ne e$ elem; a Lagrange-tétel szerint $|a|$ osztja $p$-t, tehát $|a| = p$ (az 1 az egységelem rendje), így $a$ generálja $G$-t. Az egységelem kivételével bármelyik elem generálja $G$-t.

### Triviális részcsoportok, prímrendű csoport jellemzése

Triviális csoport: a pusztán az egységelemből álló csoport. Minden más $G$ esetén az $\{e\}$ és $G$ különböző részcsoportok, ezek a **triviális részcsoportok**.

**Tétel.** Egy nem egyelemű csoport akkor és csak akkor **prímszámrendű**, ha csak triviális részcsoportja van.

- $\Rightarrow$: a prímrendű csoport ciklikus, részcsoportjai $\{e\}$ és $G$.
- $\Leftarrow$: ha $G$-nek pontosan két részcsoportja van és $a \ne e$, akkor $\langle a \rangle = G$, tehát $G$ ciklikus. Nem lehet végtelen, mert akkor pl. $a^n$ valódi részcsoportot generálna. Nem lehet összetett rendű sem: ha $|G| = n_1 n_2 \dots n_k$, ahol $n_i > 1$, akkor $\langle a^{n_i} \rangle \le G$ valódi részcsoport (mert $(a^{n_i})^{n_1 \dots n_{i-1} n_{i+1} \dots n_k} = e$).

## Kapocs

- [[concepts/dimatii/csoport]] — az alapstruktúra
- [[concepts/dimatii/reszcsoport]] — a részcsoport, amely szerint a mellékosztályokat képezzük
- [[concepts/dimatii/ciklikus-csoport]] — prímrendű csoport ciklikussága
- [[concepts/dimatii/elem-rendje]] — az elem rendje osztja a csoport rendjét
- [[concepts/dimatii/normaloszto-es-faktorcsoport]] — mikor esik egybe a bal és a jobb oldali mellékosztály
