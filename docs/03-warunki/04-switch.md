# Instrukcja switch

## Cel lekcji

Nauczysz się używać instrukcji `switch`, aby wygodnie wybrać jedną z wielu ścieżek działania programu na podstawie wartości jednej zmiennej lub wyrażenia.

Po tej lekcji powinieneś umieć:

- wyjaśnić, kiedy `switch` jest czytelniejszy niż `if / else if`,
- zapisać klasyczną instrukcję `switch`,
- użyć `case`, `break` i `default`,
- wskazać, który przypadek zostanie wykonany,
- dobrać `switch` albo `if / else if` do prostego problemu.

## 1. Krótkie przypomnienie else if

`else if` pozwala sprawdzać wiele warunków.

Czasem jednak sprawdzamy jedną zmienną na kilka konkretnych wartości, na przykład:

- numer opcji menu,
- numer dnia tygodnia,
- ocenę od `1` do `6`,
- znak działania: `+`, `-`, `*`, `/`.

W takiej sytuacji `switch` może być czytelniejszy niż długi łańcuch `if / else if`.

## 2. Składnia switch

Schemat:

```csharp
switch (zmienna)
{
    case wartosc1:
        // instrukcje
        break;

    case wartosc2:
        // instrukcje
        break;

    default:
        // instrukcje, gdy żadna wartość nie pasuje
        break;
}
```

Najważniejsze elementy:

- `switch` sprawdza wartość podaną w nawiasie,
- `case` oznacza konkretny przypadek,
- `break` kończy wykonanie danego przypadku,
- `default` działa wtedy, gdy żaden `case` nie pasuje,
- `default` jest podobny do końcowego `else`.

## 3. Pierwszy przykład - menu

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Wybierz opcję:");
        Console.WriteLine("1 - Start");
        Console.WriteLine("2 - Pomoc");
        Console.WriteLine("3 - Wyjście");

        int opcja = int.Parse(Console.ReadLine());

        switch (opcja)
        {
            case 1:
                Console.WriteLine("Wybrano start.");
                break;

            case 2:
                Console.WriteLine("Wybrano pomoc.");
                break;

            case 3:
                Console.WriteLine("Wybrano wyjście.");
                break;

            default:
                Console.WriteLine("Nieznana opcja.");
                break;
        }
    }
}
```

Jeśli `opcja` ma wartość `1`, wykona się `case 1`.

Jeśli `opcja` ma wartość `2`, wykona się `case 2`.

Jeśli `opcja` ma wartość `3`, wykona się `case 3`.

Dla innej wartości wykona się `default`.

## 4. Dzień tygodnia

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj numer dnia tygodnia od 1 do 7:");
        int dzien = int.Parse(Console.ReadLine());

        switch (dzien)
        {
            case 1:
                Console.WriteLine("Poniedziałek");
                break;

            case 2:
                Console.WriteLine("Wtorek");
                break;

            case 3:
                Console.WriteLine("Środa");
                break;

            case 4:
                Console.WriteLine("Czwartek");
                break;

            case 5:
                Console.WriteLine("Piątek");
                break;

            case 6:
                Console.WriteLine("Sobota");
                break;

            case 7:
                Console.WriteLine("Niedziela");
                break;

            default:
                Console.WriteLine("Niepoprawny numer dnia.");
                break;
        }
    }
}
```

Ten przykład dobrze pasuje do `switch`, ponieważ sprawdzamy jedną zmienną `dzien` i konkretne wartości od `1` do `7`.

## 5. Ocena szkolna

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj ocenę od 1 do 6:");
        int ocena = int.Parse(Console.ReadLine());

        switch (ocena)
        {
            case 1:
                Console.WriteLine("Niedostateczny");
                break;

            case 2:
                Console.WriteLine("Dopuszczający");
                break;

            case 3:
                Console.WriteLine("Dostateczny");
                break;

            case 4:
                Console.WriteLine("Dobry");
                break;

            case 5:
                Console.WriteLine("Bardzo dobry");
                break;

            case 6:
                Console.WriteLine("Celujący");
                break;

            default:
                Console.WriteLine("Ocena poza zakresem.");
                break;
        }
    }
}
```

`default` obsługuje sytuację, gdy użytkownik poda wartość spoza zakresu `1`-`6`.

## 6. Wybór działania kalkulatora

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj pierwszą liczbę:");
        double a = double.Parse(Console.ReadLine());

        Console.WriteLine("Podaj drugą liczbę:");
        double b = double.Parse(Console.ReadLine());

        Console.WriteLine("Wybierz działanie:");
        Console.WriteLine("+ dodawanie");
        Console.WriteLine("- odejmowanie");
        Console.WriteLine("* mnożenie");
        Console.WriteLine("/ dzielenie");

        string dzialanie = Console.ReadLine();

        switch (dzialanie)
        {
            case "+":
                Console.WriteLine($"Wynik: {a + b}");
                break;

            case "-":
                Console.WriteLine($"Wynik: {a - b}");
                break;

            case "*":
                Console.WriteLine($"Wynik: {a * b}");
                break;

            case "/":
                Console.WriteLine($"Wynik: {a / b}");
                break;

            default:
                Console.WriteLine("Nieznane działanie.");
                break;
        }
    }
}
```

To jest prosty przykład dydaktyczny. Nie sprawdza jeszcze dzielenia przez zero ani błędnych danych wejściowych. Walidacja danych będzie rozwijana później.

## 7. Switch a if / else if

Używaj `switch`, gdy:

- sprawdzasz jedną zmienną,
- porównujesz ją z konkretnymi wartościami,
- masz kilka lub kilkanaście prostych przypadków.

Używaj `if / else if`, gdy:

- warunki są zakresami, na przykład `punkty >= 90`,
- warunki są bardziej złożone,
- używasz porównań typu `>`, `<`, `>=`, `<=`,
- sprawdzasz kilka różnych zmiennych.

Progi punktów zwykle lepiej wyglądają jako `if / else if`:

```csharp
using System;

class Program
{
    static void Main()
    {
        int punkty = 82;

        if (punkty >= 90)
        {
            Console.WriteLine("Wynik bardzo dobry.");
        }
        else if (punkty >= 75)
        {
            Console.WriteLine("Wynik dobry.");
        }
        else if (punkty >= 50)
        {
            Console.WriteLine("Wynik wystarczający.");
        }
        else
        {
            Console.WriteLine("Wynik niewystarczający.");
        }
    }
}
```

Tutaj warunki są zakresami, więc klasyczne `if / else if` jest czytelniejsze.

## 8. Zgadnij, który case się wykona

Przykład z odpowiedzią:

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
                Console.WriteLine("Inna opcja");
                break;
        }
    }
}
```

Odpowiedź: program wypisze `Pomoc`, ponieważ `opcja` ma wartość `2`.

Spróbuj przewidzieć wyniki:

```csharp
using System;

class Program
{
    static void Main()
    {
        int dzien = 5;

        switch (dzien)
        {
            case 1:
                Console.WriteLine("Poniedziałek");
                break;

            case 5:
                Console.WriteLine("Piątek");
                break;

            default:
                Console.WriteLine("Inny dzień");
                break;
        }

        string znak = "*";

        switch (znak)
        {
            case "+":
                Console.WriteLine("Dodawanie");
                break;

            case "*":
                Console.WriteLine("Mnożenie");
                break;

            default:
                Console.WriteLine("Nieznane działanie");
                break;
        }

        int ocena = 7;

        switch (ocena)
        {
            case 1:
                Console.WriteLine("Niedostateczny");
                break;

            case 6:
                Console.WriteLine("Celujący");
                break;

            default:
                Console.WriteLine("Ocena poza zakresem");
                break;
        }
    }
}
```

Odpowiedzi:

- pierwszy przykład wypisze `Piątek`,
- drugi przykład wypisze `Mnożenie`,
- trzeci przykład wypisze `Ocena poza zakresem`.

## 9. Typowe błędy

### Błąd 1 - brak break

`break` kończy dany przypadek.

W podstawowych przykładach w tym kursie po każdym `case` stosujemy `break`.

Brak `break` jest częstym błędem i może powodować problem z kompilacją albo nieoczekiwane działanie zależnie od kodu.

### Błąd 2 - brak default

`default` obsługuje wartości, których nie przewidziano w `case`.

Warto dodawać `default` szczególnie przy danych od użytkownika.

### Błąd 3 - zły typ wartości w case

Jeśli `switch` sprawdza `int`, `case` powinien zawierać wartości typu `int`.

```csharp
switch (opcja)
{
    case 1:
        Console.WriteLine("Start");
        break;
}
```

Jeśli `switch` sprawdza `string`, `case` powinien zawierać tekst w cudzysłowie.

```csharp
switch (dzialanie)
{
    case "+":
        Console.WriteLine("Dodawanie");
        break;
}
```

### Błąd 4 - używanie switch do zakresów

Klasyczny `switch` dobrze sprawdza konkretne wartości.

Do zakresów typu `punkty >= 90` zwykle lepsze jest `if / else if`.

## 10. Krótka wzmianka o nowoczesnym switch

W nowszych wersjach C# istnieją także bardziej zaawansowane formy `switch`, na przykład `switch expression`.

W tym kursie na razie używamy klasycznej instrukcji `switch`, bo jest czytelna i wystarczająca do podstaw programowania konsolowego.

## 11. Zapowiedź kolejnej części

Po poznaniu `if`, `if else`, `else if` i `switch` można budować programy podejmujące decyzje.

W kolejnych działach pojawią się pętle, które pozwalają wielokrotnie wykonywać instrukcje.

## Zapamiętaj

- `switch` wybiera przypadek na podstawie wartości.
- `case` oznacza konkretną wartość.
- `break` kończy obsługę danego przypadku.
- `default` obsługuje pozostałe wartości.
- `switch` jest dobry do wielu konkretnych wartości jednej zmiennej.
- `if / else if` jest lepszy do zakresów i bardziej złożonych warunków.

## Ćwiczenia

1. Wczytaj numer dnia tygodnia i wypisz nazwę dnia za pomocą `switch`.
2. Wczytaj ocenę od `1` do `6` i wypisz jej opis.
3. Napisz menu z opcjami: `1 - Start`, `2 - Ustawienia`, `3 - Wyjście`.
4. Wczytaj znak działania `+`, `-`, `*`, `/` i wypisz nazwę działania.
5. Rozbuduj przykład kalkulatora o działanie modulo dla liczb całkowitych.
6. Dodaj `default` do przykładu, który go nie ma.
7. Wskaż, który `case` wykona się dla podanej wartości.
8. Wyjaśnij, kiedy lepiej użyć `switch`, a kiedy `if / else if`.
9. Popraw przykład, w którym `case` ma tekst, a `switch` sprawdza liczbę.
10. Napisz własny przykład `switch` z co najmniej trzema przypadkami i `default`.
