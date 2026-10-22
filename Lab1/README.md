### **Լաբորատոր աշխատանք 1**
**Class, Random, matrix, set get, private public, constructor**

#### 2. Խնդրի դրվածքը
* Ստեղծել Կլասս, որը կպարունակի NxN չափերով մատրիցա։
* Կլասսում պահել private դաշտեր՝ `N`, `A` և `B` ամբողջ թվերի համար, և նրանց համար ապահովել `{set get}` մեթոդները կարճ գրելաձևով։
* Ստեղծել private `FillMatrix` անունով մեթոդ, որը կլրացնի մատրիցայի արժեքները `[A, B]` միջակայքից պատահական թվերով։
* Ստեղծել public `ShowMatrix` մեթոդը, որը ցույց կարտածի մատրիցայի պարունակությունը։
* Ստեղծել մեթոդ, որը կվերադարձնի մատրիցայի կենտ թվերի քանակը։
* Պարամետրիզացված կոնստրուկտորով տեղադրել `N`, `A` և `B` դաշտերի արժեքները, որից հետո կանչել `FillMatrix` մեթոդը։
* Ցույց տալ կլասսի ֆունկցիոնալությունը `Main()` մեթոդում։

#### 3. Կատարած առաջադրանքը
```csharp
using System;

class MatrixHandler
{
    private int n;
    private int a;
    private int b;
    private int[,] matrix;
    private Random rnd = new Random();

    public int N
    {
        get => n;
        set => n = value;
    }

    public int A
    {
        get => a;
        set => a = value;
    }

    public int B
    {
        get => b;
        set => b = value;
    }

    public MatrixHandler(int n, int a, int b)
    {
        N = n;
        A = a;
        B = b;
        matrix = new int[N, N];
        FillMatrix();
    }

    private void FillMatrix()
    {
        for (int i = 0; i < N; i++)
        {
            for (int j = 0; j < N; j++)
            {
                matrix[i, j] = rnd.Next(A, B + 1);
            }
        }
    }

    public void ShowMatrix()
    {
        for (int i = 0; i < N; i++)
        {
            for (int j = 0; j < N; j++)
            {
                Console.Write($"{matrix[i, j],4} ");
            }
            Console.WriteLine();
        }
    }

    public int CountOddNumbers()
    {
        int count = 0;
        for (int i = 0; i < N; i++)
        {
            for (int j = 0; j < N; j++)
            {
                if (matrix[i, j] % 2 != 0)
                {
                    count++;
                }
            }
        }
        return count;
    }
}

class Program
{
    static void Main()
    {
        Console.OutputEncoding = System.Text.Encoding.UTF8;

        Console.Write("Enter matrix size (N): ");
        int n = int.Parse(Console.ReadLine());

        Console.Write("Enter range start (A): ");
        int a = int.Parse(Console.ReadLine());

        Console.Write("Enter range end (B): ");
        int b = int.Parse(Console.ReadLine());

        MatrixHandler mh = new MatrixHandler(n, a, b);

        Console.WriteLine("\n--- Generated Matrix ---");
        mh.ShowMatrix();
   }
}
        int oddCount = mh.CountOddNumbers();
        Console.WriteLine($"\nCount of odd numbers in the matrix: {oddCount}");
    }
