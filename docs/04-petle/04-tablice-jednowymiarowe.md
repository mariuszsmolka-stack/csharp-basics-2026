# Tablice jednowymiarowe - podstawy

## Cel lekcji

Nauczysz się, czym jest tablica jednowymiarowa, jak ją utworzyć oraz jak odwoływać się do jej elementów za pomocą indeksów.

## Krótkie wprowadzenie

Pojedyncza zmienna przechowuje jedną wartość.

Jeśli mamy kilka ocen, punktów albo temperatur, tworzenie wielu osobnych zmiennych jest niewygodne.

Tablica pozwala przechowywać wiele wartości tego samego typu pod jedną nazwą.

Przykład problemu bez tablicy:

```csharp
int ocena1 = 5;
int ocena2 = 4;
int ocena3 = 3;
int ocena4 = 5;
```

Przy większej liczbie danych taki zapis szybko staje się niewygodny. Trudno potem wygodnie przetwarzać takie dane w pętli.

## Czym jest tablica

Tablica to struktura, która przechowuje wiele elementów tego samego typu. Każdy element ma swój numer, czyli indeks.

Tablica przypomina rząd ponumerowanych szuflad. Każda szuflada przechowuje jedną wartość. Nazwa tablicy wskazuje cały rząd szuflad, a indeks wskazuje konkretną szufladę.

## Deklaracja i utworzenie tablicy

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] oceny = new int[4];

        oceny[0] = 5;
        oceny[1] = 4;
        oceny[2] = 3;
        oceny[3] = 5;

        Console.WriteLine(oceny[0]);
        Console.WriteLine(oceny[1]);
        Console.WriteLine(oceny[2]);
        Console.WriteLine(oceny[3]);
    }
}
```

W tym przykładzie:

- `int[]` oznacza tablicę liczb całkowitych,
- `oceny` to nazwa tablicy,
- `new int[4]` tworzy tablicę na `4` elementy,
- elementy mają indeksy `0`, `1`, `2`, `3`,
- nie ma elementu o indeksie `4`,
- `oceny[0]` oznacza pierwszy element tablicy.

## Indeksy zaczynają się od 0

Pierwszy element tablicy ma indeks `0`.

Drugi element ma indeks `1`.

Trzeci element ma indeks `2`.

Ostatni element tablicy ma indeks `Length - 1`.

Tablica o długości `4`:

| Indeks | Element |
| --- | --- |
| `0` | pierwszy |
| `1` | drugi |
| `2` | trzeci |
| `3` | czwarty |

To bardzo ważna zasada. Wiele błędów w tablicach wynika z pomylenia długości tablicy z ostatnim indeksem.

## Inicjalizacja tablicy gotowymi wartościami

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] oceny = { 5, 4, 3, 5 };

        Console.WriteLine(oceny[0]);
        Console.WriteLine(oceny[1]);
        Console.WriteLine(oceny[2]);
        Console.WriteLine(oceny[3]);
    }
}
```

Jeśli znamy wartości od razu, możemy zapisać je w nawiasach klamrowych.

C# sam rozpozna, że tablica ma `4` elementy. Indeksy nadal zaczynają się od `0`.

## Tablice różnych typów

```csharp
int[] punkty = { 10, 15, 20 };
double[] temperatury = { 21.5, 22.0, 19.8 };
string[] imiona = { "Anna", "Jan", "Ewa" };
bool[] wyniki = { true, false, true };
```

Tablica przechowuje elementy jednego typu:

- `int[]` to tablica liczb całkowitych,
- `double[]` to tablica liczb rzeczywistych,
- `string[]` to tablica tekstów,
- `bool[]` to tablica wartości `true` albo `false`.

## Zmiana wartości elementu tablicy

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] punkty = { 10, 15, 20 };

        Console.WriteLine(punkty[1]);

        punkty[1] = 18;

        Console.WriteLine(punkty[1]);
    }
}
```

`punkty[1]` oznacza drugi element tablicy.

Najpierw ma wartość `15`. Potem zmieniamy go na `18`. Po zmianie wypisze się `18`.

## Właściwość Length

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] punkty = { 10, 15, 20 };

        Console.WriteLine($"Liczba elementów: {punkty.Length}");
    }
}
```

`Length` zwraca liczbę elementów tablicy.

Dla tablicy `{ 10, 15, 20 }` wartość `Length` wynosi `3`.

Ostatni indeks to `punkty.Length - 1`. W kolejnej lekcji `Length` będzie bardzo ważne przy pętli `for`.

## Wyjaśnienie

Wyobraź sobie komodę z pięcioma szufladami na oceny.

Nie chcesz mieć pięciu osobnych zmiennych:

- `ocena1`,
- `ocena2`,
- `ocena3`,
- `ocena4`,
- `ocena5`.

Wolisz mieć jedną komodę o nazwie `oceny`.

Każda szuflada ma swój numer, czyli indeks:

- `oceny[0]` - pierwsza szuflada,
- `oceny[1]` - druga szuflada,
- `oceny[2]` - trzecia szuflada.

Tablica to uporządkowany zestaw miejsc na dane.

Nazwa tablicy mówi, o którą komodę chodzi. Indeks mówi, do której szuflady zaglądasz.

Ważne: w C# numerowanie zaczyna się od `0`, więc pierwsza szuflada ma indeks `0`, a nie `1`.

## Typowe błędy

### Błąd 1: odwołanie do nieistniejącego indeksu

```csharp
int[] liczby = { 10, 20, 30 };

Console.WriteLine(liczby[3]);
```

Tablica ma `3` elementy. Poprawne indeksy to `0`, `1`, `2`.

Indeks `3` nie istnieje. Taki błąd powoduje błąd wykonania programu.

### Błąd 2: mylenie długości z ostatnim indeksem

Jeśli `Length` wynosi `3`, ostatni indeks to `2`.

Ostatni indeks to zawsze `Length - 1`.

### Błąd 3: próba przechowywania różnych typów w jednej tablicy

`int[]` przechowuje liczby całkowite. Nie można do niej wpisać tekstu.

Tablica ma jeden określony typ elementów.

### Błąd 4: zbyt wiele osobnych zmiennych zamiast tablicy

Jeśli dane są podobnego rodzaju, na przykład oceny, punkty albo temperatury, tablica jest zwykle wygodniejsza niż wiele osobnych zmiennych.

## Zapowiedź kolejnej lekcji

W tej lekcji odwoływaliśmy się do elementów tablicy pojedynczo.

W kolejnej lekcji połączymy tablice z pętlą `for`, aby wygodnie przechodzić po wszystkich elementach tablicy.

## Zapamiętaj

- Tablica przechowuje wiele wartości tego samego typu.
- `int[]` oznacza tablicę liczb całkowitych.
- Indeks wskazuje konkretny element tablicy.
- Indeksy zaczynają się od `0`.
- Pierwszy element to `tablica[0]`.
- Ostatni element to `tablica[tablica.Length - 1]`.
- `Length` oznacza liczbę elementów tablicy.
- Odwołanie do nieistniejącego indeksu powoduje błąd.

## Ćwiczenia

1. Utwórz tablicę `int[]` z trzema ocenami i wypisz pierwszy element.
2. Utwórz tablicę `string[]` z trzema imionami i wypisz drugie imię.
3. Utwórz tablicę `double[]` z trzema temperaturami i wypisz ostatni element.
4. Zmień wartość drugiego elementu tablicy punktów.
5. Wypisz długość tablicy za pomocą `Length`.
6. Dla tablicy o długości `5` wskaż poprawne indeksy.
7. Wyjaśnij, dlaczego `tablica[5]` jest błędna dla tablicy pięcioelementowej.
8. Utwórz tablicę `bool[]` z trzema wartościami.
9. Przepisz przykład z `ocena1`, `ocena2`, `ocena3` na tablicę.
10. Wskaż, który element jest pierwszy, a który ostatni w podanej tablicy.
