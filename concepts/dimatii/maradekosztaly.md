---
tags: [concept]
sources: [DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
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

### Jelölés és szerkezet (Farkas-diák)

A maradékosztályt $[a]_m$-mel vagy $\overline{a}$-val is jelölik. Ha $(a,m) = 1$, $[a]_m$ **redukált maradékosztály**. Egy TMR-ből (pl. $\{0, 1, \dots, |m|-1\}$, vagy a legkisebb abszolútértékű maradékok: páratlan $m$-re $0, \pm1, \dots, \pm\frac{|m|-1}{2}$; páros $m$-re $0, \pm1, \dots, \pm\left(\frac{|m|}{2}-1\right)$ és $\frac{|m|}{2}$ vagy $-\frac{|m|}{2}$ egyike) kiindulva a műveletek $\overline{a} + \overline{b} = \overline{a+b}$, $\overline{a}\cdot\overline{b} = \overline{a\cdot b}$. A $(\mathbb{Z}_m, +, \cdot)$ **kommutatív, egységelemes gyűrű** — lásd [[concepts/dimatii/gyuru]].

### A maradékos számolás általános elve és tipikus hiba (Lehman–Leighton–Meyer 9.7)

**Általános elv.** Összeadások és szorzások sorozatának $n$-nel vett maradékát megkapjuk, ha (1) minden operandust a maradékával helyettesítünk, és (2) minden részeredményt azonnal $[0, n)$-be redukálunk. Formálisan: $\operatorname{rem}(i+j, n) = \operatorname{rem}(i,n) +_n \operatorname{rem}(j,n)$ és $\operatorname{rem}(ij, n) = \operatorname{rem}(i,n) \cdot_n \operatorname{rem}(j,n)$, ahol $i +_n j := \operatorname{rem}(i+j,n)$, $i \cdot_n j := \operatorname{rem}(ij,n)$. Az $[0,n)$ ezekkel a műveletekkel a $\mathbb{Z}_n$ gyűrű; a kommutativitás, asszociativitás, disztributivitás, a $0$ és $1$ egységelem, valamint az additív inverz ($k + (-k) = 0$) mind érvényes benne.

**Példa.** $\operatorname{rem}\!\left((44427^{3456789} + 15555858^{5555})\cdot 403^{6666666},\ 36\right)$. Az alapok maradékai: $\operatorname{rem}(44427,36) = 3$, $\operatorname{rem}(15555858,36) = 6$, $\operatorname{rem}(403,36) = 7$, így a kifejezés $\left(3^{3456789} + 6^{5555}\right)7^{6666666}$ maradéka. A hatványok maradékai periodikusak:

- $3, 9, 27, 9, \dots$: $3^2$-től kettesével ismétlődik, így páratlan kitevőnél ($\ge 3$) $3^{3456789} \equiv 3^3 = 27$;
- $6^2 = 36 \equiv 0$, tehát $6^{5555} \equiv 0$;
- $7^6 \equiv 1 \pmod{36}$ és $6666666 = 6 \cdot 1111111$, így $7^{6666666} \equiv 1$.

Az eredmény $(27 + 0)\cdot 1 = 27$.

**Tipikus hiba.** A kitevőt **nem** szabad a maradékával helyettesíteni: az elv az *operandusokra* vonatkozik, a kitevő viszont azt mondja meg, hány szorzást végzünk. (A kitevő redukálásának helyes változata az [[concepts/dimatii/euler-fermat-tetel]], ahol a kitevőt $\varphi(m)$-mel osztjuk.)

## Kapocs

- [[concepts/dimatii/kongruencia]] — az ekvivalenciareláció, amelynek osztályai ezek
- [[concepts/dimatii/teljes-maradekrendszer]] — osztályonként egy-egy reprezentáns
- [[concepts/dimatii/redukalt-maradekrendszer]] — a modulushoz relatív prím osztályok reprezentánsai
- [[concepts/dimatii/invertalhatosag-zm-ben]] — mikor van $\overline{a}$-nak reciproka
- [[concepts/dimatii/linearis-kongruencia]] — a megoldáshalmazok, amelyek osztályok
- [[concepts/dimatii/gyuru]] — $\mathbb{Z}_m$ kommutatív, egységelemes gyűrű
