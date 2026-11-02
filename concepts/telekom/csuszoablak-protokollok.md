---
tags: [concept]
sources: [Laki_Lecture_4.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Csúszóablak protokollok: go-back-N és szelektív ismétlés

A csúszóablak (*sliding window*) protokollokban egyszerre több keret is úton lehet: a küldő legfeljebb $n$ (az ablakméretnyi) nyugtázatlan keretet küldhet, a fogadó $n$ keretnyi puffert tart. Ez a *pipelining*, amely a nagy sávszélesség–késleltetés szorzatú vonalakat is kihasználja. Hiba esetén két stratégia van: **visszalépés N-nel** (*go-back-N*) és **szelektív ismétlés** (*selective repeat*).

## Tartalom

### Alapok

**Általános:**
- Egy időben több keret is átviteli állapotban lehet.
- A fogadó $n$ keretnek megfelelő puffert allokál; a küldő legfeljebb $n$ nyugtázatlan keretet küldhet.
- A keret sorozatbeli pozíciója adja a címkéjét (**sorozatszám**).

**Fogadó:**
- A nyugta a **következőnek várt** keret sorozatszámát tartalmazza.
- **Kumulatív nyugta**: egy nyugta több keretet is nyugtáz. Ha a 2, 3 és 4 keretet fogadtuk, egyetlen „5” nyugta mindhármat nyugtázza.
- A hibás és a nem megengedett sorozatszámú kereteket el kell dobni.

**Jellemzők:**
- A küldő nyilvántartja a küldhető sorozatszámok halmazát (**adási ablak**), a fogadó a fogadhatókét (**vételi ablak**).
- A sorozatszámok halmaza véges: $K$ bites mezőnél $[0 \,..\, 2^K - 1]$.
- Az adási ablak minden küldéssel szűkül, és minden nyugtával nő (csúszik).

### Példa: 3 bites sorozatszám

Sorozatszámok 0–7, ablakméret 7. A küldő elküldi a 0, 1, 2 keretet; a fogadó „ACK 3”-mal nyugtáz (a következő várt a 3), mire a küldő ablaka a 3–1 tartományra csúszik (körbeérve). Elküldi a 3, 4, 5, 6 keretet; „ACK 7” után az ablak ismét továbbcsúszik.

### Kétirányú forgalom és piggybacking

A gyakorlatban duplex adatfolyamot kell kezelni: vagy két külön szimplex csatornával (két áramkör), vagy egy csatornán. Utóbbinál a **piggybacking**: a kimenő nyugtát késleltetjük, hogy a következő kimenő adatkeretre „akaszthassuk” (a keret *ack* mezőjében). Az **egybites csúszóablak** (ablakméret 1) állapotgépe: A elkéri a datagramot a hálózati rétegtől → keretet épít és küld → B ellenőrzi → ha rendben, átadja a hálózati rétegnek, és nyugtát küld a hibátlan keret sorszámával → A ellenőrzi a nyugta sorszámát: ha rendben, új datagramot kér, ha nem, újraküld.

### Pipelining

Eddig feltettük, hogy a keret oda- és a nyugta visszaútja (RTT) elhanyagolható. A nagy RTT viszont rontja a kihasználtságot ([[concepts/telekom/megall-es-var-protokoll]]). **Ha az adatsebesség és az RTT szorzata nagy, érdemes nagy adási ablakot használni.** Szemléletesen: az ablaknak legalább akkorának kell lennie, hogy a küldő egy teljes RTT-n át folyamatosan küldhessen.

### Hiba egy hosszú folyam közepén

**Visszalépés N-nel (go-back-N)**
- A fogadó a hibás keret **utáni összes keretet eldobja**, és nem is nyugtázza őket.
- Amikor a küldő időzítője lejár, az **összes nyugtázatlan keretet** újraküldi, a sérült vagy elveszett kerettől kezdve.
- Egy méretű vételi ablakot feltételez; nagy hibaarány esetén sok sávszélességet pazarol.
- Példa: a 2-es keret hibás (E), a 3–8 kereteket a vevő eldobja (D); időtúllépés után a küldő 2-től kezdve mindent újraküld: 2, 3, 4, …

**Szelektív ismétlés (selective repeat)**
- A fogadó a hibás keretet eldobja, de a **hibás utáni jó kereteket puffereli**.
- Időtúllépéskor a küldő csak a **legrégebbi nyugtázatlan** keretet küldi újra.
- Negatív nyugta (**NAK**) használatával tovább javítható a hatékonyság.
- Egynél nagyobb vételi ablakot feltételez; nagy vételi ablaknál nagy a memóriaigény.
- Példa: a 2-es keret hibás, a 3–8 kereteket a vevő pufferben tartja; a küldő csak a 2-est küldi újra, utána folytatja a 9, 10, … kerettel.

| | Go-back-N | Szelektív ismétlés |
|---|---|---|
| Vételi ablak | 1 | > 1 |
| Hibás utáni jó keretek | eldobja | puffereli |
| Újraküldés | minden nyugtázatlan | csak a hibás |
| Költség | sávszélesség | memória |

**Vizsgaszempont:** a két stratégia összehasonlítása és egy idővonalas példa végigkövetése; a kumulatív nyugta jelentése; a sorozatszám-tartomány $K$ bitre.

## Kapocs

- [[concepts/telekom/megall-es-var-protokoll]] — az egykeretes eset és a kihasználtsági probléma
- [[concepts/telekom/hdlc-es-ppp]] — a HDLC 3 bites csúszóablakot használ
- [[concepts/telekom/tcp]] — a szállítói réteg csúszóablaka
