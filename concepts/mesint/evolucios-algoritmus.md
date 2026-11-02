---
tags: [concept]
sources: ["08.evolucio.pdf"]
derivation: source
kind: procedure
element: water
updated: 2026-10-12
---

# Evolúciós algoritmus

Az evolúciós algoritmus (EA) populációt tároló, nem-módosítható stratégiájú keresőrendszer: a populációt szelekció, rekombináció, mutáció és visszahelyezés ismételt alkalmazásával javítja, amíg a terminálási feltétel nem teljesül.

## Tartalom

### Evolúció mint kereső rendszer

A [[concepts/mesint/kereso-rendszer]] terminológiájában az evolúciós algoritmus a következőképp néz ki:

- A probléma több lehetséges válaszát (**egyedét**) egyszerre tároljuk, a **populációban**.
- Többnyire véletlen populációból indulunk, és lépésről lépésre javítjuk, hogy végül megjelenjen benne egy célegyed, vagy összességében jó populációhoz jussunk.
- Az egyedeket a **rátermettségi függvény** hasonlítja össze ([[concepts/mesint/ratermettseg-kiertekelese]]). Minden lépésben a kevésbé rátermett egyedek egy részét a rátermettebbekhez hasonló egyedekre cseréljük.
- A változtatás visszavonhatatlan, ezért ez **nem-módosítható stratégiájú** keresés (nincs visszalépés, nincs a régi állapotokat megőrző gráf), a [[concepts/mesint/hegymaszo-modszer]] rokona, de egyszerre sok pontot kezel.

Az általános keresőrendszer-sémában (`ADAT := kezdeti érték; while ¬terminálási feltétel(ADAT) loop SELECT SZ FROM alkalmazható szabályok; ADAT := SZ(ADAT)`) az `ADAT` a populáció, a szabályok az evolúciós operátorok.

### Evolúciós operátorok

| operátor | feladata |
|---|---|
| [[concepts/mesint/szelekcio]] | kiválaszt néhány (lehetőleg rátermett) egyedet |
| [[concepts/mesint/rekombinacio-es-keresztezes]] | a kiválasztott szülőkből a szülők tulajdonságait öröklő utódokat készít |
| [[concepts/mesint/mutacio]] | az utódok tulajdonságait kismértékben módosítja |
| [[concepts/mesint/visszahelyezes]] | az utódokból és a régi populációból új populációt alakít ki |

**Terminálási feltétel:** vagy megjelenik a célegyed a populációban, vagy a populáció egyesített rátermettségi függvényértéke egy ideje nem változik.

### Az alapalgoritmus

```
Procedure EA
  populáció := kezdeti populáció
  while terminálási feltétel nem igaz loop
    szülők := szelekció(populáció)
    utódok := rekombináció(szülők)
    utódok := mutáció(utódok)
    populáció := visszahelyezés(populáció, utódok)
  endloop
```

### Evolúciós ciklus: 8-királynő példa

Az egyedek a királynők oszloponkénti sorpozíciói (pl. `24748552`), a rátermettség az ütésben nem lévő királynőpárok száma (a példában a ciklus 24, 23, 20, 11 értékű populációból indul; részletesen: [[concepts/mesint/evolucios-kodolas]], [[concepts/mesint/ratermettseg-kiertekelese]]).

1. **Szelekció:** a 15-nél jobb egyedek közül, lehetőleg a jobbakat választja (a 11 értékű kiesik); az egyedek párba rendezve kapnak keresztezési pontot.
2. **Rekombináció:** a párok a keresztezési pont után kicserélik a farokrészt (`24748552` × `32752411` → `24752411`, `32748552`).
3. **Mutáció:** egy-egy érték módosul (az utódok rátermettsége pl. 21, 23, 25, 20).
4. **Visszahelyezés:** a jobb utódok a régi populáció rosszabb tagjainak helyére kerülnek.

A második változatban (permutációkódolás, minden sor és oszlop pontosan egy királynő) a szelekció mindenkit kiválaszt, a keresztezés után **javítás** kell a duplikátumok cseréjével, a mutáció pedig értékpárokat cserél meg.

## Kapocs

- [[concepts/mesint/evolucios-algoritmus-tervezese]] — mit kell eldönteni egy konkrét EA megtervezésekor
- [[concepts/mesint/evolucios-kodolas]] — az egyedek kódolása
- [[concepts/mesint/ratermettseg-kiertekelese]] — a rátermettségi függvény
- [[concepts/mesint/szelekcio]] — az első operátor részletesen
- [[concepts/mesint/rekombinacio-es-keresztezes]], [[concepts/mesint/mutacio]], [[concepts/mesint/visszahelyezes]] — a többi operátor
- [[concepts/mesint/kereso-rendszer]] — az általános keresőrendszer-modell
- [[concepts/mesint/n-kiralyno-problema]] — a vezérpélda állapottér-modellje
