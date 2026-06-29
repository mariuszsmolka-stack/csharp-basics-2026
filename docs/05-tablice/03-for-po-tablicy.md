# Pętla for po tablicy

## Cel lekcji

Nauczysz się przechodzić po wszystkich elementach tablicy za pomocą pętli `for`.

## Krótkie wyjaśnienie

Pętla `for` dobrze pasuje do tablic, ponieważ licznik pętli może być jednocześnie indeksem elementu.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 4, 8, 15, 16 };

        for (int i = 0; i < liczby.Length; i++)
        {
            Console.WriteLine(liczby[i]);
        }
    }
}
```

## Najważniejsze elementy

- Licznik zaczyna się od `0`.
- Warunek to zwykle `i < tablica.Length`.
- `tablica[i]` oznacza aktualny element.
- Pętla `for` pozwala też zmieniać elementy tablicy.

## Typowe błędy

- Warunek `i <= tablica.Length`, który wychodzi poza tablicę.
- Start od `1`, przez co pomijany jest pierwszy element.
- Używanie stałej liczby zamiast `Length`.

## Ćwiczenia kontrolne

1. Wypisz wszystkie elementy tablicy imion.
2. Wypisz indeks i wartość każdego elementu.
3. Zwiększ każdy element tablicy liczb o `1`.
