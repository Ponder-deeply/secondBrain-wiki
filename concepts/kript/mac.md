---
tags: [concept]
sources: [hash.pdf, mac_feladatok.pdf]
derivation: source
updated: 2026-04-22
---

# MAC (Message Authentication Code)

A MAC (üzenet-hitelesítő kód) biztosítja az üzenet **integritását** és **hitelességét**: csak a kulcs birtokában lehet érvényes tag-et generálni.

## Formális definíció

$(Gen, Mac, Vrfy)$ hármas:
- $Mac_k(m) = t$ (tag)
- $Vrfy_k(m, t) = 1 \Leftrightarrow Mac_k(m) = t$

Biztonság: hamisítás-ellenálló az existential forgery under chosen-message attack (EUF-CMA) értelemben.

## CBC-MAC

$\ell$-bites tag, $E_k$ blokktitkosító, $b$-bites blokkok:

1. $m = m_1 \| \cdots \| m_{n-1} \| m_n$, ahol $m_i \in \{0,1\}^b$, $i = 1,\ldots,n-1$, $m_n$ a maradék.
2. $c_0 = 0$
3. $c_i = E_k(c_{i-1} \oplus m_i)$, $i = 1, \ldots, n-1$
4. $c_n = E_k(c_{n-1} \oplus m_n')$
5. Output: $c_n$ első $\ell$ bitje.

### CBC-MAC támadások

**Változó hosszú üzenet-hamisítás:**
- Ha $t = Mac_k(m)$ ismert, akkor $Mac_k(m \| (m' \oplus t)) = Mac_k(m')$ — az üzenet tetszőlegesen bővíthető.
- Védekezés: az üzenet hosszát az első blokkba kell kódolni.

**Kulcsfelhasználási támadás:**
- Ha ugyanazt a kulcsot $Enc$ és $MAC$ célra is használjuk, az üzenetek kölcsönösen meghamisíthatók.

## CMAC (One-Key MAC / OMAC)

A CBC-MAC változó hosszúságú üzenetekre biztonságos változata:

1. Generálj két alkulcsot: $k_0 = E_k(0)$, majd:
   - Ha $\text{msb}(k_0) = 0$: $k_1 = k_0 \ll 1$, $k_2 = k_1 \ll 1 \oplus C$
   - Ha $\text{msb}(k_0) = 1$: $k_1 = (k_0 \ll 1) \oplus C$, $k_2 = (k_1 \ll 1) \oplus C$
   - ahol $C$ egy konstans ($C_{64} = \mathtt{0x1B}$, $C_{128} = \mathtt{0x87}$).
2. Az utolsó blokkhoz $k_1$ vagy $k_2$ XOR-olódik (ha teljes blokk: $k_1$; ha nem teljes, kitöltés után $k_2$).
3. A többi lépés azonos a CBC-MAC-kal.

**Biztonság:** CMAC biztonságos változó hosszú üzenetekre; a végső blokk megkülönböztetett kezelése kizárja a hosszabbítási támadásokat.

## Nem biztonságos MAC konstrukciók

A mac_feladatok.pdf alapján az alábbiak nem biztonságosak (EUF-CMA ellen):

- $t = F_k(m_1) \oplus \cdots \oplus F_k(m_\ell)$ — blokkok sorrendje felcserélhető.
- $t = F_k(r) \oplus F_k(m_1) \oplus \cdots \oplus F_k(m_\ell)$, $(r, t)$ a tag — szintén sérülékeny.
- $t = F_k(r) \oplus F_k(\langle 1 \rangle \| m_1) \oplus \cdots \oplus F_k(\langle \ell \rangle \| m_\ell)$, $(r, t)$ a tag.

**Miért nem jó véletlen IV CBC-MAC-ban?** Véletlen $r$ IV esetén $(m, t)$ pár ismeretével könnyen hamisítható új üzenet: $m' = m \oplus r \oplus r'$, CBC-MAC-kal $E_k(r' \oplus m') = E_k(r \oplus m) = t$ — a tag változatlan.

## Kapcsolat a hash-függvényekkel

- $h$ hash-függvényből készített $t = h(m)$ tag nem biztonságos: a hash nem tartalmaz kulcsot.
- HMAC: $HMAC_k(m) = h((k \oplus \text{opad}) \| h((k \oplus \text{ipad}) \| m))$ — biztonságos konstrukció.

## Feladatok

- [[concepts/kript/feladatok]] — mac_feladatok.pdf: CBC-MAC nem biztonságos variánsok bizonyítása, véletlen IV problémája

## Kapocs

- [[concepts/kript/hash-fuggveny]] — hash-függvények és kapcsolatuk a MAC-kel
- [[concepts/kript/blokktitkositok]] — CBC-MAC alapja az E_k blokktitkosító
- [[subjects/kript]] — tantárgy áttekintő
