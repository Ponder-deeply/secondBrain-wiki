---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# A Jordan-mérték szerinti integrál

Korlátos függvényt Jordan-mérhető halmazon integrálunk: a halmazt mérhető darabokra osztjuk, alsó és felső integrálközelítő összegeket képezünk, és ha az alsó és a felső integrál megegyezik, a függvény Riemann-integrálható.

## Tartalom

### Mérhető halmaz felosztása

Legyen $A \in \mathcal{J}_p$.

- Az $A$ egy **felosztása** $\mathcal{F} = \{B_1,\dots,B_n\}$, ha $B_1,\dots,B_n \in \mathcal{J}_p$ nemüresek, egymásba nem nyúlók (az $\operatorname{int} B_i$-k diszjunktak), és az uniójuk $A$.
- Egy $B$ halmaz **átmérője** $\operatorname{diam} B = \sup\{|x-y| : x,y \in B\}$.
- A felosztás **finomsága** $\delta(\mathcal{F}) = \max_i \operatorname{diam} B_i$.
- A $\mathcal{G} = \{C_1,\dots,C_m\}$ felosztás **finomítása** $\mathcal{F}$-nek, ha mindegyik $C_j$ részhalmaza valamelyik $B_i$-nek.

A lényeges eltérés az egyváltozós esettől, hogy itt nem osztópontok, hanem tetszőleges mérhető darabok alkotják a felosztást.

### Integrálközelítő összegek

Legyen $f : A \to \mathbb{R}$ korlátos, $\mathcal{F} = \{B_1,\dots,B_n\}$ az $A$ egy felosztása. Az alsó és felső integrálközelítő összeg

$$s(f,\mathcal{F}) = \sum_{i=1}^n t_p(B_i) \cdot \inf_{B_i} f, \qquad S(f,\mathcal{F}) = \sum_{i=1}^n t_p(B_i) \cdot \sup_{B_i} f.$$

### Finomítás monotonitása

**Állítás.** Ha $\mathcal{G}$ finomítása $\mathcal{F}$-nek, akkor

$$s(f,\mathcal{F}) \leq s(f,\mathcal{G}) \quad \text{és} \quad S(f,\mathcal{G}) \leq S(f,\mathcal{F}).$$

**Bizonyítás.** A mérték additivitása miatt $t(B_i) = \sum_{C_j \subset B_i} t(C_j)$, és $\inf_{B_i} f \leq \inf_{C_j} f$, ha $C_j \subset B_i$; így

$$s(f,\mathcal{F}) = \sum_i \Big(\sum_{C_j \subset B_i} t(C_j)\Big)\inf_{B_i} f \leq \sum_i \sum_{C_j \subset B_i} t(C_j)\inf_{C_j} f = s(f,\mathcal{G}).$$

A felső összegre ugyanez fordított iránnyal. $\square$

**Következmény.** Bármely $\mathcal{F}_1$, $\mathcal{F}_2$ felosztásra $s(f,\mathcal{F}_1) \leq S(f,\mathcal{F}_2)$: a $\mathcal{G} = \{B_i \cap C_j \neq \emptyset\}$ közös finomítást használva

$$s(f,\mathcal{F}_1) \leq s(f,\mathcal{G}) \leq S(f,\mathcal{G}) \leq S(f,\mathcal{F}_2).$$

### Alsó integrál, felső integrál, integrál

Legyen $A \in \mathcal{J}_p$, $f : A \to \mathbb{R}$ korlátos.

$$\underline{\int}_A f = \sup\{s(f,\mathcal{F}) : \mathcal{F} \text{ felosztása } A\text{-nak}\},$$

$$\overline{\int}_A f = \inf\{S(f,\mathcal{F}) : \mathcal{F} \text{ felosztása } A\text{-nak}\}.$$

Az $f$ **Riemann-integrálható** $A$-n, ha a kettő megegyezik; ekkor a közös érték az $f$ **Riemann-integrálja**:

$$\int_A f = \int_A f(x_1,\dots,x_p)\,\mathrm{d}x_1\dots\mathrm{d}x_p.$$

### Alternatív definíció téglán

Ha $A = [a_1,b_1]\times\dots\times[a_p,b_p]$ tégla, megtehetjük, hogy csak olyan felosztásokat engedünk meg, amelyek minden él egy-egy $x_{i,0} = a_i < x_{i,1} < \dots < x_{i,n_i} = b_i$ felosztásának szorzataként állnak elő; a felosztás darabjai ilyenkor a $[x_{1,j_1}, x_{1,j_1+1}] \times \dots \times [x_{p,j_p}, x_{p,j_p+1}]$ téglák. Ez szűkebb felosztásosztály, mégis ugyanazokat az alsó és felső integrálértékeket adja (nem teljesen triviális, bizonyítás nélkül).

## Kapocs

- [[concepts/analiii/jordan-merheto-halmazok-gyuruje]] — a felosztás darabjai és az integrálási tartomány is $\mathcal{J}_p$-beliek
- [[concepts/analiii/also-felso-osszegek-kockazassal]] — a definíció harmadik, rácskockákra épülő alakja és a végtelenül finomodó felosztássorozatok konvergenciája
- [[concepts/analiii/tobbvaltozos-integralhatosag]] — az oszcillációs összeggel megfogalmazott integrálhatósági kritériumok
- [[concepts/analii/hatarozott-integral-ertelmezese]] — az egyváltozós definíció, amelynek ez a szó szerinti általánosítása: ott $[a,b]$ osztópontjai, itt egy mérhető halmaz mérhető darabjai adják a felosztást, és a $x_i - x_{i-1}$ hossz helyére a $t_p(B_i)$ mérték lép
