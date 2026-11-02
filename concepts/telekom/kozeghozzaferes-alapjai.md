---
tags: [concept]
sources: [Laki_Lecture_5.pdf]
derivation: source
kind: definition
element: water
updated: 2026-09-25
---

# Közeghozzáférés-vezérlés (MAC) alapjai

Az Ethernet és a Wi-Fi **többszörös hozzáférésű** technológiák: az átviteli közegen több résztvevő osztozik (adatszórás, *broadcasting*), és az egyidejű átvitel **ütközést** okoz, ami meghiúsítja az átvitelt. A MAC (*Medium Access Control*) alréteg protokolljai szabályozzák, melyik állomás kapja meg a csatornahasználat jogát, és hogyan detektálják, kerülik el és oldják fel az ütközéseket.

## Tartalom

### A kulcskérdés

Eddig pont-pont összeköttetést feltételeztünk; most az **adatszóró csatornát** (*broadcast channel*) használó hálózatokkal foglalkozunk. Kulcskérdés: *melyik állomás kapja a csatornahasználat jogát?*

A csatornakiosztás lehet:

1. **statikus** — FDM, TDM ([[concepts/telekom/multiplexalas]]);
2. **dinamikus**:
   - (a) **verseny- vagy ütközésalapú** protokollok: ALOHA, CSMA, CSMA/CD ([[concepts/telekom/aloha]], [[concepts/telekom/csma]], [[concepts/telekom/csma-cd]]);
   - (b) **versenymentes** protokollok: bittérkép-alapú, bináris visszaszámlálás ([[concepts/telekom/versenymentes-protokollok]]);
   - (c) **korlátozott verseny** protokollok: adaptív fa protokollok.

### Miért nem elég a statikus kiosztás?

- **Frekvenciaosztásos nyalábolás**: $N$ felhasználó esetén a sávszélet $N$ egyenlő sávra osztják, mindegyikhez egy felhasználót rendelve. Az állomások nem zavarják egymást; előnyös, ha fix számú felhasználó van és mind nagy forgalmat támaszt. **Löketszerű forgalomnál problémás.**
- **Időosztásos nyalábolás**: az időegységet $N$ egyenlő időrésre (*slot*) osztják. **Löketszerű forgalomnál nem hatékony**: a csendes állomás slotja kárba vész, az aktív pedig nem kaphat többet.

### A dinamikus kiosztás modellje

1. **Állomásmodell**: $N$ független állomás; annak valószínűsége, hogy $\Delta t$ idő alatt csomag érkezik, $\lambda\Delta t$, ahol $\lambda$ az érkezési folyam rátája.
2. **Egyetlen csatorna**: minden állomás egyenrangú, minden kommunikáció ugyanazon a csatornán zajlik, és mindenki tud rajta küldeni és fogadni.
3. **Ütközés**: ha két keret egy időben kerül átvitelre, átlapolódnak, és a jel értelmezhetetlenné válik.
4. **Időmodell**:
   - *folytonos* — bármely állomás bármikor megkezdheti a keret sugárzását;
   - *diszkrét* — az időt résekre osztjuk, küldeni csak időrés elején lehet; egy időrés lehet **üres**, **sikeres** vagy **ütközéses**.
5. **Vivőjel-érzékelés**:
   - *nincs* — az állomások nem tudják megvizsgálni a csatorna állapotát, egyszerűen elkezdenek küldeni;
   - *van* — küldés előtt megvizsgálják, hogy a csatorna foglalt vagy szabad; foglalt csatornát nem próbálnak használni, amíg fel nem szabadul.

(Ez egy egyszerűsített modell.)

### Hatékonysági mértékek

- **Átvitel** (*throughput*, $S$): a sikeresen átvitt csomagok/keretek száma időegység alatt.
- **Késleltetés** (*delay*): egy csomag átviteléhez szükséges idő.
- **Fairség** (*fairness*): minden állomás egyenrangúként van kezelve.
- **Terhelés** ($G$): a protokoll által kezelendő csomagok (beérkező kérések) száma időegység alatt; $G > 1$ túlterhelés, hiszen a csatorna időegységenként egy kérést tud elvezetni.

Ideális esetben (egy csomag kiküldése egy időegység): ha $G < 1$, $S = G$; ha $G \ge 1$, $S = 1$. A valódi protokollok görbéi ez alatt maradnak — az ALOHA maximuma pl. csak $S \approx 0{,}18$.

**Vizsgaszempont:** a MAC-protokollok osztályozása (statikus / verseny / versenymentes / korlátozott verseny) és a modell öt feltevése.

## Kapocs

- [[concepts/telekom/multiplexalas]] — a statikus csatornakiosztás eszközei
- [[concepts/telekom/aloha]] — az első versenyalapú protokoll
- [[concepts/telekom/csma]] — vivőjel-érzékeléses protokollok
- [[concepts/telekom/versenymentes-protokollok]] — ütközésmentes kiosztás
