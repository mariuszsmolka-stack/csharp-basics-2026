# Dobra asercja

## Cel lekcji

Na tej lekcji nauczysz się odróżniać asercję sensowną od asercji, która niczego istotnego nie sprawdza. Zobaczysz też przykład bardziej zbliżony do zadań algorytmicznych.

## Po lekcji potrafisz

- rozpoznać zbyt oczywistą asercję,
- przygotować asercję sprawdzającą wynik własnej metody,
- dobrać znany wynik oczekiwany,
- dodać komunikat opisujący problem,
- sprawdzić prostą metodę algorytmiczną.

## 1. Bezużyteczna asercja

Taka asercja jest poprawna składniowo, ale nie jest dobrym testem programu:

```csharp
using System;
using System.Diagnostics;

class Program
{
    static void Main()
    {
        Debug.Assert(2 + 2 == 4);

        Console.WriteLine("Koniec programu.");
    }
}
```

Warunek:

```csharp
2 + 2 == 4
```

nie sprawdza kodu napisanego przez ucznia. Sprawdza tylko oczywiste działanie matematyczne.

Taka asercja nie pomaga znaleźć błędu w programie.

## 2. Lepsza asercja

Lepsza asercja sprawdza wynik własnej metody.

```csharp
using System;
using System.Diagnostics;

class Program
{
    static void Main()
    {
        int wynik = ObliczPole(4, 5);

        Debug.Assert(wynik == 20, "Metoda ObliczPole zwróciła niepoprawny wynik.");

        Console.WriteLine("Sprawdzenie zakończone.");
    }

    static int ObliczPole(int szerokosc, int wysokosc)
    {
        return szerokosc * wysokosc;
    }
}
```

Ta asercja ma sens, ponieważ:

- sprawdza metodę `ObliczPole`,
- ma znany wynik oczekiwany,
- może wykazać błąd w kodzie,
- kontroluje konkretne założenie,
- ma czytelny komunikat.

## 3. Cechy dobrej asercji

Dobra asercja powinna:

- sprawdzać wynik kodu napisanego przez ucznia,
- mieć znany wynik oczekiwany,
- być możliwa do niespełnienia w przypadku błędu programu,
- kontrolować konkretne założenie,
- być czytelna,
- pomagać w lokalizacji problemu.

## 4. Przykład algorytmiczny

W zadaniach programistycznych często trzeba analizować dane. Poniższa metoda zlicza, ile razy w napisie występuje podany znak.

Nie używamy LINQ. Kod można prześledzić krok po kroku.

```csharp
using System;
using System.Diagnostics;

class Program
{
    static void Main()
    {
        int liczbaLiter = PoliczZnak("programowanie", 'o');

        Debug.Assert(liczbaLiter == 2, "Metoda PoliczZnak zwróciła niepoprawny wynik.");

        Console.WriteLine("Sprawdzenie zakończone.");
    }

    static int PoliczZnak(string tekst, char szukanyZnak)
    {
        int licznik = 0;

        for (int i = 0; i < tekst.Length; i++)
        {
            if (tekst[i] == szukanyZnak)
            {
                licznik++;
            }
        }

        return licznik;
    }
}
```

W napisie:

```text
programowanie
```

litera `o` występuje dwa razy. Dlatego oczekiwany wynik to `2`.

## 5. Celowo błędna wersja

Poniższa metoda zawiera błąd. Zwraca `0`, ponieważ licznik nie jest zwiększany.

```csharp
static int PoliczZnak(string tekst, char szukanyZnak)
{
    int licznik = 0;

    for (int i = 0; i < tekst.Length; i++)
    {
        if (tekst[i] == szukanyZnak)
        {
            licznik = licznik;
        }
    }

    return licznik;
}
```

Asercja powinna wykazać problem.

Nie usuwamy poprawnej asercji. Poprawiamy metodę:

```csharp
licznik++;
```

## 6. Asercja a INF.04

W zadaniach egzaminacyjnych należy czytać wymagania konkretnego zadania.

Jeżeli zadanie wymaga testu lub asercji, trzeba wykonać ją zgodnie z poleceniem.

Przydatne jest umiejętne przygotowanie prostej asercji, która sprawdza wynik metody algorytmicznej, na przykład:

- liczbę znaków,
- sumę elementów,
- liczbę elementów spełniających warunek,
- wynik prostego obliczenia.

## Zapamiętaj

- Dobra asercja sprawdza wynik własnego kodu.
- Oczekiwany wynik powinien być znany.
- Komunikat powinien pomagać znaleźć problem.
- Bezużyteczna asercja nie zwiększa pewności, że program działa poprawnie.
- Jeśli dobra asercja wykryje problem, poprawiamy kod albo założenie.

## Ćwiczenia

1. Wyjaśnij, dlaczego `Debug.Assert(2 + 2 == 4);` nie jest dobrą asercją.
2. Napisz metodę `ObliczObwodProstokata(int a, int b)` i sprawdź jej wynik za pomocą `Debug.Assert`.
3. Napisz metodę `CzyParzysta(int liczba)` i przygotuj asercję dla liczby `8`.
4. Napisz metodę `PoliczDodatnie(int[] liczby)` i sprawdź ją dla krótkiej tablicy.
5. Dodaj komunikat do każdej asercji.
