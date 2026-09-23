# TryParse - bezpieczne wczytywanie danych

## Cel lekcji

Nauczysz się bezpiecznie zamieniać tekst wpisany przez użytkownika na liczbę. Poznasz `int.TryParse()` i `double.TryParse()` oraz wykorzystasz instrukcje warunkowe, pętle i parametr `out` do sprawdzania poprawności danych.

Po tej lekcji powinieneś umieć:

- wyjaśnić różnicę między `Parse()` i `TryParse()`,
- sprawdzić, czy użytkownik podał poprawną liczbę,
- wykorzystać wynik typu `bool` zwracany przez `TryParse()`,
- odczytać wynik konwersji przez parametr `out`,
- sprawdzić wymagany zakres liczby,
- ponawiać pytanie aż do wpisania poprawnych danych,
- napisać metodę bezpiecznie wczytującą liczbę całkowitą.

## 1. Problem z int.Parse()

`int.Parse()` zamienia tekst na liczbę całkowitą, jeżeli tekst ma poprawny format.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę:");
        string tekst = Console.ReadLine();

        int liczba = int.Parse(tekst);

        Console.WriteLine($"Podana liczba: {liczba}");
    }
}
```

Dla tekstu `25` program utworzy liczbę `25`. Dla tekstu `abc` albo pustej wartości konwersja nie będzie możliwa i program zakończy działanie błędem.

W programie przeznaczonym dla użytkownika lepiej sprawdzić dane przed wykonaniem obliczeń.

## 2. Czym jest int.TryParse()

`int.TryParse()` próbuje zamienić tekst na liczbę typu `int`.

```csharp
bool czyPoprawna = int.TryParse(tekst, out liczba);
```

Metoda przekazuje dwie informacje:

- zwraca `true`, jeżeli konwersja się udała,
- zwraca `false`, jeżeli konwersja się nie udała,
- przez parametr `out` przekazuje otrzymaną liczbę.

```text
poprawny tekst => true i przekonwertowana liczba
błędny tekst => false
```

`TryParse()` nie przerywa programu tylko dlatego, że użytkownik wpisał tekst, którego nie można zamienić na liczbę.

## 3. Pełny przykład z osobną zmienną string

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę:");
        string tekst = Console.ReadLine();

        int liczba;
        bool czyPoprawna = int.TryParse(tekst, out liczba);

        if (czyPoprawna)
        {
            Console.WriteLine($"Podana liczba: {liczba}");
        }
        else
        {
            Console.WriteLine("Nie podano poprawnej liczby całkowitej.");
        }
    }
}
```

Kolejność działania:

1. `Console.ReadLine()` wczytuje tekst.
2. `int.TryParse()` próbuje zamienić tekst na `int`.
3. Wynik próby trafia do zmiennej `czyPoprawna`.
4. Parametr `out` przekazuje otrzymaną liczbę do zmiennej `liczba`.
5. `if else` wybiera odpowiedni komunikat.

## 4. Deklaracja zmiennej przy out

Zmienną przechowującą wynik można zadeklarować bezpośrednio przy `out`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę:");
        string tekst = Console.ReadLine();

        bool czyPoprawna = int.TryParse(tekst, out int liczba);

        if (czyPoprawna)
        {
            Console.WriteLine($"Podana liczba: {liczba}");
        }
        else
        {
            Console.WriteLine("Niepoprawne dane.");
        }
    }
}
```

Zapis `out int liczba` jednocześnie tworzy zmienną i pozwala metodzie przypisać do niej wynik.

## 5. TryParse jako warunek instrukcji if

Wynik `TryParse()` można wykorzystać bezpośrednio jako warunek.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę:");
        string tekst = Console.ReadLine();

        if (int.TryParse(tekst, out int liczba))
        {
            Console.WriteLine($"Podana liczba: {liczba}");
        }
        else
        {
            Console.WriteLine("Nie podano poprawnej liczby.");
        }
    }
}
```

- `true` => wykonywany jest pierwszy blok,
- `false` => wykonywany jest blok `else`.

## 6. double.TryParse()

`double.TryParse()` próbuje utworzyć liczbę typu `double`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj cenę produktu:");
        string tekst = Console.ReadLine();

        if (double.TryParse(tekst, out double cena))
        {
            Console.WriteLine($"Cena: {cena}");
        }
        else
        {
            Console.WriteLine("Nie podano poprawnej ceny.");
        }
    }
}
```

Separator dziesiętny zależy od ustawień regionalnych systemu. Na polskich ustawieniach zwykle używany jest przecinek, na przykład `12,50`. W innych ustawieniach może być wymagana kropka, na przykład `12.50`.

Na tym etapie nie używamy `CultureInfo`. Sprawdzamy zapis działający na używanym komputerze.

## 7. Sprawdzanie zakresu

Poprawna konwersja nie oznacza jeszcze, że liczba jest odpowiednia dla programu. Wiek `250` jest liczbą całkowitą, ale nie jest prawidłową wartością wieku użytkownika.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj wiek:");
        string tekst = Console.ReadLine();

        if (int.TryParse(tekst, out int wiek))
        {
            if (wiek >= 0 && wiek <= 120)
            {
                Console.WriteLine($"Poprawny wiek: {wiek}");
            }
            else
            {
                Console.WriteLine("Wiek musi należeć do zakresu od 0 do 120.");
            }
        }
        else
        {
            Console.WriteLine("Wiek musi być liczbą całkowitą.");
        }
    }
}
```

Program osobno sprawdza:

- czy tekst można zamienić na `int`,
- czy liczba należy do zakresu od `0` do `120`.

## 8. Ponawianie pytania za pomocą while

```csharp
using System;

class Program
{
    static void Main()
    {
        bool czyPoprawna = false;
        int liczba = 0;

        while (!czyPoprawna)
        {
            Console.WriteLine("Podaj liczbę całkowitą:");
            string tekst = Console.ReadLine();

            czyPoprawna = int.TryParse(tekst, out liczba);

            if (!czyPoprawna)
            {
                Console.WriteLine("Niepoprawne dane. Spróbuj ponownie.");
            }
        }

        Console.WriteLine($"Wczytana liczba: {liczba}");
    }
}
```

Pętla działa, dopóki `czyPoprawna` ma wartość `false`. Po poprawnej konwersji zmienna otrzymuje wartość `true`, pętla się kończy, a `liczba` zawiera wynik.

## 9. Ponawianie pytania za pomocą do while

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba;
        bool czyPoprawna;

        do
        {
            Console.WriteLine("Podaj liczbę całkowitą:");
            string tekst = Console.ReadLine();

            czyPoprawna = int.TryParse(tekst, out liczba);

            if (!czyPoprawna)
            {
                Console.WriteLine("Niepoprawne dane. Spróbuj ponownie.");
            }
        }
        while (!czyPoprawna);

        Console.WriteLine($"Wczytana liczba: {liczba}");
    }
}
```

Pytanie pojawia się co najmniej raz. Warunek po `while` decyduje, czy trzeba je powtórzyć.

## 10. Metoda WczytajLiczbeCalkowita()

Powtarzający się kod warto umieścić w metodzie.

```csharp
using System;

class Program
{
    static int WczytajLiczbeCalkowita(string komunikat)
    {
        while (true)
        {
            Console.WriteLine(komunikat);
            string tekst = Console.ReadLine();

            if (int.TryParse(tekst, out int liczba))
            {
                return liczba;
            }

            Console.WriteLine("Niepoprawne dane. Spróbuj ponownie.");
        }
    }

    static void Main()
    {
        int wiek = WczytajLiczbeCalkowita("Podaj wiek:");
        int punkty = WczytajLiczbeCalkowita("Podaj liczbę punktów:");

        Console.WriteLine($"Wiek: {wiek}");
        Console.WriteLine($"Liczba punktów: {punkty}");
    }
}
```

Metoda:

- otrzymuje komunikat wyświetlany użytkownikowi,
- ponawia pytanie w pętli,
- zwraca liczbę dopiero po poprawnej konwersji,
- może być wywoływana wiele razy.

## 11. Bezpieczne wczytanie dwóch liczb

```csharp
using System;

class Program
{
    static int WczytajLiczbeCalkowita(string komunikat)
    {
        while (true)
        {
            Console.WriteLine(komunikat);
            string tekst = Console.ReadLine();

            if (int.TryParse(tekst, out int liczba))
            {
                return liczba;
            }

            Console.WriteLine("Niepoprawne dane. Spróbuj ponownie.");
        }
    }

    static void Main()
    {
        int pierwszaLiczba = WczytajLiczbeCalkowita("Podaj pierwszą liczbę:");
        int drugaLiczba = WczytajLiczbeCalkowita("Podaj drugą liczbę:");

        int suma = pierwszaLiczba + drugaLiczba;

        Console.WriteLine($"Suma: {suma}");
    }
}
```

Dzięki metodzie główna część programu pozostaje krótka i czytelna.

## 12. Parse, Convert i TryParse

| Cecha | `int.Parse()` | `Convert.ToInt32()` | `int.TryParse()` |
|---|---|---|---|
| Poprawny tekst | Zwraca liczbę | Zwraca liczbę | Zwraca `true` i przekazuje liczbę przez `out` |
| Błędny tekst | Kończy program błędem | Kończy program błędem | Zwraca `false` |
| Zwracany wynik | `int` | `int` | `bool` |
| Parametr `out` | Nie | Nie | Tak |
| Typowe zastosowanie | Dane uznane za poprawne | Prosta konwersja | Dane wpisywane przez użytkownika |

Dla danych wpisywanych przez użytkownika `TryParse()` zwykle jest bezpieczniejszym wyborem.

## Typowe błędy

- Oczekiwanie, że `TryParse()` zwraca przekonwertowaną liczbę.
- Zapomnienie o parametrze `out`.
- Użycie liczby jako pierwszego argumentu zamiast tekstu.
- Sprawdzenie formatu bez sprawdzenia wymaganego zakresu.
- Odwrócenie warunku pętli.
- Brak czytelnego komunikatu o błędnych danych.
- Użycie `int.TryParse()` do liczby z częścią dziesiętną.
- Założenie, że separator dziesiętny jest taki sam na każdym komputerze.

## Zapamiętaj

- `TryParse()` sprawdza, czy tekst można zamienić na określony typ.
- `int.TryParse()` próbuje utworzyć liczbę całkowitą.
- `double.TryParse()` próbuje utworzyć liczbę rzeczywistą.
- Metoda zwraca `true` albo `false`.
- Liczba jest przekazywana przez parametr `out`.
- Format i zakres danych sprawdzamy osobno.
- Pętla pozwala ponawiać pytanie.
- Powtarzający się kod można przenieść do metody.

## Ćwiczenia

1. Wczytaj wiek za pomocą `int.TryParse()` i wypisz odpowiedni komunikat.
2. Sprawdź, czy wiek należy do zakresu od `0` do `120`.
3. Wczytaj cenę za pomocą `double.TryParse()`.
4. Wczytuj liczbę w pętli, dopóki użytkownik nie poda poprawnej wartości.
5. Wczytaj bezpiecznie dwie liczby i wypisz ich sumę, różnicę oraz iloczyn.
6. Popraw program używający `int.Parse()` tak, aby błędny tekst nie kończył programu.
7. Napisz metodę `WczytajLiczbeCalkowita()` i użyj jej trzy razy.
8. Napisz metodę wczytującą liczbę całkowitą z wybranego zakresu.
9. Wyjaśnij związek między `TryParse()` i parametrem `out`.
10. Porównaj `int.Parse()` i `int.TryParse()` dla wartości `25`, `abc` oraz pustego tekstu.

## Podsumowanie

`TryParse()` umożliwia bezpieczne sprawdzanie danych wpisywanych przez użytkownika.

Metoda zwraca `bool` informujący o powodzeniu konwersji. Przekonwertowana liczba jest przekazywana przez parametr `out`.

Instrukcje warunkowe pozwalają zareagować na poprawne i błędne dane. Pętle pozwalają ponawiać pytanie, a metoda pozwala uniknąć powtarzania kodu.
