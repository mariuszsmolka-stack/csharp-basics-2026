# Instrukcje break i continue

## Cel lekcji

Nauczysz się używać instrukcji `break` i `continue` do sterowania przebiegiem pętli.

## Krótkie wprowadzenie

Zwykle pętla wykonuje się tak długo, jak pozwala jej warunek.

Czasami chcemy przerwać pętlę wcześniej. Czasami chcemy pominąć tylko jeden obieg pętli, ale nie kończyć całej pętli.

Do tego służą instrukcje `break` i `continue`.

## Instrukcja break

Instrukcja `break` natychmiast kończy najbliższą pętlę. Program przechodzi wtedy do instrukcji znajdujących się po pętli.

`break` często stosuje się wtedy, gdy znaleziono szukaną wartość albo użytkownik wybrał zakończenie.

## Przykład: przerwanie pętli for

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 1; i <= 10; i++)
        {
            if (i == 5)
            {
                break;
            }

            Console.WriteLine(i);
        }

        Console.WriteLine("Koniec pętli.");
    }
}
```

Program wypisze `1`, `2`, `3`, `4`.

Gdy `i` ma wartość `5`, wykona się `break`. Pętla zostanie przerwana, a program przejdzie do instrukcji po pętli.

## Instrukcja continue

Instrukcja `continue` pomija resztę bieżącego obiegu pętli.

Pętla nie kończy się całkowicie. Program przechodzi do następnego obiegu pętli.

`continue` często stosuje się wtedy, gdy chcemy pominąć wybrane wartości.

## Przykład: pomijanie jednej wartości

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 1; i <= 5; i++)
        {
            if (i == 3)
            {
                continue;
            }

            Console.WriteLine(i);
        }
    }
}
```

Program wypisze `1`, `2`, `4`, `5`.

Gdy `i` ma wartość `3`, instrukcja `continue` pomija `Console.WriteLine(i)`. Pętla działa dalej.

## Różnica między break i continue

| Instrukcja | Co robi | Czy pętla działa dalej? |
| --- | --- | --- |
| `break` | kończy pętlę | nie |
| `continue` | pomija bieżący obieg | tak |

Krótko:

- `break` oznacza: zakończ pętlę,
- `continue` oznacza: przejdź do następnego obiegu.

## Wyjaśnienie metodą Feynmana

Wyobraź sobie, że sprawdzasz listę zadań.

`break`: idziesz po liście i szukasz pierwszego zadania oznaczonego jako pilne. Gdy je znajdziesz, przestajesz dalej sprawdzać listę. To jest `break` - koniec pętli.

`continue`: idziesz po liście zadań. Jeśli zadanie jest już wykonane, pomijasz je i przechodzisz do następnego. To jest `continue` - pomijasz jeden przypadek, ale nadal pracujesz dalej.

## Przykład: szukanie liczby

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 1; i <= 10; i++)
        {
            if (i == 7)
            {
                Console.WriteLine("Znaleziono 7.");
                break;
            }

            Console.WriteLine($"Sprawdzam: {i}");
        }

        Console.WriteLine("Po pętli.");
    }
}
```

Pętla sprawdza kolejne liczby. Przy wartości `7` wypisuje komunikat i kończy pętlę. Liczby po `7` nie są już sprawdzane.

## Przykład: pomijanie liczb parzystych

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 1; i <= 10; i++)
        {
            if (i % 2 == 0)
            {
                continue;
            }

            Console.WriteLine(i);
        }
    }
}
```

Jeśli liczba jest parzysta, wykonuje się `continue`.

Instrukcja `Console.WriteLine(i)` zostaje pominięta dla liczb parzystych. Wypisane zostaną tylko liczby nieparzyste.

## Przykład: break w pętli while

```csharp
using System;

class Program
{
    static void Main()
    {
        while (true)
        {
            Console.WriteLine("Podaj liczbę. Wpisz 0, aby zakończyć:");
            int liczba = int.Parse(Console.ReadLine());

            if (liczba == 0)
            {
                break;
            }

            Console.WriteLine($"Podano: {liczba}");
        }

        Console.WriteLine("Program zakończony.");
    }
}
```

`while (true)` tworzy pętlę działającą bez ograniczenia. Instrukcja `break` kończy ją po wpisaniu `0`.

To przykład dydaktyczny. W prawdziwych programach trzeba uważać, aby pętla miała jasny sposób zakończenia.

## Przykład: continue przy sumowaniu

```csharp
using System;

class Program
{
    static void Main()
    {
        int suma = 0;

        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine($"Podaj liczbę {i}:");
            int liczba = int.Parse(Console.ReadLine());

            if (liczba < 0)
            {
                continue;
            }

            suma += liczba;
        }

        Console.WriteLine($"Suma liczb nieujemnych: {suma}");
    }
}
```

Liczby ujemne są pomijane.

Instrukcja `continue` sprawia, że `suma += liczba` nie wykona się dla liczb ujemnych. Liczby `0` i dodatnie zostaną dodane do sumy.

## Zgadnij, co wypisze program

Przykład z odpowiedzią:

```csharp
for (int i = 1; i <= 5; i++)
{
    if (i == 3)
    {
        break;
    }

    Console.WriteLine(i);
}
```

Odpowiedź: program wypisze `1`, `2`.

Spróbuj najpierw samodzielnie przewidzieć wyniki kolejnych przykładów.

```csharp
for (int i = 1; i <= 5; i++)
{
    if (i == 3)
    {
        continue;
    }

    Console.WriteLine(i);
}
```

```csharp
for (int i = 1; i <= 6; i++)
{
    if (i % 2 == 0)
    {
        continue;
    }

    Console.WriteLine(i);
}
```

```csharp
for (int i = 1; i <= 10; i++)
{
    if (i > 4)
    {
        break;
    }

    Console.WriteLine(i);
}
```

Odpowiedzi:

- pierwszy przykład wypisze `1`, `2`, `4`, `5`,
- drugi przykład wypisze `1`, `3`, `5`,
- trzeci przykład wypisze `1`, `2`, `3`, `4`.

## Typowe błędy

### Błąd 1: mylenie break i continue

`break` kończy całą pętlę.

`continue` kończy tylko bieżący obieg i przechodzi do następnego.

### Błąd 2: continue przed ważną instrukcją aktualizacji w while

Przykład niebezpieczny:

```csharp
int i = 1;

while (i <= 5)
{
    if (i == 3)
    {
        continue;
    }

    Console.WriteLine(i);
    i++;
}
```

Gdy `i == 3`, instrukcja `continue` pomija `i++`. Zmienna `i` zostaje równa `3`, więc powstaje pętla nieskończona.

Poprawny wariant:

```csharp
int i = 1;

while (i <= 5)
{
    if (i == 3)
    {
        i++;
        continue;
    }

    Console.WriteLine(i);
    i++;
}
```

Przed `continue` trzeba zadbać, aby zmienna sterująca pętlą zmieniła wartość.

### Błąd 3: nadużywanie break i continue

`break` i `continue` są przydatne, ale zbyt częste używanie może utrudnić czytanie programu.

Na początku kursu stosujemy je tylko wtedy, gdy wyraźnie upraszczają kod.

### Błąd 4: oczekiwanie, że break kończy cały program

`break` kończy najbliższą pętlę albo `case` w instrukcji `switch`.

Nie kończy całego programu. Po pętli wykonują się dalsze instrukcje.

## Zapowiedź podsumowania działu

Po poznaniu `while`, `do while`, `for`, licznika, akumulatora oraz `break` i `continue` można rozwiązywać wiele typowych zadań z pętlami.

Następnie warto zrobić podsumowanie działu o pętlach.

## Zapamiętaj

- `break` kończy najbliższą pętlę.
- `continue` pomija resztę bieżącego obiegu.
- Po `break` program przechodzi za pętlę.
- Po `continue` pętla przechodzi do kolejnego obiegu.
- W pętli `while` trzeba uważać, aby `continue` nie pominęło zmiany licznika.
- `break` i `continue` należy stosować świadomie.

## Ćwiczenia

1. Wypisz liczby od `1` do `10`, ale przerwij pętlę po liczbie `5`.
2. Wypisz liczby od `1` do `10` z pominięciem liczby `4`.
3. Wypisz tylko liczby nieparzyste od `1` do `20`, używając `continue`.
4. Wczytuj liczby w pętli `while` i zakończ po wpisaniu `0`.
5. Wczytaj `5` liczb i zsumuj tylko liczby nieujemne, używając `continue`.
6. Napisz pętlę, która przerwie działanie po znalezieniu liczby `7`.
7. Przewidź wynik programu z `break`.
8. Przewidź wynik programu z `continue`.
9. Popraw pętlę `while`, w której `continue` powoduje pętlę nieskończoną.
10. Wyjaśnij własnymi słowami różnicę między `break` i `continue`.
