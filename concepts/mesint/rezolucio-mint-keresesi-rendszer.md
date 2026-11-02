---
tags: [concept]
sources: [09.kovetkeztetes.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Rezolúció mint keresési rendszer

A rezolúció indirekt bizonyítás: a következmény állítását az axiómák és a célállítás negáltjának klózhalmazából az üres klóz előállításával igazoljuk. A Gregorics-kurzus ezt lokális keresésként modellezi, ahol a globális munkaterület az aktuális klózhalmaz.

## Tartalom

### Feladat és átalakítás

Példa: $A_1$: ha süt a nap, Péter strandra megy ($p\to q$); $A_2$: ha strandra megy, úszik ($q\to r$); $A_3$: Péternek nincs lehetősége otthon úszni ($\neg(s\wedge r)$). Belátandó $B$: ha süt a nap, Péter nem marad otthon ($p\to\neg s$).

A logikai következmény $p\to q,\ q\to r,\ \neg(s\wedge r)\Rightarrow p\to\neg s$ azt jelenti, hogy minden, a feltételeket kielégítő interpretáció a következményt is kielégíti. Ekvivalensen: nincs olyan interpretáció, amely a feltételeket és a következmény negáltját is kielégíti, azaz

$$(p\to q)\wedge(q\to r)\wedge\neg(s\wedge r)\wedge\neg(p\to\neg s)$$

kielégíthetetlen. KNF-ben: $(\neg p\vee q)\wedge(\neg q\vee r)\wedge(\neg s\vee\neg r)\wedge p\wedge s$. (KNF: klózok közötti "és"; klóz: literálok közötti "vagy"; literál: ítéletváltozó vagy negáltja.) Meg kell mutatni, hogy bármely interpretációval legalább az egyik klóz hamis. Az átalakítás lépései: [[concepts/mesint/sknf-atalakitas]].

### Rezolúció = indirekt bizonyítás

Tegyük fel indirekt módon, hogy van olyan interpretáció, amelyben mindegyik klóz igaz. Ha $p$ igaz, akkor $\neg p$ hamis, így $\neg p\vee q$ csak úgy lehet igaz, ha $q$ is igaz. A $q$ egyetlen klóz, ezért igaz a többi klózzal együtt: hozzávehető a klózhalmazhoz. A klózhalmazt addig bővítjük, amíg ellentmondáshoz nem jutunk (például egyszerre megjelenik $q$ és $\neg q$).

### Rezolúciós lépés

Következtetési szabály: $l\vee A,\ \neg l\vee B\Rightarrow A\vee B$, ahol $l$ az eliminált komplemens literál. Az üres klóz ($\square$) ellentmondást jelez: minden interpretációban hamis. A példában $\neg p\vee q$ és $p$ adja $q$-t; $\neg s\vee\neg r$ és $s$ adja $\neg r$-t; $\neg q\vee r$ és $\neg r$ adja $\neg q$-t; $q$ és $\neg q$ adja $\square$-t. Tehát ha süt a nap, Péter nem marad otthon.

Elsőrendű esetben a komplemens literálokat helyettesítéssel (egyesítő algoritmus) azonos alakra kell hozni, a klózok változóit előbb egyedivé kell tenni. Általános szabály: ha $C_1=P(t_{11},\dots)\vee\dots\vee C_1'$ és $C_2=\neg P(u_{11},\dots)\vee\dots\vee C_2'$, és a szereplő $P$-literálok a $\delta$ helyettesítéssel egyesíthetők, akkor $R(C_1,C_2)=C_1'\delta\vee C_2'\delta$. Formális tárgyalás: [[concepts/logika/elsorendu-rezolucio]], [[concepts/logika/legaltalanosabb-illeszto-helyettesites]], propozicionális eset: [[concepts/logika/rezolucios-kalkulus]].

### Rezolúció = lokális keresés

A [[concepts/mesint/kereso-rendszer]] komponensei:

| komponens | rezolúcióban |
|---|---|
| globális munkaterület | aktuális klózhalmaz |
| kiindulási érték | az "axiómák $\Rightarrow$ célállítás" klózai |
| terminálás, sikeres | üres klóz |
| terminálás, sikertelen | nincs újabb rezolvens klóz |
| kereső szabály | rezolvens képzés |
| vezérlési stratégia | nem módosítható (alapváltozat) |
| heurisztika | hatékonyság miatt jó lenne, de nincs |

### Algoritmus

$A_1,\dots,A_n\Rightarrow B$ helyett az $A_1,\dots,A_n,\neg B$ formulák klózformájának kielégíthetetlenségét vizsgáljuk.

1. KLÓZOK := az $A_1,\dots,A_n$ és $\neg B$ klózai
2. ciklus:
3. ha $\square\in$ KLÓZOK, akkor eredmény: kielégíthetetlen;
4. ha nincs olyan $C_1,C_2\in$ KLÓZOK, amelyre $R(C_1,C_2)$ még nem ismert, akkor eredmény: nem kielégíthetetlen;
5. válasszunk $C_1,C_2\in$ KLÓZOK párt, ahol $R(C_1,C_2)$ nem ismert;
6. KLÓZOK := KLÓZOK $\cup\ R(C_1,C_2)$.

### Tulajdonságok

- **Helyes** eljárás: ha terminál, helyes eredményt ad (üres klóz esetén a kiinduló halmaz kielégíthetetlen; ha nem állítható elő új klóz, akkor kielégíthető). Elsőrendű logikában azonban nem biztos, hogy terminál.
- **Teljes** eljárás: kielégíthetetlen klózhalmazból véges lépésben levezethető az üres klóz.
- Elsőrendű logikában a kielégíthetetlenség csak **parciálisan dönthető el**, mert a módszer nem terminál garantáltan; példa: $\{\neg P(x),\ P(y)\vee\neg P(f(y)),\ P(a)\}$.

### Kritika

A rezolúció a kurzus szerint nem jó MI-módszer: a számos modellfüggő vezérlési stratégia ellenére sem hatékony (sok felesleges lépés), és heurisztika nem építhető bele, mert a klózformára hozás után az állítások nem emlékeztetnek az eredeti feladatbeli szerepükre, így nehéz "megsúgni", mely klózokkal érdemes próbálkozni. Stratégiák: [[concepts/mesint/rezolucios-strategiak]].

## Kapocs

- [[concepts/mesint/cafolati-graf]] — a keresés állapottere és a cáfolat gráfja
- [[concepts/mesint/sknf-atalakitas]] — a kiinduló klózhalmaz előállítása
- [[concepts/mesint/valaszadas-rezolucioval]] — kérdésre adott válasz kinyerése a cáfolatból
- [[concepts/mesint/rezolucios-strategiak]] — a nemdeterminizmus kezelése
- [[concepts/mesint/kereso-rendszer]] — az általános keresőrendszer-séma
- [[concepts/logika/rezolucios-kalkulus]] — formális elmélet (ítéletlogika)
- [[concepts/logika/elsorendu-rezolucio]] — formális elmélet (elsőrendű)
