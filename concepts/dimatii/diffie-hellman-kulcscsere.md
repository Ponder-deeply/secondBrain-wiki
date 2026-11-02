---
tags: [concept]
sources: [DimatIIEa03.pdf, dm2gy05.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Diffie–Hellman kulcscsere protokoll

Whitfield Diffie és Martin Hellman 1976-os protokollja: két fél nem megbízható csatornán is közös titkos kulcsban tud megállapodni, anélkül hogy a kulcsot valaha átküldenék.

## Tartalom

Ez volt az első publikált nyilvános kulcsú kriptográfiai rendszer — egy évvel megelőzve az [[concepts/dimatii/rsa]]-t.

### A protokoll

**Nyilvános paraméterek:** $p$ nagy prím és $g$ generátor modulo $p$ (lásd [[concepts/dimatii/primitiv-gyok]]).

1. Alice választ egy $a \in_R \{0, \ldots, p-2\}$ titkos kulcsot, és elküldi a $g^a \bmod p$ nyilvános kulcsot.
2. Bob választ egy $b \in_R \{0, \ldots, p-2\}$ titkos kulcsot, és elküldi a $g^b \bmod p$ nyilvános kulcsot.
3. Alice kiszámolja $(g^b)^a$-t, Bob kiszámolja $(g^a)^b$-t.

Mindketten ugyanazt kapják, hiszen

$$(g^b)^a = g^{ab} = (g^a)^b \bmod p.$$

A **közös kulcs** tehát $g^{ab} \bmod p$, miközben a csatornán csak $g^a$ és $g^b$ haladt át.

### Biztonság

A protokoll biztonsága azon múlik, hogy a [[concepts/dimatii/diszkret-logaritmus]] kiszámítása nehéz: a lehallgató látja $g$-t, $p$-t, $g^a$-t és $g^b$-t, de ebből $a$-t vagy $b$-t kinyerni gyakorlatilag lehetetlen. $p \sim 2^{2048}$ (2048 bites) esetén a diszkrét logaritmus kiszámítása nagyságrendileg $10^{30}$ év.

A saját oldali számítás ezzel szemben olcsó: $g^a \bmod p$ és $(g^b)^a \bmod p$ egyaránt [[concepts/dimatii/gyors-hatvanyozas]]sal adódik.

### Példa

Nyilvános paraméterek: $p = 11$, $g = 2$.

- Alice titkos kulcsa $a = 4$, nyilvános kulcsa $2^4 \equiv 5 \pmod{11}$.
- Bob titkos kulcsa $b = 8$, nyilvános kulcsa $2^8 \equiv 3 \pmod{11}$.
- Közös kulcs: $(g^b)^a = 3^4 \equiv 4$ és $(g^a)^b = 5^8 \equiv 4 \pmod{11}$.

### Miért kellett

A klasszikus szimmetrikus sémák — például a [[concepts/kript/tokeletes-biztonsag]] lapon tárgyalt One-Time Pad — kritikus pontja épp a titkos kulcs átadása. A Diffie–Hellman ezt a problémát oldja meg: a kulcs sosem utazik a csatornán.

### Feladattípusok (2024. 5. sorozat)

**1. Közös kulcs titkos kulcsokból.** $p = 11$, $g = 2$, $a = 3$, $b = 4$: $A = 2^3 = 8$, $B = 2^4 = 5$, közös kulcs $B^a = 5^3 \equiv 4 \equiv A^b = 8^4 \pmod{11}$.

**2. Nyilvános és titkos kulcs keveredik.** $p = 13$, $g = 2$, Alice *nyilvános* kulcsa $A = 7$, Bob *titkos* kulcsa $b = 4$: a közös kulcs $A^b = 7^4 \equiv 9 \pmod{13}$ (ellenőrzés: Alice titkos kulcsa a $\log_2 7 = 11$, Bob nyilvános kulcsa $2^4 \equiv 3$, és $3^{11} \equiv 9$). Itt nem kell a diszkrét logaritmus, elég $A^b$.

**3. Két nyilvános kulcs.** $p = 17$, $g = 3$, $A = 7$, $B = 8$: a közös kulcs csak a diszkrét logaritmus ismeretében számolható ki (kis $p$-nél táblázatból): $\log_3 7 = 11$, $\log_3 8 = 10$, így $7^{10} \equiv 8^{11} \equiv 2 \pmod{17}$. A kérdés „mi *lehet*" — a $\log_3$ egyértelmű $\bmod 16$-ra, ezért a közös kulcs egyértelmű: $2$. Lásd [[concepts/dimatii/diszkret-logaritmus]].

## Kapocs

- [[concepts/dimatii/diszkret-logaritmus]] — a protokoll biztonságát adó nehéz probléma
- [[concepts/dimatii/primitiv-gyok]] — a nyilvános $g$ paraméter generátor modulo $p$
- [[concepts/dimatii/gyors-hatvanyozas]] — a hatványok kiszámításának eszköze
- [[concepts/dimatii/rsa]] — a másik korai nyilvános kulcsú eljárás
- [[concepts/kript/tokeletes-biztonsag]] — az OTP kulcsátadási problémája, amit a kulcscsere old fel
- [[concepts/dimatii/szamelmeleti-nyitott-problemak]] — a faktorizálás nehézsége, az RSA biztonsági alapja
