# foreach

## Cel lekcji

Nauczysz się używać pętli `foreach` do odczytu elementów tablicy.

## Krótkie wyjaśnienie

`foreach` przechodzi po wszystkich elementach tablicy bez ręcznego używania indeksów. Jest czytelny, gdy chcemy tylko odczytać wartości.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        string[] imiona = { "Ala", "Ola", "Jan" };

        foreach (string imie in imiona)
        {
            Console.WriteLine(imie);
        }
    }
}
```

## Najważniejsze elementy

- `foreach` pobiera po kolei każdy element.
- Zmienna po lewej stronie ma typ elementu tablicy.
- `in` wskazuje tablicę, po której przechodzimy.
- `foreach` jest dobry do odczytu danych.

## Typowe błędy

- Próba użycia indeksu `i`, którego nie ma w `foreach`.
- Zmiana rozmiaru tablicy, co nie jest możliwe.
- Używanie złego typu zmiennej, na przykład `int` dla tablicy `string[]`.

## Ćwiczenia kontrolne

1. Wypisz wszystkie oceny z tablicy.
2. Wypisz wszystkie nazwy produktów z tablicy.
3. Porównaj zapis `for` i `foreach` dla tej samej tablicy.
