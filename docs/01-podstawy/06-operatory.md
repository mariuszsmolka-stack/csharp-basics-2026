# Operatory w C#

## Cel lekcji

Poznasz podstawowe operatory w C# i nauczysz się używać ich w prostych programach konsolowych.

Po tej lekcji powinieneś umieć:

- wykonać proste działania arytmetyczne,
- odróżnić przypisanie `=` od porównania `==`,
- obliczyć resztę z dzielenia,
- zwiększyć lub zmniejszyć wartość zmiennej,
- sprawdzić wynik porównania jako wartość `true` albo `false`.

## 1. Czym jest operator

Operator to znak lub zapis, który wykonuje działanie na wartościach.

Przykłady operatorów:

- `+` dodaje wartości,
- `=` przypisuje wartość do zmiennej,
- `==` sprawdza, czy dwie wartości są równe,
- `>` sprawdza, czy jedna wartość jest większa od drugiej.

Operatory są bardzo często używane w obliczeniach, porównaniach i warunkach.

## 2. Operatory arytmetyczne

Operatory arytmetyczne służą do wykonywania działań matematycznych.

```csharp
using System;

class Program
{
    static void Main()
    {
        int a = 10;
        int b = 3;

        Console.WriteLine(a + b);
        Console.WriteLine(a - b);
        Console.WriteLine(a * b);
        Console.WriteLine(a / b);
        Console.WriteLine(a % b);
    }
}
```

Znaczenie operatorów:

- `+` dodawanie,
- `-` odejmowanie,
- `*` mnożenie,
- `/` dzielenie,
- `%` reszta z dzielenia.

Operator `%` zwraca resztę z dzielenia. Dla `10 % 3` wynikiem jest `1`, ponieważ `10` podzielone przez `3` daje `3` i resztę `1`.

## 3. Dzielenie całkowite i rzeczywiste

W C# wynik dzielenia zależy od typu danych.

Jeżeli dzielimy liczby typu `int`, wynik też jest liczbą całkowitą.

```csharp
using System;

class Program
{
    static void Main()
    {
        int a = 10;
        int b = 3;

        Console.WriteLine(a / b);
    }
}
```

Wynik:

```csharp
3
```

Program nie wypisze `3.3333`, ponieważ `a` i `b` są typu `int`.

Jeżeli chcemy wynik rzeczywisty, możemy użyć typu `double`.

```csharp
using System;

class Program
{
    static void Main()
    {
        double x = 10.0;
        double y = 3.0;

        Console.WriteLine(x / y);
    }
}
```

Wtedy wynik zawiera część dziesiętną.

## 4. Operator przypisania

Znak `=` oznacza przypisanie wartości do zmiennej.

```csharp
using System;

class Program
{
    static void Main()
    {
        int punkty = 10;

        Console.WriteLine(punkty);
    }
}
```

Instrukcję `int punkty = 10;` czytamy jako: utwórz zmienną `punkty` i wpisz do niej wartość `10`.

Ważne: `=` nie oznacza porównania. Do porównania równości używamy `==`.

## 5. Skrócone operatory przypisania

Skrócone operatory przypisania pozwalają krócej zapisać zmianę wartości zmiennej.

```csharp
using System;

class Program
{
    static void Main()
    {
        int punkty = 10;

        punkty += 5;
        Console.WriteLine(punkty);

        punkty -= 3;
        Console.WriteLine(punkty);

        punkty *= 2;
        Console.WriteLine(punkty);

        punkty /= 4;
        Console.WriteLine(punkty);
    }
}
```

Znaczenie zapisów:

- `punkty += 5;` oznacza `punkty = punkty + 5;`,
- `punkty -= 3;` oznacza `punkty = punkty - 3;`,
- `punkty *= 2;` oznacza `punkty = punkty * 2;`,
- `punkty /= 4;` oznacza `punkty = punkty / 4;`.

## 6. Inkrementacja i dekrementacja

Inkrementacja zwiększa wartość zmiennej o `1`.

```csharp
using System;

class Program
{
    static void Main()
    {
        int licznik = 5;

        licznik++;

        Console.WriteLine(licznik);
    }
}
```

Dekrementacja zmniejsza wartość zmiennej o `1`.

```csharp
using System;

class Program
{
    static void Main()
    {
        int licznik = 5;

        licznik--;

        Console.WriteLine(licznik);
    }
}
```

Znaczenie:

- `licznik++` oznacza zwiększenie o `1`,
- `licznik--` oznacza zmniejszenie o `1`.

## 7. Operatory porównania

Operatory porównania sprawdzają relację między wartościami.

```csharp
using System;

class Program
{
    static void Main()
    {
        int a = 10;
        int b = 3;

        Console.WriteLine(a == b);
        Console.WriteLine(a != b);
        Console.WriteLine(a > b);
        Console.WriteLine(a < b);
        Console.WriteLine(a >= b);
        Console.WriteLine(a <= b);
    }
}
```

Znaczenie operatorów:

- `==` równe,
- `!=` różne,
- `>` większe,
- `<` mniejsze,
- `>=` większe lub równe,
- `<=` mniejsze lub równe.

Do porównania równości używamy `==`, a nie `=`.

## 8. Wynik porównania jako bool

Porównania zwracają wartość typu `bool`, czyli `true` albo `false`.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 18;

        Console.WriteLine(wiek >= 18);
        Console.WriteLine(wiek < 18);
        Console.WriteLine(5 == 5);
        Console.WriteLine(5 != 5);
    }
}
```

Wartość `true` oznacza, że porównanie jest prawdziwe. Wartość `false` oznacza, że porównanie jest fałszywe.

## 9. Operatory logiczne

Operatory logiczne będą dokładniej używane w dziale o warunkach. Na razie wystarczy znać ich znaczenie.

- `&&` oznacza logiczne „i”.
- `||` oznacza logiczne „lub”.
- `!` oznacza zaprzeczenie.

Krótki przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        bool maBilet = true;
        bool maLegitymacje = false;

        Console.WriteLine(maBilet && maLegitymacje);
        Console.WriteLine(maBilet || maLegitymacje);
        Console.WriteLine(!maBilet);
    }
}
```

To jest tylko zapowiedź. Do operatorów logicznych wrócimy przy instrukcjach warunkowych.

## 10. Kolejność wykonywania działań

C# stosuje znaną z matematyki kolejność wykonywania działań.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine(2 + 3 * 4);
        Console.WriteLine((2 + 3) * 4);
    }
}
```

Najpierw wykonywane jest mnożenie, a potem dodawanie. Nawiasy pozwalają zmienić kolejność działań.

Warto używać nawiasów, gdy zapis ma być bardziej czytelny.

## 11. Proste przykłady z Console.WriteLine()

```csharp
using System;

class Program
{
    static void Main()
    {
        int a = 10;
        int b = 3;

        Console.WriteLine("Suma: " + (a + b));
        Console.WriteLine("Różnica: " + (a - b));
        Console.WriteLine("Iloczyn: " + (a * b));
        Console.WriteLine("Iloraz całkowity: " + (a / b));
        Console.WriteLine("Reszta z dzielenia: " + (a % b));
        Console.WriteLine("Czy a jest większe od b?");
        Console.WriteLine(a > b);
    }
}
```

Nawiasy w zapisie `"Suma: " + (a + b)` sprawiają, że najpierw zostanie obliczona suma, a dopiero potem wynik zostanie połączony z tekstem.

## Typowe błędy

- Użycie `=` zamiast `==` przy porównaniu.
- Oczekiwanie wyniku rzeczywistego przy dzieleniu dwóch liczb typu `int`.
- Mylenie operatora `%` z dzieleniem.
- Brak nawiasów w dłuższych działaniach.
- Próba użycia `++` albo `--` na wartości, która nie jest zmienną.
- Mylenie wartości `true` i `false` z tekstem `"true"` i `"false"`.

## Zapamiętaj

- Operator wykonuje działanie na wartościach.
- `+`, `-`, `*`, `/`, `%` to operatory arytmetyczne.
- `%` zwraca resztę z dzielenia.
- `10 / 3` dla typu `int` daje wynik całkowity.
- `10.0 / 3.0` dla typu `double` daje wynik rzeczywisty.
- `=` oznacza przypisanie.
- `==` oznacza porównanie równości.
- `+=`, `-=`, `*=`, `/=` skracają zapis zmiany wartości zmiennej.
- `++` zwiększa zmienną o `1`, a `--` zmniejsza ją o `1`.
- Porównania zwracają `true` albo `false`.
- Nawiasy mogą zmienić kolejność wykonywania działań.

## Ćwiczenia

1. Utwórz dwie zmienne typu `int` i wypisz ich sumę.
2. Wypisz różnicę, iloczyn i iloraz dwóch liczb.
3. Sprawdź resztę z dzielenia liczby przez `2`.
4. Zwiększ wartość zmiennej o `1` za pomocą `++`.
5. Zwiększ wartość zmiennej o `10` za pomocą `+=`.
6. Sprawdź, czy jedna liczba jest większa od drugiej.
7. Sprawdź, jaki wynik daje porównanie `5 == 5`.
8. Sprawdź, czym różni się `=` od `==`.
