# Ćwiczenia - testowanie i asercje

## Jak pracować z ćwiczeniami

Pracuj krok po kroku:

- najpierw uruchom podany program,
- potem sprawdź wynik,
- następnie dodaj asercję albo test,
- na końcu popraw ewentualny błąd w metodzie.

Nie usuwaj poprawnej asercji tylko dlatego, że wykazała problem.

## Ćwiczenie 1 - prosta asercja

Dana jest metoda:

```csharp
static int Pomnoz(int a, int b)
{
    return a * b;
}
```

Dopisz w `Main` prostą asercję `Debug.Assert`, która sprawdzi wynik wywołania:

```csharp
Pomnoz(3, 4)
```

Oczekiwany wynik to `12`.

## Ćwiczenie 2 - błędna metoda

Uruchom program z błędną metodą:

```csharp
using System;
using System.Diagnostics;

class Program
{
    static void Main()
    {
        int wynik = ObliczKwadrat(5);

        Debug.Assert(wynik == 25, "Metoda ObliczKwadrat zwróciła niepoprawny wynik.");

        Console.WriteLine("Koniec programu.");
    }

    static int ObliczKwadrat(int liczba)
    {
        return liczba + liczba;
    }
}
```

Wykonaj:

1. Uruchom program w konfiguracji Debug.
2. Odczytaj komunikat asercji.
3. Znajdź błąd w metodzie.
4. Popraw metodę.
5. Uruchom program ponownie.

## Ćwiczenie 3 - własna asercja

Napisz metodę:

```csharp
static int ObliczObwodProstokata(int a, int b)
{
    return 2 * a + 2 * b;
}
```

Następnie przygotuj asercję sprawdzającą wynik dla danych:

```text
a = 4
b = 5
```

Oczekiwany wynik to `18`.

## Ćwiczenie 4 - pierwszy test MSTest

W projekcie właściwym przygotuj metodę:

```csharp
public static int Odejmij(int a, int b)
{
    return a - b;
}
```

W projekcie MSTest przygotuj test sprawdzający:

```text
Odejmij(10, 3) zwraca 7
```

Użyj `Assert.AreEqual`.

## Ćwiczenie 5 - kilka testów jednej metody

Przygotuj metodę:

```csharp
public static bool CzyParzysta(int liczba)
{
    return liczba % 2 == 0;
}
```

Napisz trzy testy:

1. dla liczby parzystej dodatniej,
2. dla liczby nieparzystej,
3. dla zera.

Użyj `Assert.IsTrue` i `Assert.IsFalse`.

## Ćwiczenie 6 - przypadek typowy i brzegowy

Dana jest metoda:

```csharp
public static bool CzyZaliczyl(int punkty)
{
    return punkty >= 50;
}
```

Wskaż:

1. jeden przypadek typowy,
2. jeden przypadek brzegowy,
3. jeden przypadek poniżej granicy.

Następnie przygotuj dla nich testy MSTest.

## Przykład z odpowiedzią

Przykładowa asercja dla ćwiczenia 1:

```csharp
using System;
using System.Diagnostics;

class Program
{
    static void Main()
    {
        int wynik = Pomnoz(3, 4);

        Debug.Assert(wynik == 12, "Metoda Pomnoz zwróciła niepoprawny wynik.");

        Console.WriteLine("Koniec programu.");
    }

    static int Pomnoz(int a, int b)
    {
        return a * b;
    }
}
```

Przykładowy test dla ćwiczenia 4:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using AplikacjaKonsolowa;

namespace AplikacjaKonsolowa.Tests
{
    [TestClass]
    public class TestyProgramu
    {
        [TestMethod]
        public void Odejmij_DziesiecITrzy_ZwracaSiedem()
        {
            int wynik = Program.Odejmij(10, 3);

            Assert.AreEqual(7, wynik);
        }
    }
}
```

## Kontrola samodzielna

- Czy wiem, kiedy użyć `Debug.Assert`?
- Czy wiem, że `Debug.Assert` wymaga `using System.Diagnostics;`?
- Czy umiem odczytać komunikat niespełnionej asercji?
- Czy umiem utworzyć prosty test MSTest?
- Czy umiem wskazać przypadek typowy i brzegowy?
- Czy sprawdzam wynik własnej metody, a nie oczywiste działanie matematyczne?

## Podsumowanie

Asercje i testy pomagają sprawdzać, czy program działa zgodnie z założeniami.

`Debug.Assert` pozwala szybko sprawdzić założenie w zwykłym programie. MSTest pozwala tworzyć osobny projekt testowy i uruchamiać testy automatycznie.
