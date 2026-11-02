---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Ciklikus csoport

Egyetlen elem által generált csoport. Lényegében csak egy végtelen ciklikus csoport van ($\mathbb{Z}$ additív csoportja), és minden $n$-re egy $n$ elemű ($\mathbb{Z}_n$); ezért a ciklikus csoportok kommutatívak.

## Tartalom

### Definíció és alapok

A $G$ csoport a $g$ elem által generált **ciklikus csoport**, ha $G = \langle g \rangle = \{g^n : n \in \mathbb{Z}\}$ (lásd [[concepts/dimatii/reszcsoport]]). Ciklikus csoport homomorf képe is ciklikus, és egy generátor képe generálja a homomorf képet.

### Tétel (ciklikus csoportok szerkezete)

Végtelen ciklikus csoport izomorf $(\mathbb{Z},+)$-szal; $n$ elemű ciklikus csoport izomorf a modulo $n$ maradékosztályok $(\mathbb{Z}_n,+)$ additív csoportjával. Speciálisan a ciklikus csoportok kommutatívak.

*Bizonyítás.*

1. **Végtelen eset.** A $\varphi(n) = g^n$ ($n \in \mathbb{Z}$) leképezésre $\varphi(n+m) = g^{n+m} = g^n g^m = \varphi(n)\varphi(m)$, tehát izomorfizmus $\mathbb{Z}$ és $\langle g\rangle$ között: lényegében egyetlen végtelen ciklikus csoport van.
2. **Véges eset.** Léteznek $k > s$ egészek, hogy $g^k = g^s$, azaz $g^{k-s} = e$. Az ilyen természetes számok közül a legkisebbet jelölje $n$ (ez $g$ rendje, lásd [[concepts/dimatii/elem-rendje]]). Ekkor $g^0 = e, g, g^2, \dots, g^{n-1}$ $(*)$ páronként különbözők ($n$ minimalitása miatt), és $g$ minden hatványa szerepel közöttük: $m = qn + r$ ($0 \le r < n$, a maradékos osztás egyértelmű) esetén $g^m = (g^n)^q g^r = e^q g^r = g^r$. A $\varphi(x \bmod n) = g^x$ függvény izomorfizmus a modulo $n$ maradékosztályok additív csoportja és $(*)$ között. Tehát minden $n$-hez lényegében egyetlen $n$ elemű ciklikus csoport van.
3. **Kommutativitás.** $g^k g^s = g^{k+s} = g^s g^k$ minden $k,s \in \mathbb{Z}$-re.

### Ciklikus csoport részcsoportjai

**Tétel.** Ciklikus csoport minden részcsoportja ciklikus. *Bizonyítás.* Legyen $\langle g \rangle = G$, $H \le G$. Ha $H = \{e\}$, kész. Különben van $g$-nek pozitív kitevős hatványa $H$-ban; legyen $d$ a legkisebb pozitív kitevő, amelyre $g^d \in H$. Ekkor $\langle g^d \rangle \subseteq H$. Fordítva, ha $g^m \in H$, osszunk maradékosan: $m = qd + r$, $0 \le r < d$; ekkor $g^r = g^m (g^d)^{-q} \in H$, és $d$ minimalitása miatt $r = 0$, így $g^m = (g^d)^q \in \langle g^d \rangle$. Tehát $H = \langle g^d \rangle$.

**Tétel (8.1.23).** Legyen $G$ $n$ rendű véges ciklikus csoport, $g$ generátora, $a \in \mathbb{Z}$ és $d = \mathrm{lnko}(a, n)$. Ekkor $g^a$ a $H = \{g^d, g^{2d}, \dots, g^{md} = e\}$ ciklikus részcsoportot generálja, ahol $n = md$. $G$ minden részcsoportja előáll így valamely $d \mid n$-re, és $G$-nek $\varphi(n)$ generátora van. *Bizonyítás.* $d \mid a$ miatt $g^a = (g^d)^q$, tehát $\langle g^a \rangle \subseteq H$; az euklideszi algoritmus szerint $d = ax + ny$, így $g^d = (g^a)^x (g^n)^y = (g^a)^x$, tehát $H \subseteq \langle g^a \rangle$. A generátorok száma $\varphi(n)$ definíciójából következik ($d = 1$).

## Kapocs

- [[concepts/dimatii/reszcsoport]] — a generátum fogalma
- [[concepts/dimatii/elem-rendje]] — a generátor rendje a csoport rendje
- [[concepts/dimatii/homomorfizmus-es-izomorfizmus]] — az izomorfizmus fogalma
- [[concepts/dimatii/maradekosztaly]] — a $\mathbb{Z}_n$ additív csoportja
- [[concepts/dimatii/maradekos-osztas]] — a bizonyításban használt maradékos osztás
- [[concepts/dimatii/csoport]] — az alapfogalom
- [[concepts/dimatii/primitiv-gyok]] — $\mathbb{Z}_p^*$ ciklikus csoport generátora
