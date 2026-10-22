# MT448-Labs
### **Լաբորատոր աշխատանք 2**
**Method overloading, default parameters**

#### 2. Խնդրի դրվածքը
* Ստեղծել static `ToMultiplicate` մեթոդը, 3 օրինակով, որը կընդունի `x`, `N` փոփոխականները։
* `N`-ը կունենա ըստ լռելյայն (default) արժեք 2, կլինի `int` տիպի։
* Իսկ `x`-ը կլինի երեք տարբերակով՝ `int`, `double` և `string`։
* Ֆունկցիան պիտի վերադարձնի `N` հատ `x`-երի գումարը (կամ string-ի դեպքում միացված տարբերակով)։
* Թեստավորել overloading-ի աշխատանքը `Main()` մեթոդում։

#### 3. Կատարած առաջադրանքը
```csharp
using System;

class Program
{
    static int ToMultiplicate(int x, int n = 2)
    {
        return x * n;
    }

    static double ToMultiplicate(double x, int n = 2)
    {
        return x * n;
    }

    static string ToMultiplicate(string x, int n = 2)
    {
        string result = "";
        for (int i = 0; i < n; i++)
        {
            result += x;
        }
        return result;
    }

    static void Main()
    {

        Console.WriteLine("--- Int Testing ---");
        Console.WriteLine(ToMultiplicate(5));       // N = 2 (default) -> 10
        Console.WriteLine(ToMultiplicate(5, 3));    // N = 3 -> 15

        Console.WriteLine("\n--- Double Testing ---");
        Console.WriteLine(ToMultiplicate(4.5));     // N = 2 (default) -> 9.0
        Console.WriteLine(ToMultiplicate(2.5, 4));  // N = 4 -> 10.0

        Console.WriteLine("\n--- String Testing ---");
        Console.WriteLine(ToMultiplicate("hello"));   // N = 2 (default) 
        Console.WriteLine(ToMultiplicate("mt448", 3)); // N = 3 
    }
}
