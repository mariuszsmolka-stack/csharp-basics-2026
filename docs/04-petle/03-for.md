# for

## Cel lekcji

Nauczysz się używać pętli `for`, gdy znasz liczbę powtórzeń.

## Krótkie wyjaśnienie

Pętla `for` często służy do powtarzania instrukcji określoną liczbę razy. W jednej linii zapisujemy wartość początkową, warunek i zmianę licznika.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine(i);
        }
    }
}
```

## Najważniejsze elementy

- `int i = 1` tworzy licznik.
- `i <= 5` określa warunek działania pętli.
- `i++` zwiększa licznik po każdym obiegu.
- Pętla `for` jest bardzo przydatna przy tablicach.

## Typowe błędy

- Zła wartość początkowa licznika.
- Zły warunek końca.
- Brak średników w nawiasie pętli.
- Zmiana licznika w środku pętli bez potrzeby.

## Ćwiczenia kontrolne

1. Wypisz liczby od `0` do `9`.
2. Wypisz liczby od `5` do `15`.
3. Wypisz tabliczkę mnożenia dla liczby `7`.
