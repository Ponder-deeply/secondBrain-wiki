---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Gráf fogalmak ($\delta$-gráf, utak, költségek)

Az útkeresés gráfelméleti alapjai: irányított, élsúlyozott gráf, amelynek kifoka véges és élköltségei egy pozitív $\delta$ alulról korlátozza ($\delta$-gráf).

## Tartalom

### Gráf és élköltség

| Fogalom | Jelölés |
|---|---|
| csúcsok, irányított élek | $N$, $A\subseteq N\times N$ (végtelen számosság is lehet) |
| él $n$-ből $m$-be | $(n,m)\in A$ |
| $n$ utódai | $\Gamma(n)=\{m\in N \mid (n,m)\in A\}$ |
| $n$ szülei | $\pi(n)\in\Pi(n)=\{m\in N\mid (m,n)\in A\}$ |
| irányított gráf | $R=(N,A)$ |
| véges sok kivezető él | $\lvert\Gamma(n)\rvert<\infty$ minden $n\in N$-re |
| élköltség | $c:A\to\mathbb{R}$ |
| $\delta$-tulajdonság ($\delta\in\mathbb{R}^+$) | $c(n,m)\ge\delta>0$ minden $(n,m)\in A$-ra |
| $\delta$-gráf | $\delta$-tulajdonságú, véges sok kivezető élű, élsúlyozott irányított gráf |

### Utak és költségek

- **Irányított út:** $\alpha=(n,n_1),(n_1,n_2),\dots,(n_{k-1},m)=\langle n,n_1,\dots,n_{k-1},m\rangle$.
- Jelölések: $n\overset{\alpha}{\longrightarrow}m$, $n\to m$, $n\to M$ ($M\subseteq N$); az utak halmaza $\{n\to m\}$, $\{n\to M\}$.
- **Út hossza:** az út éleinek száma, $\lvert\alpha\rvert$.
- **Út költsége:** $c(\alpha)=c^\alpha(n,m)=\sum_{i=1}^{k}c(n_{i-1},n_i)$, ha $\alpha=\langle n=n_0,\dots,n_k=m\rangle$.
- **Optimális költség:** $c^*(n,m)=\min_{\alpha\in\{n\to m\}}c^\alpha(n,m)$, illetve $c^*(n,M)=\min_{\alpha\in\{n\to M\}}c^\alpha(n,M)$. $\delta$-gráfokban ez végtelen sok út esetén is értelmes; értéke $\infty$, ha nincs egy út se.
- **Optimális költségű út:** $n\to^* m:=\min_c\{\alpha\mid\alpha\in\{n\to m\}\}$, illetve $n\to^* M$ hasonlóan.

## Kapocs

- [[concepts/mesint/utkeresesi-problema]] — a fogalmak felhasználása
- [[concepts/mesint/es-vagy-grafok]] — hipergráfra kiterjesztve
- [[concepts/mesint/graf-reprezentacio]] — implicit/explicit megadás
