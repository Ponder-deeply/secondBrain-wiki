---
tags: [concept]
sources: [szelmJegyzet.pdf, 09.md]
derivation: source
updated: 2026-08-05
---

# Rice tétele

A Rice tétel (2.25. tétel) kimondja, hogy a rekurzívan felsorolható nyelvek bármely **nemtriviális tulajdonsága** eldönthetetlen — vagyis semmilyen nemtriviális, a felismert nyelvről szóló kérdést nem tudunk algoritmikusan eldönteni egy Turing-gépről.

## Fogalmak

**Tulajdonság:** $\mathcal{P} \subseteq \mathrm{RE}$, a rekurzívan felsorolható nyelvek egy osztálya. Egy $L \in \mathrm{RE}$ nyelv *rendelkezik a $\mathcal{P}$ tulajdonsággal*, ha $L \in \mathcal{P}$.

**Triviális tulajdonság:** $\mathcal{P} = \emptyset$ (egyetlen nyelvre sem teljesül) vagy $\mathcal{P} = \mathrm{RE}$ (minden nyelvre teljesül). $\mathcal{P}$ **nemtriviális**, ha $\mathcal{P} \neq \emptyset$ és $\mathcal{P} \neq \mathrm{RE}$. (Triviális tulajdonságra a kérdés eldöntése maga is triviális.)

**$L_\mathcal{P}$:** azon Turing-gép kódolások nyelve, amelyek $\mathcal{P}$-beli nyelvet ismernek fel:
$$L_\mathcal{P} = \{\langle M \rangle \mid L(M) \in \mathcal{P}\}$$

## Tétel

Ha $\mathcal{P} \subseteq \mathrm{RE}$ nemtriviális tulajdonság, akkor $L_\mathcal{P} \notin \mathrm{R}$.

## Bizonyítás

**1. eset: $\emptyset \notin \mathcal{P}$**

Legyen $L \in \mathcal{P}$ egy konkrét nyelv (ilyen létezik, mert $\mathcal{P} \neq \emptyset$), $M_L$ az azt felismerő TG. Megadjuk az $L_u \leq L_\mathcal{P}$ visszavezetést: $\langle M, w \rangle$ bemenetre konstruálunk egy $M'$ kétszalagos TG-t, amely $x$ bemeneten

- az egyik szalagján szimulálja $M$ működését a $w$ szón ($M$ és $w$ kódja be van építve $M'$ kódjába; $M'$ az univerzális TG-t hívja meg),
- ha $M$ nem fogadja el $w$-t, $M'$ nem csinál semmit, azaz $L(M') = \emptyset$,
- ha $M$ elfogadja $w$-t, $M'$ szimulálni kezdi $M_L$-t $x$-en, azaz $L(M') = L$.

Így:
$$\langle M, w \rangle \in L_u \Rightarrow L(M') = L \in \mathcal{P} \Rightarrow \langle M' \rangle \in L_\mathcal{P}$$
$$\langle M, w \rangle \notin L_u \Rightarrow L(M') = \emptyset \notin \mathcal{P} \Rightarrow \langle M' \rangle \notin L_\mathcal{P}$$

Tehát $\langle M, w \rangle \in L_u \iff \langle M' \rangle \in L_\mathcal{P}$, vagyis $L_u \leq L_\mathcal{P}$, és így $L_\mathcal{P} \notin \text{R}$.

**2. eset: $\emptyset \in \mathcal{P}$**

Alkalmazzuk az 1. esetet $\overline{\mathcal{P}} = \text{RE} \setminus \mathcal{P}$-re (amely szintén nemtriviális és $\emptyset \notin \overline{\mathcal{P}}$):
- $L_{\overline{\mathcal{P}}} \notin \text{R}$
- $L_{\overline{\mathcal{P}}} = \overline{L_\mathcal{P}}$ (mivel nem kellő alakú szavak mindkét esetben kódolnak TG-t, ahol $L(M) \in \mathcal{P}$ pontosan fordítva áll)
- $\overline{L_\mathcal{P}} \notin \text{R} \Rightarrow L_\mathcal{P} \notin \text{R}$

## Alkalmazások

Rice tétele alapján eldönthetetlen, hogy egy $M$ TG:
- az üres nyelvet ismeri-e fel ($\mathcal{P} = \{\emptyset\}$)
- véges nyelvet ismer-e fel ($\mathcal{P} = \{L \mid L \text{ véges}\}$)
- környezetfüggetlen nyelvet ismer-e fel ($\mathcal{P} = \{L \mid L \in \mathcal{L}_2\}$)
- elfogadja-e az üres szót ($\mathcal{P} = \{L \in \text{RE} \mid \varepsilon \in L\}$)

## Kapocs

- [[concepts/bvszam/r-re-nyelvek]] — $L_u$, R és RE
- [[concepts/bvszam/eldonthetetlen-problemak]] — eldönthetetlen problémák áttekintése
- [[concepts/bvszam/univerzalis-turing-gep]] — $L_u$, a visszavezetés forrása
- [[concepts/bvszam/visszavezetes]] — many-one visszavezetés
- [[concepts/bvszam/l0-re-ekvivalencia]] — $\mathcal{L}_0 = \text{RE}$
