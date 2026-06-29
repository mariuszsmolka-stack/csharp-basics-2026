# else if

## Cel lekcji

Nauczysz się sprawdzać kilka warunków po kolei.

## Krótkie wyjaśnienie

`else if` pozwala dodać kolejne warunki. Program sprawdza je od góry do dołu i wykonuje pierwszy pasujący blok.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int punkty = 82;

        if (punkty >= 90)
        {
            Console.WriteLine("Ocena 5");
        }
        else if (punkty >= 75)
        {
            Console.WriteLine("Ocena 4");
        }
        else if (punkty >= 50)
        {
            Console.WriteLine("Ocena 3");
        }
        else
        {
            Console.WriteLine("Ocena 2");
        }
    }
}
```

## Najważniejsze elementy

- Kolejność warunków ma znaczenie.
- Po znalezieniu pasującego warunku reszta nie jest sprawdzana.
- `else` na końcu obsługuje pozostałe przypadki.
- Przy progach liczbowych zwykle zaczynamy od największych albo od najmniejszych wartości.

## Typowe błędy

- Zła kolejność warunków, na przykład `punkty >= 50` przed `punkty >= 90`.
- Kilka niezależnych instrukcji `if`, gdy potrzebny jest jeden wybór.
- Brak końcowego `else`, gdy trzeba obsłużyć pozostałe przypadki.

## Ćwiczenia kontrolne

1. Napisz warunki dla temperatury: zimno, ciepło, gorąco.
2. Sprawdź ocenę na podstawie liczby punktów.
3. Zmień kolejność warunków i zobacz, jak zmienia się wynik.
