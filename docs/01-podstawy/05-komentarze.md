# Komentarze, czytelność kodu i konwencje nazewnictwa

## Cel lekcji

Nauczysz się stosować komentarze, pisać czytelniejszy kod i nazywać zmienne w sposób zrozumiały dla człowieka.

Po tej lekcji powinieneś umieć:

- dodać komentarz jednoliniowy,
- dodać komentarz wieloliniowy,
- rozpoznać komentarz pomocny i zbędny,
- dobrać czytelną nazwę zmiennej,
- stosować podstawową konwencję `camelCase` dla zmiennych lokalnych.

## 1. Po co stosuje się komentarze

Komentarz to tekst w kodzie, który nie jest wykonywany przez program. Komentarz jest przeznaczony dla człowieka, który czyta kod.

Komentarze pomagają wyjaśnić sens fragmentu programu. Nie powinny jednak przepisywać oczywistych instrukcji.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 16; // wiek ucznia

        Console.WriteLine(wiek);
    }
}
```

## 2. Komentarz jednoliniowy

Komentarz jednoliniowy zaczyna się od `//`. Wszystko po `//` do końca linii jest komentarzem.

```csharp
using System;

class Program
{
    static void Main()
    {
        // Wypisanie imienia ucznia.
        string imie = "Anna";

        Console.WriteLine(imie);
    }
}
```

Komentarz jednoliniowy jest dobry do krótkich wyjaśnień.

## 3. Komentarz wieloliniowy

Komentarz wieloliniowy zaczyna się od `/*` i kończy na `*/`.

```csharp
using System;

class Program
{
    static void Main()
    {
        /*
         Ten program wypisuje
         podstawowe informacje
         o uczniu.
        */

        string imie = "Anna";
        int liczbaPunktow = 25;

        Console.WriteLine(imie);
        Console.WriteLine(liczbaPunktow);
    }
}
```

Komentarz wieloliniowy przydaje się, gdy trzeba krótko opisać większy fragment kodu.

## 4. Kiedy komentarz pomaga

Komentarz pomaga, gdy wyjaśnia sens kodu.

Dobry komentarz:

```csharp
using System;

class Program
{
    static void Main()
    {
        // Liczba punktów zdobytych przez ucznia w krótkim ćwiczeniu.
        int liczbaPunktow = 25;

        Console.WriteLine(liczbaPunktow);
    }
}
```

Taki komentarz dopowiada, co oznacza wartość w programie.

## 5. Kiedy komentarz jest zbędny

Komentarz jest zbędny, gdy opisuje coś oczywistego.

```csharp
using System;

class Program
{
    static void Main()
    {
        // Utworzenie zmiennej liczbaPunktow i przypisanie wartości 25.
        int liczbaPunktow = 25;

        // Wypisanie zmiennej liczbaPunktow.
        Console.WriteLine(liczbaPunktow);
    }
}
```

Ten komentarz głównie powtarza kod. Lepiej użyć czytelnej nazwy zmiennej i dodać komentarz tylko wtedy, gdy naprawdę pomaga.

## 6. Czytelne nazwy zmiennych

Nazwy zmiennych powinny mówić, co przechowują.

Gorszy przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        int x = 25;
        int y = 5;

        Console.WriteLine(x);
        Console.WriteLine(y);
    }
}
```

Lepszy przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczbaPunktow = 25;
        int liczbaZadan = 5;

        Console.WriteLine(liczbaPunktow);
        Console.WriteLine(liczbaZadan);
    }
}
```

W kursie preferujemy czytelne nazwy, nawet jeśli są trochę dłuższe.

## 7. Konwencje nazewnictwa

Konwencja nazewnictwa to umówiony sposób nazywania elementów programu. Dzięki niej kod jest bardziej spójny i czytelny.

Dla zmiennych lokalnych w C# zwykle stosujemy `camelCase`.

`camelCase` oznacza, że:

- pierwsze słowo zaczynamy małą literą,
- kolejne słowa zaczynamy wielką literą,
- nie używamy podkreślników między słowami.

Przykłady nazw w `camelCase`:

- `liczbaPunktow`,
- `imieUcznia`,
- `sredniaOcen`,
- `czyAktywny`.

Poprawny przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczbaPunktow = 25;
        string imieUcznia = "Anna";
        double sredniaOcen = 4.75;
        bool czyZaliczyl = true;

        Console.WriteLine(liczbaPunktow);
        Console.WriteLine(imieUcznia);
        Console.WriteLine(sredniaOcen);
        Console.WriteLine(czyZaliczyl);
    }
}
```

Wariant angielski jako informacja porządkowa:

```csharp
using System;

class Program
{
    static void Main()
    {
        int pointsCount = 25;
        string studentName = "Anna";
        double averageGrade = 4.75;
        bool hasPassed = true;

        Console.WriteLine(pointsCount);
        Console.WriteLine(studentName);
        Console.WriteLine(averageGrade);
        Console.WriteLine(hasPassed);
    }
}
```

W profesjonalnym kodzie często stosuje się nazwy angielskie. W kursie szkolnym można stosować nazwy polskie, jeśli pomagają uczniowi zrozumieć program.

Najważniejsza jest konsekwencja. Nie należy bez potrzeby mieszać polskiego i angielskiego w jednej nazwie.

## 8. Przykłady gorszych nazw

```csharp
using System;

class Program
{
    static void Main()
    {
        int LiczbaPunktow = 25;
        int liczba_punktow = 25;
        int lp = 25;
        string imieucznia = "Anna";
        int liczbaPoints = 25;

        Console.WriteLine(LiczbaPunktow);
        Console.WriteLine(liczba_punktow);
        Console.WriteLine(lp);
        Console.WriteLine(imieucznia);
        Console.WriteLine(liczbaPoints);
    }
}
```

Te nazwy są gorsze, ponieważ:

- `LiczbaPunktow` nie jest zgodne z `camelCase` dla zmiennych lokalnych,
- `liczba_punktow` używa podkreślnika zamiast `camelCase`,
- `lp` jest zbyt krótkim i nieczytelnym skrótem,
- `imieucznia` nie rozdziela słów,
- `liczbaPoints` miesza język polski i angielski.

## 9. Podstawowe zasady formatowania kodu

Kod powinien być czytelny nie tylko dla komputera, ale też dla człowieka.

Podstawowe zasady:

- stosuj wcięcia wewnątrz klamerek,
- używaj pustych linii do oddzielania fragmentów kodu,
- zapisuj nawiasy klamrowe w sposób spójny,
- zapisuj jedną instrukcję w jednej linii.

Mniej czytelny zapis:

```csharp
using System;
class Program
{
static void Main()
{
string imie="Anna";int liczbaPunktow=25;Console.WriteLine(imie);Console.WriteLine(liczbaPunktow);
}
}
```

Bardziej czytelny zapis:

```csharp
using System;

class Program
{
    static void Main()
    {
        string imie = "Anna";
        int liczbaPunktow = 25;

        Console.WriteLine(imie);
        Console.WriteLine(liczbaPunktow);
    }
}
```

Oba przykłady mogą oznaczać podobne instrukcje, ale drugi jest znacznie łatwiejszy do czytania.

## Typowe błędy

- Komentowanie każdej oczywistej instrukcji.
- Brak zakończenia komentarza wieloliniowego.
- Używanie nazw zmiennych, które nic nie mówią.
- Mieszanie różnych stylów nazewnictwa.
- Mieszanie polskiego i angielskiego w jednej nazwie bez potrzeby.
- Zapisywanie wielu instrukcji w jednej linii.
- Brak wcięć wewnątrz klamerek.

## Zapamiętaj

- Komentarz nie jest wykonywany przez program.
- `//` oznacza komentarz jednoliniowy.
- `/* ... */` oznacza komentarz wieloliniowy.
- Dobry komentarz wyjaśnia sens kodu.
- Zbędny komentarz tylko powtarza oczywistą instrukcję.
- Nazwa zmiennej powinna mówić, co zmienna przechowuje.
- Dla zmiennych lokalnych w C# zwykle stosujemy `camelCase`.
- W kursie można używać polskich nazw, ale trzeba robić to konsekwentnie.
- Czytelny kod jest ważny, bo kod czyta człowiek, nie tylko komputer.

## Ćwiczenia

1. Dodaj komentarz jednoliniowy do programu.
2. Dodaj komentarz wieloliniowy przed fragmentem kodu.
3. Zmień nazwę zmiennej `x` na bardziej czytelną.
4. Popraw formatowanie przykładowego kodu.
5. Wskaż, który komentarz jest zbędny.
6. Napisz program z trzema zmiennymi o czytelnych nazwach.
7. Zmień nazwę zmiennej `liczba_punktow` na zgodną z `camelCase`.
8. Wskaż, która nazwa jest lepsza: `lp` czy `liczbaPunktow`.
9. Napisz trzy przykłady nazw zmiennych w `camelCase`.
10. Sprawdź, czy w jednym przykładzie nie mieszasz bez potrzeby nazw polskich i angielskich.
