---
tags: [concept]
sources: [DimatIIEa03.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/diszkret-logaritmus]] — a protokoll biztonságát adó nehéz probléma
- [[concepts/dimatii/primitiv-gyok]] — a nyilvános $g$ paraméter generátor modulo $p$
- [[concepts/dimatii/gyors-hatvanyozas]] — a hatványok kiszámításának eszköze
- [[concepts/dimatii/rsa]] — a másik korai nyilvános kulcsú eljárás
- [[concepts/kript/tokeletes-biztonsag]] — az OTP kulcsátadási problémája, amit a kulcscsere old fel
