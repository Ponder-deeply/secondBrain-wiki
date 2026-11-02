---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-12
---

# Az A* futási ideje

A futási időt a kiterjesztések számával mérjük a zárt csúcsok $k=|\mathit{CLOSED}|$ számához képest: az alsó korlát $k$, a felső $2^{k-1}$, és Martelli példája mutatja, hogy a felső korlát el is érhető.

## Tartalom

### Korlátok

- **Alsó korlát: $k$.** Monoton megszorításos heurisztika mellett egy csúcs legfeljebb egyszer terjesztődik ki. Ettől még a kiterjesztett csúcsok száma nagyon nagy lehet (lásd egyenletes keresés).
- **Felső korlát: $2^{k-1}$.** Martelli példája mutatja, hogy ez elérhető.

### Megjegyzés: heurisztikák összevetése

Más heurisztikával ugyanazon a feladaton javítható a kiterjesztések száma, de nem biztos, hogy ez tényleges javulás, mert $k$ is változhat. A kiterjesztések számát a zárt csúcsok számához viszonyítjuk: $h_1$ mellett $k_1$ zárt csúcs és $2^{k_1-1}$ kiterjesztés, $h_2$ mellett $k_2$ zárt csúcs és $k_2$ kiterjesztés. Mégis lehet $2^{k_1-1}<k_2$, ha $k_1\ll k_2$.

### Martelli példája

$N=\{n_i\mid i=0..k\}$, $s=n_0$, $t=n_k$; $A=\{(n_i,n_j)\mid 0\le i<j<k\}\cup\{(n_{k-1},t)\}$;
$c(n_i,n_j)=2^{k-2-i}-2^{k-1-j}+j-i$ ($0\le i<j<k$);
$h(n_i)=c(s,n_{k-1})-c(s,n_i)+k-1-i$ ($0<i<k$), $h(s)=h(t)=0$;
$c(n_{k-1},t)=h(n_1)-k+2$.

Az $n_1,\dots,n_{k-1}$ csúcsokba rendre $2^0,2^1,\dots,2^{k-2}$ különböző út vezet, így elvileg $2^{k-1}$ kiterjesztés történhet, és itt ennyi is történik.

**$k=5$ működése.** A kiterjesztési sorrend: $s,\,n_4,\,n_3,\,n_4,\,n_2,\,n_4,\,n_3,\,n_4,\,n_1,\,n_4,\,n_3,\,n_4,\,n_2,\,n_4,\,n_3,\,n_4,\,t$ — összesen $16=2^{k-1}$ kiterjesztés; $n_4$ nyolcszor, $n_3$ négyszer, $n_2$ kétszer, $n_1$ egyszer. A célcsúcs $f$ értéke a végén 14 (ez az optimális költség). A csúcsok $\pi,g,f$ címkéi minden lépésben újraszámolódnak: például $n_4$ címkéje egymás után $11,10,9,8,7,6,5,4$ lesz, ahogy egyre olcsóbb út kerül elő.

**Küszöb és árok.** A diagram a kiterjesztett csúcsok $f$ értékeit mutatja: a küszöbök (piros) a növekvő $f$ értékek, közöttük az árkok (kék), ahol az $f$ csökkenő; az árkon belüli kiterjesztések számát a következő diák elemzik (e rész kívül esik az itt feldolgozott tartományon).

## Kapocs

- [[concepts/mesint/a-csillag-algoritmus]] — hatékonyság, összefoglalás
- [[concepts/mesint/a-csillag-memoriaigenye]] — $\mathit{CLOSED}$ szerinti összehasonlítás
- [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]] — a működési grafikon fogalma
- [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]] — monotonitás
- [[concepts/mesint/b-algoritmus]] — egy változat, amely az $f=g+h$ és $f=g$ kiértékelést váltogatja
