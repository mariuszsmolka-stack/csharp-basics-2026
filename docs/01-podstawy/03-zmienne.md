# Zmienne i podstawowe typy danych w C#

## Cel lekcji

Nauczysz się tworzyć zmienne, przypisywać im wartości, zmieniać te wartości oraz używać podstawowych typów danych w C#.

Po tej lekcji powinieneś umieć:

- wyjaśnić, czym jest zmienna,
- zadeklarować zmienną,
- przypisać wartość do zmiennej,
- wypisać wartość zmiennej w konsoli,
- rozpoznać podstawowe typy danych: `int`, `double`, `char`, `string`, `bool`.

## 1. Czym jest zmienna

Zmienna to nazwane miejsce w pamięci programu. Można zapisać w niej wartość, a potem używać tej wartości w kolejnych instrukcjach.

Przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 16;

        Console.WriteLine(wiek);
    }
}
```

W tym programie zmienna `wiek` przechowuje wartość `16`.

## 2. Deklaracja zmiennej

Deklaracja zmiennej oznacza utworzenie zmiennej i podanie jej typu oraz nazwy.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek;
    }
}
```

W tej instrukcji:

- `int` oznacza typ zmiennej,
- `wiek` oznacza nazwę zmiennej,
- średnik `;` kończy instrukcję.

## 3. Przypisanie wartości

Przypisanie wartości oznacza zapisanie konkretnej wartości w zmiennej.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek;
        wiek = 16;

        Console.WriteLine(wiek);
    }
}
```

Można też połączyć deklarację i przypisanie w jednej instrukcji.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 16;

        Console.WriteLine(wiek);
    }
}
```

Operator `=` oznacza przypisanie wartości. Czytamy to jako: do zmiennej `wiek` wpisz wartość `16`.

## 4. Zmiana wartości zmiennej

Wartość zmiennej można zmienić w dalszej części programu.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 16;
        Console.WriteLine(wiek);

        wiek = 17;
        Console.WriteLine(wiek);
    }
}
```

Program najpierw wypisze `16`, a potem `17`.

Nie podajemy drugi raz typu `int`, gdy zmienna już istnieje. Typ podajemy przy deklaracji.

## 5. Podstawowe typy danych

W C# każda zmienna ma określony typ. Typ mówi, jakiego rodzaju wartość można przechowywać w zmiennej.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 16;
        double wzrost = 1.75;
        char ocena = 'A';
        string imie = "Anna";
        bool czyAktywny = true;

        Console.WriteLine(wiek);
        Console.WriteLine(wzrost);
        Console.WriteLine(ocena);
        Console.WriteLine(imie);
        Console.WriteLine(czyAktywny);
    }
}
```

Najważniejsze typy na początku kursu:

- `int` przechowuje liczby całkowite, na przykład `16`, `0`, `-5`.
- `double` przechowuje liczby rzeczywiste, na przykład `1.75`, `3.14`, `-2.5`.
- `char` przechowuje jeden znak zapisany w apostrofach, na przykład `'A'`.
- `string` przechowuje tekst zapisany w cudzysłowie, na przykład `"Anna"`.
- `bool` przechowuje wartość logiczną `true` albo `false`.

## 6. Różnica między tekstem a liczbą

Liczba i tekst to nie to samo.

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba = 16;
        string tekst = "16";

        Console.WriteLine(liczba);
        Console.WriteLine(tekst);
    }
}
```

W konsoli oba wyniki wyglądają podobnie, ale dla programu są to różne wartości:

- `16` bez cudzysłowu jest liczbą,
- `"16"` w cudzysłowie jest tekstem.

Dlatego tekst zapisujemy w cudzysłowie, a liczby zapisujemy bez cudzysłowu.

## 7. Wypisywanie wartości zmiennych

Wartość zmiennej można wypisać za pomocą `Console.WriteLine()`.

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int wiek = 16;

        Console.WriteLine(imie);
        Console.WriteLine(wiek);
    }
}
```

Jeżeli nazwa zmiennej nie jest w cudzysłowie, program wypisze jej wartość.

## 8. Łączenie tekstu z wartością zmiennej

Można połączyć tekst z wartością zmiennej za pomocą operatora `+`.

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int wiek = 16;

        Console.WriteLine("Imię: " + imie);
        Console.WriteLine("Wiek: " + wiek);
    }
}
```

Wynik w konsoli:

```csharp
Imię: Anna
Wiek: 16
```

Na tym etapie wystarczy znać proste łączenie tekstu za pomocą `+`. Bardziej wygodne sposoby formatowania wyników pojawią się w kolejnych lekcjach.

## 9. Nazwy zmiennych

Nazwy zmiennych powinny być krótkie, czytelne i związane z przechowywaną wartością.

Dobre nazwy:

- `imie`,
- `wiek`,
- `wzrost`,
- `czyAktywny`,
- `ocena`.

Słabsze nazwy:

- `x`,
- `a1`,
- `cos`,
- `dane`.

W C# często stosuje się zapis, w którym pierwsze słowo zaczyna się małą literą, a kolejne słowa wielką literą, na przykład `czyAktywny`.

## 10. C# jest językiem statycznie typowanym

C# jest językiem statycznie typowanym. Oznacza to, że typ zmiennej jest znany już podczas pisania i kompilowania programu.

Jeżeli utworzysz zmienną typu `int`, to nie możesz później wpisać do niej tekstu.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 16;

        Console.WriteLine(wiek);
    }
}
```

Taki zapis jest poprawny. Natomiast próba wpisania tekstu do zmiennej typu `int` byłaby błędem.

## Typowe błędy

- Brak średnika `;` na końcu instrukcji.
- Zapisanie tekstu bez cudzysłowu.
- Zapisanie wartości typu `char` w cudzysłowie zamiast w apostrofach.
- Próba przypisania tekstu do zmiennej typu `int`.
- Ponowne podawanie typu przy zmianie wartości istniejącej zmiennej.
- Literówka w nazwie zmiennej.
- Mylenie wartości `true` i `false` z tekstem `"true"` i `"false"`.

## Zapamiętaj

- Zmienna to nazwane miejsce na wartość.
- Deklaracja zmiennej podaje jej typ i nazwę.
- Operator `=` przypisuje wartość do zmiennej.
- Wartość zmiennej można zmienić.
- `int` służy do liczb całkowitych.
- `double` służy do liczb rzeczywistych.
- `char` służy do pojedynczego znaku w apostrofach.
- `string` służy do tekstu w cudzysłowie.
- `bool` przechowuje `true` albo `false`.
- C# jest językiem statycznie typowanym.

## Ćwiczenia

1. Utwórz zmienną `imie` i wypisz jej wartość.
2. Utwórz zmienną `wiek` typu `int` i wypisz jej wartość.
3. Utwórz zmienną `srednia` typu `double` i wypisz jej wartość.
4. Utwórz zmienną `czyUczen` typu `bool`.
5. Wypisz zdanie złożone z tekstu i wartości zmiennej.
6. Zmień wartość jednej zmiennej i wypisz ją ponownie.
7. Sprawdź, co się stanie, gdy tekst zapiszesz bez cudzysłowu.
