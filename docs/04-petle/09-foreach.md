# Pętla foreach

## Cel lekcji

Nauczysz się używać pętli `foreach`, gdy chcesz wygodnie przejść po wartościach tablicy i nie potrzebujesz indeksu elementu.

## Krótkie przypomnienie for po tablicy

Pętla `for` używa indeksu.

Indeks pozwala odwołać się do konkretnego elementu tablicy.

Czasem indeks jest potrzebny, ale czasem chcemy tylko odczytać wszystkie wartości.

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 4, 7, 2, 9 };

        for (int i = 0; i < liczby.Length; i++)
        {
            Console.WriteLine(liczby[i]);
        }
    }
}
```

W takim kodzie `i` jest indeksem, a `liczby[i]` jest aktualną wartością z tablicy.

## Składnia foreach

Schemat pętli `foreach` wygląda tak:

```csharp
foreach (typ element in tablica)
{
    // instrukcje wykonywane dla każdego elementu
}
```

`foreach` przechodzi po kolejnych elementach tablicy.

W każdej iteracji zmienna `element` przechowuje aktualną wartość.

Nie używamy indeksu i nie musimy pisać warunku `i < tablica.Length`.

## Pierwszy przykład foreach

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 4, 7, 2, 9 };

        foreach (int liczba in liczby)
        {
            Console.WriteLine(liczba);
        }
    }
}
```

W tym przykładzie:

- `liczby` to tablica,
- `liczba` to aktualny element tablicy,
- pętla wykona się raz dla każdego elementu,
- kod wypisze `4`, `7`, `2`, `9`.

## Nazwa zmiennej w foreach

Zmienna w `foreach` powinna mieć nazwę pojedynczą, a tablica zwykle ma nazwę mnogą.

Dobre przykłady:

```csharp
foreach (int liczba in liczby)
foreach (string imie in imiona)
foreach (double temperatura in temperatury)
foreach (int ocena in oceny)
```

`liczby` oznacza zbiór wielu liczb.

`liczba` oznacza jedną aktualną liczbę.

Taka konwencja poprawia czytelność kodu.

## foreach z tablicą tekstów

```csharp
using System;

class Program
{
    static void Main()
    {
        string[] imiona = { "Anna", "Jan", "Ewa" };

        foreach (string imie in imiona)
        {
            Console.WriteLine($"Uczeń: {imie}");
        }
    }
}
```

Pętla przechodzi po kolejnych tekstach z tablicy `imiona`.

W każdym obiegu zmienna `imie` przechowuje jedno imię.

## Sumowanie za pomocą foreach

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 4, 7, 2, 9 };

        int suma = 0;

        foreach (int liczba in liczby)
        {
            suma += liczba;
        }

        Console.WriteLine($"Suma: {suma}");
    }
}
```

W tym przykładzie:

- `suma` jest akumulatorem,
- `liczba` to aktualny element tablicy,
- `suma += liczba` dodaje aktualny element do sumy.

## Średnia za pomocą foreach

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] oceny = { 5, 4, 3, 5 };

        int suma = 0;

        foreach (int ocena in oceny)
        {
            suma += ocena;
        }

        double srednia = (double)suma / oceny.Length;

        Console.WriteLine($"Średnia: {srednia:F2}");
    }
}
```

Do sumowania używamy `foreach`.

Do liczby elementów nadal używamy `oceny.Length`.

Przy średniej z liczb typu `int` używamy `(double)`, aby otrzymać dzielenie rzeczywiste.

## Zliczanie elementów tablicy spełniających warunek

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 4, -2, 0, 7, -5, 3 };

        int liczbaDodatnich = 0;

        foreach (int liczba in liczby)
        {
            if (liczba > 0)
            {
                liczbaDodatnich++;
            }
        }

        Console.WriteLine($"Liczb dodatnich: {liczbaDodatnich}");
    }
}
```

`foreach` dobrze pasuje, gdy sprawdzamy wartości tablicy.

Nie potrzebujemy indeksu.

Warunek dotyczy aktualnej wartości `liczba`.

## Kiedy for, a kiedy foreach

| Sytuacja | Lepszy wybór |
| --- | --- |
| Potrzebujesz indeksu | `for` |
| Chcesz zmienić element tablicy po indeksie | `for` |
| Chcesz wypisać wszystkie wartości | `foreach` |
| Chcesz policzyć sumę wartości | `foreach` albo `for` |
| Chcesz pokazać numer elementu użytkownikowi | `for` |
| Chcesz używać `i + 1` | `for` |

`foreach` jest czytelny, gdy interesują nas same wartości.

`for` jest potrzebny, gdy ważny jest indeks.

W tym kursie uczymy obu zapisów, bo oba są przydatne.

## Przykład, w którym lepszy jest for

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] punkty = { 10, 15, 20 };

        for (int i = 0; i < punkty.Length; i++)
        {
            Console.WriteLine($"Indeks {i}: {punkty[i]}");
        }
    }
}
```

Tutaj potrzebujemy indeksu, dlatego `for` jest lepszy niż `foreach`.

## Przykład zmiany elementów tablicy

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] punkty = { 10, 15, 20 };

        for (int i = 0; i < punkty.Length; i++)
        {
            punkty[i] += 1;
        }

        foreach (int punkt in punkty)
        {
            Console.WriteLine(punkt);
        }
    }
}
```

Do zmiany elementów tablicy używamy indeksu, dlatego modyfikacja jest wykonana pętlą `for`.

Potem wartości można wypisać pętlą `foreach`.

## Wyjaśnienie metodą Feynmana

Wyobraź sobie, że masz pudełko z kartkami.

Na każdej kartce jest jedna liczba.

Pętla `for` mówi: weź kartkę numer `0`, potem numer `1`, potem numer `2`.

Pętla `foreach` mówi: weź po kolei każdą kartkę z pudełka.

Jeśli nie obchodzi cię numer kartki, tylko jej zawartość, `foreach` jest prostszy.

Jeśli potrzebujesz numeru kartki, użyj `for`.

## Typowe błędy

### Błąd 1: oczekiwanie indeksu w foreach

`foreach` daje aktualną wartość.

Nie daje automatycznie indeksu.

Jeśli potrzebujesz indeksu, użyj `for`.

### Błąd 2: mylenie nazwy tablicy i elementu

Nieczytelnie:

```csharp
foreach (int liczby in liczby)
```

Taka nazwa jest myląca.

Lepiej używać `liczba` dla pojedynczego elementu i `liczby` dla tablicy.

Poprawnie:

```csharp
foreach (int liczba in liczby)
```

### Błąd 3: próba użycia Length nie tam, gdzie trzeba

W `foreach` nie piszemy warunku `i < tablica.Length`.

`foreach` sam przechodzi po wszystkich elementach.

### Błąd 4: używanie foreach, gdy trzeba zmieniać elementy po indeksie

Jeśli chcesz zmienić `tablica[i]`, zwykle użyj `for`.

`foreach` jest najlepszy do odczytu wartości.

## Zgadnij, co wypisze program

Przykład z odpowiedzią:

```csharp
int[] liczby = { 2, 4, 6 };

foreach (int liczba in liczby)
{
    Console.WriteLine(liczba);
}
```

Odpowiedź: program wypisze `2`, `4`, `6`.

Spróbuj najpierw samodzielnie przewidzieć wyniki kolejnych przykładów.

```csharp
string[] imiona = { "Ala", "Ola" };

foreach (string imie in imiona)
{
    Console.WriteLine($"Cześć, {imie}");
}
```

```csharp
int[] liczby = { 1, 2, 3, 4 };
int suma = 0;

foreach (int liczba in liczby)
{
    suma += liczba;
}

Console.WriteLine(suma);
```

```csharp
int[] liczby = { -1, 5, 0, 7 };
int licznik = 0;

foreach (int liczba in liczby)
{
    if (liczba > 0)
    {
        licznik++;
    }
}

Console.WriteLine(licznik);
```

Odpowiedzi:

- pierwszy przykład wypisze `Cześć, Ala` oraz `Cześć, Ola`,
- drugi przykład wypisze `10`,
- trzeci przykład wypisze `2`.

## Zapowiedź kolejnej lekcji

Pętla `foreach` upraszcza przechodzenie po wartościach tablicy.

W kolejnej lekcji można omówić `break` i `continue`, czyli instrukcje sterujące przebiegiem pętli.

## Zapamiętaj

- `foreach` przechodzi po kolejnych wartościach tablicy.
- `foreach` nie wymaga indeksu.
- Zmienna w `foreach` przechowuje aktualny element.
- `for` jest lepszy, gdy potrzebujesz indeksu.
- `foreach` jest czytelny, gdy chcesz tylko odczytać wartości.
- Do zmiany elementów tablicy zwykle używamy `for`.
- Dobra nazwa to na przykład `foreach (int liczba in liczby)`.

## Ćwiczenia

1. Wypisz wszystkie elementy tablicy `int[]` za pomocą `foreach`.
2. Wypisz wszystkie imiona z tablicy `string[]`.
3. Oblicz sumę elementów tablicy za pomocą `foreach`.
4. Oblicz średnią ocen z tablicy, używając `foreach`.
5. Policz liczby dodatnie w tablicy za pomocą `foreach`.
6. Policz liczby parzyste w tablicy za pomocą `foreach`.
7. Wskaż, kiedy lepszy będzie `for`, a kiedy `foreach`.
8. Popraw nieczytelny zapis `foreach (int liczby in liczby)`.
9. Napisz przykład, w którym potrzebujesz indeksu i dlatego używasz `for`.
10. Napisz własny przykład użycia `foreach`.
