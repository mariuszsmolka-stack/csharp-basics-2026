# Tablice wielowymiarowe

## Od tablicy jednowymiarowej do wielowymiarowej

Tablica jednowymiarowa przypomina listę:

```csharp
int[] liczby = { 1, 2, 3 };
```

Tablica dwuwymiarowa przypomina tabelę:

```csharp
int[,] tabela =
{
    { 1, 2, 3 },
    { 4, 5, 6 }
};
```

Tablica wielowymiarowa ma więcej niż jeden wymiar. Tablica dwuwymiarowa też jest tablicą wielowymiarową, ale najczęściej osobno mówimy o tablicach 2D, bo są najważniejsze w praktyce.

## Wymiar tablicy

Liczba wymiarów mówi, ilu indeksów potrzeba, aby odczytać jeden element tablicy.

- Jeden wymiar: jeden indeks, np. `liczby[0]`.
- Dwa wymiary: dwa indeksy, np. `tabela[0, 1]`.
- Trzy wymiary: trzy indeksy, np. `dane[0, 1, 2]`.

| Rodzaj tablicy | Składnia typu | Przykład dostępu |
|---|---|---|
| Jednowymiarowa | `int[]` | `liczby[0]` |
| Dwuwymiarowa | `int[,]` | `tabela[0, 1]` |
| Trójwymiarowa | `int[,,]` | `dane[0, 1, 2]` |

## Tablica trójwymiarowa

Tablicę trójwymiarową można wyobrazić sobie jako kilka tabel ułożonych jedna za drugą.

```csharp
int[,,] dane = new int[2, 3, 4];
```

Wyjaśnienie:

- pierwszy wymiar ma rozmiar `2`,
- drugi wymiar ma rozmiar `3`,
- trzeci wymiar ma rozmiar `4`,
- do elementu trzeba podać trzy indeksy.

## Dostęp do elementu

```csharp
using System;

class Program
{
    static void Main()
    {
        int[,,] dane = new int[2, 3, 4];

        dane[0, 0, 0] = 10;
        dane[0, 1, 2] = 25;
        dane[1, 2, 3] = 99;

        Console.WriteLine(dane[0, 0, 0]);
        Console.WriteLine(dane[0, 1, 2]);
        Console.WriteLine(dane[1, 2, 3]);
    }
}
```

Każdy element tablicy trójwymiarowej ma trzy indeksy. W przykładzie program zapisuje i odczytuje trzy różne elementy.

## Diagram: trzy indeksy

```mermaid
---
config:
  flowchart:
    curve: linear
---
flowchart LR
    A([Start])
    B["Tablica trójwymiarowa"]
    C["Indeks 1"]
    D["Indeks 2"]
    E["Indeks 3"]
    F["Odczyt elementu"]
    G([Koniec])

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
```

Diagram pokazuje, że do elementu tablicy trójwymiarowej potrzebne są trzy indeksy.

## GetLength w tablicy trójwymiarowej

Metoda `GetLength` pozwala sprawdzić rozmiar wybranego wymiaru.

- `GetLength(0)` zwraca rozmiar pierwszego wymiaru,
- `GetLength(1)` zwraca rozmiar drugiego wymiaru,
- `GetLength(2)` zwraca rozmiar trzeciego wymiaru.

```csharp
using System;

class Program
{
    static void Main()
    {
        int[,,] dane = new int[2, 3, 4];

        Console.WriteLine(dane.GetLength(0));
        Console.WriteLine(dane.GetLength(1));
        Console.WriteLine(dane.GetLength(2));
    }
}
```

Program wypisze `2`, potem `3`, a potem `4`.

## Przechodzenie po tablicy trójwymiarowej

```csharp
using System;

class Program
{
    static void Main()
    {
        int[,,] dane = new int[2, 2, 3];

        for (int i = 0; i < dane.GetLength(0); i++)
        {
            for (int j = 0; j < dane.GetLength(1); j++)
            {
                for (int k = 0; k < dane.GetLength(2); k++)
                {
                    dane[i, j, k] = i + j + k;
                    Console.WriteLine(dane[i, j, k]);
                }
            }
        }
    }
}
```

Wyjaśnienie:

- pierwsza pętla przechodzi po pierwszym wymiarze,
- druga pętla przechodzi po drugim wymiarze,
- trzecia pętla przechodzi po trzecim wymiarze,
- im więcej wymiarów, tym trudniej czytać kod.

## Kiedy to może mieć sens

Tablice wielowymiarowe mogą mieć sens na przykład dla:

- danych pomiarowych: dzień, godzina, numer czujnika,
- kilku plansz gry,
- prostych danych przestrzennych,
- zestawów tabel.

Na poziomie początkującym najważniejsze są tablice jednowymiarowe i dwuwymiarowe.

## Dlaczego trzeba uważać

Tablice wielowymiarowe szybko robią się trudne do czytania. Jeżeli program ma dużo wymiarów, łatwo pomylić indeksy.

Dlatego zwykle warto bardzo dobrze opanować tablice 1D i 2D, a tablice 3D traktować jako temat dodatkowy.

## Najczęstsze błędy

- Pomylenie `int[,]` z `int[,,]`.
- Użycie za małej liczby indeksów.
- Użycie za dużej liczby indeksów.
- Pomylenie kolejności indeksów.
- Użycie `GetLength(1)` zamiast `GetLength(2)`.
- Wyjście poza zakres tablicy.
- Tworzenie tablicy wielowymiarowej tam, gdzie wystarczyłaby zwykła tablica.

## Ćwiczenia

1. Wskaż, ile indeksów potrzeba do odczytu elementu z tablicy `int[]`.
2. Wskaż, ile indeksów potrzeba do odczytu elementu z tablicy `int[,]`.
3. Wskaż, ile indeksów potrzeba do odczytu elementu z tablicy `int[,,]`.
4. Utwórz tablicę trójwymiarową `int[,,]` o rozmiarze `2x2x2`.
5. Przypisz wartość do elementu `dane[0, 1, 1]`.
6. Wypisz rozmiary wszystkich trzech wymiarów za pomocą `GetLength`.
7. Napisz trzy pętle `for` przechodzące po wszystkich elementach tablicy trójwymiarowej.

## Podsumowanie

Tablica wielowymiarowa ma więcej niż jeden wymiar.

Tablica dwuwymiarowa jest najważniejszym praktycznym przykładem tablicy wielowymiarowej.

Tablica trójwymiarowa w C# ma typ na przykład `int[,,]`. Do elementu tablicy trójwymiarowej potrzeba trzech indeksów.

`GetLength` pozwala sprawdzić rozmiar konkretnego wymiaru. Z dużą liczbą wymiarów trzeba uważać, bo kod staje się trudniejszy do czytania.
