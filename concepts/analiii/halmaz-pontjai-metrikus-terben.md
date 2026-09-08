---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.7.3.–1.7.4. Tétel, 1.8. viii)–ix) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Belső, külső, határ-, izolált és torlódási pont

Egy metrikus tér minden pontja egy adott $H$ halmazhoz képest pontosan háromféle lehet: belső, külső vagy határpont. Az ebből képzett halmazok — belső, külső, határ, derivált halmaz, lezárt — adják azt a szótárat, amelyben a nyíltság és a zártság kimondható.

## Tartalom

Legyen $(M,d)$ metrikus tér, $H \subset M$ és $a \in M$.

### A pontok osztályozása

- $a$ a $H$ **belső pontja** (másképp: $H$ *környezete* $a$-nak), ha $\exists r > 0:\ B(a,r) \subset H$. A belső pontok halmaza a $H$ **belseje**, jele $\operatorname{int} H$.
- $a$ a $H$ **külső pontja**, ha $\exists r > 0:\ B(a,r) \cap H = \emptyset$. A külső pontok halmaza a $H$ **külseje**, jele $\operatorname{ext} H$.
- $a$ a $H$ **határpontja**, ha sem nem belső, sem nem külső pont; ekvivalensen, ha bármely $r > 0$ esetén $B(a,r)$ belemetsz $H$-ba és $M \setminus H$-ba is. A határpontok halmaza a $H$ **határa**, jele $\operatorname{mar} H$ vagy $\partial H$.
- $a$ a $H$ **izolált pontja**, ha $\exists r > 0:\ B(a,r) \cap H = \{a\}$.
- $a$ a $H$ **torlódási pontja**, ha bármely $r > 0$ esetén $\bigl|B(a,r) \cap H\bigr| = \infty$.

Az első három osztály diszjunkt módon fedi le az egész teret: $M = \operatorname{int} H \ \dot\cup\ \partial H \ \dot\cup\ \operatorname{ext} H$.

### Derivált halmaz és lezárt

- A $H$ **derivált halmaza**, jele $H'$, a torlódási pontok halmaza.
- A $H$ **lezártja**, jele $\operatorname{cl} H$, három egyenértékű módon: $H \cup \partial H$; a legszűkebb $H$-t tartalmazó zárt halmaz; a $H$-t tartalmazó zárt halmazok metszete.

Az izolált pont és a torlódási pont kizárja egymást: egy $H$-beli pont vagy izolált, vagy torlódási pontja $H$-nak. A lezárt ennek megfelelően $\operatorname{cl}H = H \cup H'$, elemeit a $H$ **érintkezési pontjainak** is nevezzük: $b$ pontosan akkor érintkezési pont, ha minden $K(b)$ környezetre $K(b)\cap H \neq \emptyset$.

**Sorozatos jellemzés.** Az $\alpha$ akkor és csak akkor torlódási pontja a $H \neq \emptyset$ halmaznak, ha van olyan $(x_n) : \mathbb{N}\to H\setminus\{\alpha\}$ sorozat, amelyre $\lim(x_n)=\alpha$; a sorozat ráadásul injektívnek is választható.

## Kapocs

- [[concepts/analiii/nyilt-es-zart-halmazok]] — a nyíltság és zártság ezekre a fogalmakra épül
- [[concepts/analiii/konvergencia-metrikus-terben]] — a torlódási pont sorozatos átfogalmazása
- [[concepts/analiii/sehol-sem-suru-halmazok]] — a sehol sem sűrűség az $\operatorname{int}\operatorname{cl} S = \emptyset$ feltétel
- [[concepts/analiii/metrikus-ter]] — az alapstruktúra
- [[concepts/analiii/kompaktsag-ekvivalens-jellemzesei]] — a torlódási pontos kompaktság-jellemzés
