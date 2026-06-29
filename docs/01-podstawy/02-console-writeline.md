# Console.WriteLine

## Cel lekcji

Nauczysz się wypisywać tekst i wartości w konsoli.

## Krótkie wyjaśnienie

`Console.WriteLine()` wypisuje dane i przechodzi do następnej linii. To jedna z najczęściej używanych instrukcji na początku nauki C#.

## Przykłady kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Cześć!");
        Console.WriteLine("Uczę się C#.");
        Console.WriteLine(2026);
    }
}
```

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine(2 + 3);
        Console.WriteLine("2 + 3");
    }
}
```

## Najważniejsze elementy

- Tekst zapisujemy w cudzysłowie.
- Liczby można wypisywać bez cudzysłowu.
- `2 + 3` daje wynik `5`.
- `"2 + 3"` jest zwykłym tekstem.

## Typowe błędy

- Brak cudzysłowu przy tekście.
- Mylenie tekstu `"5"` z liczbą `5`.
- Pisanie `WriteLine` bez `Console.`.

## Ćwiczenia kontrolne

1. Wypisz swoje imię i nazwisko w dwóch liniach.
2. Wypisz wynik działania `10 - 4`.
3. Wypisz tekst `10 - 4` bez obliczania.
