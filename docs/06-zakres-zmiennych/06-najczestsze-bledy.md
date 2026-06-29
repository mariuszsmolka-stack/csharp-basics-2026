# Najczęstsze błędy — zakres zmiennych

## Po co analizować błędy

Błędy zakresu zmiennych są częste u początkujących. Programista widzi nazwę w kodzie, ale kompilator sprawdza zakres, czyli miejsce, w którym dana zmienna naprawdę istnieje.

W tej lekcji każdy błąd ma krótki przykład, wyjaśnienie problemu i poprawioną wersję.

## Błąd 1: użycie zmiennej poza blokiem if

Przykład błędny:

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 18;

        if (wiek >= 18)
        {
            string komunikat = "Osoba pełnoletnia";
        }

        Console.WriteLine(komunikat);
    }
}
```

Problem:

* `komunikat` został zadeklarowany wewnątrz bloku `if`,
* poza blokiem `if` nie istnieje,
* dlatego `Console.WriteLine` nie ma dostępu do tej zmiennej.

Poprawka:

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 18;
        string komunikat = "";

        if (wiek >= 18)
        {
            komunikat = "Osoba pełnoletnia";
        }

        Console.WriteLine(komunikat);
    }
}
```

## Błąd 2: użycie licznika for po pętli

Przykład błędny:

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 0; i < 5; i++)
        {
            Console.WriteLine(i);
        }

        Console.WriteLine(i);
    }
}
```

Problem:

* `i` zostało zadeklarowane w nagłówku pętli `for`,
* po zakończeniu pętli `i` nie jest dostępne,
* licznik pętli zwykle służy tylko do sterowania pętlą.

Poprawka bez wypisywania `i` po pętli:

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 0; i < 5; i++)
        {
            Console.WriteLine(i);
        }
    }
}
```

Poprawka z osobną zmienną, jeśli wartość jest naprawdę potrzebna po pętli:

```csharp
using System;

class Program
{
    static void Main()
    {
        int ostatniaLiczba = 0;

        for (int i = 0; i < 5; i++)
        {
            ostatniaLiczba = i;
            Console.WriteLine(i);
        }

        Console.WriteLine(ostatniaLiczba);
    }
}
```

## Błąd 3: akumulator zadeklarowany wewnątrz pętli

Przykład błędny:

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 1; i <= 5; i++)
        {
            int suma = 0;
            suma += i;
        }

        Console.WriteLine(suma);
    }
}
```

Problem:

* `suma` została zadeklarowana wewnątrz pętli,
* poza pętlą nie istnieje,
* dodatkowo w każdej iteracji byłaby tworzona od nowa,
* akumulator powinien być zadeklarowany przed pętlą.

Poprawka:

```csharp
using System;

class Program
{
    static void Main()
    {
        int suma = 0;

        for (int i = 1; i <= 5; i++)
        {
            suma += i;
        }

        Console.WriteLine(suma);
    }
}
```

## Błąd 4: użycie zmiennej przed deklaracją

Przykład błędny:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine(liczba);

        int liczba = 10;
    }
}
```

Problem:

* zmienna jest dostępna dopiero od miejsca deklaracji,
* nie można użyć zmiennej wcześniej, niż została zadeklarowana.

Poprawka:

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba = 10;

        Console.WriteLine(liczba);
    }
}
```

## Błąd 5: metoda próbuje użyć zmiennej lokalnej z Main

Przykład błędny:

```csharp
using System;

class Program
{
    static void PokazWynik()
    {
        Console.WriteLine(wynik);
    }

    static void Main()
    {
        int wynik = 100;

        PokazWynik();
    }
}
```

Problem:

* `wynik` jest zmienną lokalną `Main`,
* metoda `PokazWynik` ma własny zakres,
* metoda `PokazWynik` nie widzi automatycznie zmiennych lokalnych z `Main`,
* dane trzeba przekazać przez parametr.

Poprawka:

```csharp
using System;

class Program
{
    static void PokazWynik(int wynik)
    {
        Console.WriteLine(wynik);
    }

    static void Main()
    {
        int wynik = 100;

        PokazWynik(wynik);
    }
}
```

## Błąd 6: parametr i zmienna lokalna o tej samej nazwie

Przykład błędny:

```csharp
using System;

class Program
{
    static void PokazLiczbe(int liczba)
    {
        int liczba = 5;

        Console.WriteLine(liczba);
    }

    static void Main()
    {
        PokazLiczbe(10);
    }
}
```

Problem:

* parametr `liczba` już istnieje w zakresie metody,
* nie można zadeklarować drugiej zmiennej lokalnej o tej samej nazwie w tej samej metodzie,
* należy użyć innej nazwy dla zmiennej pomocniczej.

Poprawka:

```csharp
using System;

class Program
{
    static void PokazLiczbe(int liczba)
    {
        int podwojona = liczba * 2;

        Console.WriteLine(podwojona);
    }

    static void Main()
    {
        PokazLiczbe(10);
    }
}
```

## Błąd 7: mylące przesłanianie pola klasy

Kod legalny, ale mylący:

```csharp
using System;

class Program
{
    static int liczba = 100;

    static void Main()
    {
        int liczba = 5;

        Console.WriteLine(liczba);
    }
}
```

Problem:

* kod może być legalny,
* lokalna `liczba` przesłania pole klasy,
* program wypisze `5`,
* mimo że kod działa, jest mniej czytelny.

Lepsza wersja z różnymi nazwami:

```csharp
using System;

class Program
{
    static int domyslnaLiczba = 100;

    static void Main()
    {
        int aktualnaLiczba = 5;

        Console.WriteLine(aktualnaLiczba);
    }
}
```

## Jak unikać błędów zakresu

* Deklaruj zmienną tam, gdzie naprawdę jest potrzebna.
* Jeżeli wynik ma być użyty po pętli, zadeklaruj zmienną przed pętlą.
* Jeżeli metoda potrzebuje danych z `Main`, przekaż je przez parametry.
* Nie używaj tej samej nazwy dla różnych rzeczy.
* Nie zakładaj, że wcięcia decydują o zakresie. W C# decydują klamry.
* Czytaj komunikaty kompilatora.

## Ćwiczenia

1. Popraw program, w którym zmienna zadeklarowana w `if` jest używana poza `if`.
2. Popraw program, w którym licznik `for` jest używany po pętli.
3. Popraw program, w którym akumulator `suma` jest zadeklarowany wewnątrz pętli.
4. Popraw program, w którym zmienna jest użyta przed deklaracją.
5. Popraw program, w którym metoda próbuje użyć zmiennej lokalnej z `Main`.
6. Popraw program, w którym parametr i zmienna lokalna mają tę samą nazwę.
7. Wyjaśnij, dlaczego przesłanianie pola klasy przez zmienną lokalną może być mylące.
8. Napisz własny przykład błędu zakresu zmiennej i jego poprawkę.

## Podsumowanie

Zmienna istnieje tylko w swoim zakresie. Zakres w C# wyznaczają klamry i miejsce deklaracji.

Zmienna z `if` nie jest dostępna poza `if`. Licznik `for` zwykle nie jest dostępny po pętli. Akumulator deklarujemy przed pętlą.

Metoda nie widzi automatycznie zmiennych lokalnych z `Main`. Dobre nazwy zmiennych zmniejszają ryzyko pomyłek.
