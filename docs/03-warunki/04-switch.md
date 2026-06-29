# switch

## Cel lekcji

Nauczysz się używać instrukcji `switch` do wyboru jednej z wielu stałych opcji.

## Krótkie wyjaśnienie

`switch` sprawdza wartość zmiennej i porównuje ją z przypadkami `case`. Jest wygodny, gdy porównujemy jedną zmienną z kilkoma konkretnymi wartościami.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int dzien = 3;

        switch (dzien)
        {
            case 1:
                Console.WriteLine("Poniedziałek");
                break;
            case 2:
                Console.WriteLine("Wtorek");
                break;
            case 3:
                Console.WriteLine("Środa");
                break;
            default:
                Console.WriteLine("Inny dzień");
                break;
        }
    }
}
```

## Najważniejsze elementy

- `switch` sprawdza jedną wartość.
- `case` oznacza konkretny przypadek.
- `break` kończy obsługę danego przypadku.
- `default` obsługuje sytuację, gdy nic nie pasuje.

## Typowe błędy

- Brak `break`.
- Używanie `switch` do złożonych przedziałów, gdzie lepsze jest `if else`.
- Brak `default`, gdy trzeba obsłużyć nieznaną wartość.

## Ćwiczenia kontrolne

1. Napisz `switch` dla numeru miesiąca od 1 do 3.
2. Napisz `switch` dla znaku działania: `+`, `-`, `*`, `/`.
3. Dodaj `default` dla niepoprawnej opcji menu.
