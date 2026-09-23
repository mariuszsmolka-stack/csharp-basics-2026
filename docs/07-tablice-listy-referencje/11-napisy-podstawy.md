# Napisy - podstawy

## Cel lekcji

Nauczysz się tworzyć i wczytywać napisy, sprawdzać ich długość, odczytywać pojedyncze znaki oraz przechodzić po napisie za pomocą pętli. Poznasz także podstawowe sposoby łączenia i porównywania napisów.

Po tej lekcji powinieneś umieć:

- utworzyć zmienną typu `string`,
- rozpoznać pusty napis,
- wczytać napis za pomocą `Console.ReadLine()`,
- połączyć napisy operatorem `+`,
- zastosować interpolację napisów,
- użyć podstawowych sekwencji specjalnych,
- odczytać długość napisu,
- odczytać znak o podanym indeksie,
- odróżnić typ `string` od typu `char`,
- przejść po znakach napisu za pomocą `for` i `foreach`,
- porównać dwa napisy,
- wyjaśnić, na czym polega niezmienność napisów.

## 1. Czym jest napis

Napis jest ciągiem znaków przechowywanym w zmiennej typu `string`. Napisem może być imię, zdanie, adres albo dowolny inny tekst.

```csharp
using System;

class Program
{
    static void Main()
    {
        string miasto;
        miasto = "Wałbrzych";

        string przedmiot = "Informatyka";

        Console.WriteLine(miasto);
        Console.WriteLine(przedmiot);
    }
}
```

Zmienna `miasto` została najpierw zadeklarowana, a później otrzymała wartość. W przypadku zmiennej `przedmiot` deklaracja i inicjalizacja zostały wykonane w jednej instrukcji.

## 2. Pusty napis

Pusty napis nie zawiera żadnego znaku. Można go utworzyć na dwa sposoby.

```csharp
using System;

class Program
{
    static void Main()
    {
        string pierwszyTekst = "";
        string drugiTekst = string.Empty;

        Console.WriteLine($"Długość pierwszego napisu: {pierwszyTekst.Length}");
        Console.WriteLine($"Długość drugiego napisu: {drugiTekst.Length}");
    }
}
```

Oba napisy mają długość `0`. Zapisy `""` i `string.Empty` oznaczają pusty napis.

Pusty napis jest istniejącym napisem, który nie zawiera znaków. Nie jest tym samym co brak przypisanej wartości.

## 3. Wczytywanie napisu

`Console.ReadLine()` wczytuje tekst wpisany przez użytkownika i zwraca wartość typu `string`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj swoje imię:");
        string imie = Console.ReadLine();

        Console.WriteLine($"Witaj, {imie}!");
    }
}
```

Program czeka na wpisanie tekstu i naciśnięcie klawisza Enter. Wczytany napis zostaje zapisany w zmiennej `imie`.

## 4. Łączenie napisów za pomocą operatora +

Operator `+` pozwala połączyć kilka napisów w jeden nowy napis.

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        string nazwisko = "Nowak";

        string pelneDane = imie + " " + nazwisko;

        Console.WriteLine(pelneDane);
    }
}
```

Między imieniem i nazwiskiem dodano napis zawierający jedną spację.

## 5. Interpolacja napisów

Interpolacja pozwala umieszczać wartości zmiennych wewnątrz napisu. Przed otwierającym cudzysłowem zapisujemy znak `$`, a nazwy zmiennych umieszczamy w nawiasach klamrowych.

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int wiek = 17;

        string opis = $"Uczeń ma na imię {imie} i ma {wiek} lat.";

        Console.WriteLine(opis);
    }
}
```

Zapis `{imie}` zostaje zastąpiony wartością zmiennej `imie`, a zapis `{wiek}` wartością zmiennej `wiek`.

## 6. Sekwencje specjalne

Niektóre znaki zapisujemy wewnątrz napisu za pomocą sekwencji rozpoczynających się od ukośnika odwrotnego `\`.

- `\n` powoduje przejście do nowego wiersza.
- `\t` wstawia tabulator.
- `\"` pozwala umieścić cudzysłów wewnątrz napisu.
- `\\` pozwala umieścić ukośnik odwrotny w napisie.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Pierwszy wiersz\nDrugi wiersz");
        Console.WriteLine("Nazwa:\tKlawiatura");
        Console.WriteLine("Powiedział: \"Dzień dobry\"");
        Console.WriteLine("C:\\Dane\\plik.txt");
    }
}
```

Sekwencja specjalna jest zapisana za pomocą kilku znaków w kodzie, ale reprezentuje określony znak lub sposób formatowania wyniku.

## 7. Długość napisu - Length

Właściwość `Length` podaje liczbę znaków znajdujących się w napisie.

```csharp
using System;

class Program
{
    static void Main()
    {
        string napis = "Ala ma kota";
        string pustyNapis = string.Empty;

        Console.WriteLine($"Napis: {napis}");
        Console.WriteLine($"Liczba znaków: {napis.Length}");
        Console.WriteLine($"Długość pustego napisu: {pustyNapis.Length}");
    }
}
```

Napis `Ala ma kota` ma `11` znaków. Spacje również są znakami i są uwzględniane przez `Length`.

Pusty napis ma długość `0`.

## 8. Indeksowanie napisu

Każdy znak napisu ma własny indeks. Indeksy zaczynają się od `0`.

```text
indeks pierwszego znaku => 0
indeks ostatniego znaku => napis.Length - 1
```

Wynik odczytania pojedynczego elementu napisu ma typ `char`.

```csharp
using System;

class Program
{
    static void Main()
    {
        string napis = "Program";

        char pierwszyZnak = napis[0];
        char drugiZnak = napis[1];
        char ostatniZnak = napis[napis.Length - 1];

        Console.WriteLine($"Pierwszy znak: {pierwszyZnak}");
        Console.WriteLine($"Drugi znak: {drugiZnak}");
        Console.WriteLine($"Ostatni znak: {ostatniZnak}");
    }
}
```

Dla napisu o długości `7` poprawne indeksy to wartości od `0` do `6`. Indeks `7` jest już poza napisem.

## 9. Bezpieczny odczyt pierwszego i ostatniego znaku

Przed odczytaniem znaku trzeba upewnić się, że napis nie jest pusty.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj napis:");
        string napis = Console.ReadLine();

        if (napis.Length > 0)
        {
            char pierwszyZnak = napis[0];
            char ostatniZnak = napis[napis.Length - 1];

            Console.WriteLine($"Pierwszy znak: {pierwszyZnak}");
            Console.WriteLine($"Ostatni znak: {ostatniZnak}");
        }
        else
        {
            Console.WriteLine("Podano pusty napis.");
        }
    }
}
```

Warunek `napis.Length > 0` sprawdza, czy napis zawiera co najmniej jeden znak.

## 10. Typ string a typ char

Typ `string` przechowuje cały napis. Typ `char` przechowuje pojedynczy element napisu.

- Literał typu `string` zapisujemy w cudzysłowie podwójnym, na przykład `"Kot"`.
- Literał typu `char` zapisujemy w apostrofach, na przykład `'K'`.

```csharp
using System;

class Program
{
    static void Main()
    {
        string slowo = "Kot";
        char znak = 'K';
        char pierwszyZnak = slowo[0];

        Console.WriteLine(slowo);
        Console.WriteLine(znak);
        Console.WriteLine(pierwszyZnak);
    }
}
```

Zmienna `slowo` przechowuje napis, a zmienne `znak` i `pierwszyZnak` przechowują pojedyncze wartości typu `char`.

## 11. Przechodzenie po napisie za pomocą for

Pętla `for` pozwala wykorzystać kolejne indeksy napisu.

```csharp
using System;

class Program
{
    static void Main()
    {
        string napis = "Kot";

        for (int indeks = 0; indeks < napis.Length; indeks++)
        {
            Console.WriteLine($"Indeks {indeks}: {napis[indeks]}");
        }
    }
}
```

Zmienna `indeks` zaczyna od `0` i przyjmuje kolejne poprawne indeksy. Warunek `indeks < napis.Length` zatrzymuje pętlę przed wyjściem poza napis.

## 12. Przechodzenie po napisie za pomocą foreach

Pętla `foreach` pozwala pobierać kolejne znaki bez samodzielnego używania indeksów.

```csharp
using System;

class Program
{
    static void Main()
    {
        string napis = "Kot";

        foreach (char znak in napis)
        {
            Console.WriteLine(znak);
        }
    }
}
```

`foreach` jest wygodny, gdy potrzebujemy kolejnych znaków, ale nie potrzebujemy ich indeksów.

| Cecha | `for` | `foreach` |
|---|---|---|
| Dostęp do indeksu | Tak | Nie bez dodatkowej zmiennej |
| Dostęp do znaku | Przez `napis[indeks]` | Bezpośrednio przez zmienną `znak` |
| Typowe zastosowanie | Potrzebny indeks znaku | Potrzebne tylko kolejne znaki |
| Zapis dla początkującego | Wymaga licznika i warunku | Krótszy i prostszy |

## 13. Porównywanie napisów

Operator `==` sprawdza, czy napisy są równe. Operator `!=` sprawdza, czy napisy są różne.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj pierwszy napis:");
        string pierwszyNapis = Console.ReadLine();

        Console.WriteLine("Podaj drugi napis:");
        string drugiNapis = Console.ReadLine();

        if (pierwszyNapis == drugiNapis)
        {
            Console.WriteLine("Napisy są równe.");
        }
        else
        {
            Console.WriteLine("Napisy są różne.");
        }

        if (pierwszyNapis != drugiNapis)
        {
            Console.WriteLine("Operator != potwierdza, że napisy są różne.");
        }
    }
}
```

Podstawowe porównanie napisów rozróżnia wielkie i małe litery.

```text
"Ala" == "ala" => false
```

## 14. Niezmienność napisów

Napis jest niezmienny. Oznacza to, że nie można zastąpić pojedynczego znaku wewnątrz istniejącej wartości typu `string`.

Zapis `tekst[0] = 'A';` jest niedozwolony.

Operacja na napisie może utworzyć nowy napis. Początkowa wartość pozostaje bez zmian.

```csharp
using System;

class Program
{
    static void Main()
    {
        string tekstPoczatkowy = "Ala";
        string nowyTekst = tekstPoczatkowy + " ma kota";

        Console.WriteLine($"Początkowy napis: {tekstPoczatkowy}");
        Console.WriteLine($"Nowy napis: {nowyTekst}");
    }
}
```

Po utworzeniu zmiennej `nowyTekst` zmienna `tekstPoczatkowy` nadal zawiera napis `Ala`.

## Podstawowe elementy pracy z napisami

| Zapis | Znaczenie | Przykład |
|---|---|---|
| `string` | Typ przechowujący napis | `string imie = "Anna";` |
| `char` | Typ przechowujący pojedynczy znak | `char litera = 'A';` |
| `""` | Pusty napis | `string tekst = "";` |
| `string.Empty` | Pusty napis | `string tekst = string.Empty;` |
| `Length` | Liczba znaków napisu | `napis.Length` |
| `napis[indeks]` | Znak o podanym indeksie | `napis[0]` |
| `+` | Łączenie napisów | `imie + " " + nazwisko` |
| `$` | Interpolacja napisu | `$"Witaj, {imie}!"` |
| `==` | Sprawdzenie równości napisów | `pierwszy == drugi` |
| `!=` | Sprawdzenie różności napisów | `pierwszy != drugi` |

## Typowe błędy

- Użycie apostrofów dla całego napisu.
- Użycie cudzysłowu podwójnego dla wartości typu `char`.
- Odwołanie do indeksu równego `napis.Length`.
- Próba odczytania ostatniego znaku pustego napisu.
- Założenie, że indeksowanie zaczyna się od `1`.
- Pominięcie spacji podczas określania długości napisu.
- Próba zmiany pojedynczego znaku za pomocą indeksu.
- Pomylenie operatora przypisania `=` z operatorem porównania `==`.
- Oczekiwanie, że napisy `"Ala"` i `"ala"` są równe.
- Użycie w pętli warunku `indeks <= napis.Length` zamiast `indeks < napis.Length`.
- Pomylenie indeksu znaku z samym znakiem.

## Zapamiętaj

- `string` przechowuje napis.
- `char` przechowuje pojedynczy znak.
- Pusty napis można zapisać jako `""` albo `string.Empty`.
- Indeksy zaczynają się od `0`.
- `Length` podaje liczbę znaków napisu.
- Ostatni poprawny indeks to `napis.Length - 1`.
- `for` pozwala korzystać z indeksów.
- `foreach` pozwala wygodnie odczytywać kolejne znaki.
- Operatory `==` i `!=` porównują napisy.
- Podstawowe porównanie rozróżnia wielkie i małe litery.
- Napis jest niezmienny.
- Przed odczytem znaku warto sprawdzić, czy napis nie jest pusty.

## Ćwiczenia

1. Utwórz zmienną typu `string`, przypisz do niej swoje imię i wypisz jej wartość.
2. Utwórz pusty napis za pomocą `""` oraz `string.Empty`. Wypisz długość obu napisów.
3. Wczytaj imię użytkownika i wyświetl powitanie.
4. Połącz imię i nazwisko za pomocą operatora `+`.
5. Utwórz zmienne `imie` i `wiek`, a następnie zastosuj interpolację do zbudowania jednego zdania.
6. Za pomocą sekwencji specjalnych wypisz tekst w dwóch wierszach, użyj tabulatora, cudzysłowu oraz ukośnika odwrotnego.
7. Wczytaj napis i wypisz jego długość.
8. Dla niepustego napisu wypisz pierwszy i ostatni znak.
9. Napisz program, który przed odczytaniem znaków sprawdza, czy użytkownik nie podał pustego napisu.
10. Przejdź po napisie za pomocą pętli `for` i wypisz każdy znak wraz z jego indeksem.
11. Przejdź po napisie za pomocą `foreach` i wypisz każdy znak w osobnym wierszu.
12. Wczytaj dwa napisy i sprawdź za pomocą `==`, czy są równe.
13. Sprawdź, czy dwa napisy różnią się tylko wielkością liter. Wskazówka: odpowiednie metody zostaną omówione w następnej lekcji.
14. Wczytaj napis oraz jeden znak. Policz, ile razy wskazany znak występuje w napisie.
15. Napisz program, który wypisuje znaki napisu w odwrotnej kolejności. Użyj pętli `for`.
16. Wyjaśnij własnymi słowami, co oznacza, że napis jest niezmienny.

## Podsumowanie

Typ `string` służy do przechowywania napisów, a typ `char` do przechowywania pojedynczych znaków. Właściwość `Length` podaje liczbę znaków, a indeks pozwala odczytać wybrany znak.

Pętla `for` jest wygodna, gdy potrzebujemy indeksów. Pętla `foreach` pozwala prosto odczytywać kolejne znaki.

Napisy można łączyć, interpolować i porównywać. Napis jest niezmienny, dlatego operacje prowadzące do powstania zmienionej treści tworzą nową wartość.
