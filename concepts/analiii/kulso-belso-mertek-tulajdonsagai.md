---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# A külső és belső Jordan-mérték tulajdonságai

A külső Jordan-mérték szubadditív, a belső szuperadditív, mindkettő monoton, de egyik sem additív; a lezárás, a belső rész és a határ mértéke a $k(A) = b(A) + k(\partial A)$ összefüggésben kapcsolódik össze.

## Tartalom

### Szubadditivitás, szuperadditivitás, monotonitás

Legyen $A, B \subset \mathbb{R}^p$ korlátos.

- $k(A \cup B) \leq k(A) + k(B)$ — a külső Jordan-mérték **szubadditív**.
- Ha $(\operatorname{int} A) \cap (\operatorname{int} B) = \emptyset$, akkor $b(A \cup B) \geq b(A) + b(B)$ — a belső mérték **szuperadditív**.
- Ha $A \subset B$, akkor $k(A) \leq k(B)$ és $b(A) \leq b(B)$ — mindkét mérték **monoton**.

**Bizonyítás.** A megfelelő állítások a kockaszámlálásra triviálisan igazak: $k_n(A \cup B) \leq k_n(A) + k_n(B)$, illetve $b_n(A \cup B) \geq b_n(A) + b_n(B)$; innen határátmenet ([[concepts/analiii/jordan-mertek-kockazassal]]). $\square$

### Egyik mérték sem additív

Legyen $S = [0,1]^p \cap \mathbb{Q}^p$ és $T = [0,1]^p \setminus \mathbb{Q}^p$. Ekkor

- $k(S) = k(T) = 1$, de $k(S \cup T) = 1 \neq k(S) + k(T)$;
- $b(S) = b(T) = 0$, de $b(S \cup T) = 1 \neq b(S) + b(T)$.

Ezért a $\mathbb{R}^p$ *összes* korlátos részhalmazán nem lehet additív térfogatot kapni sem $k$-val, sem $b$-vel; a mérhető halmazokra kell szorítkozni.

### Lezárás, belső rész, határ

Legyen $A \subset \mathbb{R}^p$ korlátos. Ekkor

$$k(A) = k(\operatorname{cl} A), \qquad b(A) = b(\operatorname{int} A), \qquad k(A) = b(A) + k(\partial A).$$

Ha $A$ mérhető, akkor $t(\operatorname{cl} A) = t(\operatorname{int} A) = t(A)$.

**Bizonyítás.** A kockaszámlálás szintjén az első két állítás azonosság: $k_n(A) = k_n(\operatorname{cl} A)$ és $b_n(A) = b_n(\operatorname{int} A)$, hiszen a fedő kockákat a lezárás, a belső kockákat a belső rész definiálja. A harmadik a $k_n(\operatorname{cl} A) = b_n(\operatorname{int} A) + k_n(\partial A)$ felbontásból jön: minden fedő kocka vagy belső, vagy határkocka. A negyedikhez

$$t(A) = b(A) \leq b(\operatorname{cl} A) \leq k(\operatorname{cl} A) = k(A) = t(A),$$

tehát végig egyenlőség áll; a belső részre ugyanez a becslés fordítva. $\square$

### Következmény: a mérhetőség kritériuma

$A \subset \mathbb{R}^p$ akkor és csak akkor Jordan-mérhető, ha $k(\partial A) = 0$, azaz ha a határa nullmértékű. Ez a $k(A) = b(A) + k(\partial A)$ azonosság közvetlen átfogalmazása, és a gyakorlatban ez a mérhetőség szokásos ellenőrzési módja.

## Kapocs

- [[concepts/analiii/jordan-kulso-belso-mertek]] — a $k$ és $b$ definíciója, amelynek tulajdonságairól itt szó van
- [[concepts/analiii/jordan-mertek-kockazassal]] — a bizonyítások eszköze: minden állítást a $k_n$, $b_n$ szinten látunk be, majd határátmenetet végzünk
- [[concepts/analiii/jordan-nullmerteku-halmazok]] — a $k(\partial A) = 0$ kritérium kihasználása konkrét halmazokra
- [[concepts/analii/riemann-integral-tulajdonsagok]] — az egyváltozós elméletben ugyanezt a szerepet a „véges halmazon való megváltoztatás nem számít" tétel tölti be; a többváltozós megfelelője a nullmértékű halmaz fogalma
