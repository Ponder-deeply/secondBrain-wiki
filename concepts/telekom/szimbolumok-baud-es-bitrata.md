---
tags: [concept]
sources: [Laki_Lecture_2.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-09-25
---

# Szimbólumok, baud és bitráta

A fizikai rétegen nem feltétlenül egy bitet viszünk át jelelemenként: ha a jel több diszkrét szintet (vagy fázist, frekvenciát) különböztet meg, egy **szimbólum** több bitet kódol. Ezért kell különválasztani a szimbólumrátát (baud) és az adatrátát (bit/s).

## Tartalom

### Definíciók

- **Szimbólum**: a jel egy diszkrét állapota, amelyet egy jelintervallum alatt küldünk. $M$ különböző szimbólum esetén egy szimbólum $\log_2 M$ bitet hordoz.
- **Szimbólumráta (baud)**: az elküldött szimbólumok száma másodpercenként.
- **Adatráta (bps)**: az elküldött bitek száma másodpercenként.

Az összefüggés:

$$\text{bitráta} = \text{baud} \cdot \log_2 M.$$

### Példák

- 4 szimbólum: A(00), B(01), C(10), D(11). A `01 10 00 10` bitsorozat négy szimbólumként (1, 2, 0, 2 szintként) megy át — kétszer annyi bit, mint szimbólum.
- Egy **600 baudos modem**, amely **16 szimbólumot** különböztet meg: $\log_2 16 = 4$ bit/szimbólum, tehát $600 \cdot 4 = 2400$ bps adatráta érhető el.
- A modulációknál: a **QPSK** 4 fázist használ ($\pi/4, 3\pi/4, 5\pi/4, 7\pi/4$), így az adatráta a szimbólumráta kétszerese; a **QAM-16** 16 amplitúdó–fázis kombinációval négyszeres adatrátát ad ([[concepts/telekom/modulacio]]).

### Digitális és analóg átvitel

- **Digitális átvitel**: diszkrét szignálok véges halmazát használja (pl. rögzített feszültség- vagy áramerősség-értékek).
- **Analóg átvitel**: szignálok folytonos halmazát használja.
- **A digitális előnye**: a vétel pontossága és az eredeti jel helyreállítható, mert a vevőnek csak azt kell eldöntenie, melyik diszkrét szinthez van legközelebb a vett érték.
- **Az analóg hátránya**: a fellépő hibák önmagukat erősíthetik (erősítéskor a zaj is erősödik).

A több szimbólum ára: minél több szintet zsúfolunk ugyanabba az amplitúdótartományba, annál közelebb vannak egymáshoz, és annál kisebb zaj is téves döntést okoz.

**Vizsgaszempont:** a baud–bps átváltás tipikus számolási feladat; figyelni kell, hogy a szimbólumok *számából* a bitek számát logaritmussal kapjuk ($16 \to 4$ bit, nem $16$ bit).

## Kapocs

- [[concepts/telekom/fourier-analizis-es-savkorlat]] — miért korlátozott a jelváltások sebessége
- [[concepts/telekom/modulacio]] — PSK, QPSK, QAM: a szimbólumok előállítása szélessávon
- [[concepts/telekom/digitalis-vonali-kodolasok]] — alapsávú, kétszintű kódolások
