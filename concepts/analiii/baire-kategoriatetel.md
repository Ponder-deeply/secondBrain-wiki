---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Baire-kategóriatétel

Teljes metrikus térből megszámlálható sok sehol sem sűrű halmazt kivéve sűrű halmaz marad — így teljes tér soha nem áll elő megszámlálható sok „kicsi" halmaz uniójaként. Ez a tétel adja a kicsi és nagy halmazok egyik legfontosabb, topológiai értelmezését.

## Tartalom

### A tétel

**Tétel (Baire-kategóriatétel).** Legyen $(M,d)$ teljes metrikus tér. Ha $S_1, S_2, \dots \subset M$ sehol sem sűrű halmazok, akkor

$$M \setminus \Bigl(\bigcup_{n=1}^\infty S_n\Bigr)$$

sűrű $M$-ben.

**Következmény.** Teljes metrikus tér nem áll elő megszámlálható sok sehol sem sűrű halmaz uniójaként.

### Kategóriák

Legyen $(M,d)$ teljes metrikus tér, $H \subset M$.

- $H$ **I. kategóriájú**, ha megszámlálható sok sehol sem sűrű halmaz uniója. Ezek a „kicsi" halmazok — megszámlálható sok kicsi halmaz uniója is kicsi.
- $H$ **II. kategóriájú**, ha nem I. kategóriájú. Ezek a „nagy" halmazok.
- $H$ **reziduális**, ha $M \setminus H$ I. kategóriájú. Ezek a „nagyon nagy" halmazok, amelyek komplementuma kicsi.

### Változatok kicsi és nagy halmazokra

Egy halmazt többféleképpen tekinthetünk kicsinek; közös elvárás, hogy megszámlálható sok kicsi halmaz uniója is kicsi legyen.

- **Számosság szerint:** egy nem megszámlálható alaptérben (pl. $\mathbb{R}^p$) a megszámlálható halmazok a kicsik.
- **Mérték szerint:** a nullmértékű (0 térfogatú) halmazok a kicsik. Ahhoz, hogy a megszámlálható unió is kicsi maradjon, a térfogat fogalmát újra kell gondolni — ez a Mértékelmélet tárgya.
- **Kategória szerint:** a Baire-tétel értelmében az I. kategóriájú halmazok a kicsik. A leggyakoribb terep megint a $C[a,b]$ tér a maximumnormával.

A három fogalom nem esik egybe; egy halmaz lehet nullmértékű, de II. kategóriájú, és fordítva.

### Bizonyítás

Legyen $B(a_0, r_0)$ tetszőleges gömb; ebben kell találnunk olyan $c$ pontot, amely egyik $S_n$-nek sem eleme.

Rekurzívan definiálunk egy $B(a_n, r_n)$ gömbsorozatot. Ha $B(a_{n-1}, r_{n-1})$ már megvan, akkor $B(a_n,r_n)$-et úgy választjuk, hogy

$$B(a_n,r_n) \subset B(a_{n-1},r_{n-1}), \qquad B(a_n,r_n) \cap S_n = \emptyset, \qquad r_n \leq \tfrac12 r_{n-1}.$$

Ez lehetséges, mert $S_n$ sehol sem sűrű. Bármely $n, m \geq n_0$ esetén $a_n, a_m \in B(a_{n_0}, r_{n_0})$, ezért

$$d(a_m, a_n) < 2r_{n_0} \leq \frac{r_0}{2^{n_0-1}},$$

tehát $(a_n)$ Cauchy-sorozat, és $M$ teljessége miatt konvergens. Legyen $c = \lim a_n$. Minden $n > m$ esetén $a_n \in B(a_m, r_m)$, és a lezárt zártsága miatt $c \in \overline{B}(a_m,r_m)$ is teljesül minden $m$-re — így $c \notin \bigcup S_m$. Mivel $c \in B(a_0,r_0)$, a komplementer valóban sűrű. $\blacksquare$

## Kapocs

- [[concepts/analiii/sehol-sem-suru-halmazok]] — a bizonyítás és a definíciók előfeltétele
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a teljesség, ami nélkül a tétel hamis
- [[concepts/analiii/konvergencia-metrikus-terben]] — a beágyazott gömbök konstrukciójának eszköze
- [[concepts/analiii/cantor-metszettetel]] — rokon egymásba skatulyázott halmazokra épülő tétel
