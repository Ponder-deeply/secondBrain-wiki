---
tags: [concept]
sources: [Laki_Lecture_2.pdf]
derivation: source
kind: comparison
element: air
updated: 2026-09-25
---

# Moduláció: alapsáv és szélessáv

Alapsávú átvitelnél a digitális jel közvetlenül árammá vagy feszültséggé alakul; szélessávú átvitelnél egy szinuszos **vivőhullám** amplitúdóját, frekvenciáját vagy fázisát változtatjuk a jel szerint. Digitális jelnél ezeket *keying*-nek (billentyűzésnek) nevezik: ASK, FSK, PSK, illetve kombinációjuk, a QAM.

## Tartalom

### Alapsáv és szélessáv

- **Alapsáv** (*baseband*): a digitális jel direkt árammá vagy feszültséggé alakul; a jel minden frekvencián átvitelre kerül; átviteli korlátok (távolság, sávszélesség) terhelik. Kódolásai: [[concepts/telekom/digitalis-vonali-kodolasok]].
- **Szélessáv** (*broadband*): egy széles frekvenciatartományban történik az átvitel. A jel modulálásának lehetőségei:
  - az adatok vivőhullámra „ültetése” (amplitúdómoduláció);
  - a vivőhullám megváltoztatása (frekvencia- vagy fázismoduláció);
  - különböző vivőhullámok egyidejű használata.

A két lánc felépítése:

- alapsáv: forráskódolás → csatornakódolás → fizikai átvitel → **médium** → fizikai vétel → csatornadekódolás → forrásdekódolás;
- szélessáv: ugyanez, de a csatornakódolás után **moduláció**, a vétel után **demoduláció** is van. A csatornaszimbólumokból a moduláció egy *véges hullámforma-halmaz* elemeit állítja elő.

### A szinuszrezgés paraméterei

$$s(t) = A\sin(2\pi f t + \varphi),$$

ahol $A$ az amplitúdó, $f$ a frekvencia ($T = 1/f$ a periódusidő), $\varphi$ a fáziseltolás. A három moduláció pontosan ezt a három paramétert „használja fel”.

### A három alapmoduláció

| Moduláció | Képlet | Analóg jelre | Digitális jelre |
|---|---|---|---|
| **Amplitúdó** | $f_A(t) = s(t)\cdot\sin(2\pi f t + \varphi)$ | AM | **ASK** (*amplitude shift keying*): a szignál erőssége egy diszkrét halmaz értékei szerint változik |
| **Frekvencia** | $f_F(t) = a\cdot\sin(2\pi\, s(t)\, t + \varphi)$ | FM | **FSK**: a szimbólumokhoz különböző frekvenciák tartoznak |
| **Fázis** | $f_P(t) = a\cdot\sin(2\pi f t + s(t))$ | PM (nem igazán használják) | **PSK**: a szimbólumokhoz különböző fázisok tartoznak |

Itt $s(t)$ a modulálandó (hasznos) jel, $f$ a vivő frekvenciája, $a$ állandó amplitúdó. Ránézésre: AM-nél a vivő „burkolója” követi a jelet, FM-nél a hullámok sűrűsödnek és ritkulnak, PSK-nál a fázisváltásoknál „törés” van a hullámban.

### Több szimbólum: QPSK és QAM

- **PSK több szimbólummal**: a fáziseltolások a vevő számára könnyen felismerhetők. 4 szimbólum esetén a fázisok $\pi/4, 3\pi/4, 5\pi/4, 7\pi/4$ — ez a **QPSK** (*Quadrature Phase Shift Keying*): 2 bit/szimbólum, tehát a szimbólumrátához képest **kétszeres** adatráta.
- **Amplitúdó- és fázismoduláció kombinálva**: 16 különböző (amplitúdó, fázis) pár — ez a **QAM-16** (*Quadrature Amplitude Modulation*): 4 bit/szimbólum, **négyszeres** adatráta.

A szimbólumokat a *konstellációs diagramon* ábrázoljuk: a pont szöge a fázis, az origótól vett távolsága az amplitúdó. QPSK-nál 4 pont egy körön, QAM-16-nál 4×4-es rács.

**Vizsgaszempont:** a három moduláció képlete és hogy melyik paramétert kódolja; QPSK/QAM-16 bit/szimbólum értéke; alapsáv vs. szélessáv láncának különbsége (moduláció/demoduláció).

## Kapocs

- [[concepts/telekom/szimbolumok-baud-es-bitrata]] — baud és bps kapcsolata
- [[concepts/telekom/digitalis-vonali-kodolasok]] — az alapsávú párja
- [[concepts/telekom/multiplexalas]] — különböző vivők egyidejű használata (FDM)
