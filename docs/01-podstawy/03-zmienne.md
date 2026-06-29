# Zmienne

## Cel lekcji

Nauczysz się tworzyć zmienne i zapisywać w nich wartości.

## Krótkie wyjaśnienie

Zmienna to nazwane miejsce w pamięci programu. Możemy zapisać w niej wartość, a potem używać tej wartości w kolejnych instrukcjach.

## Przykłady kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Ala";
        int wiek = 16;

        Console.WriteLine(imie);
        Console.WriteLine(wiek);
    }
}
```

```csharp
int a = 7;
int b = 3;
int suma = a + b;

Console.WriteLine(suma);
```

## Najważniejsze elementy

- Najpierw podajemy typ zmiennej.
- Potem podajemy nazwę zmiennej.
- Operator `=` przypisuje wartość do zmiennej.
- Nazwy zmiennych powinny być czytelne, na przykład `wiek`, `suma`, `ocena`.

## Typowe błędy

- Użycie zmiennej przed jej utworzeniem.
- Próba wpisania tekstu do zmiennej typu `int`.
- Mylenie przypisania `=` z porównaniem `==`.
- Literówki w nazwach zmiennych.

## Ćwiczenia kontrolne

1. Utwórz zmienną `miasto` i wypisz jej wartość.
2. Utwórz dwie liczby całkowite i wypisz ich sumę.
3. Zmień wartość zmiennej `wiek` i ponownie ją wypisz.
