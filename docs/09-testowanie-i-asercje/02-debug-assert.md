# Debug.Assert

## Cel lekcji

Na tej lekcji użyjesz `Debug.Assert` w zwykłym programie konsolowym C#. Zobaczysz, jak asercja sprawdza wynik metody i jak Visual Studio 2022 informuje o problemie.

## Po lekcji potrafisz

- dodać `using System.Diagnostics;`,
- zapisać `Debug.Assert(warunek);`,
- zapisać `Debug.Assert(warunek, "Opis problemu");`,
- uruchomić program w konfiguracji Debug,
- wyjaśnić różnicę między Debug i Release w kontekście `Debug.Assert`,
- odczytać komunikat niespełnionej asercji.

## 1. Gdzie pracujemy

Na początku nie tworzymy osobnego projektu testowego. Pracujemy w zwykłym projekcie konsolowym C#.

W Visual Studio 2022:

1. Otwórz rozwiązanie z projektem konsolowym.
2. W oknie Solution Explorer otwórz plik z klasą `Program`.
3. Na górze pliku dodaj:

```csharp
using System.Diagnostics;
```

Ten zapis pozwala korzystać z klasy `Debug`.

## 2. Podstawowa postać Debug.Assert

Podstawowa postać asercji wygląda tak:

```csharp
Debug.Assert(warunek);
```

Wersja z komunikatem wygląda tak:

```csharp
Debug.Assert(warunek, "Opis problemu");
```

Komunikat pomaga szybciej zrozumieć, co zostało sprawdzone.

## 3. Pierwszy pełny przykład

Metoda `Dodaj` zwraca sumę dwóch liczb.

```csharp
using System;
using System.Diagnostics;

class Program
{
    static void Main()
    {
        int wynik = Dodaj(2, 3);

        Debug.Assert(wynik == 5, "Metoda Dodaj zwróciła niepoprawny wynik.");

        Console.WriteLine("Program zakończył działanie.");
    }

    static int Dodaj(int a, int b)
    {
        return a + b;
    }
}
```

W tym przykładzie:

- metoda `Dodaj(2, 3)` powinna zwrócić `5`,
- zmienna `wynik` przechowuje wartość zwróconą przez metodę,
- warunek `wynik == 5` sprawdza oczekiwany wynik,
- wynik `true` oznacza, że sprawdzane założenie jest spełnione,
- wynik `false` oznacza, że metoda zwróciła inną wartość niż oczekiwana.

## 4. Jak uruchomić program w Visual Studio 2022

W Visual Studio 2022 konfiguracja uruchamiania znajduje się zwykle na górnym pasku narzędzi.

Sprawdź:

1. Czy na pasku narzędzi widoczna jest lista z napisem `Debug`.
2. Jeżeli widzisz `Release`, rozwiń listę i wybierz `Debug`.
3. Uruchom program przyciskiem Start albo klawiszem `F5`.

Konfiguracja `Debug` jest przeznaczona do pracy nad programem i wykrywania błędów.

Konfiguracja `Release` jest przeznaczona do gotowej wersji programu. W kontekście `Debug.Assert` ważne jest to, że asercje klasy `Debug` działają w konfiguracji Debug, a w typowej konfiguracji Release nie są wykonywane.

Dlatego podczas nauki asercji wybieramy `Debug`.

## 5. Co obserwować

Jeżeli warunek asercji jest prawdziwy, program działa dalej.

W naszym przykładzie warunek jest prawdziwy:

```csharp
wynik == 5
```

Program powinien wypisać:

```text
Program zakończył działanie.
```

Jeżeli warunek asercji jest fałszywy, Visual Studio informuje o problemie. Może pojawić się okno albo komunikat związany z nieudaną asercją. Komunikat podany w drugim parametrze pomaga zrozumieć, czego dotyczy problem.

## 6. Celowo błędna metoda

Teraz zobacz, co stanie się przy błędzie w metodzie.

```csharp
using System;
using System.Diagnostics;

class Program
{
    static void Main()
    {
        int wynik = Dodaj(2, 3);

        Debug.Assert(wynik == 5, "Metoda Dodaj zwróciła niepoprawny wynik.");

        Console.WriteLine("Program zakończył działanie.");
    }

    static int Dodaj(int a, int b)
    {
        return a - b;
    }
}
```

Metoda jest błędna, ponieważ zamiast dodawać, odejmuje liczby.

Dla danych `2` i `3` otrzymujemy:

```text
2 - 3 = -1
```

Warunek:

```csharp
wynik == 5
```

nie jest spełniony.

W takiej sytuacji nie usuwamy asercji tylko dlatego, że pokazała problem. Poprawiamy błędną metodę:

```csharp
static int Dodaj(int a, int b)
{
    return a + b;
}
```

## 7. Dlaczego komunikat jest ważny

Porównaj dwa zapisy:

```csharp
Debug.Assert(wynik == 5);
```

oraz:

```csharp
Debug.Assert(wynik == 5, "Metoda Dodaj zwróciła niepoprawny wynik.");
```

Drugi zapis jest czytelniejszy. Gdy asercja nie zostanie spełniona, komunikat podpowiada, czego dotyczy problem.

## 8. Typowe błędy

- Brak `using System.Diagnostics;`.
- Uruchomienie programu w konfiguracji `Release` i oczekiwanie działania `Debug.Assert`.
- Sprawdzanie warunku, który nie dotyczy własnego kodu.
- Usunięcie asercji zamiast poprawienia błędnej metody.
- Mylenie `=` z `==`.

## Zapamiętaj

- `Debug.Assert` działa w zwykłym projekcie konsolowym.
- Do użycia `Debug.Assert` potrzebne jest `using System.Diagnostics;`.
- Warunek w asercji powinien być prawdziwy.
- Komunikat w drugim parametrze pomaga znaleźć problem.
- W konfiguracji Debug asercja pomaga wykryć błędne założenie lub błąd w kodzie.

## Ćwiczenia

1. Przepisz pierwszy przykład i uruchom go w konfiguracji Debug.
2. Zmień oczekiwany wynik z `5` na `6` i sprawdź, co zrobi asercja.
3. Przywróć poprawny warunek `wynik == 5`.
4. Zmień metodę `Dodaj`, aby celowo zwracała błędny wynik.
5. Odczytaj komunikat asercji, a potem popraw metodę.
