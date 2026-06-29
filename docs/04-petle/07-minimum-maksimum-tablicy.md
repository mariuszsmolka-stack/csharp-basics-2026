# Minimum i maksimum elementów tablicy

## Cel lekcji

Nauczysz się znajdować najmniejszy i największy element tablicy za pomocą pętli oraz zmiennych pomocniczych `minimum` i `maksimum`.

## Krótkie wprowadzenie

Mając wiele liczb w tablicy, często chcemy znaleźć najmniejszą albo największą wartość.

Nie robimy tego ręcznie. Używamy pętli i porównujemy kolejne elementy tablicy.

## Dlaczego zaczynamy od pierwszego elementu

Nie ustawiamy minimum na `0`, bo tablica może zawierać tylko liczby dodatnie albo tylko liczby ujemne.

Nie ustawiamy maksimum na `0`, bo tablica może zawierać same liczby ujemne.

Bezpieczny sposób to przyjąć pierwszy element tablicy jako początkowe minimum albo maksimum.

```csharp
int minimum = liczby[0];
int maksimum = liczby[0];
```

Na początku zakładamy, że pierwszy element jest jednocześnie najmniejszy i największy.

Potem sprawdzamy kolejne elementy:

- jeśli znajdziemy mniejszy, aktualizujemy `minimum`,
- jeśli znajdziemy większy, aktualizujemy `maksimum`.

## Znalezienie minimum

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 7, 3, 9, 2, 5 };

        int minimum = liczby[0];

        for (int i = 1; i < liczby.Length; i++)
        {
            if (liczby[i] < minimum)
            {
                minimum = liczby[i];
            }
        }

        Console.WriteLine($"Minimum: {minimum}");
    }
}
```

W tym przykładzie:

- `minimum` zaczyna od `liczby[0]`,
- pętla zaczyna od `i = 1`, bo pierwszy element jest już przyjęty jako początkowe minimum,
- jeśli `liczby[i]` jest mniejsze od `minimum`, aktualizujemy `minimum`,
- po zakończeniu pętli `minimum` zawiera najmniejszą wartość.

## Przebieg szukania minimum krok po kroku

Dla tablicy:

```csharp
int[] liczby = { 7, 3, 9, 2, 5 };
```

porównania wyglądają tak:

| i | liczby[i] | minimum przed porównaniem | decyzja | minimum po porównaniu |
| --- | --- | --- | --- | --- |
| `1` | `3` | `7` | `3 < 7`, zmiana minimum | `3` |
| `2` | `9` | `3` | `9 < 3` fałsz | `3` |
| `3` | `2` | `3` | `2 < 3`, zmiana minimum | `2` |
| `4` | `5` | `2` | `5 < 2` fałsz | `2` |

Ostateczne minimum to `2`.

## Znalezienie maksimum

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 7, 3, 9, 2, 5 };

        int maksimum = liczby[0];

        for (int i = 1; i < liczby.Length; i++)
        {
            if (liczby[i] > maksimum)
            {
                maksimum = liczby[i];
            }
        }

        Console.WriteLine($"Maksimum: {maksimum}");
    }
}
```

`maksimum` zaczyna od `liczby[0]`.

Jeśli znajdziemy większą wartość, aktualizujemy `maksimum`.

Po zakończeniu pętli `maksimum` zawiera największą wartość.

## Minimum i maksimum w jednej pętli

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 7, 3, 9, 2, 5 };

        int minimum = liczby[0];
        int maksimum = liczby[0];

        for (int i = 1; i < liczby.Length; i++)
        {
            if (liczby[i] < minimum)
            {
                minimum = liczby[i];
            }

            if (liczby[i] > maksimum)
            {
                maksimum = liczby[i];
            }
        }

        Console.WriteLine($"Minimum: {minimum}");
        Console.WriteLine($"Maksimum: {maksimum}");
    }
}
```

W jednej pętli można sprawdzać oba warunki.

Każdy element porównujemy z aktualnym minimum i aktualnym maksimum. Na końcu mamy obie wartości.

## Wczytanie liczb do tablicy i znalezienie minimum oraz maksimum

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = new int[5];

        for (int i = 0; i < liczby.Length; i++)
        {
            Console.WriteLine($"Podaj liczbę numer {i + 1}:");
            liczby[i] = int.Parse(Console.ReadLine());
        }

        int minimum = liczby[0];
        int maksimum = liczby[0];

        for (int i = 1; i < liczby.Length; i++)
        {
            if (liczby[i] < minimum)
            {
                minimum = liczby[i];
            }

            if (liczby[i] > maksimum)
            {
                maksimum = liczby[i];
            }
        }

        Console.WriteLine($"Minimum: {minimum}");
        Console.WriteLine($"Maksimum: {maksimum}");
    }
}
```

Pierwsza pętla wczytuje dane.

Druga pętla szuka minimum i maksimum.

Zaczynamy porównywanie od indeksu `1`, bo indeks `0` jest wartością startową.

## Wyjaśnienie metodą Feynmana

Wyobraź sobie, że masz stos kartek z wynikami uczniów.

Bierzesz pierwszą kartkę i mówisz: na razie to jest najmniejszy wynik i największy wynik.

Potem bierzesz kolejne kartki:

- jeśli wynik jest mniejszy niż zapisane minimum, podmieniasz minimum,
- jeśli wynik jest większy niż zapisane maksimum, podmieniasz maksimum.

Na końcu nie musisz pamiętać wszystkich porównań. Wystarczy, że masz aktualne minimum i aktualne maksimum.

W programie:

- `liczby[0]` to pierwsza kartka,
- `minimum` to najmniejszy znaleziony wynik,
- `maksimum` to największy znaleziony wynik,
- pętla `for` przechodzi po kolejnych kartkach.

## Typowe błędy

### Błąd 1: ustawienie minimum na 0

Niepoprawnie:

```csharp
int minimum = 0;
```

Jeśli wszystkie liczby w tablicy są dodatnie, wynik może przypadkowo wyjść `0`, mimo że `0` nie ma w tablicy.

Minimum powinno pochodzić z tablicy.

Poprawnie:

```csharp
int minimum = liczby[0];
```

### Błąd 2: ustawienie maksimum na 0

Niepoprawnie:

```csharp
int maksimum = 0;
```

Jeśli wszystkie liczby są ujemne, program błędnie uzna `0` za maksimum.

Maksimum powinno pochodzić z tablicy.

Poprawnie:

```csharp
int maksimum = liczby[0];
```

### Błąd 3: rozpoczynanie pętli od złego indeksu

Jeśli `minimum = liczby[0]`, pętlę można zacząć od `i = 1`.

Można też zacząć od `i = 0`, ale wtedy pierwszy element zostanie porównany sam ze sobą.

W tej lekcji stosujemy `i = 1`, bo jest to czytelne.

### Błąd 4: pomylenie znaków porównania

Do minimum używamy `<`.

Do maksimum używamy `>`.

Pomylenie znaków daje odwrotny wynik.

### Błąd 5: pusta tablica

W tej lekcji zakładamy, że tablica ma co najmniej jeden element.

Dla pustej tablicy zapis `liczby[0]` byłby błędny. Obsługę takich przypadków można omówić później.

## Zgadnij, jaki będzie wynik

Przykład z odpowiedzią:

```csharp
int[] liczby = { 8, 4, 6 };
int minimum = liczby[0];

for (int i = 1; i < liczby.Length; i++)
{
    if (liczby[i] < minimum)
    {
        minimum = liczby[i];
    }
}

Console.WriteLine(minimum);
```

Odpowiedź: program wypisze `4`.

Spróbuj najpierw samodzielnie przewidzieć wyniki kolejnych przykładów.

```csharp
int[] liczby = { 3, 9, 1, 5 };
int maksimum = liczby[0];

for (int i = 1; i < liczby.Length; i++)
{
    if (liczby[i] > maksimum)
    {
        maksimum = liczby[i];
    }
}

Console.WriteLine(maksimum);
```

```csharp
int[] liczby = { -5, -2, -9 };
int maksimum = liczby[0];

for (int i = 1; i < liczby.Length; i++)
{
    if (liczby[i] > maksimum)
    {
        maksimum = liczby[i];
    }
}

Console.WriteLine(maksimum);
```

```csharp
int[] liczby = { 10, 10, 10 };
int minimum = liczby[0];

for (int i = 1; i < liczby.Length; i++)
{
    if (liczby[i] < minimum)
    {
        minimum = liczby[i];
    }
}

Console.WriteLine(minimum);
```

Odpowiedzi:

- pierwszy przykład wypisze `9`,
- drugi przykład wypisze `-2`,
- trzeci przykład wypisze `10`.

## Zapowiedź kolejnej lekcji

Minimum i maksimum to podstawowe operacje na tablicach.

W kolejnej lekcji można wykorzystać warunki do zliczania elementów spełniających określone kryteria, na przykład liczb dodatnich, parzystych albo większych od podanej wartości.

## Zapamiętaj

- Minimum to najmniejsza wartość w tablicy.
- Maksimum to największa wartość w tablicy.
- Bezpiecznie zaczynać od `tablica[0]`.
- Do minimum używamy porównania `<`.
- Do maksimum używamy porównania `>`.
- Pętla może zaczynać się od indeksu `1`, jeśli `tablica[0]` jest wartością startową.
- Nie ustawiamy minimum i maksimum na `0` bez uzasadnienia.
- Zakładamy, że tablica ma co najmniej jeden element.

## Ćwiczenia

1. Utwórz tablicę liczb i znajdź jej minimum.
2. Utwórz tablicę liczb i znajdź jej maksimum.
3. Wczytaj `5` liczb do tablicy i znajdź minimum.
4. Wczytaj `5` liczb do tablicy i znajdź maksimum.
5. Wczytaj `5` liczb do tablicy i znajdź minimum oraz maksimum w jednej pętli.
6. Sprawdź działanie programu dla samych liczb ujemnych.
7. Popraw program, w którym minimum ustawiono na `0`.
8. Popraw program, w którym maksimum ustawiono na `0`.
9. Wyjaśnij, dlaczego ostatni indeks tablicy to `Length - 1`.
10. Napisz własny przykład szukania minimum albo maksimum.
