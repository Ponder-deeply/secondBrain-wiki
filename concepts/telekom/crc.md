---
tags: [concept]
sources: [Laki_Lecture_4.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# CRC — ciklikus redundancia-ellenőrzés

A polinom-kód (CRC, *Cyclic Redundancy Check*) a bitsorozatokat $\mathbb{Z}_2$ feletti polinomoknak tekinti. A küldő úgy fűz ellenőrző biteket a kerethez, hogy az eredmény osztható legyen egy előre egyeztetett **generátorpolinommal**; ha a vevőnél az osztás maradéka nem nulla, hiba történt. Ez a legelterjedtebb hibajelző kód (Ethernet, HDLC).

## Tartalom

### Polinomok $\mathbb{Z}_2$ felett

$$p(x) = \sum_{i=0}^{n} a_i x^i = a_n x^n + \dots + a_1 x + a_0,\qquad a_i \in \{0,1\}.$$

- Minden művelet (összeadás, kivonás, szorzás, osztás) **mod 2** történik.
- A polinom az együtthatók $(a_n,\dots,a_1,a_0)$ vektorával reprezentálható. Például a „b” karakter `01100010` kódja a $p(x) = x^6 + x^5 + x$ hatodfokú polinom.
- Az összeadás és a kivonás egyaránt a **kizáró vagy (XOR)** művelet: `11110000 − 10100110 = 01010110`, `10011011 + 11001010 = 01010001`. Nincs átvitel és kölcsönkérés.

### Az algoritmus

A küldő és a vevő egyaránt ismeri a $G(x)$ generátorpolinomot, amelynek foka $r$. Az üzenet $M(x)$, $m$ bites.

1. Fűzzünk $r$ darab 0 bitet a keret alacsony helyi értékű végéhez: az $m + r$ bites sorozat az $x^r M(x)$ polinomot reprezentálja.
2. Osszuk el $x^r M(x)$-et $G(x)$-szel modulo 2.
3. Vonjuk ki a maradékot (mindig legfeljebb $r$ bites) $x^r M(x)$-ből mod 2 — azaz írjuk a hozzáfűzött nullák helyére. Az eredmény a továbbítandó keret, $T(x) = x^r M(x) + \big(x^r M(x) \bmod G(x)\big)$, amely osztható $G(x)$-szel.
4. A vevő $T(x) + E(x)$-et kapja, ahol $E(x)$ a **hibapolinom** (hiba nélkül $E(x)=0$). Ezt elosztja $G(x)$-szel: ha a maradék $R(x) \ne 0$, hiba történt.

### Kidolgozott példa

- Keret: `1101011011`, generátor: `10011` ($G(x) = x^4 + x + 1$, $r = 4$).
- Nullákkal kiegészítve: `11010110110000`.
- Maradékos osztás XOR-lépésekkel: `11010` ⊕ `10011` = `1001`, lehozva `10011` ⊕ `10011` = `0`, … végül `10100` ⊕ `10011` = `0111` → a maradék **`1110`**.
- A továbbítandó üzenet: `1101011011` **`1110`** = `11010110111110`.

A vevő ezt elosztva `10011`-gyel 0 maradékot kap.

### Milyen hibákat ismer fel?

A hibát pontosan akkor nem vesszük észre, ha $E(x)$ osztható $G(x)$-szel, például ha $E(x) = x^j G(x)$. $G(x)$ legmagasabb és legalacsonyabb fokú tagjának együtthatója mindig 1.

- **Egybites hiba**: $E(x) = x^i$ ($i$ a hibás bit sorszáma). Mivel $G(x)$ legalább két tagból áll, nem oszthatja $x^i$-t — **minden egybites hibát jelez**.
- **Két izolált egybites hiba**: $E(x) = x^i + x^j = x^j(x^{i-j} + 1)$, $i > j$. Felismerhető, ha $G(x)$ nem osztható $x$-szel, és nem osztja $(x^k + 1)$-et semmilyen, a maximális kerethossznál kisebb $k$-ra (pl. $x^{15} + x^{14} + 1$).
- **Páratlan számú hiba**: ha $E(x)$ páratlan sok tagból áll, nem lehet $x+1$ többszöröse. Ha tehát $G(x)$ az $x + 1$ többszöröse, **minden páratlan számú hiba felismerhető**.
- **Csoportos hiba**: egy $r$ ellenőrző bittel ellátott polinom-kód **minden legfeljebb $r$ hosszú burst hibát** jelez.

### A gyakorlatban

Az IEEE 802 (Ethernet) által használt CRC-32 generátor:
$$x^{32} + x^{26} + x^{23} + x^{22} + x^{16} + x^{12} + x^{11} + x^{10} + x^8 + x^7 + x^5 + x^4 + x^2 + x + 1.$$
Minden legfeljebb 32 bites hibacsomót és minden páratlan számú bitet érintő hibát jelez. Peterson és Brown (1961) megmutatta, hogy egyszerű **léptető regiszteres áramkörrel** a CRC hardverben számolható és ellenőrizhető. A HDLC a CRC-CCITT polinomot használja ([[concepts/telekom/hdlc-es-ppp]]).

**Vizsgaszempont:** a CRC kiszámítása adott keretre és generátorra kézzel (mod 2 osztás) szinte biztos feladat; mellé a felismerhető hibaosztályok felsorolása.

## Kapocs

- [[concepts/telekom/hibakezeles-alapjai]] — redundancia, FEC vs. ARQ
- [[concepts/telekom/hamming-tavolsag-es-korlat]] — a kódok hibakezelő képességének mérése
- [[concepts/telekom/hdlc-es-ppp]] — CRC a keretek lábrészében
- [[concepts/telekom/ethernet]] — 32 bites CRC a keret végén
