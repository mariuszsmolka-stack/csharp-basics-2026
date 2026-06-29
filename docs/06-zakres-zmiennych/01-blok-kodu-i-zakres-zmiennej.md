# Blok kodu i zakres zmiennej

## Co to jest blok kodu

Blok kodu to fragment programu ograniczony klamrami `{ }`.

```csharp
{
    // instrukcje
}
```

Blokami kodu są między innymi:

* ciało metody `Main`,
* ciało instrukcji `if`,
* ciało pętli `for`,
* ciało pętli `while`.

Blok kodu porządkuje instrukcje i wyznacza miejsce, w którym istnieją niektóre zmienne.

## Zmienna lokalna

Zmienna lokalna to zmienna zadeklarowana wewnątrz metody albo bloku kodu.

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczba = 10;

        Console.WriteLine(liczba);
    }
}
```

Zmienna `liczba` istnieje wewnątrz metody `Main`. Można jej używać w tym bloku od miejsca deklaracji.

## Zakres zmiennej

Zakres zmiennej to fragment programu, w którym można używać danej zmiennej.

Najważniejsza zasada:

* zmienna jest dostępna od miejsca deklaracji do końca bloku, w którym została zadeklarowana,
* po wyjściu z bloku zmienna przestaje być dostępna.

Jeżeli zmienna została zadeklarowana wewnątrz klamerek, to zwykle nie można jej użyć poza tymi klamrami.

## Diagram: gdzie istnieje zmienna

```mermaid
---
config:
  flowchart:
    curve: linear
---
flowchart LR
    A([Start])
    B["Wejście do bloku"]
    C["Deklaracja zmiennej"]
    D["Użycie zmiennej"]
    E["Wyjście z bloku"]
    F["Zmienna niedostępna"]
    G([Koniec])

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
```

Diagram pokazuje, że zmienna istnieje tylko w określonym fragmencie programu. Po zakończeniu bloku nie można już jej używać.

## Zmienna w instrukcji if

Przykład poprawny:

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 18;

        if (wiek >= 18)
        {
            string komunikat = "Osoba pełnoletnia";
            Console.WriteLine(komunikat);
        }
    }
}
```

Zmienna `komunikat` istnieje tylko wewnątrz bloku `if`. Dlatego w tym przykładzie jest wypisywana od razu w tym samym bloku.

Przykład błędny:

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 18;

        if (wiek >= 18)
        {
            string komunikat = "Osoba pełnoletnia";
        }

        Console.WriteLine(komunikat);
    }
}
```

Ten program zawiera błąd. Zmienna `komunikat` została zadeklarowana wewnątrz `if`, więc nie istnieje poza tym blokiem.

## Zmienna zadeklarowana przed blokiem

Jeżeli zmienna ma być użyta po zakończeniu `if`, można zadeklarować ją wcześniej.

```csharp
using System;

class Program
{
    static void Main()
    {
        int wiek = 18;
        string komunikat = "";

        if (wiek >= 18)
        {
            komunikat = "Osoba pełnoletnia";
        }

        Console.WriteLine(komunikat);
    }
}
```

Zmienna `komunikat` została zadeklarowana przed instrukcją `if`, więc można jej użyć także po zakończeniu bloku `if`.

## Zmienna w pętli for

W pętli `for` często deklarujemy zmienną licznika.

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 0; i < 5; i++)
        {
            Console.WriteLine(i);
        }
    }
}
```

Zmienna `i` istnieje w pętli `for` i jest używana jako licznik.

Przykład błędny:

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 0; i < 5; i++)
        {
            Console.WriteLine(i);
        }

        Console.WriteLine(i);
    }
}
```

Po zakończeniu pętli zmienna `i` nie jest dostępna. Dlatego ostatnia instrukcja powoduje błąd.

## Dlaczego to jest ważne

Zakres zmiennych jest ważny, ponieważ:

* program jest czytelniejszy,
* zmienne nie zaśmiecają całej metody,
* łatwiej unikać przypadkowego użycia niewłaściwej zmiennej,
* kompilator pomaga wykrywać błędy.

Dzięki zakresom zmiennych program ma lepszy porządek.

## Najczęstsze błędy

* Użycie zmiennej poza blokiem, w którym została zadeklarowana.
* Deklarowanie zmiennej zbyt głęboko.
* Oczekiwanie, że zmienna z `if` będzie dostępna po `if`.
* Oczekiwanie, że licznik pętli `for` będzie dostępny po pętli.
* Mylenie bloku kodu z wcięciami.

W C# o bloku decydują klamry `{ }`, a nie samo wcięcie. Wcięcia pomagają czytać kod, ale nie wyznaczają zakresu zmiennej.

## Ćwiczenia

1. Wskaż, w którym bloku zadeklarowana jest zmienna `liczba`.
2. Napisz program, w którym zmienna `tekst` jest zadeklarowana w `Main` i wypisana na ekranie.
3. Napisz program z `if`, w którym zmienna `komunikat` jest zadeklarowana wewnątrz `if` i wypisana wewnątrz `if`.
4. Popraw program, w którym zmienna zadeklarowana w `if` jest używana poza `if`.
5. Napisz pętlę `for` z licznikiem `i` i wyjaśnij, gdzie dostępna jest zmienna `i`.
6. Sprawdź, co się stanie, gdy spróbujesz użyć zmiennej `i` po zakończeniu pętli `for`.
7. Napisz program, w którym zmienna `wynik` jest zadeklarowana przed `if`, a jej wartość jest ustawiana wewnątrz `if`.

## Podsumowanie

Blok kodu w C# wyznaczają klamry `{ }`.

Zmienna lokalna istnieje tylko w określonym zakresie. Jest dostępna od miejsca deklaracji do końca bloku, w którym została zadeklarowana.

Zmienna zadeklarowana w `if` nie jest dostępna poza `if`. Zmienna licznika `for` zwykle nie jest dostępna po zakończeniu pętli.

Dobre rozumienie zakresu zmiennych pomaga pisać poprawne i czytelne programy.
