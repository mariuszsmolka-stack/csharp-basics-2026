# while

## Cel lekcji

Nauczysz się używać pętli `while`.

## Krótkie wyjaśnienie

Pętla `while` wykonuje instrukcje tak długo, jak warunek jest spełniony. Warunek jest sprawdzany przed każdym wykonaniem pętli.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int licznik = 1;

        while (licznik <= 5)
        {
            Console.WriteLine(licznik);
            licznik++;
        }
    }
}
```

## Najważniejsze elementy

- Warunek pętli jest w nawiasach okrągłych.
- Kod pętli jest w klamrach.
- Zmienna sterująca musi się zmieniać.
- `licznik++` zwiększa wartość o `1`.

## Typowe błędy

- Brak zmiany licznika i pętla nieskończona.
- Warunek, który od początku jest fałszywy.
- Zła granica, na przykład `< 5` zamiast `<= 5`.

## Ćwiczenia kontrolne

1. Wypisz liczby od `1` do `10`.
2. Wypisz liczby od `10` do `1`.
3. Wypisz tylko liczby parzyste od `2` do `20`.
