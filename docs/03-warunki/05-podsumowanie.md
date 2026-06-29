# Podsumowanie działu - instrukcje warunkowe

## Cel lekcji

Powtórzysz najważniejsze informacje z działu o instrukcjach warunkowych i zobaczysz, kiedy używać `if`, `if else`, `else if` oraz `switch`.

Po tym podsumowaniu powinieneś umieć:

- rozpoznać warunek dający `true` albo `false`,
- dobrać odpowiednią instrukcję warunkową,
- odróżnić `=` od `==`,
- wskazać typowe błędy w instrukcjach warunkowych,
- wyjaśnić, kiedy lepszy jest `switch`, a kiedy `if / else if`.

## 1. Po co są instrukcje warunkowe

Instrukcje warunkowe pozwalają programowi podejmować decyzje.

Bez instrukcji warunkowych program wykonuje polecenia po kolei. Dzięki warunkom może wykonać różne instrukcje zależnie od danych.

Przykłady decyzji:

- czy liczba jest dodatnia,
- czy osoba jest pełnoletnia,
- czy wynik punktowy jest wystarczający,
- którą opcję menu wybrał użytkownik.

## 2. Warunek

Warunek to wyrażenie, które daje wynik `true` albo `false`.

```csharp
using System;

class Program
{
    static void Main()
    {
        int x = 12;

        Console.WriteLine(x > 10);
        Console.WriteLine(x == 5);
    }
}
```

Warunki są podstawą działania instrukcji `if`, `if else`, `else if` i często także wyboru, czy dana ścieżka programu ma się wykonać.

## 3. Najważniejsze konstrukcje

| Konstrukcja | Kiedy używać | Przykład |
| --- | --- | --- |
| `if` | gdy sprawdzamy jeden warunek | `liczba > 0` |
| `if else` | gdy są dwie możliwości | pełnoletni / niepełnoletni |
| `else if` | gdy jest kilka warunków | progi punktowe |
| `switch` | gdy sprawdzamy jedną wartość | menu, dzień tygodnia |

## 4. if

`if` wykonuje kod tylko wtedy, gdy warunek jest spełniony.

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba = 8;

        if (liczba > 0)
        {
            Console.WriteLine("Liczba jest dodatnia.");
        }
    }
}
```

Jeśli warunek jest `false`, blok `if` zostaje pominięty.

## 5. if else

`if else` wybiera jedną z dwóch możliwości.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 16;

        if (wiek >= 18)
        {
            Console.WriteLine("Osoba pełnoletnia.");
        }
        else
        {
            Console.WriteLine("Osoba niepełnoletnia.");
        }
    }
}
```

Gdy warunek jest `true`, wykonuje się blok `if`. Gdy warunek jest `false`, wykonuje się blok `else`.

## 6. else if

`else if` pozwala wybrać jedną możliwość spośród wielu warunków.

```csharp
using System;

class Program
{
    static void Main()
    {
        int punkty = 80;

        if (punkty >= 90)
        {
            Console.WriteLine("Bardzo dobry");
        }
        else if (punkty >= 75)
        {
            Console.WriteLine("Dobry");
        }
        else if (punkty >= 50)
        {
            Console.WriteLine("Wystarczający");
        }
        else
        {
            Console.WriteLine("Niewystarczający");
        }
    }
}
```

Warunki są sprawdzane od góry do dołu. Wykonuje się pierwszy pasujący blok, a reszta łańcucha jest pomijana.

## 7. switch

`switch` wybiera przypadek na podstawie jednej wartości.

```csharp
using System;

class Program
{
    static void Main()
    {
        int opcja = 2;

        switch (opcja)
        {
            case 1:
                Console.WriteLine("Start");
                break;

            case 2:
                Console.WriteLine("Pomoc");
                break;

            default:
                Console.WriteLine("Nieznana opcja");
                break;
        }
    }
}
```

`case` oznacza konkretną wartość, `break` kończy obsługę przypadku, a `default` obsługuje pozostałe wartości.

## 8. Operatory często używane w warunkach

Najczęściej spotykane operatory:

- `==` - porównanie równości,
- `!=` - różne,
- `>` - większe,
- `<` - mniejsze,
- `>=` - większe lub równe,
- `<=` - mniejsze lub równe,
- `%` - reszta z dzielenia,
- `&&` - logiczne „i”,
- `||` - logiczne „lub”.

Przykłady:

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba = 12;

        Console.WriteLine(liczba == 12);
        Console.WriteLine(liczba != 0);
        Console.WriteLine(liczba % 2 == 0);
        Console.WriteLine(liczba >= 1 && liczba <= 20);
    }
}
```

## 9. Różnica między = i ==

`=` przypisuje wartość do zmiennej.

`==` porównuje wartości.

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba = 10;

        if (liczba == 10)
        {
            Console.WriteLine("Liczba wynosi 10.");
        }
    }
}
```

W warunkach do sprawdzania równości używamy `==`.

## 10. Kilka if a if / else if / else

Kilka osobnych `if` oznacza kilka niezależnych sprawdzeń.

`if / else if / else` oznacza jeden łańcuch wyboru.

Jeśli chcemy wybrać jedną kategorię wyniku, zwykle używamy `if / else if / else`.

## 11. Kiedy switch, a kiedy if / else if

`switch` jest dobry, gdy:

- sprawdzamy jedną zmienną,
- porównujemy ją z konkretnymi wartościami,
- mamy menu, wybór dnia tygodnia albo wybór działania.

`if / else if` jest lepszy, gdy:

- sprawdzamy zakresy,
- używamy warunków typu `punkty >= 90`,
- warunki są bardziej złożone,
- trzeba porównać kilka różnych wartości.

## 12. Przykład całościowy

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę punktów:");
        int punkty = int.Parse(Console.ReadLine());

        if (punkty >= 50)
        {
            Console.WriteLine("Test zaliczony.");
        }
        else
        {
            Console.WriteLine("Test niezaliczony.");
        }

        Console.WriteLine("Wybierz opcję:");
        Console.WriteLine("1 - Pokaż wynik");
        Console.WriteLine("2 - Pokaż opis");
        Console.WriteLine("3 - Zakończ");

        int opcja = int.Parse(Console.ReadLine());

        switch (opcja)
        {
            case 1:
                Console.WriteLine($"Liczba punktów: {punkty}");
                break;

            case 2:
                Console.WriteLine("To jest prosty przykład użycia instrukcji warunkowych.");
                break;

            case 3:
                Console.WriteLine("Koniec programu.");
                break;

            default:
                Console.WriteLine("Nieznana opcja.");
                break;
        }
    }
}
```

`if else` sprawdza, czy test jest zaliczony.

`switch` obsługuje wybór użytkownika z menu.

Są to dwa różne zastosowania instrukcji warunkowych.

## Najczęstsze błędy

1. Użycie `=` zamiast `==`.
2. Brak nawiasów klamrowych.
3. Średnik po `if`.
4. Zła kolejność warunków w `else if`.
5. Kilka osobnych `if` zamiast `if / else if / else`.
6. Brak `default` w `switch` przy danych od użytkownika.
7. Używanie `switch` do zakresów, gdzie czytelniejszy jest `if / else if`.

## Zgadnij, co wypisze program

Przykład 1:

```csharp
using System;

class Program
{
    static void Main()
    {
        int x = 12;

        if (x > 10)
        {
            Console.WriteLine("A");
        }
        else
        {
            Console.WriteLine("B");
        }
    }
}
```

Przykład 2:

```csharp
using System;

class Program
{
    static void Main()
    {
        int punkty = 80;

        if (punkty >= 90)
        {
            Console.WriteLine("Bardzo dobry");
        }
        else if (punkty >= 75)
        {
            Console.WriteLine("Dobry");
        }
        else if (punkty >= 50)
        {
            Console.WriteLine("Wystarczający");
        }
        else
        {
            Console.WriteLine("Niewystarczający");
        }
    }
}
```

Przykład 3:

```csharp
using System;

class Program
{
    static void Main()
    {
        int opcja = 3;

        switch (opcja)
        {
            case 1:
                Console.WriteLine("Start");
                break;

            case 2:
                Console.WriteLine("Pomoc");
                break;

            case 3:
                Console.WriteLine("Wyjście");
                break;

            default:
                Console.WriteLine("Nieznana opcja");
                break;
        }
    }
}
```

Odpowiedzi:

- przykład 1 wypisze `A`,
- przykład 2 wypisze `Dobry`,
- przykład 3 wypisze `Wyjście`.

## Najważniejsze do zapamiętania

- Instrukcje warunkowe pozwalają programowi podejmować decyzje.
- Warunek daje wynik `true` albo `false`.
- `if` wykonuje kod tylko przy spełnionym warunku.
- `if else` wybiera jedną z dwóch możliwości.
- `else if` pozwala sprawdzić wiele warunków.
- `switch` wybiera przypadek na podstawie jednej wartości.
- `=` przypisuje wartość, a `==` porównuje wartości.
- Kolejność warunków w `else if` ma znaczenie.
- `default` w `switch` obsługuje pozostałe wartości.

## Minićwiczenia powtórkowe

1. Wczytaj liczbę i sprawdź, czy jest dodatnia, ujemna, czy równa zero.
2. Wczytaj wiek i wypisz, czy osoba jest pełnoletnia.
3. Wczytaj liczbę punktów i wypisz kategorię wyniku.
4. Wczytaj numer dnia tygodnia i użyj `switch` do wypisania nazwy dnia.
5. Wczytaj znak działania `+`, `-`, `*`, `/` i użyj `switch` do wypisania nazwy działania.
6. Popraw błąd z `=` zamiast `==`.
7. Popraw złą kolejność progów punktowych.
8. Wyjaśnij, czym różni się `if else` od `else if`.
9. Wyjaśnij, kiedy `switch` jest czytelniejszy niż `else if`.
10. Napisz własny przykład programu z menu tekstowym.
