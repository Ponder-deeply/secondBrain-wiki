---
tags: [concept]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Ítéletlogika ábécéje ($V_0$)

Az ítéletlogika leíró nyelvének ábécéje, $V_0$, azon jelekből áll, amelyekből a formulák felépülnek: ítéletváltozókból, logikai összekötőjelekből és elválasztójelekből.

## Tartalom

### Nyelvdefiníció

Egy formális nyelv három komponens megadásával áll elő:

$$\text{Nyelv} = \text{Ábécé} + \text{Szintaxis} + \text{Szemantika}$$

Az ítéletlogika esetében ezek rendre a $V_0$ ábécé (ez a lap), az $L_0$ szintaxis ([[concepts/logika/iteletlogikai-formula]]) és a szemantika ([[concepts/logika/iteletlogikai-interpretacio]]).

### Az ábécé jelei

- **Ítéletváltozók** ($V_v$): $X, Y, X_i, \dots$ — a nyelv egyedüli interpretálandó jelei.
- **Unér logikai műveleti jel:** $\neg$ (negáció).
- **Binér logikai műveleti jelek:**
  - $\wedge$ (konjunkció)
  - $\vee$ (diszjunkció)
  - $\supset$ (implikáció)
- **Elválasztójelek:** `(` és `)`.

> **Jelölés.** A tantárgy az implikációt $\supset$ jellel írja, nem a máshol szokásos $\to$ vagy $\Rightarrow$ jellel. A vault más lapjain — például [[concepts/bvszam/itelet-kalkulus]] — a $\to$ szerepel; a két jelölés ugyanazt a műveletet jelenti, és a logika tárgy lapjain végig $\supset$-t használunk.

A továbbiakban $\circ$ a három binér művelet bármelyikét jelöli; ez a rövidítés teszi lehetővé, hogy a szerkezeti rekurzióval adott definíciókban a három eset egyetlen sorban szerepeljen.

### Mit ír le és mit nem

Az ítéletlogika tárgya az **egyszerű állítások** és a belőlük logikai műveletekkel kapott **összetett állítások** vizsgálata.

- **Egyszerű állítás:** olyan kijelentés, amelynek tartalmáról eldönthető, hogy igaz-e; hozzárendeljük az $i$ (igaz) vagy $h$ (hamis) igazságértéket.
- **Összetett állítás:** egyszerű állításokból álló mondat, amelynek igazságértéke **csak** az egyszerű állítások igazságértékeitől függ. Ezért csak olyan nyelvtani kötőszavakat tartalmazhat, amelyek logikai műveleteknek feleltethetők meg.

Az ábécé így szándékosan szegényes: az állítás belső szerkezetét (egyedek, tulajdonságok, kvantorok) nem ábrázolja, azok az elsőrendű logika eszközei.

### Logikai művelet mint függvény

A logikai összekötőjelek jelentése függvény. Ha $D$ az értelmezési tartomány és $R$ az értékkészlet, akkor egy $D \to R$ leképezés

- **logikai függvény (reláció)**, ha $R = \{i, h\}$,
- **logikai művelet**, ha alakja $\{i,h\}^n \to \{i,h\}$.

Így a negáció egy $\{i,h\} \to \{i,h\}$, a konjunkció, diszjunkció és implikáció pedig $\{i,h\}^2 \to \{i,h\}$ alakú logikai művelet. A $\{i,h\}^2$ jelölés a halmaz önmagával vett direktszorzata — $A \times B$ az összes olyan $(a,b)$ pár halmaza, ahol $a \in A$ és $b \in B$, $U^n$ pedig $U$ elemeiből képezhető összes $n$ elemű sorozat halmaza. A halmazelméleti előismereteket lásd: [[concepts/bvszam/halmaz-relacio-alapfogalmak]].

## Kapocs

- [[concepts/logika/iteletlogikai-formula]] — a $V_0$ jeleiből épülő $L_0$ szintaxis
- [[concepts/logika/igazsagtabla]] — a négy összekötőjel jelentése igazságtáblával
- [[concepts/logika/zarojelelhagyas]] — az elválasztójelek elhagyásának szabályai
- [[concepts/bvszam/halmaz-relacio-alapfogalmak]] — direktszorzat és függvény
- [[concepts/bvszam/itelet-kalkulus]] — ugyanez a nyelv $\to$ jelöléssel, tömörebben
