---
tags: [concept]
sources: [Laki_Lecture_3.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Hamming-kód a keretek hibajavításában

A Hamming-kód paritásbitek ügyes elhelyezésével egyetlen bithibát nemcsak felismer, hanem **meg is talál és kijavít**: a kettőhatvány sorszámú pozíciókon ülő ellenőrző bitek mindegyike a bitek egy csoportjának paritását állítja be, és a hibás csoportok sorszámainak összege épp a hibás bit pozíciója.

## Tartalom

### Felépítés

1. A kódszó bitjeit **1-től kezdve** számozzuk.
2. A **kettőhatvány sorszámú pozíciók** (1, 2, 4, 8, 16, …) az ellenőrző bitek.
3. A többi helyet (3, 5, 6, 7, 9, 10, 11, …) sorban az üzenet bitjeivel töltjük fel.
4. Minden ellenőrző bit a bitek egy csoportjának paritását állítja párosra (vagy páratlanra).
5. Melyik ellenőrző bit melyik pozíciót fedi? A $k$ pozíciót **kettőhatványok összegeként** írjuk fel; a felbontásban szereplő ellenőrző bitek ellenőrzik a $k$-adik pozíciót. Például $k = 13 = 1 + 4 + 8$, így a 13. bitet az 1., 4. és 8. ellenőrző bit fedi.

7 bites ASCII üzenetnél 4 ellenőrző bit kell (1, 2, 4, 8), a kódszó 11 bites. Az üzenetpozíciók felbontása:

| Pozíció | 3 | 5 | 6 | 7 | 9 | 10 | 11 |
|---|---|---|---|---|---|---|---|
| Felbontás | 1+2 | 1+4 | 2+4 | 1+2+4 | 1+8 | 2+8 | 1+2+8 |

Tehát $p_1$ a 3, 5, 7, 9, 11; $p_2$ a 3, 6, 7, 10, 11; $p_4$ az 5, 6, 7; $p_8$ a 9, 10, 11 pozíciókat fedi.

### Kódolási példa (even parity)

Az „E” karakter: ASCII 69 = `1000101`. Az üzenetbitek a 3, 5, 6, 7, 9, 10, 11 pozíciókra kerülnek: $d_3=1, d_5=0, d_6=0, d_7=0, d_9=1, d_{10}=0, d_{11}=1$.

- $p_1$: $d_3+d_5+d_7+d_9+d_{11} = 1+0+0+1+1 = 3$ → páratlan, tehát $p_1 = 1$.
- $p_2$: $d_3+d_6+d_7+d_{10}+d_{11} = 1+0+0+0+1 = 2$ → $p_2 = 0$.
- $p_4$: $d_5+d_6+d_7 = 0$ → $p_4 = 0$.
- $p_8$: $d_9+d_{10}+d_{11} = 2$ → $p_8 = 0$.

A kódszó: `10100000101`. A diák további sorai ugyanígy: L (76) → `10110011100`, T (84) → `00110101100`, szóköz (32) → `10001100000`, I (73) → `11110011001`, K (75) → `00110010011`.

### Dekódolás és javítás

A vevő egy számlálót 0-ra állít, majd minden ellenőrző bitet megvizsgál: ha a $k$-adik paritás nem stimmel, a számlálóhoz $k$-t ad.

- Ha a számláló **0**, a kapott üzenetet érvényes kódszónak tekinti.
- Ha **nem 0**, a számláló a **hibás bit sorszáma**. Például ha az 1., 2. és 8. paritás hibás, a 11. bit változott meg.

Példák:
- Fogadott „E”: `10100100101`. A $p_2$ és $p_4$ csoport hibás, számláló $= 2 + 4 = 6$ → a 6. bit hibás (valóban: `…0000…` helyett `…0100…`), átfordítva visszakapjuk a `10100000101` kódszót.
- Fogadott „L”: `11110011100`. Csak $p_2$ hibás, számláló $= 2$ → maga az ellenőrző bit sérült, az üzenet hibátlan.

### Miért működik?

Minden pozíció egyedi paritáscsoport-kombinációhoz tartozik (a bináris felírása), ezért egyetlen bithiba pontosan azokat a csoportokat rontja el, amelyek sorszámainak összege a pozíció. A kód egy bithibát javít, vagyis Hamming-távolsága legalább 3 ($2d+1$ szabály, [[concepts/telekom/hamming-tavolsag-es-korlat]]).

**Vizsgaszempont:** tipikus feladat egy 7 bites karakter Hamming-kódszavának elkészítése, illetve egy vett kódszóban a hibás bit megkeresése a számlálóval.

## Kapocs

- [[concepts/telekom/hibakezeles-alapjai]] — a paritásbit és a redundancia
- [[concepts/telekom/hamming-tavolsag-es-korlat]] — a javítóképesség elméleti háttere
- [[concepts/telekom/crc]] — detektálásra optimalizált alternatíva
- [[concepts/dimatii/hamming-kod]] — ugyanez a kód lineáris algebrai (ellenőrző mátrixos) tárgyalásban
