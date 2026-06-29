# Formatowanie wyników w konsoli

## Cel lekcji

Nauczysz się czytelnie wypisywać dane w konsoli, łączyć tekst ze zmiennymi oraz formatować liczby rzeczywiste.

Po tej lekcji powinieneś umieć:

- połączyć tekst z wartością zmiennej za pomocą operatora `+`,
- użyć interpolacji napisów,
- wypisać kilka zmiennych w jednym zdaniu,
- ograniczyć liczbę miejsc po przecinku przy wypisywaniu wyniku,
- odróżnić wartość zmiennej od sposobu jej pokazania na ekranie.

## 1. Dlaczego sposób wypisywania wyniku jest ważny

Program powinien wypisywać wyniki tak, aby użytkownik wiedział, co oznaczają.

Mniej czytelny wynik:

```csharp
17
```

Bardziej czytelny wynik:

```csharp
Liczba punktów: 17
```

Drugi komunikat jest lepszy, ponieważ od razu wiadomo, czego dotyczy liczba.

## 2. Przypomnienie Console.WriteLine()

`Console.WriteLine()` wypisuje dane w konsoli i przechodzi do nowej linii.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Wynik programu:");
        Console.WriteLine(25);
    }
}
```

W tej lekcji skupiamy się na tym, jak przygotować czytelny tekst do wypisania.

## 3. Łączenie tekstu i zmiennych operatorem +

Operator `+` może łączyć tekst z wartością zmiennej.

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int wiek = 16;

        Console.WriteLine("Imię: " + imie);
        Console.WriteLine("Wiek: " + wiek);
        Console.WriteLine("Uczeń: " + imie + ", wiek: " + wiek);
    }
}
```

Ten zapis jest poprawny, ale przy dłuższych zdaniach może stać się mało czytelny.

## 4. Interpolacja napisów

Interpolacja napisów pozwala wygodnie wstawiać wartości zmiennych do tekstu.

Interpolowany napis zaczyna się od znaku `$` przed cudzysłowem.

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int wiek = 16;

        Console.WriteLine($"Uczeń: {imie}, wiek: {wiek}");
    }
}
```

Zmienne w interpolowanym tekście zapisujemy w nawiasach klamrowych `{}`.

## 5. Dlaczego interpolacja jest czytelniejsza

Porównaj dwa zapisy.

Łączenie operatorem `+`:

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int wiek = 16;

        Console.WriteLine("Uczeń: " + imie + ", wiek: " + wiek);
    }
}
```

Interpolacja napisów:

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int wiek = 16;

        Console.WriteLine($"Uczeń: {imie}, wiek: {wiek}");
    }
}
```

Drugi zapis jest zwykle czytelniejszy, bo zdanie wygląda prawie tak samo jak tekst, który zobaczy użytkownik.

## 6. Wypisywanie kilku zmiennych w jednym zdaniu

Interpolacja dobrze sprawdza się, gdy chcemy wypisać kilka wartości naraz.

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        string szkola = "Technikum";
        int punkty = 25;

        Console.WriteLine($"{imie} uczy się w szkole: {szkola}.");
        Console.WriteLine($"{imie} zdobyła {punkty} punktów.");
    }
}
```

W nawiasach klamrowych można umieszczać nazwy zmiennych.

## 7. Wynik obliczenia w czytelnym formacie

Możemy wypisać działanie i jego wynik w jednym zdaniu.

```csharp
using System;

class Program
{
    static void Main()
    {
        int a = 10;
        int b = 3;

        int suma = a + b;

        Console.WriteLine($"{a} + {b} = {suma}");
    }
}
```

Dzięki temu użytkownik widzi nie tylko wynik, ale też działanie.

## 8. Formatowanie liczb rzeczywistych

Liczby typu `double` mogą mieć wiele miejsc po przecinku.

```csharp
using System;

class Program
{
    static void Main()
    {
        double wynik = 10.0 / 3.0;

        Console.WriteLine($"Wynik: {wynik}");
        Console.WriteLine($"Wynik do 2 miejsc po przecinku: {wynik:F2}");
        Console.WriteLine($"Wynik do 1 miejsca po przecinku: {wynik:F1}");
        Console.WriteLine($"Wynik bez miejsc po przecinku: {wynik:F0}");
    }
}
```

Znaczenie zapisów:

- `{wynik}` wypisuje wartość w domyślny sposób,
- `{wynik:F2}` wypisuje liczbę z dwoma miejscami po przecinku,
- `{wynik:F1}` wypisuje liczbę z jednym miejscem po przecinku,
- `{wynik:F0}` wypisuje liczbę bez miejsc po przecinku.

## 9. Wartość zmiennej a sposób wypisania

Formatowanie nie musi zmieniać samej wartości zmiennej. Zmienia tylko sposób pokazania tej wartości na ekranie.

```csharp
using System;

class Program
{
    static void Main()
    {
        double wynik = 10.0 / 3.0;

        Console.WriteLine($"Wynik dokładny: {wynik}");
        Console.WriteLine($"Wynik sformatowany: {wynik:F2}");
        Console.WriteLine($"Ta sama zmienna ponownie: {wynik}");
    }
}
```

Zmienna `wynik` nadal przechowuje swoją wartość. Format `F2` wpływa na wypisanie, a nie na samą zmienną.

## 10. Średnia dwóch liczb

Poniższy przykład wczytuje dwie liczby typu `double`, oblicza średnią i wypisuje wynik z dokładnością do dwóch miejsc po przecinku.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj pierwszą liczbę:");
        double a = double.Parse(Console.ReadLine());

        Console.WriteLine("Podaj drugą liczbę:");
        double b = double.Parse(Console.ReadLine());

        double srednia = (a + b) / 2;

        Console.WriteLine($"Średnia wynosi: {srednia:F2}");
    }
}
```

W zależności od ustawień regionalnych systemu wynik liczby rzeczywistej może być wypisany z przecinkiem albo kropką jako separatorem dziesiętnym.

## 11. Prosty przykład z polem prostokąta

```csharp
using System;

class Program
{
    static void Main()
    {
        double bokA = 4.5;
        double bokB = 3.2;

        double pole = bokA * bokB;

        Console.WriteLine($"Pole prostokąta wynosi {pole:F2}.");
    }
}
```

Taki komunikat jest czytelniejszy niż wypisanie samej liczby.

## Typowe błędy

- Brak znaku `$` przed interpolowanym tekstem.
- Zapisanie nazwy zmiennej jako zwykłego tekstu, na przykład `"imie"` zamiast `{imie}`.
- Brak nawiasów klamrowych wokół zmiennej w interpolacji.
- Mylenie formatowania wyniku ze zmianą wartości zmiennej.
- Zbyt długi zapis z wieloma operatorami `+`, który trudno czytać.

## Zapamiętaj

- `Console.WriteLine()` wypisuje dane w konsoli.
- Operator `+` może łączyć tekst z wartością zmiennej.
- Interpolacja napisów zaczyna się od znaku `$` przed cudzysłowem.
- Zmienne w interpolowanym tekście zapisujemy w nawiasach klamrowych `{}`.
- `$"Uczeń: {imie}"` jest zwykle czytelniejsze niż długie łączenie tekstu za pomocą `+`.
- `{wynik:F2}` oznacza wypisanie liczby z dwoma miejscami po przecinku.
- `{wynik:F1}` oznacza wypisanie liczby z jednym miejscem po przecinku.
- `{wynik:F0}` oznacza wypisanie liczby bez miejsc po przecinku.
- Formatowanie zmienia sposób pokazania wartości, ale nie musi zmieniać samej wartości zmiennej.

## Ćwiczenia

1. Wypisz imię i wiek użytkownika w jednym zdaniu.
2. Przepisz przykład z operatorem `+` na interpolację napisów.
3. Wypisz wynik działania w formacie: `5 + 3 = 8`.
4. Oblicz pole prostokąta i wypisz wynik w czytelnym zdaniu.
5. Wczytaj cenę produktu i wypisz ją z dwoma miejscami po przecinku.
6. Wczytaj dwie liczby typu `double` i wypisz średnią z dokładnością do dwóch miejsc po przecinku.
7. Sprawdź różnicę między `{wynik}`, `{wynik:F2}` i `{wynik:F0}`.
8. Napisz trzy komunikaty dla użytkownika z użyciem interpolacji napisów.
