---
tags: [concept]
sources: [Laki_Lecture_2.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-09-25
---

# Fourier-analízis és sávkorlát a jelátvitelben

Vezetéken az adatot valamilyen fizikai jellemző (feszültség, áramerősség) időbeli változtatásával visszük át; ezt egy $f(t)$ függvény írja le. A Fourier-sor szerint minden periodikus jel szinuszos harmonikusok összege — a valódi csatorna viszont csak véges sok harmonikust enged át, és azokat is gyengítve, torzítva. Ezért lesz a vett négyszögjelből „hullámos” görbe.

## Tartalom

### A Fourier-sor

Bármely $T$ periódusidejű $g(t)$ periodikus függvény előáll

$$g(t) = \frac{1}{2}c + \sum_{n=1}^{\infty} a_n \sin(2\pi n f t) + \sum_{n=1}^{\infty} b_n \cos(2\pi n f t)$$

alakban, ahol

- $f = 1/T$ az **alapfrekvencia**,
- $a_n$ és $b_n$ az $n$-edik **harmonikus** szinuszos, illetve koszinuszos amplitúdója,
- $c$ a jel kétszeres átlagértéke (egyenkomponens).

Az együtthatók:

$$a_n = \frac{2}{T}\int_0^T g(t)\sin(2\pi n f t)\,dt,\qquad b_n = \frac{2}{T}\int_0^T g(t)\cos(2\pi n f t)\,dt,\qquad c = \frac{2}{T}\int_0^T g(t)\,dt.$$

### Nem periodikus digitális jel

Egy bitsorozat nem periodikus, de elképzelhetjük, hogy végtelen sokszor ismétlődik: így periodikus függvényt kapunk, amelynek periódusa a teljes bitminta (a „b” esetén 8 bitidő).

### Példa: a „b” karakter

A „b” ASCII-kódja `01100010` (8 bit). A jel Fourier-együtthatói:

$$a_n = \frac{1}{\pi n}\left[\cos\left(\frac{\pi n}{4}\right) - \cos\left(\frac{3\pi n}{4}\right) + \cos\left(\frac{6\pi n}{4}\right) - \cos\left(\frac{7\pi n}{4}\right)\right]$$

$$b_n = \frac{1}{\pi n}\left[\sin\left(\frac{3\pi n}{4}\right) - \sin\left(\frac{\pi n}{4}\right) + \sin\left(\frac{7\pi n}{4}\right) - \sin\left(\frac{6\pi n}{4}\right)\right],\qquad c = \frac{3}{4}.$$

(A $c = 3/4$ onnan jön, hogy a 8 bitből 3 egyes: az átlag $3/8$, és $c$ ennek kétszerese.)

A **harmonikus amplitúdók négyzetösszege** ($a_n^2 + b_n^2$) arányos az adott frekvencián továbbított energiával. Ha a csatorna csak az első 1, 2, 4 vagy 8 harmonikust engedi át, a visszaállított jel egyre jobban közelíti az eredeti négyszögjelet (Tanenbaum klasszikus ábrája): 1 harmonikusnál csak egy szinusz, 8 harmonikusnál már jól felismerhető a bitminta.

**Következmény:** a csatorna (jel)sávszélessége korlátozza, hány harmonikus jut át, és ezzel azt, milyen gyorsan küldhetünk biteket úgy, hogy a vevő még helyesen döntsön.

### A valódi csatorna hatásai

- **Elnyelődés / csillapítás** (*attenuation*), jele $\alpha$: a küldési ($P_0$) és vételi ($P_1$) teljesítmény hányadosa, decibelben:
  $$\alpha\,[\mathrm{dB}] = 10 \cdot \log_{10}\frac{P_0}{P_1}.$$
  Nagy elnyelődésnél kevés energia éri el a vevőt, a jel helyreállítása lehetetlen. Befolyásolja az átviteli közeg és az adó–vevő távolság. Példa: ha a vett teljesítmény a küldött fele, $\alpha = 10\log_{10}2 \approx 3$ dB.
- **Frekvenciafüggő elnyelődés**: a különböző harmonikusok eltérő mértékben gyengülnek (optikai kábelnél pl. a 0,85, 1,30 és 1,55 µm-es sávokban kicsi a csillapítás).
- **Fáziseltolódás**: a különböző frekvenciák terjedési sebessége eltér, ez frekvenciafüggő torzítást okoz.
- **Zaj**: hő, más rendszerek zavarása. A „túl rossz vétel” példáján a zajos, torzult jelből már nem olvasható ki a bitminta.

**Vizsgaszempont:** a dB-képlet és jelentése (hányados, logaritmikus skála), valamint annak megértése, hogy a sávkorlát miért torzítja a négyszögjelet.

## Kapocs

- [[concepts/telekom/halozati-alapfogalmak]] — jel- és hálózati sávszélesség különbsége
- [[concepts/telekom/szimbolumok-baud-es-bitrata]] — hogyan lehet egy jelváltással több bitet vinni
- [[concepts/telekom/atviteli-kozegek]] — a közegek csillapítási jellemzői
- [[concepts/telekom/digitalis-vonali-kodolasok]] — a bitek jellé alakítása
