# Przypadki testowe

## Cel lekcji

Na tej lekcji nauczysz się dobierać kilka przypadków testowych dla jednej metody. Zobaczysz, że jeden test zwykle nie wystarcza, aby dobrze sprawdzić działanie programu.

## Po lekcji potrafisz

- odróżnić przypadek typowy od brzegowego,
- przygotować kilka testów jednej metody,
- sprawdzić wynik dla różnych danych,
- dobrać testy do prostego algorytmu,
- opisać znaczenie danych testowych.

## 1. Co to jest przypadek testowy

Przypadek testowy to konkretne dane wejściowe oraz oczekiwany wynik.

Przykład:

```text
Dane: 4
Oczekiwany wynik: true
```

Dla metody sprawdzającej parzystość liczby oznacza to:

```text
Liczba 4 powinna być parzysta.
```

## 2. Rodzaje przypadków

W prostych zadaniach można przygotować:

- przypadek typowy,
- przypadek brzegowy,
- inny sensowny przypadek.

Przypadek typowy sprawdza zwykłe dane.

Przypadek brzegowy sprawdza dane na granicy warunku.

Inny sensowny przypadek sprawdza dodatkową sytuację, która może wystąpić w programie.

## 3. Metoda do testowania

Przykładowa metoda sprawdza, czy uczeń zaliczył test.

Warunek zaliczenia:

```text
liczba punktów >= 50
```

Kod w projekcie właściwym:

```csharp
using System;

namespace AplikacjaKonsolowa
{
    public class Program
    {
        public static void Main()
        {
            bool wynik = CzyZaliczyl(50);
            Console.WriteLine(wynik);
        }

        public static bool CzyZaliczyl(int punkty)
        {
            return punkty >= 50;
        }
    }
}
```

## 4. Kilka testów jednej metody

Kod w projekcie testowym:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using AplikacjaKonsolowa;

namespace AplikacjaKonsolowa.Tests
{
    [TestClass]
    public class TestyProgramu
    {
        [TestMethod]
        public void CzyZaliczyl_Punkty60_ZwracaTrue()
        {
            bool wynik = Program.CzyZaliczyl(60);

            Assert.IsTrue(wynik);
        }

        [TestMethod]
        public void CzyZaliczyl_Punkty50_ZwracaTrue()
        {
            bool wynik = Program.CzyZaliczyl(50);

            Assert.IsTrue(wynik);
        }

        [TestMethod]
        public void CzyZaliczyl_Punkty49_ZwracaFalse()
        {
            bool wynik = Program.CzyZaliczyl(49);

            Assert.IsFalse(wynik);
        }
    }
}
```

W tych testach:

- `60` to przypadek typowy pozytywny,
- `50` to przypadek brzegowy,
- `49` to przypadek tuż poniżej granicy.

## 5. Przykład z tablicą

Metoda zlicza elementy dodatnie w tablicy.

```csharp
using System;

namespace AplikacjaKonsolowa
{
    public class Program
    {
        public static void Main()
        {
            int[] liczby = { -2, 0, 4, 7 };
            int wynik = PoliczDodatnie(liczby);

            Console.WriteLine(wynik);
        }

        public static int PoliczDodatnie(int[] liczby)
        {
            int licznik = 0;

            for (int i = 0; i < liczby.Length; i++)
            {
                if (liczby[i] > 0)
                {
                    licznik++;
                }
            }

            return licznik;
        }
    }
}
```

Przykładowe testy:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using AplikacjaKonsolowa;

namespace AplikacjaKonsolowa.Tests
{
    [TestClass]
    public class TestyProgramu
    {
        [TestMethod]
        public void PoliczDodatnie_MieszaneLiczby_ZwracaDwa()
        {
            int[] liczby = { -2, 0, 4, 7 };

            int wynik = Program.PoliczDodatnie(liczby);

            Assert.AreEqual(2, wynik);
        }

        [TestMethod]
        public void PoliczDodatnie_BrakDodatnich_ZwracaZero()
        {
            int[] liczby = { -5, -1, 0 };

            int wynik = Program.PoliczDodatnie(liczby);

            Assert.AreEqual(0, wynik);
        }

        [TestMethod]
        public void PoliczDodatnie_WszystkieDodatnie_ZwracaTrzy()
        {
            int[] liczby = { 1, 2, 3 };

            int wynik = Program.PoliczDodatnie(liczby);

            Assert.AreEqual(3, wynik);
        }
    }
}
```

## 6. Odniesienie do INF.04

W zadaniach INF.04 należy czytać wymagania konkretnego zadania.

Nie każdy arkusz wymaga MSTest. Nie każde zadanie wymaga tej samej liczby testów. Nie zawsze trzeba użyć tej samej metody klasy `Assert`.

Przydatne jest jednak to, aby umieć:

- przygotować prostą asercję sprawdzającą wynik metody,
- przygotować test jednostkowy sprawdzający poprawny wynik,
- dobrać dane typowe i brzegowe,
- sprawdzić metodę dla kilku zestawów danych.

## Zapamiętaj

- Testowanie nie polega na sprawdzeniu jednego przypadkowego zestawu danych.
- Przypadek typowy sprawdza zwykłe dane.
- Przypadek brzegowy sprawdza dane na granicy warunku.
- Kilka testów jednej metody daje większą pewność niż jeden test.
- Dane testowe powinny mieć znany wynik oczekiwany.

## Ćwiczenia

1. Dla metody `CzyZaliczyl` wskaż przypadek typowy i brzegowy.
2. Dodaj test dla wartości `0` punktów.
3. Dodaj test dla wartości `100` punktów.
4. Przygotuj trzy testy metody `CzyParzysta`.
5. Przygotuj trzy testy metody `PoliczDodatnie`.
