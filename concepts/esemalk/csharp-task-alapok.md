---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Taszk-alapú aszinkron programozás alapjai

A `Task` típus: a párhuzamos és késleltetett végrehajtás magasabb
absztrakciós szintű koncepciója, amely feloldja a `Thread` típus korlátait.

## Tartalom

A .NET Framework 4.0-s verziója (2010) óta elérhető a párhuzamos és
késleltetett végrehajtás magasabb absztrakciós szintű koncepciója, a
**taszkok** (`Task`).

- A taszk egy *lambda*-kifejezésként (`Func`, `Action`) megadott eljárást
  hajt végre aszinkron módon, jellemzően egy külön szálon.
- Az új szál a .NET-ben elérhető szálkészletből (*thread pool*) kerül
  kivételre, amely a szálak újrafelhasználását biztosítja.
- A művelet a példány `Start()` metódusával hajtható végre, de szinkron
  művelet is futtatható aszinkron módon a `Task.Run(…)` metódusával, amely
  egy `Task`-ot ad vissza.
- A művelet eredménye a `Task` objektum `Result` tulajdonságával kérhető le
  (amely megvárja a taszk befejezését). A taszk a `Wait()` metódussal és
  változataival is megvárható.

```csharp
private Int32 Compute(){ /* ... */ }
    // ez eredményt előállító számítás

private void RunCompute() {
    Task<Int32> myTask =
        new Task<Int32>(() => Compute());
        // taszk létrehozása a végrehajtandó művelettel
    myTask.Start(); // taszk elindítása
    // további műveletek ...

    Int32 result = myTask.Result;
    // eredmény megvárása

    // további műveletek ...
}
```

Alternatív, tömörebb módon:

```csharp
private void RunCompute() {
    Int32 result = Task.Run(() => Compute()).Result;
        // taszk végrehajtása és az eredmény megvárása

    // további műveletek ...
}
```

Egy másik példa, amely két paraméter összeadását végzi el egy gyerekszálon,
és az eredményt a `Result` tulajdonságon keresztül adja vissza:

```csharp
class Program {
    public static int Add(int a, int b) {
        Console.WriteLine("Child thread starts");
        int result = a + b;
        Console.WriteLine("Child thread goes to sleep");
        Thread.Sleep(5000); // the thread is paused for 5000 ms
        Console.WriteLine("Child thread resumes and finishes");
        return result;
    }

    public static void Main(string[] args) {
        int x = 30, y = 12;
        Task<int> task = new Task<int>(() => Add(x, y));
        Console.WriteLine("Main thread starts");
        task.Start();

        Console.WriteLine("Main thread waiting");
        int sum = task.Result; // várakozás az eredményre
        Console.WriteLine("Main thread finishes, sum = {0}", sum);
    }
}
```

A taszk-alapú megközelítés éppen azokat a problémákat oldja meg, amelyek az
alacsony absztrakciós szintű `Thread` típusú szálkezelést jellemzik: erősen
típusos paraméterátadás és eredmény-visszaadás lambda-kifejezéssel, valamint
a `Result` lekérdezésekor a gyerekszálban keletkezett kivétel is
továbbterjed a hívó felé.

## Kapocs

- [[concepts/esemalk/folyamat-es-szal]] — a folyamat és a szál alapfogalma
- [[concepts/esemalk/csharp-szal-letrehozasa-kezelese]] — a `Thread` típus és
  korlátai, amelyeket a taszk-alapú programozás felold
