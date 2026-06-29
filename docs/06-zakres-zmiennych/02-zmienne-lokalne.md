# Zmienne lokalne

## Co to jest zmienna lokalna

Zmienna lokalna to zmienna zadeklarowana wewnątrz metody lub bloku kodu.

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

Zmienna `liczba` jest zmienną lokalną metody `Main`. Można jej używać w tej metodzie od miejsca deklaracji do końca jej zakresu.

## Zmienna lokalna przechowuje dane tymczasowe

Zmienna lokalna często służy do przechowania wartości potrzebnej tylko przez pewien fragment programu.

```csharp
using System;

class Program
{
    static void Main()
    {
        int a = 5;
        int b = 7;
        int suma = a + b;

        Console.WriteLine(suma);
    }
}
```

Zmienna `suma` jest wynikiem pomocniczym. Jest potrzebna po to, aby zapamiętać wynik dodawania przed wypisaniem go na ekranie.

## Zmienna lokalna w metodzie pomocniczej

Zmienne lokalne mogą występować nie tylko w `Main`, ale także w innych metodach.

```csharp
using System;

class Program
{
    static void PokazWynik()
    {
        int a = 4;
        int b = 6;
        int suma = a + b;

        Console.WriteLine(suma);
    }

    static void Main()
    {
        PokazWynik();
    }
}
```

Zmienne `a`, `b` i `suma` istnieją wewnątrz metody `PokazWynik`. Nie są dostępne bezpośrednio w metodzie `Main`.

## Diagram: zmienne lokalne w metodzie

```mermaid
---
config:
  flowchart:
    curve: linear
---
flowchart LR
    A([Start])
    B["Wejście do metody"]
    C["Utworzenie zmiennych"]
    D["Użycie zmiennych"]
    E["Koniec metody"]
    F["Zmienne niedostępne"]
    G([Koniec])

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
```

Diagram pokazuje, że zmienne lokalne istnieją podczas wykonywania metody. Po zakończeniu metody nie można już ich używać.

## Zmienna lokalna w if

Zmienną lokalną można zadeklarować także wewnątrz bloku `if`.

```csharp
using System;

class Program
{
    static void Main()
    {
        if (true)
        {
            string tekst = "Warunek spełniony";
            Console.WriteLine(tekst);
        }
    }
}
```

Zmienna `tekst` istnieje tylko w bloku `if`. Po zamknięciu klamry `}` tego bloku nie jest już dostępna.

## Zmienna lokalna w pętli

Zmienna lokalna może być używana wewnątrz pętli.

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 0; i < 5; i++)
        {
            int kwadrat = i * i;
            Console.WriteLine(kwadrat);
        }
    }
}
```

W tym przykładzie:

* `i` jest licznikiem pętli,
* `kwadrat` jest zmienną lokalną tworzoną w każdej iteracji bloku pętli,
* po zakończeniu bloku pętli `kwadrat` nie jest dostępny.

## Dobre nazwy zmiennych lokalnych

Nazwa zmiennej lokalnej powinna mówić, do czego zmienna służy.

Dobre nazwy:

* `suma`,
* `srednia`,
* `minimum`,
* `licznik`,
* `komunikat`.

Słabe nazwy:

* `x`,
* `y`,
* `a1`,
* `temp`, jeśli nie wiadomo, co oznacza.

Krótkie nazwy typu `i` są akceptowalne jako licznik prostej pętli.

## Zmienna lokalna a parametr metody

Zmienna lokalna jest tworzona wewnątrz metody lub bloku.

Parametr metody także ma nazwę i przechowuje wartość, ale otrzymuje ją z miejsca, w którym metoda została wywołana.

Szczegóły parametrów będą jeszcze wykorzystywane w kolejnych lekcjach. Na tym etapie najważniejsze jest to, że zarówno zmienne lokalne, jak i parametry mają swój zakres.

## Najczęstsze błędy

* Użycie zmiennej przed deklaracją.
* Użycie zmiennej poza jej zakresem.
* Deklarowanie zmiennej, która nigdy nie jest używana.
* Nadawanie zmiennym nieczytelnych nazw.
* Mylenie zmiennej lokalnej z parametrem metody.
* Deklarowanie zmiennej zbyt wcześnie albo zbyt późno.

## Ćwiczenia

1. Napisz program, w którym w `Main` zadeklarujesz zmienną lokalną `liczba` i wypiszesz ją na ekranie.
2. Napisz program, w którym zmienne `a` i `b` przechowują dwie liczby, a zmienna `suma` przechowuje ich sumę.
3. Napisz metodę `PokazSume`, w której zadeklarujesz zmienne lokalne `a`, `b` i `suma`.
4. Napisz program z `if`, w którym zmienna `komunikat` jest zadeklarowana i użyta wewnątrz bloku `if`.
5. Napisz pętlę `for`, w której zmienna `kwadrat` jest obliczana wewnątrz bloku pętli.
6. Sprawdź, co stanie się, gdy spróbujesz użyć zmiennej zadeklarowanej w `if` poza blokiem `if`.
7. Popraw nazwy zmiennych w krótkim programie tak, aby były bardziej czytelne.

## Podsumowanie

Zmienna lokalna jest zadeklarowana wewnątrz metody lub bloku.

Zmienna lokalna służy do przechowywania danych tymczasowych i istnieje tylko w swoim zakresie.

Zmienna lokalna powinna mieć czytelną nazwę. Dobre rozumienie zmiennych lokalnych ułatwia pisanie metod i większych programów.
