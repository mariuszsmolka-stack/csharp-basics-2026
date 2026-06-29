# if else

## Cel lekcji

Nauczysz się wybierać jedną z dwóch możliwości.

## Krótkie wyjaśnienie

`if else` pozwala wykonać jeden blok kodu, gdy warunek jest spełniony, albo drugi blok, gdy warunek nie jest spełniony.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba = 7;

        if (liczba % 2 == 0)
        {
            Console.WriteLine("Liczba parzysta.");
        }
        else
        {
            Console.WriteLine("Liczba nieparzysta.");
        }
    }
}
```

## Najważniejsze elementy

- `else` nie ma własnego warunku.
- Blok `else` wykonuje się, gdy warunek z `if` jest fałszywy.
- Operator `%` pomaga sprawdzić resztę z dzielenia.
- Warunek `liczba % 2 == 0` sprawdza parzystość.

## Typowe błędy

- Dopisywanie warunku po `else`.
- Użycie `=` zamiast `==`.
- Zła logika warunku, na przykład sprawdzanie parzystości przez `liczba / 2 == 0`.

## Ćwiczenia kontrolne

1. Sprawdź, czy uczeń zdał, gdy ma co najmniej 50 punktów.
2. Sprawdź, czy hasło jest równe `"admin"`.
3. Sprawdź, czy liczba jest dodatnia albo niedodatnia.
