# Pierwszy program w C# i Console.WriteLine()

## Cel lekcji

Poznasz pierwszy program konsolowy w C#, klasyczną strukturę programu z metodą `Main()` oraz instrukcję `Console.WriteLine()`.

Po tej lekcji powinieneś umieć:

- rozpoznać miejsce, od którego program zaczyna działanie,
- wypisać prosty tekst w konsoli,
- odróżnić tekst w cudzysłowie od kodu programu,
- dodać prosty komentarz do kodu.

## 1. Czym jest program konsolowy

Program konsolowy to program, który działa w oknie konsoli. Użytkownik widzi tekst, może wpisywać dane z klawiatury, a program może wypisywać wyniki.

Na początku kursu będziemy pisać właśnie takie programy, ponieważ są proste i dobrze pokazują podstawy programowania.

W kolejnych lekcjach nauczysz się pobierać dane, tworzyć zmienne i wykonywać obliczenia. W tej lekcji skupiamy się tylko na pierwszym programie i wypisywaniu tekstu.

## 2. Pierwszy program w C#

W tym kursie jako podstawowy wariant programu stosujemy klasyczną strukturę z metodą `Main()`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Witaj w C#!");
    }
}
```

Po uruchomieniu programu w konsoli pojawi się tekst:

```csharp
Witaj w C#!
```

## 3. Klasyczna struktura programu

Przyjrzyjmy się najważniejszym elementom programu.

```csharp
using System;
```

Ta linia pozwala korzystać z elementów przestrzeni `System`, na przykład z `Console`.

```csharp
class Program
{
}
```

`class Program` to kontener na kod programu. Na tym etapie nie musisz jeszcze znać szczegółów programowania obiektowego. Wystarczy zapamiętać, że klasa pomaga uporządkować kod.

```csharp
static void Main()
{
}
```

`Main()` to miejsce startu programu. Instrukcje zapisane wewnątrz `Main()` wykonują się po uruchomieniu programu.

```csharp
Console.WriteLine("Witaj w C#!");
```

Ta instrukcja wypisuje tekst w konsoli i przechodzi do nowej linii.

## 4. Dlaczego używamy Main()

W tym kursie używamy wersji z `Main()`, ponieważ:

- uczeń widzi strukturę programu,
- łatwo wskazać, gdzie program zaczyna działanie,
- od początku pojawia się pojęcie klasy i metody na poziomie organizacyjnym,
- kod jest czytelny i uporządkowany,
- później łatwiej przejść do metod, klas i większych programów.

Nie omawiamy jeszcze dokładnie klas i metod. Na razie wystarczy wiedzieć, że `Main()` jest punktem startowym programu.

## 5. Skrócony zapis w nowszym C#

W nowszych wersjach C# można napisać najprostszy program krócej:

```csharp
Console.WriteLine("Witaj w C#!");
```

Taki zapis nazywa się często top-level statements. Kompilator tworzy część struktury programu automatycznie.

To wygodne, ale w tym kursie świadomie używamy wersji z `class Program` i `Main()`, ponieważ lepiej pokazuje budowę programu.

## 6. Krótko o namespace

`namespace` to przestrzeń nazw. Pomaga porządkować większe programy, szczególnie gdy projekt ma wiele plików i klas.

Na początku kursu `namespace` nie jest konieczny. Wrócimy do niego przy organizacji większych projektów.

Pełniejszy wariant programu może wyglądać tak:

```csharp
using System;

namespace MojPierwszyProgram
{
    class Program
    {
        static void Main()
        {
            Console.WriteLine("Witaj w C#!");
        }
    }
}
```

Na razie nie używamy tego wariantu jako podstawowego.

## 7. Rola Console.WriteLine()

`Console.WriteLine()` służy do wypisywania informacji w konsoli.

Przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("To jest mój pierwszy program.");
        Console.WriteLine("Uczę się języka C#.");
        Console.WriteLine("Programowanie konsolowe jest dobrym początkiem.");
    }
}
```

Każde `Console.WriteLine()` wypisuje tekst i przechodzi do następnej linii.

## 8. Tekst w cudzysłowie a kod programu

Tekst, który ma zostać wypisany, zapisujemy w cudzysłowie.

```csharp
Console.WriteLine("Cześć!");
```

W tym przykładzie tekstem jest:

```csharp
Cześć!
```

Natomiast `Console.WriteLine`, nawiasy, cudzysłowy i średnik są częścią kodu programu.

Porównaj:

```csharp
Console.WriteLine("C#");
Console.WriteLine("Console.WriteLine");
```

Pierwsza instrukcja wypisze tekst `C#`. Druga instrukcja wypisze tekst `Console.WriteLine`, bo znajduje się on w cudzysłowie.

## 9. Komentarze

Komentarz to tekst w kodzie, który nie jest wykonywany przez program. Służy do krótkiego wyjaśnienia kodu.

Komentarz jednowierszowy zapisujemy po `//`.

```csharp
using System;

class Program
{
    static void Main()
    {
        // Wypisanie powitania w konsoli.
        Console.WriteLine("Dzień dobry!");
    }
}
```

Komentarz wielowierszowy zapisujemy między `/*` i `*/`.

```csharp
using System;

class Program
{
    static void Main()
    {
        /*
         Ten program wypisuje
         trzy linie tekstu.
        */
        Console.WriteLine("Linia 1");
        Console.WriteLine("Linia 2");
        Console.WriteLine("Linia 3");
    }
}
```

Komentarze powinny pomagać w czytaniu kodu. Nie trzeba komentować każdej prostej instrukcji.

## 10. Proste przykłady wypisywania tekstu

Wypisanie jednej linii:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Mam na imię Jan.");
    }
}
```

Wypisanie kilku linii:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Szkoła");
        Console.WriteLine("Klasa");
        Console.WriteLine("Przedmiot: programowanie");
    }
}
```

Wypisanie pustej linii:

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Pierwsza linia");
        Console.WriteLine();
        Console.WriteLine("Trzecia linia");
    }
}
```

## Typowe błędy

- Brak średnika `;` na końcu instrukcji.
- Brak cudzysłowu przy tekście.
- Wpisanie `console` małą literą zamiast `Console`.
- Usunięcie jednej z klamerek `{` albo `}`.
- Umieszczenie instrukcji poza metodą `Main()`.
- Mylenie tekstu w cudzysłowie z kodem programu.

## Zapamiętaj

- Program konsolowy działa w oknie konsoli.
- W tym kursie używamy klasycznej struktury z `class Program` i `Main()`.
- `Main()` to miejsce startu programu.
- Instrukcje wewnątrz `Main()` wykonują się po uruchomieniu programu.
- `Console.WriteLine()` wypisuje tekst i przechodzi do nowej linii.
- Tekst do wypisania zapisujemy w cudzysłowie.
- Komentarze `//` i `/* ... */` nie są wykonywane przez program.
- Skrócony zapis bez `Main()` istnieje, ale w tym kursie używamy wersji klasycznej.

## Ćwiczenia

1. Wypisz swoje imię.
2. Wypisz nazwę szkoły.
3. Wypisz trzy linie tekstu.
4. Dodaj komentarz do programu.
5. Zmień tekst wypisywany przez program.
6. Uruchom program i wskaż, która instrukcja została wykonana jako pierwsza w `Main()`.
7. Porównaj wariant klasyczny z krótkim zapisem i wskaż, którego będziemy używać w kursie.
