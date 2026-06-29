# Tablice jednowymiarowe

## Cel lekcji

Nauczysz się tworzyć tablice jednowymiarowe w C#.

## Krótkie wyjaśnienie

Tablica przechowuje wiele wartości tego samego typu. Zamiast tworzyć kilka zmiennych, można utworzyć jedną tablicę.

## Przykłady kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] oceny = { 5, 4, 3, 5 };

        Console.WriteLine(oceny[0]);
        Console.WriteLine(oceny[1]);
    }
}
```

```csharp
int[] liczby = new int[3];

liczby[0] = 10;
liczby[1] = 20;
liczby[2] = 30;
```

## Najważniejsze elementy

- `int[]` oznacza tablicę liczb całkowitych.
- Elementy tablicy mają ten sam typ.
- Wartości można podać od razu w klamrach.
- Długość tablicy utworzonej przez `new int[3]` wynosi `3`.

## Typowe błędy

- Próba wpisania tekstu do tablicy `int[]`.
- Mylenie liczby elementów z ostatnim indeksem.
- Próba zmiany długości tablicy po utworzeniu.

## Ćwiczenia kontrolne

1. Utwórz tablicę trzech imion.
2. Utwórz tablicę pięciu liczb całkowitych.
3. Wypisz pierwszy element tablicy.
