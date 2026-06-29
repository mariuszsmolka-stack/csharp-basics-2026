# Indeksy

## Cel lekcji

Nauczysz się odczytywać elementy tablicy za pomocą indeksów.

## Krótkie wyjaśnienie

Indeks to numer miejsca w tablicy. W C# indeksy zaczynają się od `0`, więc pierwszy element ma indeks `0`, a drugi indeks `1`.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        string[] dni = { "poniedziałek", "wtorek", "środa" };

        Console.WriteLine(dni[0]);
        Console.WriteLine(dni[1]);
        Console.WriteLine(dni[2]);
        Console.WriteLine($"Liczba elementów: {dni.Length}");
    }
}
```

## Najważniejsze elementy

- Pierwszy indeks to `0`.
- Ostatni indeks to `Length - 1`.
- `Length` zwraca liczbę elementów tablicy.
- Dostęp do elementu zapisujemy jako `tablica[indeks]`.

## Typowe błędy

- Odczyt `dni[3]` z tablicy, która ma tylko 3 elementy.
- Mylenie `Length` z ostatnim indeksem.
- Używanie nawiasów okrągłych zamiast kwadratowych.

## Ćwiczenia kontrolne

1. Wypisz ostatni element tablicy o długości `4`.
2. Sprawdź wartość `Length` dla tablicy pięciu liczb.
3. Spróbuj odczytać element poza zakresem i zapamiętaj komunikat błędu.
