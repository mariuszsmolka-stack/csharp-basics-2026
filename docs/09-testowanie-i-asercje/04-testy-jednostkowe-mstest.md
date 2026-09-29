# Testy jednostkowe i MSTest

## Cel lekcji

Na tej lekcji poznasz różnicę między `Debug.Assert` a testem jednostkowym. Zobaczysz też, jak w Visual Studio 2022 dodać projekt MSTest do istniejącego rozwiązania.

## Po lekcji potrafisz

- wyjaśnić, czym jest test jednostkowy,
- odróżnić `Debug.Assert` od MSTest,
- dodać projekt MSTest w Visual Studio 2022,
- dodać referencję do projektu właściwego,
- przygotować klasę i metodę tak, aby projekt testowy miał do nich dostęp.

## 1. Debug.Assert a MSTest

`Debug.Assert` to asercja użyta w zwykłym kodzie programu podczas jego uruchamiania.

MSTest to mechanizm testów jednostkowych. W tym podejściu tworzymy osobny projekt testowy, którego zadaniem jest uruchamianie metod testowych i automatyczne sprawdzanie wyników.

```text
Debug.Assert
=> sprawdzanie założenia w zwykłym programie

MSTest
=> osobny projekt testowy i osobne metody testowe
```

To nie są identyczne rozwiązania.

## 2. Czym jest test jednostkowy

Test jednostkowy sprawdza mały fragment programu, najczęściej jedną metodę.

Dobry test jednostkowy:

- przygotowuje dane,
- wywołuje testowaną metodę,
- sprawdza otrzymany wynik,
- ma jasną nazwę,
- sprawdza konkretny przypadek.

## 3. Założenie przykładu

Uczeń ma już zwykły projekt konsolowy C# w rozwiązaniu Visual Studio.

Przykładowy projekt właściwy może nazywać się:

```text
AplikacjaKonsolowa
```

Projekt testowy może nazywać się:

```text
AplikacjaKonsolowa.Tests
```

Nazwy mogą być inne, ale powinny być czytelne.

## 4. Dodanie projektu MSTest w Visual Studio 2022

W Visual Studio 2022:

1. Otwórz rozwiązanie z projektem konsolowym.
2. W oknie Solution Explorer znajdź nazwę rozwiązania.
3. Kliknij prawym przyciskiem myszy nazwę rozwiązania, a nie pojedynczy plik.
4. Wybierz `Add`.
5. Wybierz `New Project`.
6. W polu wyszukiwania wpisz `MSTest`.
7. Wybierz projekt testowy MSTest dla C#.
8. Kliknij `Next`.
9. Nadaj projektowi nazwę, na przykład `AplikacjaKonsolowa.Tests`.
10. Upewnij się, że projekt testowy będzie dodany do tego samego rozwiązania.
11. Zakończ tworzenie projektu.

Po tych krokach w jednym rozwiązaniu powinny być dwa projekty:

- projekt właściwy, na przykład `AplikacjaKonsolowa`,
- projekt testowy, na przykład `AplikacjaKonsolowa.Tests`.

## 5. Dodanie referencji do projektu właściwego

Projekt testowy musi widzieć kod projektu właściwego.

W Visual Studio 2022:

1. W oknie Solution Explorer kliknij prawym przyciskiem projekt testowy.
2. Wybierz `Add`.
3. Wybierz `Project Reference`.
4. Zaznacz projekt właściwy, na przykład `AplikacjaKonsolowa`.
5. Zatwierdź wybór.

Referencja jest potrzebna, aby test mógł wywołać metodę z projektu właściwego.

## 6. Widoczność klasy i metody

Projekt testowy jest osobnym projektem. Dlatego metoda testowana musi być dostępna z zewnątrz.

W projekcie właściwym można przygotować kod tak:

```csharp
using System;

namespace AplikacjaKonsolowa
{
    public class Program
    {
        public static void Main()
        {
            int wynik = Dodaj(2, 3);
            Console.WriteLine(wynik);
        }

        public static int Dodaj(int a, int b)
        {
            return a + b;
        }
    }
}
```

Ważne elementy:

- `public class Program` pozwala użyć klasy z projektu testowego,
- `public static int Dodaj(...)` pozwala wywołać metodę z testu,
- `namespace AplikacjaKonsolowa` porządkuje kod i ułatwia wskazanie klasy w teście.

Jeżeli klasa albo metoda nie będzie publiczna, projekt testowy może nie mieć do niej dostępu.

## 7. Test Explorer

Testy w Visual Studio 2022 uruchamiamy w oknie Test Explorer.

Aby je otworzyć:

1. Na górnym pasku menu wybierz `Test`.
2. Wybierz `Test Explorer`.

W oknie Test Explorer znajduje się lista testów.

Z tego okna można:

- uruchomić pojedynczy test,
- uruchomić wszystkie testy,
- zobaczyć testy zakończone powodzeniem,
- zobaczyć testy zakończone niepowodzeniem,
- odczytać szczegóły błędu, w tym wartość oczekiwaną i otrzymaną, jeżeli Visual Studio ją pokazuje.

## Zapamiętaj

- MSTest wymaga osobnego projektu testowego.
- Projekt testowy powinien być w tym samym rozwiązaniu.
- Projekt testowy potrzebuje referencji do projektu właściwego.
- Testowana klasa i metoda muszą być dostępne dla projektu testowego.
- Test Explorer służy do uruchamiania testów i sprawdzania wyników.

## Ćwiczenia

1. Wyjaśnij różnicę między `Debug.Assert` i MSTest.
2. Utwórz w Visual Studio 2022 projekt MSTest w tym samym rozwiązaniu co projekt konsolowy.
3. Dodaj referencję projektu testowego do projektu właściwego.
4. Przygotuj metodę `public static int Dodaj(int a, int b)`.
5. Otwórz okno `Test Explorer`.
