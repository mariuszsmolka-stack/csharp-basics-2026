# Typy danych

## Cel lekcji

Poznasz podstawowe typy danych: `int`, `double`, `string`, `bool` i `char`.

## Krótkie wyjaśnienie

Typ danych określa, jaką wartość może przechowywać zmienna. C# jest językiem silnie typowanym, więc typ zmiennej jest ważny.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba = 10;
        double temperatura = 21.5;
        string imie = "Ola";
        bool czyPelnoletni = false;
        char znak = 'A';

        Console.WriteLine(liczba);
        Console.WriteLine(temperatura);
        Console.WriteLine(imie);
        Console.WriteLine(czyPelnoletni);
        Console.WriteLine(znak);
    }
}
```

## Najważniejsze elementy

- `int` przechowuje liczby całkowite.
- `double` przechowuje liczby z częścią dziesiętną.
- `string` przechowuje tekst.
- `bool` przechowuje wartość `true` albo `false`.
- `char` przechowuje jeden znak w apostrofach.

## Typowe błędy

- Zapis liczby `21,5` zamiast `21.5` w kodzie.
- Zapis znaku `char` w cudzysłowie zamiast w apostrofach.
- Przypisanie tekstu do zmiennej liczbowej.
- Mylenie `string` i `char`.

## Ćwiczenia kontrolne

1. Utwórz zmienną typu `double` z ceną produktu.
2. Utwórz zmienną typu `bool`, która przechowuje informację, czy pada deszcz.
3. Utwórz zmienną typu `char` z pierwszą literą swojego imienia.
