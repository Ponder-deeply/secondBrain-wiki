---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Borel tétele: kompaktság $\mathbb{R}^p$-ben

$\mathbb{R}^p$-ben a fedéses kompaktság pontosan a korlátosság és zártság együttese. A jegyzet fő bizonyítási útja a racionális gömbökre épülő Lindelöf-lemmán át vezet, amely tetszőleges nyílt fedést megszámlálhatóra szűkít.

## Tartalom

### Racionális gömbök

**Definíció.** A $B(a,r)$ gömb **racionális gömb**, ha $a \in \mathbb{Q}^p$ és $r \in \mathbb{Q}$. Ezekből megszámlálhatóan sok van.

**Lemma.** $\mathbb{R}^p$-ben minden nyílt halmaz előáll a benne fekvő racionális gömbök uniójaként.

*Bizonyítás.* Legyen $G$ nyílt és $a \in G$. Van olyan $r>0$, hogy $B(a,r) \subset G$. A $\mathbb{Q}^p$ sűrűsége miatt vehetünk egy $b \in B(a, r/3) \cap \mathbb{Q}^p$ pontot és egy racionális $r/3 < s < 2r/3$ számot. Ekkor $a \in B(b,s) \subset B(a,r) \subset G$, mert $|a-b| < \frac r3 < s$, és bármely $x \in B(b,s)$-re $|x-a| \leq |x-b| + |b-a| < \frac{2r}{3} + \frac r3 = r$. Tehát $G$ minden pontját lefedi egy $G$-ben fekvő racionális gömb. $\blacksquare$

### Lindelöf-lemma

**Lemma.** $\mathbb{R}^p$-ben nyílt halmazok tetszőleges $G_i$ ($i \in I$) rendszeréből kiválasztható megszámlálható részrendszer ugyanazzal az unióval: van olyan megszámlálható $J \subset I$, hogy $\bigcup_{i\in J} G_i = \bigcup_{i \in I} G_i$.

*Bizonyítás.* Soroljuk fel a racionális gömböket: $B_1, B_2, \dots$. Legyen $K = \{k \in \mathbb{N} : \exists i \in I,\ B_k \subset G_i\}$, és minden $k \in K$-hoz legyen $i_k \in I$ olyan, hogy $B_k \subset G_{i_k}$. Azt állítjuk, hogy $J = \{i_k : k \in K\}$ jó. A $\bigcup_{i\in J} G_i \subset \bigcup_{i\in I}G_i$ tartalmazás triviális. Az előző lemma szerint $G_i = \bigcup_{B_k \subset G_i} B_k$, ezért

$$\bigcup_{i\in I}G_i = \bigcup_{i\in I}\Bigl(\bigcup_{B_k \subset G_i} B_k\Bigr) = \bigcup_{k\in K}B_k \subset \bigcup_{k\in K}G_{i_k} = \bigcup_{i\in J}G_i. \qquad \blacksquare$$

### Borel tétele

**Tétel.** $K \subset \mathbb{R}^p$ akkor és csak akkor kompakt, ha korlátos és zárt.

*Bizonyítás.* Az „odafelé" irány a kompaktság általános következménye. Fordítva: legyen $K$ korlátos és zárt, és $\bigcup_{i\in I}G_i$ egy tetszőleges nyílt fedése. A Lindelöf-lemma miatt $I$ helyett vehetjük egy megszámlálható $J$ részét. Ha $J$ véges, készen vagyunk; tegyük fel, hogy $J = \{i_1,i_2,\dots\}$. Legyen

$$K_n = K \setminus (G_{i_1}\cup\dots\cup G_{i_n}), \qquad K_\infty = K \setminus (G_{i_1}\cup G_{i_2}\cup\dots).$$

Ezek zárt, korlátos halmazok, $K \supset K_1 \supset K_2 \supset \dots$, és $\bigcap K_n = K_\infty$. Ha valamelyik $K_n$ üres, akkor $K \subset G_{i_1}\cup\dots\cup G_{i_n}$, kész. Ha egyik sem üres, akkor a Cantor-metszettétel szerint $K_\infty$ sem üres, de akkor a $G_{i_n}$ halmazok nem is fedik le $K$-t — ellentmondás. $\blacksquare$

### Alternatív bizonyítás, Lindelöf-lemma nélkül (kockafelezés)

Indirekt: legyen $K$ korlátos, zárt, de nem kompakt, és $\bigcup_{i\in I}G_i \supset K$ olyan nyílt fedés, amelyből nem választható ki véges fedés. Nevezzünk egy halmazt **rossz**nak, ha a $G_i$ halmazok közül semelyik véges sok nem fedi le; a feltevés szerint $K$ rossz.

Rekurzívan konstruálunk csökkenő $D_0 \supset D_1 \supset \dots$ tengelypárhuzamos zárt kockákat úgy, hogy minden $n$-re $D_n \cap K$ rossz. A $D_0$-t választhatjuk $K$-t tartalmazónak ($K$ korlátos). Ha $D_n$ megvan, felezzük el minden tengelyre merőlegesen: $2^p$ feleakkora zárt kockát kapunk. Legyen $D_{n+1}$ egy olyan kis kocka, amelyre $D_{n+1}\cap K$ rossz. Ilyen van: ha mindegyik $C_j \cap K$ lefedhető lenne véges sok $G_i$-vel, akkor ez a $2^p$ véges fedés együtt $D_n \cap K$-t is lefedné.

A $D_n \cap K$ halmazok korlátosak, zártak, nemüresek (mert rosszak) és csökkenőek, tehát a Cantor-metszettétel szerint van közös pontjuk; a felezés miatt pontosan egy: $\bigcap_{n}(D_n\cap K) = \{c\}$. A $c \in K$ pontot lefedi valamely $G_i$, ami nyílt, tehát $B(c,r)\subset G_i$ valamilyen $r>0$-ra. Válasszunk olyan nagy $n$-et, hogy $D_n$ átmérője kisebb legyen $r$-nél; mivel $c \in D_n$, ezért $D_n \subset B(c,r) \subset G_i$, így

$$(D_n\cap K)\subset D_n\subset B(c,r)\subset G_i.$$

Ez ellentmondás: a rossz $D_n\cap K$ halmazt egyetlen $G_i$ lefedte. $\blacksquare$

## Kapocs

- [[concepts/analiii/kompakt-halmazok]] — a kompaktság definíciója és a „kompakt $\Rightarrow$ korlátos és zárt" irány
- [[concepts/analiii/cantor-metszettetel]] — mindkét bizonyítás záró lépése
- [[concepts/analiii/sehol-sem-suru-halmazok]] — a $\mathbb{Q}^p$ sűrűsége, amin a racionális gömbök lemmája múlik
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a nyílt halmazok szerkezete
