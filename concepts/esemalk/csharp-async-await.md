---
tags: [concept, esemalk/tobbszalu-programozas-csharp-ban]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# `async`/`await` — aszinkron programozás C#-ban

Az `async`/`await` nyelvi konstrukció taszkalapú aszinkron műveletek
szekvenciális stílusban történő megírását teszi lehetővé.

## Tartalom

Az aszinkron műveletek eredménye egy másik aszinkron műveletben bevárható:

- aszinkron műveletet az `async` kulcsszóval hozhatunk létre,
- az eredményt az `await` utasítással várhatjuk be.

```csharp
private async void ReadStreamAsync(Stream str) {
    StreamReader reader = new StreamReader(str);
    String line = await reader.ReadLineAsync();
        // aszinkron módon olvasunk, és megvárjuk
        // a művelet lefutását
    …
}
```

### Végrehajtási sorrend

Egy `async` metódus az első `await` utasításig **szinkron** módon fut le:

- az `await` utasítás elérésekor az adott `Task` egy másik szálon kerül
  kiértékelésre,
- közben a tartalmazó metódus felfüggesztésre kerül, és a vezérlés a hívó
  eljáráshoz kerül vissza,
- a `Task` befejezésekor az `await` utasítást tartalmazó metódus további
  része a második szálon kerül végrehajtásra.

### Elnevezési konvenció és interfészek

A háttérben futtatandó tevékenységek jelentős része (pl. fájlkezelés,
hálózatkezelés) aszinkron műveletként is elérhető (.NET Framework 4.5 és C#
5.0 óta):

- ezt a műveletek nevében konvencionálisan az `Async` szuffixszel jelezzük,
  amelyet saját metódusainknál is érdemes követni (pl. `ReadLineAsync`),
- az aszinkronitást csak a megvalósításban kell jelölnünk, interfészben nem —
  csupán a taszk visszatérési értékét kell megadnunk:

```csharp
interface IAsyncInterface {
    Task ProcessAsync();
    Task<Int32> ComputeAsync();
    // aszinkron műveletek (visszatérési értékből látszik)
}

async Task SomeMethod(IAsyncInterface asInst) {
    Int32 result = await asInst.ComputeAsync();
        // eredmény bevárása
}
```

Egy meglévő szinkron művelet aszinkron módon, `Task.Run`-nal történő
becsomagolásával implementálható:

```csharp
class AsyncImplementation : IAsyncInterface {
    private void Process(); // szinkron művelet

    public async Task ProcessAsync() {
        await Task.Run(() => Process());
            // a tevékenység aszinkron végrehajtása
    }
    public async Task<Int32> ComputeAsync() {
        await Task.Run(() => { … return value; });
    }
}
```

Teljes példa két egész szám aszinkron összeadására:

```csharp
class Program {
    public static int Add(int a, int b) {
        /* ... */
    }

    public static async Task<int> AddAsync(int a, int b) {
        return await Task.Run(() => Add(a, b));
    }

    public static void Main(string[] args) {
        int x = 30;
        int y = 12;

        Console.WriteLine("Main thread starts");
        Task<int> task = AddAsync(x, y);

        Console.WriteLine("Main thread waiting");
        int sum = task.Result;
        Console.WriteLine("Main thread finishes, sum = {0}", sum);
    }
}
```

## Kapocs

- [[concepts/esemalk/csharp-task-alapok]] — a `Task` típus, amelyre az
  `async`/`await` épül
- [[concepts/esemalk/csharp-szal-letrehozasa-kezelese]] — a `Thread` típus,
  amelynek korlátait a taszkalapú (és aszinkron) programozás feloldja
- [[concepts/esemalk/taszk-kivetelkezes-aggregateexception]] — kivételkezelés
  taszkokkal és `async`/`await`-tel
- [[concepts/esemalk/winforms-fibonacci-parhuzamositas-pelda]] — teljes
  `async`/`await` példa WinForms alkalmazásban
