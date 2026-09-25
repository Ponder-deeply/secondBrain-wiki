---
tags: [concept, dimatii/forraskodolas]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# Betűnkénti kódolás

Olyan kódolás, amelyben az üzenetet betűkre bontjuk, minden betűt egy szótár alapján külön kódolunk, és a kapott kódszavakat sorrendben egymás mellé írjuk.

## Tartalom

**Kódolás** alatt a legáltalánosabb értelemben az üzenetek halmazának egy másik halmazba való leképezését értjük. Ha a leképezés injektív, akkor a kódolás **felbontható**, **egyértelműen dekódolható**, vagy **veszteségmentes**; egyébként **veszteséges**, mert információvesztéssel jár.

### Ábécék és szavak

A betűnkénti kódolás során az üzenetet meghatározott módon egymáshoz átfedés nélkül csatlakozó részekre bontjuk, egy-egy ilyen részt egy szótár alapján kódolunk, és a kapott kódokat az eredeti sorrendnek megfelelően egymás láncoljuk.

Az általánosság csorbítása nélkül feltehetjük, hogy a szótár alapján kódolandó elemi üzenetek egy $A$ **ábécé** (a *kódolandó ábécé*) betűi, és egy-egy ilyen betű kódja egy másik, előbbitől nem feltétlenül különböző $B$ ábécé (a *kódoló ábécé* vagy *kódábécé*) betűivel felírt **szó**, vagyis $B$-ből vett betűk véges sorozata. Az ábécékről feltesszük, hogy nem-üresek és végesek.

Az $A$ ábécé betűivel felírható, legalább egy betűt tartalmazó szavak halmazát $A^+$ jelöli, míg az egyetlen betűt sem tartalmazó **üres szóval** (jele: $\emptyset$ vagy $\lambda$) kibővített halmazt $A^*$.

### A kódolás formalizálása

A betűnkénti kódolást egy $\varphi : A \to B^*$ leképezés határozza meg, amelyet természetes módon terjesztünk ki egy $\psi : A^* \to B^*$ leképezéssé: az $\alpha = a_1 a_2 \dots a_n \in A^*$ szóra
$$\psi(\alpha) = \varphi(a_1)\varphi(a_2)\dots\varphi(a_n).$$
Az $\mathrm{rng}(\psi)$ halmazt **kódnak** nevezzük, elemeit **kódszavaknak**.

Ha $\varphi$ nem injektív, vagy az üres szó benne van az értékkészletében, akkor a kapott $\psi$ kódolás nem injektív, tehát nem felbontható. Ezért betűnkénti kódolásnál mindig feltesszük, hogy $\varphi$ injektív, és $B^+$-ba képez.

### Prefix, szuffix, infix

Tekintsünk egy $A$ ábécét, és legyen $\alpha, \beta, \gamma \in A^*$. Ekkor $\alpha$ **prefixe** (előtagja), $\gamma$ **szuffixe** (utótagja) az $\alpha\gamma$ szónak, $\beta$ pedig **infixe** (belső tagja) az $\alpha\beta\gamma$ szónak.

Szavak egy halmazát **prefixmentes halmaznak** nevezzük, ha nincs benne két különböző szó, hogy egyik a másiknak prefixe.

Az üres szó és maga $\alpha$ is prefixe, szuffixe és infixe $\alpha$-nak; ezeket $\alpha$ **triviális** prefixeinek, szuffixeinek, illetve infixeinek nevezzük. Egy prefixet, szuffixet, illetve infixet **valódinak** nevezünk, ha nem egyezik meg $\alpha$-val.

### Példa

Legyen $A = \{a, b, c\}$, $B = \{0,1\}$, és tekintsük a következő $\varphi$ leképezéseket:

| | 1. | 2. | 3. | 4. | 5. | 6. |
|---|---|---|---|---|---|---|
| $\varphi(a)$ | 01 | 1 | 01 | 0 | 00 | 01 |
| $\varphi(b)$ | 1101 | 01 | 011 | 10 | 10 | 001 |
| $\varphi(c)$ | 01 | 10 | 11 | 11 | 11 | 0001 |

1. $\varphi(a) = \varphi(c)$, tehát $\varphi$ nem injektív;
2. $\psi(ab) = 101 = \psi(ca)$, tehát nem felbontható;
3. nem prefix, de felbontható;
4. prefix;
5. egyenletes;
6. vesszős.

## Kapocs

- [[concepts/dimatii/prefix-kod]] — a felbonthatóságot garantáló legfontosabb kódosztályok
- [[concepts/dimatii/mcmillan-egyenlotlenseg]] — mikor létezik adott szóhosszakkal felbontható betűnkénti kódolás
- [[concepts/dimatii/kodfa]] — a betűnkénti kódolás fa alakú szemléltetése
- [[concepts/dimatii/optimalis-kod]] — a lehető legrövidebb átlagos szóhosszú felbontható betűnkénti kód
- [[concepts/bvszam/abece-es-szavak]] — ugyanez az ábécé- és szófogalom a formális nyelvek oldaláról
