# Suma, średnia, minimum i maksimum

## Cel lekcji

Nauczysz się wykonywać podstawowe obliczenia na elementach tablicy.

## Krótkie wyjaśnienie

Tablice często służą do przechowywania wielu liczb. Możemy policzyć ich sumę, średnią, wartość najmniejszą i największą.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 4, 9, 2, 7 };

        int suma = 0;
        int minimum = liczby[0];
        int maksimum = liczby[0];

        for (int i = 0; i < liczby.Length; i++)
        {
            suma += liczby[i];

            if (liczby[i] < minimum)
            {
                minimum = liczby[i];
            }

            if (liczby[i] > maksimum)
            {
                maksimum = liczby[i];
            }
        }

        double srednia = (double)suma / liczby.Length;

        Console.WriteLine($"Suma: {suma}");
        Console.WriteLine($"Średnia: {srednia:F2}");
        Console.WriteLine($"Minimum: {minimum}");
        Console.WriteLine($"Maksimum: {maksimum}");
    }
}
```

## Najważniejsze elementy

- Sumę zaczynamy zwykle od `0`.
- Minimum i maksimum można ustawić na pierwszy element tablicy.
- Średnia to suma podzielona przez liczbę elementów.
- `(double)suma` pomaga otrzymać wynik z częścią dziesiętną.

## Typowe błędy

- Ustawienie minimum na `0`, gdy wszystkie liczby mogą być dodatnie albo ujemne.
- Dzielenie całkowite przy obliczaniu średniej.
- Warunek `i <= liczby.Length`.
- Brak sprawdzenia, czy tablica ma elementy w bardziej zaawansowanych programach.

## Ćwiczenia kontrolne

1. Policz sumę elementów tablicy.
2. Policz średnią i wypisz ją z dwoma miejscami po przecinku.
3. Znajdź najmniejszą i największą liczbę w tablicy.
