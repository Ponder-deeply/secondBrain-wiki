---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# A lebontási tétel

Téglák szorzatán integrálható függvény esetén a belső változó szerinti alsó és felső integrál is integrálható a külső változóban, és mindkét kétszeres integrál a szorzattéglán vett integrállal egyenlő.

## Tartalom

### A kulcslemma

**Lemma.** Legyen $A \subset \mathbb{R}^p$, $B \subset \mathbb{R}^q$ tégla, $C = A\times B \subset \mathbb{R}^{p+q}$; az $\mathbb{R}^{p+q}$-beli pontokat $(x,y) = (x_1,\dots,x_p,y_1,\dots,y_q)$ alakban írjuk. Legyen $f : C \to \mathbb{R}$ korlátos. Ekkor

$$\underline{\int}_{(x,y)\in C} f \;\leq\; \underline{\int}_{x\in A}\left(\underline{\int}_{y\in B} f(x,y)\,\mathrm{d}y\right)\mathrm{d}x$$

és

$$\overline{\int}_{x\in A}\left(\overline{\int}_{y\in B} f(x,y)\,\mathrm{d}y\right)\mathrm{d}x \;\leq\; \overline{\int}_{(x,y)\in C} f.$$

**Bizonyítás (a második egyenlőtlenségre).** Adott $\varepsilon > 0$-hoz vegyük $C$-nek olyan $\mathcal{F}$ felosztását kis téglákra, amelyen a felső összeg $\varepsilon$-nál jobban közelíti $\overline{\int}_C f$-et. Ilyen felosztás megkapható $A$ és $B$ egy-egy téglafelosztásának szorzataként: $A = R_1\cup\dots\cup R_n$, $B = T_1\cup\dots\cup T_m$, $C = \bigcup_{i,j}(R_i\times T_j)$. Legyen $M_{i,j} = \sup_{x\in R_i,\, y\in T_j} f(x,y)$. Ekkor lépésenként a szuprémumot felülről becsülve

$$\overline{\int}_{x\in A}\left(\overline{\int}_{y\in B} f\,\mathrm{d}y\right)\mathrm{d}x \leq \sum_{i=1}^n t^p(R_i)\sum_{j=1}^m t^q(T_j)M_{i,j} = \sum_{i,j} t^{p+q}(R_i\times T_j)M_{i,j} = S(f,\mathcal{F}) < \overline{\int}_C f + \varepsilon.$$

Mivel ez minden $\varepsilon > 0$-ra igaz, az állítás következik. $\square$

Az egyenlőtlenségek iránya lényeges: a lemma egyik irányban sem állít egyenlőséget, csak korlátozza a belső integrálok viselkedését.

### A lebontási tétel

**Tétel.** Legyen $A \subset \mathbb{R}^p$, $B \subset \mathbb{R}^q$ tégla, $C = A\times B$, és $f : C \to \mathbb{R}$ korlátos, **integrálható**. Ekkor

- az $x \mapsto \underline{\int}_{y\in B} f(x,y)\,\mathrm{d}y$ és az $x \mapsto \overline{\int}_{y\in B} f(x,y)\,\mathrm{d}y$ függvény is integrálható $A$-n, és

$$\int_{x\in A}\left(\underline{\int}_{y\in B} f\,\mathrm{d}y\right)\mathrm{d}x = \int_{x\in A}\left(\overline{\int}_{y\in B} f\,\mathrm{d}y\right)\mathrm{d}x = \int_{(x,y)\in C} f(x,y)\,\mathrm{d}x\mathrm{d}y;$$

- ugyanez a szerepek felcserélésével az $y \mapsto \underline{\int}_{x\in A} f\,\mathrm{d}x$ és $y \mapsto \overline{\int}_{x\in A} f\,\mathrm{d}x$ függvényekre is fennáll.

**Bizonyítás.** A lemmát az integrálhatósággal összefűzve

$$\int_C f = \underline{\int}_C f \leq \underline{\int}_{x\in A}\left(\underline{\int}_{y\in B} f\,\mathrm{d}y\right)\mathrm{d}x \leq \overline{\int}_{x\in A}\left(\underline{\int}_{y\in B} f\,\mathrm{d}y\right)\mathrm{d}x \leq \overline{\int}_{x\in A}\left(\overline{\int}_{y\in B} f\,\mathrm{d}y\right)\mathrm{d}x \leq \overline{\int}_C f = \int_C f,$$

tehát a lánc minden tagja egyenlő. A másik három résztállítás ugyanígy megy. $\square$

### Miért az alsó/felső integrállal kell megfogalmazni?

Ahhoz, hogy a szokásos $\int_{x\in A}\big(\int_{y\in B} f\,\mathrm{d}y\big)\mathrm{d}x$ alak értelmes legyen, az kell, hogy $\underline{\int}_{y\in B} f\,\mathrm{d}y$ és $\overline{\int}_{y\in B} f\,\mathrm{d}y$ egy „nagy" halmazon megegyezzenek. Lehetnek kivételes $x$-ek, amelyekre $y\mapsto f(x,y)$ nem integrálható; ezek valamilyen értelemben „kicsi" halmazt alkotnak, de lehet kontinuum számosságú (például Cantor-halmaz), sőt lehet nem Jordan-mérhető (például sűrű) is. A pontos leírás a mértékelmélet kurzus feladata.

## Kapocs

- [[concepts/analiii/szukcessziv-integralas]] — a lebontási tétel közvetlen következménye, a többszörös integrál gyakorlati kiszámítási eszköze
- [[concepts/analiii/jordan-mertek-szerinti-integral]] — az alsó és felső integrál fogalma, amely nélkül a tétel nem is fogalmazható meg
- [[concepts/analiii/tobbvaltozos-integral-muveletei]] — a nullával való kiterjesztés, amely a tétel nem téglaalakú tartományra való átvitelét lehetővé teszi
