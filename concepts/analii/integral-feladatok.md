---
tags: [concept]
sources: [07_Gy_An_II_A_B.pdf, 08_Gy_An_II_A_B.pdf, 09_Gy_An_II_A_B.pdf, 10_Gy_An_II_A_B.pdf]
references: ["An II A/B 11–12. gyakorlat"]
derivation: source
updated: 2026-09-04
---

# Integrálási feladatbank

Az Analízis II. 7–12. gyakorlatok feladatainak egységes gyűjtője. Levezetések nélkül; minden feladathoz a megoldási ötlet rövid leírása. Mintakatalógus: [[concepts/analii/integral-mintak|integral-mintak]].

## 1. Feladatok

### Határozatlan integrál — alapok (Gy 7)

1. $\int (6x^2 - 8x + 3)\,dx$, $x\in\mathbb{R}$
2. $\int \dfrac{x^2}{x^2+1}\,dx$, $x\in\mathbb{R}$
3. $\int \sqrt{x\sqrt{x\sqrt{x}}}\,dx$, $x>0$
4. $\int \dfrac{\cos^2 x - 5}{1 + \cos 2x}\,dx$, $|x|<\pi/2$
5. $\int \dfrac{2x}{x^2+3}\,dx$, $x\in\mathbb{R}$
6. $\int \sin^3 x\cdot \cos x\,dx$, $x\in\mathbb{R}$
7. $\int \dfrac{dx}{x\ln x}$, $x>1$
8. $\int \sin^3 x\cdot \cos^4 x\,dx$, $x\in\mathbb{R}$
9. $\int \sin^2 x\,dx$, $x\in\mathbb{R}$
10. $\int \dfrac{dx}{\cos^2 x\cdot \sqrt{tg^3 x}}$, $x\in(0,\pi/2)$
11. $\int (x^2+2x-1)\cdot e^{-2x}\,dx$, $x\in\mathbb{R}$
12. $\int e^{2x}\cdot \sin x\,dx$, $x\in\mathbb{R}$
13. $\int x^2\cdot \ln x\,dx$, $x>0$
14. $\int arctg(3x)\,dx$, $x\in\mathbb{R}$
15. $\int \sqrt{1-x^2}\,dx$, $x\in(-1,1)$

### Racionális törtfüggvények (Gy 8)

16. $\int \dfrac{1}{(x-\alpha)^n}\,dx$, $x<\alpha$, $n\in\mathbb{N}^+$
17. $\int \dfrac{3}{2x+6}\,dx$, $x>-3$
18. $\int \dfrac{x+1}{x^2+2x+5}\,dx$, $x\in\mathbb{R}$
19. $\int \dfrac{2x+3}{x^2+2x+5}\,dx$, $x\in\mathbb{R}$
20. $\int \dfrac{1}{x^2-6x+8}\,dx$, $x\in(2,4)$
21. $\int \dfrac{3x-5}{x^2+2x+1}\,dx$, $x>-1$
22. $\int \dfrac{x^3+x^2-x+3}{x^2-1}\,dx$, $x\in(-1,1)$
23. $\int \dfrac{1}{x^3+4x}\,dx$, $x>0$
24. $\int \dfrac{x^3+9x-9}{x^4+9x^2}\,dx$, $x>0$

### Második helyettesítés — exp, gyökök (Gy 9)

25. $\int \dfrac{4}{e^{2x}-4}\,dx$, $x>\ln 2$
26. $\int \dfrac{e^{3x}}{e^x+2}\,dx$, $x\in\mathbb{R}$
27. $\int \dfrac{1}{1+\sqrt{x}}\,dx$, $x>0$
28. $\int x\sqrt{5x+3}\,dx$, $x>-3/5$
29. $\int \dfrac{1}{x^2}\cdot \sqrt[3]{\dfrac{x+1}{x}}\,dx$, $x>0$
30. $\int \dfrac{1}{\sqrt{x}+\sqrt[3]{x}}\,dx$, $x>0$

### Trigonometrikus racionális, szorzatok (Gy 10)

31. $\int \dfrac{1}{\sin x}\,dx$, $x\in(0,\pi)$
32. $\int \dfrac{1+\sin x}{1-\cos x}\,dx$, $x\in(0,\pi)$ — Weierstrass-helyettesítéssel
33. $\int \dfrac{1+\sin x}{1-\cos x}\,dx$, $x\in(0,\pi)$ — $\frac{1+\cos x}{1+\cos x}$ bővítéssel
34. $\int \dfrac{1+\sin x}{1-\cos x}\,dx$, $x\in(0,2\pi)$ — félszögekre áttéréssel
35. $\int \sin^2 x\cdot \cos^3 x\,dx$, $x\in\mathbb{R}$
36. $\int \sin^2 x\cdot \cos^4 x\,dx$, $x\in\mathbb{R}$

### Határozott integrál és alkalmazásai (Gy 11–12)

37. $\int_{10}^{66} \dfrac{1}{x-\sqrt[3]{x-2}-2}\,dx$
38. $\int_1^e \dfrac{\sin(\ln x)}{x}\,dx$
39. $\int_{-2}^{\sqrt{3}-2} \dfrac{dx}{x^2+4x+5}$
40. $\int_3^4 \dfrac{dx}{x^2-3x+2}$
41. $\int_0^\pi e^{-x}\cdot \cos^2 x\,dx$
42. Az $y=x-1$ egyenes és $y^2=2x+6$ parabola által közrezárt síkidom területe.
43. Milyen arányú részekre osztja az $y^2=2x$ parabola az $x^2+y^2=8$ kör által határolt síkrész területét?
44. Az $f(x)=\sin^2 x$ ($x\in[0,\pi]$) grafikon $x$-tengely körüli forgástestének térfogata.
45. Az $f(x) = \tfrac{2(x-1)^{3/2}}{3}$ ($2\le x\le 5$) ívhossza.
46. Bizonyítsuk: $\lim_{n\to\infty}\left(\tfrac{1}{n+1}+\cdots+\tfrac{1}{n+n}\right)=\ln 2$.

## 2. Megoldások (rövid ötlet)

1. Linearitás, $\int x^n$ alapintegrálokra bontva → $2x^3-4x^2+3x+c$.
2. Számláló: $x^2 = (x^2+1)-1$ → $x - arctg x + c$.
3. Beágyazott gyökök hatványkitevőként: $x^{7/8}$ → $\tfrac{8}{15}\sqrt[8]{x^{15}}+c$.
4. $1+\cos 2x = 2\cos^2 x$; szétbontás → $\tfrac{x}{2}-\tfrac{5}{2}tg x + c$.
5. Számláló = nevező deriváltja → $\int f'/f$ típus → $\ln(x^2+3)+c$.
6. $\cos x = (\sin x)'$ → $\int f^\alpha f'$ → $\sin^4 x/4 + c$.
7. $1/x = (\ln x)'$ → $\int f'/f$ → $\ln(\ln x) + c$ ($x>1$).
8. $\sin^3 x = (1-\cos^2 x)\sin x$ → két $\int f^\alpha f'$ → $\cos^7 x/7 - \cos^5 x/5 + c$.
9. Linearizáló: $\sin^2 x = (1-\cos 2x)/2$ → $x/2 - \sin 2x/4 + c$.
10. $1/\cos^2 x = (tg x)'$ → $\int (tg x)^{-3/2}\cdot (tg x)'$ → $-2/\sqrt{tg x}+c$.
11. Kétszer parc. int., $g' = e^{-2x}$ → polinomtényező csökken $0$-ig.
12. Kétszer parc. int. (mindkétszer trigonometrikus $g'$); az eredeti integrál visszajön; egyenletből kifejezve → $e^{2x}(2\sin x - \cos x)/5 + c$.
13. Parc. int., $g'=x^2$ így $f=\ln x$ deriválódik → $\tfrac{x^3}{3}\ln x - \tfrac{x^3}{9}+c$.
14. „1-trükk”: $\int 1\cdot arctg(3x)$; parc. int. után $\int 3x/(1+9x^2)$ = $\tfrac{1}{6}\int (1+9x^2)'/(1+9x^2)$ → $xarctg(3x)-\tfrac{1}{6}\ln(1+9x^2)+c$.
15. „1-trükk” + parc. int.; $-x^2/\sqrt{1-x^2} = ((1-x^2)-1)/\sqrt{1-x^2}$ szétbontás; egyenletből $\tfrac{x\sqrt{1-x^2}+\arcsin x}{2}+c$.
16. $n=1$: $\ln(\alpha-x)+c$; $n\ge 2$: $\int (x-\alpha)^{-n}$ → $1/((1-n)(x-\alpha)^{n-1})+c$.
17. Konstans kiemelése + $\int f'/f$ → $\tfrac{3}{2}\ln(2x+6)+c$.
18. Számlálóból $\tfrac{1}{2}(2x+2)$ kialakítása → $\int f'/f$ → $\tfrac{1}{2}\ln(x^2+2x+5)+c$.
19. Bontás: $2x+3 = (2x+2)+1$; első tag 2. alaptípus ($\ln$), másik 3. alaptípus teljes négyzettel: $(x+1)^2+4$ → $arctg((x+1)/2)/2$.
20. Faktorizáció $(x-2)(x-4)$, parciális törtek $A=-1/2$, $B=1/2$; $2<x<4$-en $\ln\sqrt{(4-x)/(x-2)}+c$.
21. $(x+1)^2$ nevező, parc. törtek $A=3$, $B=-8$; $3\ln(x+1)+8/(x+1)+c$.
22. Maradékos osztás: $x+1 + 4/(x^2-1)$; tört $\to 2/(x-1)-2/(x+1)$; $(-1,1)$-en $\tfrac{x^2}{2}+x+\ln\bigl((1-x)/(x+1)\bigr)^2+c$.
23. Nevező $x(x^2+4)$; parc. törtek $1/(4x) - x/(4(x^2+4))$ → $\tfrac{1}{4}\ln x - \tfrac{1}{8}\ln(x^2+4)+c$.
24. Nevező $x^2(x^2+9)$; parc. törtek $A=1, B=-1, C=0, D=1$ → $\ln x + 1/x + \tfrac{1}{3}arctg(x/3)+c$.
25. $t=e^x$, $x=\ln t$, $dx = dt/t$; parc. törtek $4/(t(t-2)(t+2))$ → $-x+\tfrac{1}{2}\ln(e^x-2)+\tfrac{1}{2}\ln(e^x+2)+c$.
26. $t=e^x$ → $\int t^2/(t+2)\,dt$; polinomosztás → $e^{2x}/2 - 2e^x + 4\ln(e^x+2)+c$.
27. $t=\sqrt{x}$, $x=t^2$, $dx=2t\,dt$ → $\int 2t/(1+t)\,dt$ → $2\sqrt{x}-2\ln(\sqrt{x}+1)+c$.
28. $t=\sqrt{5x+3}$, $x=(t^2-3)/5$ → polinom $t$-ben → $\tfrac{2}{125}\sqrt{(5x+3)^5}-\tfrac{2}{25}\sqrt{(5x+3)^3}+c$.
29. $t=\sqrt[3]{(x+1)/x}$, $x=1/(t^3-1)$ ($t>1$); $dx,1/x^2$ behelyettesítve $\int -3t^3\,dt$ → $-\tfrac{3}{4}\sqrt[3]{((x+1)/x)^4}+c$.
30. $x=t^6$ közös többszörös; integrandus $1/(t^3+t^2)\cdot 6t^5 = 6t^3/(t+1)$ racionális → $2\sqrt{x}-3\sqrt[3]{x}+6\sqrt[6]{x}-6\ln(\sqrt[6]{x}+1)+c$.
31. Weierstrass $t=tg(x/2)$; $\sin x = 2t/(1+t^2)$, $dx = 2/(1+t^2)\,dt$ → $\int dt/t$ → $\ln tg(x/2)+c$.
32. Weierstrass; $\sin, \cos$ behelyettesítve, parc. törtek → $-ctg(x/2)+2\ln tg(x/2)-\ln(1+tg^2(x/2))+c$.
33. $(1+\cos x)$ bővítés, nevezőben $\sin^2 x$; négy tagra szétbontás → $-ctg x + \ln tg(x/2) - 1/\sin x + \ln \sin x + c$.
34. Félszögek: $1+\sin x = 1+2\sin(x/2)\cos(x/2)$, $1-\cos x = 2\sin^2(x/2)$ → $-\operatorname{ctg}(x/2)+2\ln\sin(x/2)+c$ (a $(0,2\pi)$-en is érvényes).
35. $\cos$ páratlan: $\cos^3 = (1-\sin^2)\cos$ → $\int \sin^2\cos - \sin^4\cos$ → $\sin^3 x/3 - \sin^5 x/5 + c$.
36. Mindkét fokszám páros — két út: (a) linearizáló formulákkal fokszámfelezés és iteráció; (b) $1-\sin^2$ kifejtés + $\int\cos^n$ rekurzió. Eredmény: $-\tfrac{1}{6}\sin x\cos^5 x + \tfrac{1}{24}\sin x\cos^3 x + \tfrac{1}{16}\sin x\cos x + \tfrac{x}{16}+c$.
37. 2. helyettesítés $t=\sqrt[3]{x-2}$, $x=t^3+2$; $dx=3t^2\,dt$; integrandus $3t/(t^2-1)$ → $\tfrac{3}{2}\ln(\sqrt[3]{(x-2)^2}-1)$; Newton–Leibniz → $\tfrac{3}{2}\ln 5$.
38. $(\ln x)' = 1/x$ → $\int f\circ g\cdot g'$ alak → $-\cos(\ln x)$; $[1,e]$-n $1-\cos 1$.
39. Teljes négyzet: $x^2+4x+5 = 1+(x+2)^2$ → $arctg(x+2)$; határok $\sqrt{3}-2$, $-2$ → $\pi/3$.
40. $(x-2)(x-1)$ parc. törtek; $\ln((x-2)/(x-1))$; $[3,4]$ → $\ln(4/3)$.
41. Linearizáló: $\cos^2 = (1+\cos 2x)/2$; külön $\int e^{-x}\cos 2x$ kétszeri parc. int.-tel (visszatérő); végeredmény $V$ → $\tfrac{3}{5}(1-e^{-\pi})$.
42. Metszéspontok $(-1,-2),(5,4)$; két részre bontás $A_1$ ($-3\le x\le -1$, $\pm\sqrt{2x+6}$), $A_2$ ($-1\le x\le 5$, $\sqrt{2x+6}$ és $x-1$); $\tfrac{16}{3}+\tfrac{38}{3}=18$.
43. Metszéspontok $(2,\pm 2)$; $A_1$ ($0\le x\le 2$, $\pm\sqrt{2x}$) integrállal $16/3$; $A_2$ körszelet = derékszögű körcikk ($t(K)/4=2\pi$) − háromszög ($4$) = $2\pi-4$; arány: $(3\pi+2)/(9\pi-2)\approx 0{,}435$.
44. $V=\pi\int_0^\pi \sin^4 x\,dx$; linearizáló kétszer (vagy rekurziós formula) → $\sin^4 = \tfrac{3}{8}-\tfrac{1}{2}\cos 2x + \tfrac{1}{8}\cos 4x$ → $V = 3\pi^2/8$.
45. $f'(x)=\sqrt{x-1}$; $\sqrt{1+(f')^2} = \sqrt{x}$; $\ell = \int_2^5 \sqrt{x}\,dx = \tfrac{2}{3}(\sqrt{125}-\sqrt{8})\approx 5{,}57$.
46. Átalakítás $s_n = \tfrac{1}{n}\sum_{k=1}^n \tfrac{1}{1+k/n}$ → $f(x)=1/(1+x)$ Riemann-összege $[0,1]$-en; folytonos ⇒ integrálható → $\int_0^1 dx/(1+x) = \ln 2$.

## Kapocs

- [[concepts/analii/integral-mintak]] — a felhasznált minták indexe
- [[concepts/analii/hatarozatlan-integral]], [[concepts/analii/alapintegralok|alapintegralok]]
- [[concepts/analii/newton-leibniz-tetel]], [[concepts/analii/hatarozott-integral-helyettesites|hatarozott-integral-helyettesites]], [[concepts/analii/hatarozott-integral-parcialisintegrals|hatarozott-integral-parcialisintegrals]]
- [[concepts/analii/sikido-terulete]], [[concepts/analii/ivhossz|ivhossz]], [[concepts/analii/forgastest-terfogata|forgastest-terfogata]]
