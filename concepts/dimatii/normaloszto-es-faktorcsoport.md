---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Normálosztó és faktorcsoport

A normálosztó olyan részcsoport, amelynél a bal és a jobb oldali mellékosztályok egybeesnek; szerinte a mellékosztályok a komplexusszorzással csoportot (faktorcsoportot) alkotnak.

## Tartalom

### Normálosztó

**Definíció.** A $G$ csoport $N$ részcsoportját **invariáns** vagy **normális részcsoportnak** (**normálosztónak**) nevezzük, jelben $N \triangleleft G$, ha $Na = aN$ minden $a \in G$-re.

**Tétel.** Legyen $N \le G$. Ekvivalensek:

1. $N$ normálosztó;
2. $a^{-1}Na = N$ minden $a \in G$-re;
3. $a^{-1}Na \subseteq N$ minden $a \in G$-re.

*Bizonyítás.* (1)$\Rightarrow$(2): $a^{-1}Na = a^{-1}aN = N$. (2)$\Rightarrow$(1): $Na = a(a^{-1}Na) = aN$. (2)$\Rightarrow$(3) triviális. (3)$\Rightarrow$(2): $a^{-1}$-re is érvényes a feltétel, így $aNa^{-1} \subseteq N$, ebből $N = a^{-1}(aNa^{-1})a \subseteq a^{-1}Na$, tehát $a^{-1}Na = N$.

**Következmények.** Normálosztók metszete is normálosztó (a (3) feltételből). Az $x \mapsto a^{-1}xa$ leképezés ($a \in G$ rögzített) a **belső automorfizmus**; a (2)-ből: a normálosztók pontosan azok a részcsoportok, amelyeknek minden belső automorfizmus melletti képe saját maga.

### Műveletkompatibilis osztályozás

**Tétel.** Legyen $G$ csoport.

1. Egy $N$ normálosztó szerinti mellékosztályok a csoportnak a művelettel kompatibilis osztályozását alkotják;
2. minden, a művelettel kompatibilis osztályozás esetén az egységelem osztálya normálosztó, és az osztályozás ezen normálosztó szerinti mellékosztályokból áll;
3. a mellékosztályok közötti művelet megegyezik az osztályok mint halmazok komplexusszorzásával.

*Bizonyítás.* (1) Ha $a' \in Na$, $b' \in Nb$, akkor $Na' = Na$, $Nb' = Nb$, és $a'b' \in (Na)(Nb) = N(aN)b = N(Na)b = N^2ab = Nab$, tehát $a'b' \sim ab$. (3) $\{a'b' : a' \in Na, b' \in Nb\} = (Na)(Nb) = Nab$. (2) Legyen $N$ az $e$ osztálya. Ha $a \in N$, akkor $e = a^{-1}a \sim a^{-1}e = a^{-1}$, így $N^{-1} \subseteq N$; ha $a, b \in N$, akkor $ab \sim ee = e$, így $NN \subseteq N$; tehát $N$ részcsoport. Ha $x \in N$ és $g$ tetszőleges, akkor $g^{-1}xg \sim g^{-1}eg = e$, azaz $g^{-1}Ng \subseteq N$, így $N$ normálosztó. Végül $a \sim b \Rightarrow a^{-1}ab^{-1} \sim a^{-1}bb^{-1}$, vagyis $b^{-1} \sim a^{-1}$, és $e = aa^{-1} \sim ab^{-1}$, azaz $ab^{-1} \in N$; fordítva, ha $ab^{-1} \in N$, akkor $ab^{-1} \sim e$ és $a = ab^{-1}b \sim eb = b$. Az osztályozás tehát pontosan az $N$ szerinti mellékosztályokból áll.

### Faktorcsoport

**Következmény.** Egy $G$ csoportnak egy $N$ normálosztó szerinti mellékosztályai a (komplexus)szorzásra nézve csoportot alkotnak. *Bizonyítás.* Az $a \mapsto Na$ (kanonikus) leképezés homomorf, és a homomorf invariánsok félcsoportban tétele szerint (lásd [[concepts/dimatii/homomorfizmus-es-izomorfizmus]]) $G$ homomorf képe csoport.

**Definíció.** A $G$ csoport $N$ normálosztója szerinti mellékosztályok a komplexusszorzással **$G$ $N$ szerinti faktorcsoportját** alkotják, jelölése $G/N$.

## Kapocs

- [[concepts/dimatii/mellekosztaly-es-lagrange-tetel]] — a mellékosztályok és az index
- [[concepts/dimatii/csoport]] — az alapfogalom
- [[concepts/dimatii/reszcsoport]] — a normálosztó speciális részcsoport
- [[concepts/dimatii/homomorfizmus-es-izomorfizmus]] — a kanonikus leképezés homomorf, a faktorcsoport homomorf kép
