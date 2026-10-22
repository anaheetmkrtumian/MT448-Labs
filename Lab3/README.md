### **Լաբորատոր աշխատանք 3**
**String, Formatting, Enum Switch**

#### 2. Խնդրի դրվածքը
* ստեղծել Movie.cs կլասսը որը կպարունակի [ֆիլմի համարը, ֆիլմի անունը, տարեթիվը, ֆիլմի ժանրը, դիտումների քանակը, լայքերի քանակը]
* ֆիլմի ժանրի համար ստեղծել enum 5 տարբերակ պարունակող, ըստ ձեր  հայեցողությամբ
* Մուրտքագրումը կատարել Console-ից ReadLine() մեթոդով, ժանրը գրել որպես 1 ից 5 թիվ, որից հետո ինֆորմացիան տարանջատել (split) և տեղավորել կլասսի դաշտերում.
* ստեղծել նաև մեթոդ որը կհաշվի ֆիլմի ռեյտինգը հետևյալ բանաձևով SQRT(Likes ^ 2 / Views) կլինի double տիպի;
* Movie.cs կլասսի համար override անել ToString() մեթոդը որը ցույց կտա կլասսի պարունակությունը հետևյալ կերպ
    - ֆիլմի համարը, {4 տառաչափ, կցել աջ}
    - ֆիլմի անունը, {15 տառաչափ, կցել ձախ}
    - տարեթիվը,    {8 տառաչափ, կցել ձախ և փակագծերի մեջ օր․"(2011)"}
    - ֆիլմի ժանրը,  {12 տառաչափ, տեքստային, կցել ձախ}
    - ռեյտինգը {8 տառաչափ, ստրոակետրից հետո 1000-րդական ճշտությամբ, անպայման ցույց տա նաև եթե զրոներ են}
* ցույց տալ կլասսի ֆունկիոնալությունը Main() մեթոդում, ծրագիրը սկզբում կընդհունի քանակը օրինակ 7 և հետո ցիկլով կնդունի 7 հատ ֆիլմի տվյալներ, այնուհետև ցիկլով ցույց կտա ֆորմատավորված տեսքով։  
* որպեսզի ավելորդ չբարդացնեք բոլոր մեմբերները և մեթոդները ստեղծել public

#### 3. Կատարած առաջադրանքը
```csharp
using System;

enum Genre
{
    Action = 1,
    Comedy,
    Drama,
    SciFi,
    Horror
}

class Movie
{
    public int Number { get; set; }
    public string Title { get; set; }
    public int Year { get; set; }
    public Genre MovieGenre { get; set; }
    public int Views { get; set; }
    public int Likes { get; set; }

    public Movie(int number, string title, int year, Genre genre, int views, int likes)
    {
        Number = number;
        Title = title;
        Year = year;
        MovieGenre = genre;
        Views = views;
        Likes = likes;
    }

    public double CalculateRating()
    {
        if (Views == 0) return 0;
        return Math.Sqrt((double)(Likes * Likes) / Views);
    }

    public override string ToString()
    {
        string genreStr = MovieGenre.ToString();
        string yearStr = $"({Year})";
        double rating = CalculateRating();

        return $"{Number,4} | {Title,-15} | {yearStr,-8} | {genreStr,-12} | {rating,8:F3}";
    }
}

class Program
{
    static void Main()
    {
        Console.OutputEncoding = System.Text.Encoding.UTF8;

        Console.Write("Enter the number of movies: ");
        int count = int.Parse(Console.ReadLine());

        Movie[] movies = new Movie[count];

        for (int i = 0; i < count; i++)
        {
            Console.WriteLine($"\nEnter movie #{i + 1} data:");
            string input = Console.ReadLine();
            string[] parts = input.Split(' ');

            int number = int.Parse(parts[0]);
            string title = parts[1];
            int year = int.Parse(parts[2]);
            Genre genre = (Genre)int.Parse(parts[3]);
            int views = int.Parse(parts[4]);
            int likes = int.Parse(parts[5]);

            movies[i] = new Movie(number, title, year, genre, views, likes);
        }

        Console.WriteLine("\n--- Movies List ---");
        foreach (var movie in movies)
        {
            Console.WriteLine(movie.ToString());
        }
    }
}
