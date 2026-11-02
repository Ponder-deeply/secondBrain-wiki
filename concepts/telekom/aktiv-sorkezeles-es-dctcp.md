---
tags: [concept]
sources: [Laki_Lecture_10.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-09-25
---

# Sorkezelés a routerekben: drop-tail, RED, ECN és DCTCP

A TCP torlódásvezérlése csak a végpontokon fut; a routerek viszont eldönthetik, **mikor és hogyan** jelezzék a torlódást. Az alapeset a FIFO + drop-tail; a **RED** már a sor telítődése előtt, valószínűségi alapon dob vagy jelöl; az **ECN** dobás helyett az IP-fejlécben jelzi a torlódást; a **DCTCP** pedig adatközpontokra szabva a jelölések *arányára* reagál.

## Tartalom

### Tipikus Internet-sorkezelés: FIFO + drop-tail

- A legegyszerűbb választás, széles körben használják.
- **FIFO** (*first-in-first-out*) — egyetlen forgalmi osztályt feltételez; ez az **ütemezési elv** (*scheduling discipline*).
- **Drop-tail** — ha a sor tele, az érkező csomagot eldobja, függetlenül a folyamtól és a fontosságtól; ez a **dobási politika** (*drop policy*).

### RED — Random Early Detection

- A router a **sorhossz mozgó átlagát** (`avgq`) tartja nyilván, és minden csomag érkezésekor újraszámolja.
- Ha `avgq < min_th`: nem tesz semmit (kevés sorban állás, a csomagok átmennek).
- Ha `min_th ≤ avgq < max_th`: kiszámít egy $P_a$ valószínűséget, és ezzel a valószínűséggel **megjelöli** az érkező csomagot — eldobja vagy ECN-jelzést állít be. A jelölés valószínűsége a sorhosszal arányosan nő; így értesíti a forrásokat a **kezdődő** torlódásról.
- Ha `avgq ≥ max_th`: minden csomagot jelöl/dob — védelem a rosszul viselkedő források ellen.

A dobási valószínűség grafikonja: `min_th` alatt 0, `min_th` és `max_th` között lineárisan nő $\max_p$-ig, `max_th`-nál 1-re ugrik.

### Csomagdobás vagy ECN-jelölés

**Csomagdobás:** újraküldés szükséges; egyszerűbb megvalósítás; a forrás csak az időkorlát lejárta (vagy dupACK-ok) után tud reagálni.

**ECN** (*Explicit Congestion Notification*):
- **végponti támogatás** szükséges;
- az IP-fejléc 2 bites ECN mezője (a DSCP mellett): `00` Not-ECT, `01` ECT(1), `10` ECT(0), `11` **CE** (*Congestion Experienced*); az ECN-képes csomagot ECT-vel jelölik;
- dobás helyett a router a **CE (11)** jelet állítja be;
- a fogadó érzékeli a CE-t, és a visszamenő TCP-nyugtában bebillenti az **ECE** flaget, amely jelzi a forrásnak a torlódást;
- a hagyományos TCP-források (Reno, CUBIC…) az ECE-t **csomagvesztésnek értelmezik** (felezik az ablakot), de **újraküldés nem kell**.

### DCTCP — Data Center TCP

**Adatközponti forgalom:** a **Partition/Aggregate** minta sok nagy webalkalmazás alapja (keresés, közösségi oldalak; pl. a Facebook webszerverei aggregátorok, a memcached szerverek munkások). A terhelés háromféle:
- Partition/Aggregate lekérdezések — **késleltetésérzékeny**;
- rövid üzenetek (50 KB–1 MB; koordináció, vezérlési állapot) — **késleltetésérzékeny**;
- nagy folyamok (1–50 MB; adatfrissítés) — **átvitelérzékeny**.

**Problémák:**
- **Incast** — szinkronizált kis folyamok ütköznek egy switch-portnál (a Partition/Aggregate okozza); TCP-időtúllépés, és $\text{RTO}_{min} = 300$ ms, miközben az RTT < 1 ms.
- **Queue buildup** — a nagy folyamok felépítik a sorokat, ami a rövid folyamok késleltetését növeli (Bing-mérés: a csomagok 90%-ánál RTT < 1 ms, 10%-ánál 1–15 ms).
- **Buffer pressure** — a közös pufferből a nagy folyamok kiszorítják a többit.

**Követelmények:** nagy löket-tűrés (*burst tolerance*), alacsony késleltetés és nagy átvitel — **egyszerre**.

**A két kulcsötlet:**
1. **A torlódás mértékére reagáljon, ne a puszta jelenlétére.** Csökkenti a küldési ráta szórását, így kisebb sor is elég. Példa 10 ACK-ra: `1011110111` jelölésnél a TCP 50%-kal, a DCTCP 40%-kal vágja az ablakot; `0000000001`-nél a TCP szintén 50%-kal, a DCTCP csak 5%-kal.
2. **A pillanatnyi sorhossz alapján jelöljön** (nem átlag alapján) — gyors visszajelzés a löketek kezelésére.

**Algoritmus:**
- **Switch oldalon:** jelöld a csomagot (ECN), ha a sorhossz $> K$.
- **Küldő oldalon:** tartsd nyilván a jelölt csomagok arányának mozgó átlagát, $\alpha$-t. RTT-nként:
$$F = \frac{\#\,\text{jelölt ACK}}{\#\,\text{összes ACK}},\qquad \alpha \leftarrow (1-g)\,\alpha + g\,F,$$
$$\text{cwnd} \leftarrow \left(1 - \frac{\alpha}{2}\right)\text{cwnd}.$$
Ha minden csomag jelölt ($\alpha = 1$), ez a TCP-féle felezés; kevés jelölésnél csak enyhe csökkentés.

**Vizsgaszempont:** a RED három tartománya; ECN kódpontjai és a CE → ECE visszajelzés; a DCTCP ablakcsökkentési képlete és miért jobb adatközpontban, mint a TCP felezése.

## Kapocs

- [[concepts/telekom/tcp-torlodasvezerles]] — a végponti torlódásvezérlés, amelyet ezek kiegészítenek
- [[concepts/telekom/tcp]] — RTO és a TCP Incast
- [[concepts/telekom/ipv4-fejlec-es-fragmentacio]] — a szolgálat típusa mező, amelyből a DSCP/ECN lett
- [[concepts/bigdata/mapreduce]] — a Partition/Aggregate jellegű adatközponti munkaterhelés
