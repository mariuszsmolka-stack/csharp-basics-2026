# Konwersja typów

## Cel lekcji

Nauczysz się zamieniać tekst pobrany z konsoli na liczby.

## Krótkie wyjaśnienie

`Console.ReadLine()` zwraca `string`. Jeżeli użytkownik wpisze `15`, program widzi to najpierw jako tekst `"15"`. Aby wykonać obliczenia, trzeba zamienić tekst na liczbę.

## Przykłady kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.Write("Podaj wiek: ");
        int wiek = int.Parse(Console.ReadLine());

        Console.WriteLine("Za rok będziesz mieć " + (wiek + 1) + " lat.");
    }
}
```

```csharp
Console.Write("Podaj cenę: ");
double cena = double.Parse(Console.ReadLine());

Console.WriteLine("Cena: " + cena);
```

```csharp
int liczba = Convert.ToInt32(Console.ReadLine());
double wzrost = Convert.ToDouble(Console.ReadLine());
```

```csharp
int liczba;
bool czyPoprawna = int.TryParse(Console.ReadLine(), out liczba);
```

## Najważniejsze elementy

- `int.Parse()` zamienia tekst na `int`.
- `double.Parse()` zamienia tekst na `double`.
- `Convert.ToInt32()` zamienia wartość na liczbę całkowitą.
- `Convert.ToDouble()` zamienia wartość na liczbę typu `double`.
- `TryParse()` jest bezpieczniejszy, bo pozwala sprawdzić, czy konwersja się udała.

## Typowe błędy

- Wpisanie liter tam, gdzie program oczekuje liczby.
- Brak konwersji przed obliczeniami.
- Problemy z separatorem dziesiętnym zależne od ustawień systemu.
- Mylenie `int.Parse` i `double.Parse`.

## Ćwiczenia kontrolne

1. Pobierz dwie liczby całkowite i wypisz ich sumę.
2. Pobierz cenę produktu typu `double` i wypisz ją.
3. Sprawdź, co się stanie, gdy zamiast liczby wpiszesz tekst.
