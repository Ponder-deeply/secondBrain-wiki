---
tags: [concept]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Maradékosztály

Egy kongruencia megoldása gyakran nem egy konkrét szám, hanem számok egész halmaza; a maradékosztály ezt a halmazt teszi önálló objektummá, amelyekkel számolni is lehet.

## Tartalom

### Definíció

Sokszor egy probléma megoldása nem egy szám, hanem számok családja:

- $2x \equiv 5 \pmod 7$ megoldásai: $\{6 + 7\ell \,:\, \ell \in \mathbb{Z}\}$;
- $10x \equiv 8 \pmod{22}$ megoldásai: $\{14 + 22\ell\}$ és $\{3 + 22\ell\}$.

**Definíció.** Egy rögzített $m$ modulus és $a$ egész esetén az $a$-val kongruens elemek halmazát az $a$ által reprezentált **maradékosztálynak** nevezzük:
$$\overline{a} = \{x \in \mathbb{Z} \,:\, x \equiv a \pmod m\} = \{a + \ell m \,:\, \ell \in \mathbb{Z}\}.$$

**Példa.** A $2x \equiv 5 \pmod 7$ megoldása $\overline{6}$. A $10x \equiv 8 \pmod{22}$ megoldásai $\overline{14}$ és $\overline{3}$. $m = 7$ modulussal $\overline{2} = \overline{23} = \{\dots, -5, 2, 9, 16, 23, 30, \dots\}$.

**Általában:** $\overline{a} = \overline{b} \iff a \equiv b \pmod m$.

### Műveletek

A maradékosztályok között természetes módon definiálhatunk műveleteket:

$$\overline{a} + \overline{b} \;\stackrel{\text{def}}{=}\; \overline{a+b}, \qquad \overline{a}\cdot\overline{b} \;\stackrel{\text{def}}{=}\; \overline{a\cdot b}.$$

**Állítás.** Ez értelmes definíció: ha $\overline{a} = \overline{a^*}$ és $\overline{b} = \overline{b^*}$, akkor $\overline{a} + \overline{b} = \overline{a^*} + \overline{b^*}$, illetve $\overline{a}\cdot\overline{b} = \overline{a^*}\cdot\overline{b^*}$.

**Bizonyítás.** $\overline{a} = \overline{a^*}$, $\overline{b} = \overline{b^*}$ azt jelenti, hogy $a \equiv a^* \pmod m$ és $b \equiv b^* \pmod m$. A [[concepts/dimatii/kongruencia]] összeadási tulajdonsága szerint $a + b \equiv a^* + b^* \pmod m$, azaz $\overline{a+b} = \overline{a^*+b^*}$. A szorzás hasonlóan. $\square$

**Jelölés.** Rögzített $m$ modulus esetén $\mathbb{Z}_m$ a maradékosztályok halmaza az így definiált összeadással és szorzással.

**Példa.** $\mathbb{Z}_3 = \{\overline{0}, \overline{1}, \overline{2}\}$ és $\mathbb{Z}_4 = \{\overline{0}, \overline{1}, \overline{2}, \overline{3}\}$ művelettáblái közvetlenül kiszámolhatók; például $\mathbb{Z}_4$-ben $\overline{2}\cdot\overline{2} = \overline{0}$, azaz $\mathbb{Z}_4$-ben van nullosztó.

## Kapocs

- [[concepts/dimatii/kongruencia]] — az ekvivalenciareláció, amelynek osztályai ezek
- [[concepts/dimatii/teljes-maradekrendszer]] — osztályonként egy-egy reprezentáns
- [[concepts/dimatii/redukalt-maradekrendszer]] — a modulushoz relatív prím osztályok reprezentánsai
- [[concepts/dimatii/invertalhatosag-zm-ben]] — mikor van $\overline{a}$-nak reciproka
- [[concepts/dimatii/linearis-kongruencia]] — a megoldáshalmazok, amelyek osztályok
