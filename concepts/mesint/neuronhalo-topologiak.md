---
tags: [concept]
sources: [12.neuronhalok.pdf]
derivation: source
kind: overview
element: water
updated: 2026-10-12
---

# Neuronháló topológiák

A mesterséges neuronháló három alkotóeleme a neuron, a hálózati topológia és a tanulási szabály; a topológia a neuronokból álló irányított gráf, amelynek típusai: előrecsatolt (MLP), konvolúciós és rekurrens háló.

## Tartalom

### Biológiai háttér

Az idegsejt dendritjein keletkező ingerületek összegződnek, és ha ez egy küszöböt elér, az axon mentén (membránpotenciál $-90\,\text{mV}\to +30\,\text{mV}$) továbbadódik a szomszédok dendritjeinek, a szinapszisokon át.

### Alkotóelemek

1. **Mesterséges neuron** — bemenő értékekből kimenő értéket számoló egység, amelynek képlete változtatható, tanítható ([[concepts/mesint/altalanositott-perceptron]]).
2. **Hálózati topológia** — sok neuron egymáshoz kapcsolva: az egyik kimenete a másik bemenete. Egyes neuronok a bemenetüket kívülről kapják, másokat a háló kimenetének tekintünk.
3. **Tanulási szabály** — a neuron számítási képletét meghatározó eljárás, ami lehet tanító példák alapján működő algoritmus is.

### A topológia mint gráf

Irányított gráf, csúcsai neuronok (rétegekbe csoportosíthatók), az $a\to b$ él azt jelenti, hogy $a$ kimenete $b$ bemenete. Speciális csúcsok jelölik a bemeneteket. Kapcsolat lehet:

- szomszédos rétegek között,
- rétegeken átívelő,
- rétegen belüli,
- visszacsatolás.

### Többrétegű előrecsatolt háló (feed forward MLP)

Rétegek: 0. (bemenet), 1., …, $r$. (kimenet). $o^{[s]}_j$ az $s$-edik réteg $j$-edik neuronjának kimenete, $w^{[s]}_{ij}$ az $s$-edik réteg $j$-edik neuronjában az $i$-edik bemenethez tartozó súly, $n^{[s-1]}$ az $(s-1)$-edik réteg neuronjainak száma. Minden réteg a közvetlenül előtte levő réteg kimenetét kapja.

Számítási modell (deriválható $g$ esetén):

$$f(\Theta,\mathbf{x}) = g\big(\mathbf{w}^{[r]}\cdots g(\mathbf{w}^{[2]}\, g(\mathbf{w}^{[1]}\mathbf{x}))\cdots\big),\qquad o^{[s]}_j = g\Big(\sum_{i=0}^{n^{[s-1]}} w^{[s]}_{ij}\, o^{[s-1]}_i\Big)$$

ahol $\Theta$ az összes $w^{[s]}_{ij}$ súly együttese. Tanítása: [[concepts/mesint/hiba-visszaterjesztes]].

Példa: számjegyfelismerés — $6\times 7=42$ pixel mint 42 bemenet, 10 kimeneti neuron (számjegyenként egy, amely akkor tüzel, ha a rendszer azt a számjegyet véli felismerni).

### Konvolúciós háló

Teljesen összekötött rétegnél a következő réteg egy neuronja az előző réteg minden neuronjához kapcsolódik: $1000\times1000$-es első rétegnél $10^6$ súly neurononként. Lokálisan összekötött (konvolúciós) hálónál egy $2\times2$-es szűrő használatával neurononként csak 4 súlyt kell tárolni. Részletek: [[concepts/bigdata/konvolucios-halozat]].

### Rekurrens háló

A bemenet és/vagy kimenet változó hosszúságú sorozat. A neuron "emlékszik" a korábbi bemenetekre: az új bemenetre a korábbi bemenetekre kiszámolt állapotot is felhasználva reagál. Időben kiterítve: $s_t$ az állapot, $x_t$ a bemenet, $o_t$ a kimenet; $U$ a bemenet–állapot, $V$ az állapot–állapot (visszacsatolás), $W$ az állapot–kimenet súly.

## Kapocs

- [[concepts/mesint/altalanositott-perceptron]] — a hálózat építőeleme
- [[concepts/mesint/hiba-visszaterjesztes]] — az MLP tanítása
- [[concepts/mesint/hopfield-halo]] — visszacsatolt hálótípus
- [[concepts/mesint/retegenkenti-aktivacios-fuggveny]] — rétegenként különböző $g$
- [[concepts/bigdata/konvolucios-halozat]] — a konvolúciós háló részletei
