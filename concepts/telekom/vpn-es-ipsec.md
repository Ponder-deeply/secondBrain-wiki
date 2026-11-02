---
tags: [concept]
sources: [Laki_Lecture_8.pdf, Laki_Lecture_9.pdf]
derivation: source
kind: definition
element: air
updated: 2026-09-25
---

# Virtuális magánhálózatok (VPN) és IPsec

A VPN (*Virtual Private Network*) fizikailag távoli hosztokat — például egy cég távoli telephelyeinek rendszereit — egy közös **logikai** hálózattá kapcsol össze úgy, hogy bérelt vonalak helyett a nyilvános Internetet használja. A virtuális linkeket **alagutakkal** (IP-az-IP-ben beágyazással) valósítják meg, a védelmet pedig az **IPsec** kriptográfiája adja.

## Tartalom

### Fő jellemzők és alapelv

- Közeli (helyi) hálózatként fut az Interneten keresztül.
- Az üzenetek titkosítására **IPsec**-et használ.
- **Alapelv:** bérelt vonalak (*leased line*) helyett a publikusan hozzáférhető Internetet használjuk; így az Internettől **logikailag** elkülöníthető hálózatot kapunk — ezek a virtuális magánhálózatok.
- A célok közé kell venni a **külső támadó kizárását**: bérelt vonalnál „nincs bejárat” (*no way in*), az Interneten viszont „talán van” (*maybe…*).

### Alagutak (tunnels)

- Egy magánhálózaton belül a hosztok egymásnak **normál módon** küldhetnek üzenetet.
- A virtuális linken az **alagút-végpontok** (*tunnel endpoint*, jellemzően a telephelyek routerei) **beágyazzák** a csomagokat: **IP az IP-be** mechanizmus. A belső csomag (belső IP-fejléc, TCP, alkalmazás) egy új, külső IP-fejlécet kap, amely a két végpont nyilvános címét tartalmazza; a túloldali végpont leveszi a külső fejlécet, és a belső csomagot a magánhálózatban továbbítja.

(Ugyanez az elv teszi lehetővé az IPv6 forgalom átvitelét IPv4 mag felett — [[concepts/telekom/ipv6]].)

**Az alagút önmagában kevés a védelemhez.** Hiányosságok: nincs **bizalmasság** és **autentikáció** — egy támadó olvashat és küldhet üzeneteket. Válasz: **kriptográfia** használata.

### IPsec

- **Hosszú távú célja** az IP-réteg biztonságossá tétele: bizalmasság és autentikáció.
- **Műveletei:**
  - hosztpárok kommunikációjához **kulcsokat** állít be;
  - a kommunikációt **kapcsolatorientáltabbá** teszi;
  - **fejléceket és lábléceket** ad az IP-csomagokhoz a védelmük érdekében.
- Több módot támogat; ezek egyike az **alagút mód** (*tunnel mode*).

**Az alagút módú csomag felépítése:**

| Új IP-fejléc | ESP-fejléc | Régi IP-fejléc | TCP-fejléc | Payload + padding | Autentikáció (HMAC) |
|---|---|---|---|---|---|

- **Titkosított** rész: a régi IP-fejléctől a payload + padding végéig (vagyis a teljes eredeti csomag — a belső címek is rejtve maradnak).
- **Autentikált** rész: az ESP-fejléctől a payload + padding végéig; ezt a végén álló **HMAC** védi.

**Vizsgaszempont:** a VPN alapelve (bérelt vonal helyett Internet + alagút), az IP-az-IP-ben beágyazás, és hogy miért kell mellé kriptográfia; az IPsec alagút módú csomag rétegei.

## Kapocs

- [[concepts/telekom/retegzett-halozati-architektura]] — beburkolás, amelyet az alagút megismétel
- [[concepts/telekom/ipv6]] — tunnelek IPv6 átvitelére IPv4 felett
- [[concepts/kript/mac]] — az üzenethitelesítő kód, amelyre a HMAC épül
- [[concepts/kript/blokktitkositok]] — a titkosítás kriptográfiai háttere
