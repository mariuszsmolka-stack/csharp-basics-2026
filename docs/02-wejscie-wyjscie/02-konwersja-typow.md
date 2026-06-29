# Konwersja typów po Console.ReadLine()

## Cel lekcji

Nauczysz się zamieniać tekst wczytany z konsoli na liczby, aby można było wykonać proste obliczenia.

Po tej lekcji powinieneś umieć:

- wyjaśnić, dlaczego `Console.ReadLine()` zwraca `string`,
- zamienić tekst na liczbę całkowitą za pomocą `int.Parse()`,
- zamienić tekst na liczbę rzeczywistą za pomocą `double.Parse()`,
- użyć `Convert.ToInt32()` i `Convert.ToDouble()`,
- wykonać proste obliczenia na liczbach wczytanych z konsoli.

## 1. Przypomnienie: Console.ReadLine() zwraca string

`Console.ReadLine()` zawsze zwraca tekst typu `string`.

Nawet jeśli użytkownik wpisze:

```csharp
123
```

program najpierw traktuje tę wartość jako tekst `"123"`, a nie jako liczbę `123`.

Jeżeli chcemy wykonać obliczenia, musimy przekonwertować tekst na odpowiedni typ liczbowy.

## 2. Dlaczego nie można od razu liczyć na tekście

Tekst `"123"` i liczba `123` to dla programu różne wartości.

Przykład błędu logicznego bez konwersji:

```csharp
using System;

class Program
{
    static void Main()
    {
        string a = "10";
        string b = "20";

        Console.WriteLine(a + b);
    }
}
```

Program wypisze:

```csharp
1020
```

To nie jest dodawanie liczb. To tekstowe sklejenie wartości `"10"` i `"20"`.

Aby otrzymać wynik `30`, potrzebne są liczby, a nie teksty.

## 3. Konwersja tekstu na int

`int.Parse()` zamienia poprawny tekst liczbowy na liczbę całkowitą typu `int`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj swój wiek:");
        string tekst = Console.ReadLine();

        int wiek = int.Parse(tekst);

        Console.WriteLine("Twój wiek to: " + wiek);
    }
}
```

W tym przykładzie są dwa etapy:

- wczytanie tekstu do zmiennej `tekst`,
- konwersja tekstu na liczbę `int`.

Na początku kursu taki zapis jest czytelny, bo pokazuje dokładnie, co dzieje się w programie.

## 4. Krótszy zapis z int.Parse()

Można też zapisać wczytanie i konwersję w jednej instrukcji.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę:");
        int liczba = int.Parse(Console.ReadLine());

        Console.WriteLine("Podana liczba: " + liczba);
    }
}
```

Ten zapis jest poprawny, ale na początku kursu dłuższy zapis bywa czytelniejszy, bo pokazuje dwa etapy:

- wczytanie tekstu,
- konwersję tekstu na liczbę.

## 5. Dodawanie dwóch liczb

Po konwersji można wykonywać działania matematyczne.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj pierwszą liczbę:");
        int a = int.Parse(Console.ReadLine());

        Console.WriteLine("Podaj drugą liczbę:");
        int b = int.Parse(Console.ReadLine());

        int suma = a + b;

        Console.WriteLine("Suma: " + suma);
    }
}
```

Zmienne `a` i `b` są typu `int`, dlatego operator `+` dodaje liczby.

## 6. Konwersja tekstu na double

`double.Parse()` zamienia poprawny tekst liczbowy na liczbę rzeczywistą typu `double`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj wzrost w metrach:");
        double wzrost = double.Parse(Console.ReadLine());

        Console.WriteLine("Wzrost: " + wzrost);
    }
}
```

Typ `double` stosujemy do liczb z częścią dziesiętną, na przykład wzrostu, ceny albo średniej.

Uwaga praktyczna: w zależności od ustawień systemu liczby rzeczywiste mogą wymagać przecinka albo kropki jako separatora dziesiętnego. Na polskich ustawieniach regionalnych często używany jest przecinek, na przykład `1,75`.

## 7. Konwersja za pomocą Convert

Do konwersji można użyć także klasy `Convert`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę punktów:");
        int punkty = Convert.ToInt32(Console.ReadLine());

        Console.WriteLine("Liczba punktów: " + punkty);
    }
}
```

Drugi przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj cenę produktu:");
        double cena = Convert.ToDouble(Console.ReadLine());

        Console.WriteLine("Cena produktu: " + cena);
    }
}
```

Najważniejsze metody:

- `Convert.ToInt32()` zamienia wartość na liczbę całkowitą,
- `Convert.ToDouble()` zamienia wartość na liczbę rzeczywistą.

## 8. Parse i Convert

`Parse` i `Convert` służą do konwersji danych.

Na tym etapie możesz zapamiętać proste rozróżnienie:

- `int.Parse()` i `double.Parse()` jasno pokazują, na jaki typ zamieniamy tekst,
- `Convert.ToInt32()` i `Convert.ToDouble()` są alternatywnym sposobem konwersji.

W prostych programach konsolowych oba sposoby mogą być używane. Ważne jest, aby rozumieć, że przed obliczeniami tekst z `Console.ReadLine()` trzeba zamienić na liczbę.

## 9. Typowe błędy przy konwersji

Program może zakończyć się błędem, jeśli użytkownik wpisze dane w złym formacie.

Typowe sytuacje:

- użytkownik wpisze tekst zamiast liczby, na przykład `ala`,
- użytkownik zostawi pustą wartość i naciśnie Enter,
- użytkownik wpisze liczbę rzeczywistą z separatorem niezgodnym z ustawieniami systemu.

Przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę:");
        int liczba = int.Parse(Console.ReadLine());

        Console.WriteLine("Liczba: " + liczba);
    }
}
```

Jeśli użytkownik wpisze `abc`, program nie będzie mógł zamienić tego tekstu na `int`.

## 10. TryParse jako bezpieczniejszy sposób

`TryParse` pozwala bezpieczniej sprawdzić, czy konwersja się udała.

Na razie traktujemy `TryParse` tylko jako zapowiedź. Szczegółowo wrócimy do niego później, gdy będziemy omawiać sprawdzanie poprawności danych.

## 11. Proste obliczenia po konwersji

Po zamianie tekstu na liczby można wykonać obliczenia.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj długość boku kwadratu:");
        int bok = int.Parse(Console.ReadLine());

        int obwod = 4 * bok;

        Console.WriteLine("Obwód kwadratu: " + obwod);
    }
}
```

W tym przykładzie zmienna `bok` jest liczbą typu `int`, dlatego można obliczyć obwód kwadratu.

## Typowe błędy

- Wykonywanie obliczeń na tekście zamiast na liczbach.
- Zapominanie, że `Console.ReadLine()` zwraca `string`.
- Wpisanie tekstu tam, gdzie program oczekuje liczby.
- Wpisanie pustej wartości.
- Użycie złego separatora dziesiętnego przy liczbie typu `double`.
- Mylenie `int.Parse()` z `double.Parse()`.
- Oczekiwanie, że `Console.ReadLine()` samodzielnie rozpozna typ liczby.

## Zapamiętaj

- `Console.ReadLine()` zawsze zwraca `string`.
- Tekst `"123"` nie jest tym samym co liczba `123`.
- `int.Parse()` zamienia poprawny tekst liczbowy na `int`.
- `double.Parse()` zamienia poprawny tekst liczbowy na `double`.
- `Convert.ToInt32()` i `Convert.ToDouble()` są alternatywnym sposobem konwersji.
- Jeśli użytkownik wpisze dane w złym formacie, program może zakończyć się błędem.
- `TryParse` pozwala bezpieczniej sprawdzić, czy konwersja się udała, ale dokładniej omówimy to później.
- Przed wykonaniem obliczeń dane tekstowe trzeba przekonwertować na liczby.

## Ćwiczenia

1. Wczytaj wiek użytkownika jako `int` i wypisz go.
2. Wczytaj dwie liczby całkowite i wypisz ich sumę.
3. Wczytaj dwie liczby całkowite i wypisz ich różnicę.
4. Wczytaj długość boku kwadratu i oblicz jego obwód.
5. Wczytaj cenę produktu jako `double` i wypisz ją.
6. Wczytaj dwie liczby typu `double` i wypisz ich średnią.
7. Sprawdź, co się stanie, gdy zamiast liczby wpiszesz tekst.
8. Sprawdź, co wypisze program, gdy połączysz string `"10"` i string `"20"`.
9. Przepisz jeden przykład z `int.Parse()` na `Convert.ToInt32()`.
10. Wskaż, które dane trzeba przekonwertować przed wykonaniem obliczeń.
