# Brain — jegyzetwiki

Egyetemi anyagokból épített, kézzel gondozott fogalomwiki. Minden lap egy
fogalom: rövid összefoglaló, kifejtés, majd a kapcsolódó lapokra mutató
hivatkozások.

A tartalom **magyar nyelvű**. Obsidian-vaultként a legkényelmesebb olvasni —
klónozd, és nyisd meg a mappát Obsidiannal —, de a lapok sima Markdown-fájlok,
GitHubon is olvashatók.

## Szerkezet

```
concepts/<tárgy>/   fogalomlapok, tárgyanként egy mappa
subjects/           tárgyanként egy gyűjtőlap
outputs/            generált melléktermékek (ábrák, animációk, összefoglalók)
index.md            a tárgyak katalógusa — innen érdemes indulni
```

Minden lap fejlécében ott a `derivation:` mező: `source` (forrásdokumentumból
készült), `inferred` (több forrásból szintetizált vagy átfogalmazott) vagy
`unsourced` (kanonikus tananyag, forrásfájl nélkül).

## Ez a tár egy tükör

Ez a repó egy privát vault **automatikusan frissülő pillanatképe**. Nincs közös
előzménye a forrásrepóval, és minden szinkron felülírja a tartalmát.

Ebből következik:

- **Ne nyiss ide pull requestet** — a következő szinkron eltünteti. Hibát
  jelezni issue-ban lehet.
- A commit-előzmény nem a lapok valódi szerkesztéstörténete, csak a szinkroné.

## Ami nincs itt

A wiki forrásdokumentumai — egyetemi előadásdiák, jegyzetek, tankönyvek — **nem
részei ennek a tárnak**, mert nem az én műveim, és nincs jogom terjeszteni őket.
A lapok `sources:` mezője megnevezi, melyik forrásból készültek, de a fájlokat
nem tartalmazza. Ugyanezért hiányoznak a forrásfájlokra mutató hivatkozások is.

## Licenc

A lapok szövege: [CC BY-SA 4.0](LICENSE).

Ez **kizárólag az általam írt tartalomra** vonatkozik. A wiki tananyagot
ismertet: a benne tárgyalt tételek, definíciók és bizonyítások a matematika és
az informatika közkincse, az őket ismertető megfogalmazás az enyém. Ahol egy lap
egy konkrét forrás gondolatmenetét követi, a `sources:` és `references:` mező
megnevezi.
