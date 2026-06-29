# Formatowanie wyników

## Cel lekcji

Nauczysz się czytelnie wypisywać wyniki i zaokrąglać liczby do dwóch miejsc po przecinku.

## Krótkie wyjaśnienie

Wyniki programu powinny być zrozumiałe dla użytkownika. W C# wygodnie używać interpolacji stringów, czyli zapisu `$"..."`.

## Przykłady kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Ola";
        int punkty = 17;

        Console.WriteLine($"{imie} zdobyła {punkty} punktów.");
    }
}
```

```csharp
double wynik = 10.0 / 3.0;

Console.WriteLine($"Wynik: {wynik:F2}");
Console.WriteLine(Math.Round(wynik, 2));
```

## Najważniejsze elementy

- `$"..."` pozwala wstawiać wartości zmiennych do tekstu.
- Wartości wpisujemy w nawiasach klamrowych `{}`.
- `{wynik:F2}` wyświetla liczbę z dwoma miejscami po przecinku.
- `Math.Round(wynik, 2)` zaokrągla wartość do dwóch miejsc.

## Typowe błędy

- Brak znaku `$` przed tekstem z `{}`.
- Zapisanie nazwy zmiennej w cudzysłowie zamiast w `{}`.
- Mylenie wyświetlenia z zaokrągleniem wartości.

## Ćwiczenia kontrolne

1. Wypisz zdanie z imieniem i wiekiem przy użyciu interpolacji.
2. Oblicz średnią z dwóch liczb i wypisz ją z dwoma miejscami po przecinku.
3. Porównaj wynik `{liczba:F2}` i `Math.Round(liczba, 2)`.
