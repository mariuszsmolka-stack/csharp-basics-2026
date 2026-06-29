# Console.ReadLine

## Cel lekcji

Nauczysz się pobierać dane wpisane przez użytkownika w konsoli.

## Krótkie wyjaśnienie

`Console.ReadLine()` czeka, aż użytkownik wpisze tekst i naciśnie Enter. Wynik tej instrukcji zawsze jest typu `string`, nawet jeśli użytkownik wpisze liczbę.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.Write("Podaj imię: ");
        string imie = Console.ReadLine();

        Console.WriteLine("Witaj, " + imie + "!");
    }
}
```

## Najważniejsze elementy

- `Console.Write()` wypisuje tekst bez przejścia do nowej linii.
- `Console.ReadLine()` pobiera tekst.
- Dane wpisane z klawiatury trafiają do zmiennej typu `string`.
- Liczby pobrane przez `ReadLine()` trzeba zamienić na typ liczbowy.

## Typowe błędy

- Próba zapisania `Console.ReadLine()` bezpośrednio do zmiennej typu `int`.
- Brak komunikatu dla użytkownika, co ma wpisać.
- Mylenie `Console.ReadLine()` z `Console.WriteLine()`.

## Ćwiczenia kontrolne

1. Pobierz imię użytkownika i wypisz powitanie.
2. Pobierz nazwę miasta i wypisz zdanie z tą nazwą.
3. Sprawdź, jaki błąd pojawi się przy próbie wpisania `Console.ReadLine()` do zmiennej `int`.
