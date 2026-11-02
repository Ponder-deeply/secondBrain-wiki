---
tags: [concept]
sources: [04.visszalep.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Visszalépéses keresés

A visszalépéses keresés (backtracking) olyan keresőrendszer, amelynek globális munkaterülete egyetlen út a startcsúcsból az aktuális csúcsba, és a vezérlés a visszalépés szabályát csak a legvégső esetben alkalmazza.

## Tartalom

A visszalépéses keresés a [[concepts/mesint/kereso-rendszer]] egy speciális esete:

- **Globális munkaterület:** egy út a startcsúcsból az aktuális csúcsba (az útról leágazó, még ki nem próbált élekkel együtt). Kezdetben a startcsúcsot tartalmazó nulla hosszúságú út.
- **Keresés szabályai:** a nyilvántartott út végéhez egy új (ki nem próbált) él hozzáfűzése, vagy a legutolsó él törlése (a visszalépés szabálya).
- **Vezérlési stratégia:** a visszalépés szabályát csak a legvégső esetben alkalmazza, vagyis amikor [[concepts/mesint/visszalepes-feltetelei]] valamelyike fennáll.
- **Terminálás:** célcsúcs elérésekor (siker), vagy a startcsúcsból való visszalépéskor (kudarc).

### Változatok

- **VL1:** a visszalépés feltételei közül az első kettőt (zsákutca, zsákutca-torkolat) építjük be. Bizonyítható: véges körmentes irányított gráfokon mindig terminál, és ha létezik megoldás, talál egyet (az ok: egy startcsúcsból induló útból véges sok van). Rekurzív algoritmussal implementálják, indítása `megoldás := VL1(startcsúcs)`.
- **VL2:** mind a négy feltételt beépítjük (kör és mélységi korlát is). Bizonyítható: $\delta$-gráfban mindig terminál; ha létezik a mélységi korlátnál nem hosszabb megoldás, talál egyet. Lásd [[concepts/mesint/melysegi-korlatos-visszalepes]].

### VL1 algoritmusa

```
Recursive procedure VL1(akt : N) return (A*; hiba)
1. if cél(akt) then return(nil) endif
2. for ∀új ∈ Γ(akt) loop
3.     megoldás := VL1(új)
4.     if megoldás ≠ hiba then
5.         return(fűz((akt,új), megoldás)) endif
6. endloop
7. return(hiba)
end
```

$N$ a csúcsok, $A$ az élek halmaza, $A^*$ a véges élsorozatok halmaza.

### VL2 algoritmusa

```
Recursive procedure VL2(út : N*) return (A*; hiba)
1. akt := utolsó_csúcs(út)
2. if cél(akt) then return(nil) endif
3. if hossza(út) ≥ korlát then return(hiba) endif
4. if akt ∈ maradék(út) then return(hiba) endif
5. for ∀új ∈ Γ(akt) − π(akt) loop
6.     megoldás := VL2(fűz(út, új))
7.     if megoldás ≠ hiba then
8.         return(fűz((akt,új),megoldás)) endif
9. endloop
10. return(hiba)
end
```

Indítás: `megoldás := VL2(<startcsúcs>)`. A 3. sor a mélységi korlát, a 4. sor a kör vizsgálata.

### Nyomkövetés

A diák az $n$-királynő problémát ([[concepts/mesint/n-kiralyno-problema]], 2. állapottér-modell, sorrendi szabály balról-jobbra, $n=4$) követik végig: 48 lépés, ebből 22 visszalépés. Belülről nézve elég lenne az aktuális csúcsot tárolni az aktuális út helyett, mert a [[concepts/mesint/allapotter-modell]]ben az állapot egyértelműen meghatározza a helyzetet.

## Kapocs

- [[concepts/mesint/visszalepes-feltetelei]] — mikor kell visszalépni
- [[concepts/mesint/sorrendi-heurisztikak]] — a visszalépések számának csökkentése sorrenddel
- [[concepts/mesint/forward-checking]] — vágó szabállyal korábbi visszalépés
- [[concepts/mesint/melysegi-korlatos-visszalepes]] — a VL2 részletei
- [[concepts/mesint/visszalepeses-kereses-ertekelese]] — erősségek és gyengeségek
- [[concepts/mesint/kereso-rendszer]] — az általános keretrendszer
