# Podsumowanie działu - wejście i wyjście w konsoli

## Cel lekcji

Powtórzysz najważniejsze informacje z działu o wejściu i wyjściu w konsoli oraz zobaczysz jeden przykład łączący wczytywanie danych, konwersję, obliczenia i formatowanie wyniku.

Po tym podsumowaniu powinieneś umieć:

- wypisać komunikat dla użytkownika,
- wczytać tekst z konsoli,
- zamienić tekst na liczbę,
- wykonać proste obliczenie,
- wypisać wynik w czytelnej formie.

## 1. Console.WriteLine()

`Console.WriteLine()` wypisuje dane w konsoli i przechodzi do nowej linii.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Witaj w programie!");
    }
}
```

Używamy go do pokazywania komunikatów, pytań i wyników.

## 2. Console.ReadLine()

`Console.ReadLine()` wczytuje tekst wpisany przez użytkownika i czeka na naciśnięcie Enter.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj imię:");
        string imie = Console.ReadLine();

        Console.WriteLine("Witaj, " + imie + "!");
    }
}
```

`Console.ReadLine()` zawsze zwraca `string`.

## 3. Console.ReadLine() zwraca string

Nawet jeśli użytkownik wpisze `10`, program najpierw traktuje tę wartość jako tekst `"10"`.

Tekst `"10"` nie jest tym samym co liczba `10`.

Jeżeli chcemy wykonać obliczenia, trzeba wykonać konwersję.

## 4. Konwersja na int

Do liczb całkowitych możemy użyć `int.Parse()` albo `Convert.ToInt32()`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę punktów:");
        int punkty = int.Parse(Console.ReadLine());

        Console.WriteLine("Punkty: " + punkty);
    }
}
```

Alternatywny zapis:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę punktów:");
        int punkty = Convert.ToInt32(Console.ReadLine());

        Console.WriteLine("Punkty: " + punkty);
    }
}
```

## 5. Konwersja na double

Do liczb rzeczywistych możemy użyć `double.Parse()` albo `Convert.ToDouble()`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj cenę:");
        double cena = double.Parse(Console.ReadLine());

        Console.WriteLine("Cena: " + cena);
    }
}
```

Alternatywny zapis:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj cenę:");
        double cena = Convert.ToDouble(Console.ReadLine());

        Console.WriteLine("Cena: " + cena);
    }
}
```

Przy `double` trzeba pamiętać, że separator dziesiętny zależy od ustawień systemu. Na polskich ustawieniach często używany jest przecinek, na przykład `12,50`.

## 6. TryParse

`TryParse` jest bezpieczniejszym sposobem konwersji, ponieważ pozwala sprawdzić, czy zamiana tekstu na liczbę się udała.

Na tym etapie wystarczy zapamiętać, że `TryParse` istnieje. Szczegółowo wrócimy do niego później, przy sprawdzaniu poprawności danych.

## 7. Interpolacja napisów

Interpolacja napisów pozwala czytelnie wstawiać wartości zmiennych do tekstu.

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int punkty = 25;

        Console.WriteLine($"Uczeń: {imie}, punkty: {punkty}");
    }
}
```

Interpolowany tekst zaczyna się od `$`, a zmienne zapisujemy w nawiasach klamrowych `{}`.

## 8. Formatowanie liczb

Format `{wynik:F2}` wypisuje liczbę z dwoma miejscami po przecinku.

```csharp
using System;

class Program
{
    static void Main()
    {
        double wynik = 10.0 / 3.0;

        Console.WriteLine($"Wynik: {wynik:F2}");
    }
}
```

Formatowanie dotyczy sposobu wypisania wyniku. Nie musi zmieniać samej wartości zmiennej.

## 9. Przykład całościowy

Ten przykład łączy wypisywanie komunikatów, wczytywanie danych, konwersję typów, obliczenia i formatowanie wyniku.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj imię:");
        string imie = Console.ReadLine();

        Console.WriteLine("Podaj liczbę punktów:");
        int punkty = int.Parse(Console.ReadLine());

        Console.WriteLine("Podaj maksymalną liczbę punktów:");
        int maksimum = int.Parse(Console.ReadLine());

        double procent = (double)punkty / maksimum * 100;

        Console.WriteLine($"Uczeń: {imie}");
        Console.WriteLine($"Wynik: {punkty}/{maksimum}");
        Console.WriteLine($"Procent: {procent:F2}%");
    }
}
```

W obliczeniu procentu użyto `(double)`, aby zamienić wartość `punkty` na liczbę rzeczywistą.

Bez tego można przypadkowo otrzymać dzielenie całkowite, czyli wynik bez części dziesiętnej.

Format `F2` dotyczy sposobu wypisania wyniku. Dzięki temu procent jest pokazany z dwoma miejscami po przecinku.

## 10. Typowe błędy

- Brak konwersji przed obliczeniami.
- Wpisanie tekstu tam, gdzie program oczekuje liczby.
- Pomylenie tekstu `"10"` z liczbą `10`.
- Sklejenie tekstów `"10"` i `"20"` zamiast dodania liczb.
- Problem przecinka lub kropki przy liczbach typu `double`.
- Brak komunikatu przed `Console.ReadLine()`.
- Brak znaku `$` przy interpolacji napisów.

## Najważniejsze do zapamiętania

- `Console.WriteLine()` wypisuje dane.
- `Console.ReadLine()` wczytuje tekst.
- `Console.ReadLine()` zwraca `string`.
- Przed obliczeniami tekst trzeba zamienić na liczbę.
- `int.Parse()` i `Convert.ToInt32()` służą do konwersji na `int`.
- `double.Parse()` i `Convert.ToDouble()` służą do konwersji na `double`.
- `TryParse` jest bezpieczniejszą konwersją, do której wrócimy później.
- Interpolacja ma zapis `$"Tekst {zmienna}"`.
- `{wynik:F2}` wypisuje liczbę z dwoma miejscami po przecinku.

## Minićwiczenia powtórkowe

1. Wczytaj imię i wiek, a następnie wypisz je w jednym zdaniu.
2. Wczytaj dwie liczby całkowite i wypisz ich sumę.
3. Wczytaj dwie liczby typu `double` i wypisz średnią z dokładnością do dwóch miejsc po przecinku.
4. Wczytaj cenę netto i wypisz prosty komunikat z tą ceną.
5. Sprawdź, co się stanie, gdy do `int.Parse()` wpiszesz tekst.
6. Popraw program, który skleja teksty `"10"` i `"20"` zamiast dodać liczby.
