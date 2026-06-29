# ref i out

## Przypomnienie: zwykłe przekazywanie przez wartość

Zwykły parametr typu `int` dostaje kopię wartości.

```csharp
using System;

class Program
{
    static void ZmienLiczbe(int liczba)
    {
        liczba = 99;
    }

    static void Main()
    {
        int x = 10;

        ZmienLiczbe(x);

        Console.WriteLine(x);
    }
}
```

Program wypisze `10`, bo zmiana parametru `liczba` nie zmienia zmiennej `x` w `Main`.

## Po co jest ref

`ref` pozwala przekazać zmienną tak, aby metoda mogła zmienić jej wartość w miejscu wywołania.

Ważne zasady:

- `ref` zapisujemy w definicji metody,
- `ref` zapisujemy także przy wywołaniu metody,
- zmienna przekazana przez `ref` musi być wcześniej zainicjalizowana.

## Przykład ref

```csharp
using System;

class Program
{
    static void ZmienLiczbe(ref int liczba)
    {
        liczba = 99;
    }

    static void Main()
    {
        int x = 10;

        ZmienLiczbe(ref x);

        Console.WriteLine(x);
    }
}
```

Wyjaśnienie:

- metoda `ZmienLiczbe` otrzymuje dostęp do zmiennej `x`,
- przypisanie `liczba = 99` zmienia `x`,
- program wypisze `99`.

## Diagram: ref zmienia zmienną z Main

```mermaid
---
config:
  flowchart:
    curve: linear
---
flowchart LR
    A([Start])
    B["Main: x = 10"]
    C["ZmienLiczbe(ref x)"]
    D["Metoda ustawia 99"]
    E["x w Main ma 99"]
    F([Koniec])

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
```

Diagram pokazuje, że `ref` pozwala metodzie zmienić zmienną z miejsca wywołania.

## Zamiana wartości dwóch zmiennych

```csharp
using System;

class Program
{
    static void Zamien(ref int a, ref int b)
    {
        int pomocnicza = a;
        a = b;
        b = pomocnicza;
    }

    static void Main()
    {
        int pierwsza = 5;
        int druga = 10;

        Zamien(ref pierwsza, ref druga);

        Console.WriteLine(pierwsza);
        Console.WriteLine(druga);
    }
}
```

Wyjaśnienie:

- `ref` pozwala metodzie zmienić obie zmienne z `Main`,
- zmienna `pomocnicza` jest potrzebna, aby nie stracić jednej wartości,
- po wywołaniu `pierwsza` ma `10`, a `druga` ma `5`.

## Po co jest out

`out` służy do przekazywania wartości z metody na zewnątrz.

Parametr `out` nie musi mieć wartości przed wywołaniem, ale metoda musi przypisać mu wartość przed zakończeniem.

Ważne zasady:

- `out` zapisujemy w definicji metody,
- `out` zapisujemy także przy wywołaniu metody,
- metoda musi ustawić wartość parametru `out`,
- `out` często służy do zwrócenia dodatkowej wartości obok zwykłego `return`.

## Przykład out

```csharp
using System;

class Program
{
    static void UstawLiczbe(out int liczba)
    {
        liczba = 50;
    }

    static void Main()
    {
        int x;

        UstawLiczbe(out x);

        Console.WriteLine(x);
    }
}
```

Wyjaśnienie:

- `x` nie musi mieć wartości przed wywołaniem,
- metoda `UstawLiczbe` musi przypisać wartość do `liczba`,
- po wywołaniu `x` ma wartość `50`.

## out i wynik dodatkowy

```csharp
using System;

class Program
{
    static bool SprobujPodzielic(int a, int b, out double wynik)
    {
        if (b == 0)
        {
            wynik = 0;
            return false;
        }

        wynik = (double)a / b;
        return true;
    }

    static void Main()
    {
        double wynik;

        bool czySieUdalo = SprobujPodzielic(10, 2, out wynik);

        if (czySieUdalo)
        {
            Console.WriteLine(wynik);
        }
        else
        {
            Console.WriteLine("Nie można dzielić przez zero.");
        }
    }
}
```

Wyjaśnienie:

- metoda zwraca `bool`, czyli informację, czy operacja się udała,
- parametr `out wynik` zwraca obliczoną wartość,
- jeśli dzielenie nie jest możliwe, metoda też musi przypisać coś do `wynik`.

## ref a out

| Cecha | `ref` | `out` |
|---|---|---|
| Czy zmienna musi mieć wartość przed wywołaniem? | Tak | Nie |
| Czy metoda może zmienić zmienną z Main? | Tak | Tak |
| Czy metoda musi przypisać wartość? | Nie zawsze | Tak |
| Typowe użycie | Zmiana istniejącej wartości | Zwrócenie dodatkowego wyniku |
| Słowo przy wywołaniu | `ref` | `out` |

## Kiedy używać ref i out

`ref` i `out` są przydatne, ale nie powinny być pierwszym wyborem w prostych programach.

Najczęściej lepiej:

- zwrócić wynik przez `return`,
- użyć czytelnej metody zwracającej wartość,
- stosować `ref` i `out` dopiero wtedy, gdy faktycznie trzeba zmienić zmienną z miejsca wywołania albo zwrócić dodatkowy wynik.

## Najczęstsze błędy

- Wpisanie `ref` tylko w definicji metody, ale nie przy wywołaniu.
- Wpisanie `ref` przy wywołaniu, ale nie w definicji metody.
- Przekazanie przez `ref` zmiennej, która nie ma wartości.
- Brak przypisania wartości do parametru `out` w każdej możliwej ścieżce metody.
- Nadużywanie `ref` zamiast `return`.
- Mylenie `ref` i `out`.
- Próba przekazania bezpośredniej liczby, np. `ref 5`, zamiast zmiennej.

## Ćwiczenia

1. Napisz metodę `ZmienLiczbe(ref int liczba)`, która ustawia liczbę na `100`.
2. Napisz program, który pokazuje różnicę między zwykłym parametrem `int` a parametrem `ref int`.
3. Napisz metodę `Zamien(ref int a, ref int b)`, która zamienia wartości dwóch zmiennych.
4. Napisz metodę `UstawZero(out int liczba)`, która przypisuje do parametru wartość `0`.
5. Napisz metodę `SprobujPodzielic(int a, int b, out double wynik)`, która zwraca `false` przy dzieleniu przez zero.
6. Wskaż, czy w danym przykładzie lepiej użyć `return`, `ref` czy `out`.
7. Popraw metodę z `out`, w której nie każda ścieżka przypisuje wartość do parametru.
8. Wyjaśnij własnymi słowami różnicę między `ref` i `out`.

## Podsumowanie

Zwykłe przekazywanie parametru typu `int` daje metodzie kopię wartości.

`ref` pozwala metodzie zmienić istniejącą zmienną z miejsca wywołania.

`out` pozwala metodzie zwrócić wartość przez parametr.

Zmienna `ref` musi mieć wartość przed wywołaniem. Parametr `out` musi otrzymać wartość w metodzie.

`ref` i `out` trzeba zapisać zarówno w definicji metody, jak i przy wywołaniu. W prostych przypadkach często wystarczy `return`.
