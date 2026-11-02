---
tags: [concept]
sources: [Laki_Lecture_6.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Feszítőfa protokoll (IEEE 802.1 Spanning Tree)

Ha a bridge-ekkel összekötött LAN-ok topológiájában kör van, az elárasztott keretek a végtelenségig keringenek. Az IEEE 802.1 egy elosztott algoritmust definiál egy **feszítőfa** felépítésére és karbantartására: a bridge-ek gyökeret választanak, mindegyik megkeresi a legrövidebb utat a gyökérhez, és csak ezen utak uniója mentén továbbítanak kereteket — a többi portot letiltják.

## Tartalom

### Feszítőfa

Egy gráf éleinek olyan részhalmaza, amely
- **lefed minden csomópontot**, és
- **nem tartalmaz kört**;

így a struktúra egy fa. Egy gráfnak általában több feszítőfája is van.

### A 802.1 algoritmus három lépése

1. Az egyik bridge-et megválasztjuk a fa **gyökerének**.
2. Minden bridge megkeresi a **legrövidebb utat a gyökérhez**.
3. Ezen utak **uniója** a feszítőfa.

A fa építése során a bridge-ek konfigurációs üzeneteket — **BPDU**-kat (*Configuration Bridge Protocol Data Units*) — cserélnek:
- a gyökérelem megválasztásához;
- a legrövidebb utak meghatározásához;
- a gyökérhez legközelebbi szomszéd (*next hop*) állomás és a hozzá tartozó port azonosításához;
- a feszítőfához tartozó portok kiválasztásához.

### A gyökér meghatározása

- Kezdetben **minden bridge feltételezi magáról, hogy ő a gyökér**.
- A bridge-ek minden irányba szétküldik BPDU-jukat, amelynek három mezője: **Bridge ID**, **Gyökér ID**, **útköltség a gyökérhez**.
- A fogadott BPDU-k alapján minden switch választ:
  - egy új **gyökérelemet** — a **legkisebb ismert Gyökér ID** alapján;
  - egy új **gyökérportot** — melyik interfésze megy a gyökér irányába;
  - egy új **kijelölt bridge-et** — a következő állomás a gyökérhez vezető úton.

### Példa

Hét switch, azonosítók: 0, 12, 3, 27, 41, 9, 68. A címkék `ID: gyökér/távolság` alakúak. A gyökér a legkisebb azonosítójú **0** (0/0). Közvetlen szomszédai a 12 és a 27 (0/1). A 3 és a 41 két ugrásra van (0/2): a 3 a 12-n át, a 41 a 27-en át. A 9 és a 68 három ugrásra (0/3), mindkettő a 41-en át. A fán kívül maradó élek — a 41 és a 3 közötti, valamint a 68 és a 9 közötti link — **letiltódnak** (az ábrán piros X). Az eredmény hurokmentes, és minden switch elérhető.

### Korlátok

A feszítőfa **nem foglalkozik terheléselosztással**: a letiltott linkek kihasználatlanok, a gyökér közelében forgalmi csomópontok (*hot spot*) alakulnak ki. Ez az egyik oka annak, hogy a 2. rétegbeli megoldás nem skálázható az egész Internetre ([[concepts/telekom/bridge-es-switch]]).

**Vizsgaszempont:** a BPDU mezői, a gyökérválasztás szabálya (legkisebb ID), és egy kis topológián a feszítőfa, a gyökérportok és a letiltott linkek meghatározása.

## Kapocs

- [[concepts/telekom/bridge-es-switch]] — a hurkok problémája és a címtanulás
- [[concepts/telekom/routing-alapok]] — legrövidebb utak, nyelőfa a hálózati rétegben
- [[concepts/bvszam/hamilton-np-teljes]] — a korlátozott feszítőfa probléma NP-teljessége (más kontextus)
