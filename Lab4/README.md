### **Լաբորատոր աշխատանք 4**
**using in, out, ref, params, and parameters by default values**

#### 2. Խնդրի դրվածքը
* Ստեղծել static A(), B(), C() մեթոդները, համապատասխանաբար in, out, ref մոդիֆիկատորները փորձարկելու համար։
* Ստեղծել նաև SumValues(params ...) մեթոդը, որը կգումարի մուտքում եկած ամբողջ թվերը, թվերի քանակը ֆիքսված չէ։
* Ցույց տալ թե ինչպես են աշխատում այս մեթոդները Main() մեթոդում։

#### 3. Կատարած առաջադրանքը
```csharp
using System;

class Program
{
    static void A(in int x)
    {
        Console.WriteLine(x);
    }

    static void B(out int x)
    {
        x = 10;
    }

    static void C(ref int x)
    {
        x += 5;
    }

    static int SumValues(params int[] numbers)
    {
        int sum = 0;
        foreach (var n in numbers)
        {
            sum += n;
        }
        return sum;
    }

    static void Main()
    {
        int a = 2;
        A(in a);

        int b;
        B(out b);

        int c = 10;
        C(ref c);

        int total = SumValues(1, 2, 3, 4);
        Console.WriteLine(total);
    }
}
