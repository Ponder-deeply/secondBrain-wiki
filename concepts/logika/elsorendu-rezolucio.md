---
tags: [concept]
sources: [Rezolúció_II.pdf]
references: [Tk. 6.3.80, Tk. 6.3.83, Tk. 6.3.88, Tk. 278. o./6.3.90. példa]
derivation: source
updated: 2026-09-08
---

# Elsőrendű rezolúció

Az elsőrendű rezolúció az ítéletlogikai rezolúciós kalkulus elsőrendű általánosítása: két elsőrendű klóz elsőrendű rezolvense a [[concepts/logika/legaltalanosabb-illeszto-helyettesites|legáltalánosabb illesztő helyettesítéssel]] unifikált literálok elhagyásával adódó bináris rezolvensek (a szülőklózok és faktoraik közötti bináris rezolvensek) egyike; a kalkulus helyes és teljes.

## Tartalom

### Elsőrendű rezolvens (Tk. 6.3.83)

A $C_1$ és $C_2$ szülő klózok **elsőrendű rezolvense** a következő bináris rezolvensek valamelyike:

1. $C_1$ és $C_2$ [[concepts/logika/legaltalanosabb-illeszto-helyettesites|bináris rezolvense]],
2. $C_1$ és $C_2$ egy faktorának bináris rezolvense,
3. $C_1$ egy faktorának és $C_2$-nek a bináris rezolvense,
4. $C_1$ egy faktorának és $C_2$ egy faktorának a bináris rezolvense.

A faktorizáció (2–4. eset) azért szükséges, mert előfordulhat, hogy egy $S$ klózhalmaz kielégíthetetlen, de faktorizáció nélkül nem vezethető le belőle az üres klóz (Tk. 278. o./6.3.90. példa).

### Elsőrendű rezolúciós levezetés

Egy $S$ elsőrendű klózhalmazból való **rezolúciós levezetés** egy véges $k_1, k_2, \dots, k_n$ klózsorozat, ahol minden $j = 1, 2, \dots, n$-re

1. vagy $k_j \in S$,
2. vagy van olyan $1 \le s, t \le j$, hogy $k_j$ a $k_s, k_t$ klózpár elsőrendű rezolvense.

A levezetés célja az üres klóz ($\square$) levezetése — ez a megállási feltétel, akárcsak az ítéletlogikai [[concepts/logika/rezolucios-kalkulus|rezolúciós kalkulusban]].

### Példa levezetésre

Legyen $S = \{\lnot P(x) \vee Q(f(x),x),\ P(g(b)),\ \lnot Q(y,z)\}$. A levezetés $\lnot Q(y,z)$-ből indul:

1. $\lnot Q(y,z) \in S$
2. $\lnot P(x) \vee Q(f(x),x) \in S$; az 1. és 2. bináris rezolvense a $(y \| f(x)), (z \| x)$ legáltalánosabb illesztő helyettesítéssel: $\lnot P(x)$
3. $\lnot P(x)$ — a 2. lépés eredménye
4. $P(g(b)) \in S$; a 3. és 4. bináris rezolvense az $(x \| g(b))$ helyettesítéssel: $\square$
5. $\square$

Az üres klóz levezetése igazolja, hogy $S$ kielégíthetetlen.

### Helyesség (Tk. 6.3.88)

**Tétel:** ha egy $S$ elsőrendű klózhalmazból levezethető az üres klóz, akkor $S$ kielégíthetetlen.

**Bizonyítás vázlata:** legyen $k_1, k_2, \dots, k_n = \square$ egy levezetés. Tegyük fel indirekt, hogy $S$ kielégíthető. Megmutatható, hogy a levezetés minden klóza $S$ következménye: ha $k_j \in S$, akkor triviálisan $S \models k_j$; ha $k_j$ egy $s,t \le j$ indexű $k_s, k_t$ elsőrendű rezolvense, akkor $S \models k_s$ és $S \models k_t$, és a rezolvensre vonatkozó tétel szerint $\{k_s, k_t\} \models k_j$, tehát $S \models k_j$. Így $S \models \square$ is teljesülne, de az üres klóz azonosan hamis — ellentmondás. Tehát $S$ kielégíthetetlen.

### Teljesség

**Tétel:** ha az $S$ klózhalmaz kielégíthetetlen, akkor $S$-nek van elsőrendű rezolúciós cáfolata.

**Bizonyítás vázlata:** $S$ kielégíthetetlen, tehát a [[concepts/logika/herbrand-tetel|H1 tétel]] szerint van végesen zárt szemantikus fája. A véges zárt szemantikus fa biztosítja, hogy a fát lezáró alapklózhalmazból az üres klózra létezik [[concepts/logika/herbrand-tetel|alaprezolúciós]] levezetés. Ezt kell "felemelni" ($S$-beli, nem alap klózokra vonatkozó levezetéssé) — ezt biztosítja a **lifting lemma**: ha $C_1, C_2$ elsőrendű klózok valamely $\sigma$ helyettesítéssel kapott $C_1\sigma, C_2\sigma$ példányainak elsőrendű rezolvense $C^*$, akkor $C^*$ a $C_1, C_2$ klózok $C$ elsőrendű rezolvensének valamely példánya. A lemma ismételt alkalmazásával az alaprezolúciós cáfolatból egyértelműen előállítható egy elsőrendű rezolúciós cáfolat $S$-ből.

## Kapocs

- [[concepts/logika/legaltalanosabb-illeszto-helyettesites]] — a faktor és a bináris rezolvens fogalma, amire az elsőrendű rezolvens épül
- [[concepts/logika/elsorendu-kloz]] — az elsőrendű klóz és klózhalmaz, amelyeken a levezetés folyik
- [[concepts/logika/herbrand-tetel]] — a H1 tétel és az alaprezolúció, amelyre a teljességi bizonyítás épül
- [[concepts/logika/elsorendu-szemantikus-fa]] — a szemantikus fa, amelynek zártsága a teljesség bizonyításának kulcsa
- [[concepts/logika/rezolucios-kalkulus]] — az ítéletlogikai rezolúciós kalkulus, amelynek ez az elsőrendű általánosítása
