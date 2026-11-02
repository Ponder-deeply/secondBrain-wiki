---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Homomorfizmus és izomorfizmus

Művelettartó leképezések elnevezései (epi-, mono-, izo-, endo-, automorfizmus), az összetétel és az inverz tulajdonságai, valamint az, hogy a homomorf kép megőrzi a félcsoport-tulajdonságot, az egységelemet, az inverzeket és a felcserélhetőséget.

## Tartalom

### Elnevezések

Legyen $\cdot$ a $G$-n, $\otimes$ a $G'$-n értelmezett bináris művelet. A $\varphi : G \to G'$ függvény **homomorfizmus**, ha műveletőrző: minden $a_1, a_2 \in G$ esetén

$$\varphi(a_1 a_2) = \varphi(a_1) \otimes \varphi(a_2).$$

- **epimorfizmus**: szürjektív homomorfizmus;
- **monomorfizmus**: injektív homomorfizmus;
- **izomorfizmus**: bijektív homomorfizmus;
- **endomorfizmus**: $G = G'$;
- **automorfizmus**: $G = G'$ és bijektív.

### Összetétel és inverz

- Homomorfizmusok összetétele homomorfizmus: ha $\varphi' : G' \to G''$ is az, akkor $(\varphi' \circ \varphi)(xy) = \varphi'(\varphi(x)\varphi(y)) = \varphi'(\varphi(x))\,\varphi'(\varphi(y))$.
- Izomorfizmusok összetétele izomorfizmus.
- Izomorfizmus inverze is izomorfizmus: $\varphi^{-1}(\varphi(x)\varphi(y)) = \varphi^{-1}(\varphi(xy)) = xy = \varphi^{-1}(\varphi(x))\,\varphi^{-1}(\varphi(y))$.

### Izomorf struktúrák

A $(H, \cdot)$ és $(G, \otimes)$ bináris műveletes struktúrák **izomorfak** ($H \cong G$), ha létezik $\varphi : G \to H$ izomorfizmus. A $\varphi(G)$ halmaz $G$ **homomorf képe**.

Példák:

1. $a > 1$ esetén az $x \mapsto a^x$ leképezés $(\mathbb{R}, +)$-t a pozitív valós számok szorzásra vett csoportjára izomorfan képezi.
2. $(\mathbb{R}, +)$ és $(\mathbb{R} \setminus \{0\}, \cdot)$ **nem** izomorfak: a másodikban két olyan elem van ($1$ és $-1$), amelynek négyzete az egységelem, az elsőben csak a $0$.

### Homomorf invariánsok félcsoportban

Ha $G$ félcsoport, a $\varphi$ által adott homomorf képre (a képelemeket $'$ jelöli):

1. a homomorf kép is félcsoport: $(a'b')c' = (ab)'c' = (abc)' = a'(bc)' = a'(b'c')$;
2. ha $e$ jobb oldali / bal oldali egységelem / egységelem $G$-ben, akkor $e'$ is az a képben: $g'e' = (ge)' = g'$;
3. ha $g^*$ jobb oldali / bal oldali inverze / inverze $g$-nek, akkor $g^{*\prime}$ ugyanaz $g'$-nek: $g' g^{*\prime} = (gg^*)' = e'$;
4. ha $g$ és $h$ felcserélhető, akkor $g'$ és $h'$ is: $g'h' = (gh)' = (hg)' = h'g'$.

Ezek miatt a félcsoport-, egységelem-, inverz- és kommutativitás-tulajdonságok izomorfia alatt öröklődnek. Fordítva, az ellenpélda (2) mutatja, hogy egy ilyen megkülönböztető tulajdonság (pl. az egységelem négyzetgyökeinek száma) nem-izomorfiát bizonyít.

## Kapocs

- [[concepts/dimatii/muvelettarto-lekepezes]] — a művelettartás alapfogalma, amelynek a homomorfizmus az általánosítása
- [[concepts/dimatii/algebrai-struktura]] — a struktúrák, amelyek között a leképezés hat
- [[concepts/dimatii/felcsoport-es-monoid]] — egységelem és inverz a félcsoportban
- [[concepts/dimatii/csoport]] — csoportok izomorfiája
