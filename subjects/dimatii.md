---
tags:
  - subject
sources:
  - DimatIIEa01.pdf
  - DimatIIEa02.pdf
  - DimatIIEa03.pdf
  - DimatIIEa04.pdf
  - DimatIIEa05.pdf
  - DimatIIEa06.pdf
  - DimatIIEa07.pdf
  - DimatIIEa08.pdf
  - DimatIIEa09.pdf
  - DimatIIEa10.pdf
derivation: source
updated: 2026-09-08
state: "[[V]]"
---

# Diszkrét matematika II. (dimatii)

A félév négy egymásra épülő tömbje: az elemi számelmélet és a kongruenciák, ezek kriptográfiai alkalmazásai, az algebrai struktúrák (félcsoporttól a testig) és a polinomelmélet, végül a kódolás — forráskódolás az entrópia felől, hibakorlátozó és lineáris kódok a véges testek felől.

## Tárgykör

- Előadó: Fancsali Szabolcs Levente (ELTE IK, Komputeralgebra Tanszék), Mérai László diái alapján
- Félév: v. félév
- Forrás: az `Egyetem/v/dimatii/_irodalom/` tíz előadásfóliája (`DimatIIEa01`–`DimatIIEa10`)

A fóliák több helyen ismételnek: az Ea02 eleje az Ea01 zárása, az Ea06 az Ea05 második fele, az Ea10 pedig szó szerint az Ea09. Ahol egy lap két fóliából merít, mindkét fájl szerepel a `sources:` mezőjében.

## Fogalomlapok

### Elemi számelmélet (1. előadás)

Az oszthatóság rendezésétől a számelmélet alaptételéig: az egész számok multiplikatív szerkezete és az azt feltáró algoritmusok.

- [[concepts/dimatii/oszthatosag]] — az $a \mid b$ reláció, alaptulajdonságai és öröklődése lineáris kombinációra
- [[concepts/dimatii/egyseg-es-asszocialt]] — egység, asszociáltság mint az oszthatóság szimmetrikus magja, triviális osztók
- [[concepts/dimatii/felbonthatatlan-es-prim]] — irreducibilitás és prímtulajdonság, a két fogalom szétválása $\mathbb{Z}[i\sqrt5]$-ben
- [[concepts/dimatii/maradekos-osztas]] — a maradékos osztás tétele, `mod`/`div` jelölés
- [[concepts/dimatii/szamrendszerek]] — $q$ alapú felírás egyértelműsége és az átváltás algoritmusa
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — lnko az oszthatósági rendezés szerint, relatív prímség
- [[concepts/dimatii/legkisebb-kozos-tobbszoros]] — lkkt, és az $(m,n)\cdot[m,n] = mn$ összefüggés
- [[concepts/dimatii/euklideszi-algoritmus]] — az algoritmus és helyességének bizonyítása
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az $xa + yb = (a,b)$ előállítás és alkalmazásai
- [[concepts/dimatii/szamelmelet-alaptetele]] — prímfelbontás, kanonikus alak, lnko/lkkt kitevős képlete
- [[concepts/dimatii/osztok-szama]] — $\tau(n) = \prod(\alpha_i+1)$
- [[concepts/dimatii/primek-eloszlasa]] — Euklidész és Dirichlet tétele, prímszámtétel, Eratoszthenész szitája

### Kongruenciák (1–2. előadás)

A modulo $m$ számolás: a reláció, a megoldható egyenlettípusok, és a maradékosztályok gyűrűje.

- [[concepts/dimatii/kongruencia]] — a definíció, alaptulajdonságok, és az egyszerűsítési tétel $m/(c,m)$-mel
- [[concepts/dimatii/linearis-kongruencia]] — megoldhatóság $(a,m) \mid b$ mellett, a megoldások száma és előállítása
- [[concepts/dimatii/linearis-diofantikus-egyenlet]] — $ax + by = c$ kongruenciás átfogalmazása
- [[concepts/dimatii/szimultan-kongruenciak]] — kongruenciarendszerek normalizálása és megoldása
- [[concepts/dimatii/kinai-maradektetel]] — a tétel és konstruktív bizonyítása
- [[concepts/dimatii/maradekosztaly]] — $\overline{a}$, a műveletek jóldefiniáltsága, $\mathbb{Z}_m$
- [[concepts/dimatii/teljes-maradekrendszer]] — reprezentánsrendszerek és az eltolás–szorzás lemma
- [[concepts/dimatii/redukalt-maradekrendszer]] — $\mathbb{Z}_m^*$ és a lemma redukált változata
- [[concepts/dimatii/invertalhatosag-zm-ben]] — nullosztó vs. invertálható elem, $\mathbb{Z}_p$ test volta
- [[concepts/dimatii/euler-fi-fuggveny]] — $\varphi(m)$, multiplikativitása és szorzatképlete
- [[concepts/dimatii/euler-fermat-tetel]] — a tétel, a kis Fermat-tétel, és alkalmazásai

### Alkalmazások: kriptográfia (3. előadás)

A kongruenciaelmélet gyakorlati hozadéka — a nyilvános kulcsú kriptográfia két alapsémája.

- [[concepts/dimatii/gyors-hatvanyozas]] — $a^n \bmod m$ $O(\log n)$ moduláris szorzással
- [[concepts/dimatii/primitiv-gyok]] — generátor $\mathbb{Z}_p^*$-ban
- [[concepts/dimatii/diszkret-logaritmus]] — az index, azonosságai modulo $p-1$, és a probléma nehézsége
- [[concepts/dimatii/rsa]] — kulcsgenerálás, helyesség az Euler–Fermat-tételből, digitális aláírás
- [[concepts/dimatii/diffie-hellman-kulcscsere]] — közös titok $g^{ab} \bmod p$ alakban

### Algebrai struktúrák (3–4. előadás)

A struktúrahierarchia grupoidtól testig, a polinomgyűrű felépítéséig.

- [[concepts/dimatii/muvelet]] — az $X^r \to X$ művelet, asszociativitás, kommutativitás
- [[concepts/dimatii/muvelettarto-lekepezes]] — az $f(x*y) = f(x) \circ f(y)$ feltétel és példái
- [[concepts/dimatii/algebrai-struktura]] — a $(H; M)$ pár, grupoid, a hierarchia váza
- [[concepts/dimatii/felcsoport-es-monoid]] — asszociativitás és semleges elem
- [[concepts/dimatii/csoport]] — inverz és egyértelműsége, Abel-csoport
- [[concepts/dimatii/gyuru]] — a gyűrű három feltétele, egységelemes és kommutatív gyűrű
- [[concepts/dimatii/nullosztomentes-gyuru]] — nullosztómentesség és a karakterisztika
- [[concepts/dimatii/integritasi-tartomany]] — kommutatív nullosztómentes gyűrű, egység vs. egységelem
- [[concepts/dimatii/test]] — ferdetest és test, „minden test nullosztómentes"
- [[concepts/dimatii/polinomgyuru]] — a polinom mint véges tartójú sorozat, $R[x]$ gyűrű volta

### Polinomok (5–7. előadás)

Az egész számok számelméletének párhuzama polinomokra: maradékos osztás, gyökök, felbonthatóság, és a végén a véges testek konstrukciója.

- [[concepts/dimatii/polinom-foka]] — fokbecslések, nullpolinom, fokösszegzés nullosztómentes esetben
- [[concepts/dimatii/helyettesitesi-ertek-es-polinomfuggveny]] — gyök, polinomfüggvény, és a két fogalom szétválása
- [[concepts/dimatii/horner-elrendezes]] — $f(c)$ $n$ szorzással, gyöktényező kiemelése
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a tétel egység főegyütthatójú osztóval
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a „legfeljebb $\deg(f)$ gyök" korlát és a $\mathbb{Z}_6$-os ellenpélda
- [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]] — kitüntetett közös osztó és a $d = uf + vg$ előállítás
- [[concepts/dimatii/polinom-algebrai-derivaltja]] — az algebrai derivált és a karakterisztika szerepe
- [[concepts/dimatii/gyok-multiplicitasa]] — többszörös gyök, és amit a derivált elárul róla
- [[concepts/dimatii/lagrange-interpolacio]] — alappolinomok, az interpolációs tétel, titokmegosztási alkalmazás
- [[concepts/dimatii/irreducibilis-polinom]] — felbonthatatlanság test fölött, gyök-kritérium $\deg \le 3$-ra
- [[concepts/dimatii/irreducibilis-polinomok-c-es-r-folott]] — az algebra alaptételének következményei
- [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]] — primitív rész, Gauss lemmája, a $\mathbb{Z}$–$\mathbb{Q}$ ekvivalencia
- [[concepts/dimatii/schonemann-eisenstein-kriterium]] — elégséges irreducibilitási feltétel $\mathbb{Z}[x]$-ben
- [[concepts/dimatii/racionalis-gyokteszt]] — a $p \mid f_0$, $q \mid f_n$ feltétel, és $\sqrt{2}$ irracionalitása
- [[concepts/dimatii/veges-testek]] — $\mathbb{Z}_p[x]$ faktorizálása irreducibilis polinommal, a $p^n$ elemű testek

### Forráskódolás (8. előadás)

Mennyi az üzenet információtartalma, és milyen rövid kód érheti el ezt a határt.

- [[concepts/dimatii/entropia]] — átlagos információtartalom és a $H_r \le \log_r k$ korlát
- [[concepts/dimatii/betunkenti-kodolas]] — kódolás, felbonthatóság, a $\varphi$/$\psi$ leképezéspár
- [[concepts/dimatii/prefix-kod]] — prefix, egyenletes és vesszős kódok felbonthatósága
- [[concepts/dimatii/mcmillan-egyenlotlenseg]] — $\sum r^{-\ell_j} \le 1$ mint a felbonthatóság feltétele
- [[concepts/dimatii/kodfa]] — a kódolás fa alakú szemléltetése
- [[concepts/dimatii/optimalis-kod]] — átlagos szóhossz és az optimális kód létezése
- [[concepts/dimatii/shannon-tetel-zajmentes-csatornara]] — $H_r \le \bar\ell < H_r + 1$
- [[concepts/dimatii/huffman-kod]] — az $r$-áris Huffman-konstrukció és optimalitása
- [[concepts/dimatii/shannon-kod]] — hosszválasztás $r^{-\ell_j} \le p_j$ szerint

### Hibakorlátozó és lineáris kódok (9–10. előadás)

Zajos csatorna: mikor vehető észre és mikor javítható a hiba, és hogyan teszi mindezt hatékonnyá a lineáris algebra.

- [[concepts/dimatii/hamming-tavolsag]] — a Hamming-metrika és a kód távolsága
- [[concepts/dimatii/hibajelzes-es-hibajavitas]] — $t$-hibajelző és $t$-hibajavító kód, ARQ és FEC
- [[concepts/dimatii/hibakorlatozo-kodolas-peldai]] — ISBN, paritásbit, kétdimenziós paritásellenőrzés
- [[concepts/dimatii/singleton-korlat]] — $|K| \le q^{n-d+1}$ és az MDS-kód
- [[concepts/dimatii/hamming-korlat]] — gömbpakolási korlát és perfekt kód
- [[concepts/dimatii/linearis-kod]] — $[n,k,d]_q$ kód mint altér, $d(K) = w(K)$
- [[concepts/dimatii/generatormatrix]] — kódolás mátrixszorzásként, szisztematikus alak
- [[concepts/dimatii/ellenorzo-matrix]] — $\mathrm{Ker}(\mathbf H) = \mathrm{Im}(\mathbf G)$ és a távolság leolvasása
- [[concepts/dimatii/szindroma-dekodolas]] — szindróma, mellékosztály-vezető, minimális távolságú dekódolás
- [[concepts/dimatii/hamming-kod]] — az $n = 2^r-1$ perfekt 1-hibajavító kód
- [[concepts/dimatii/ciklikus-kod]] — ciklikus eltolásra zárt kód

## Kapocs

- [[subjects/kript]] — a kriptográfiai alkalmazások (Caesar-kód, tökéletes biztonság, titokmegosztás) önálló tárgyalása
- [[subjects/bvszam]] — ábécé és szavak, valamint a FACTORING bonyolultsági elhelyezése
- [[subjects/linalg]] — a lineáris kódok mögötti altér- és mátrixapparátus
