# Czym jest asercja

## Cel lekcji

Na tej lekcji poznasz pojęcie asercji. Zobaczysz, że asercja sprawdza założenie programu i pomaga wykryć sytuację, w której program działa inaczej, niż zakładaliśmy.

## Po lekcji potrafisz

- wyjaśnić, czym jest asercja,
- wskazać warunek sprawdzany przez asercję,
- odróżnić asercję od zwykłej instrukcji `if`,
- odróżnić asercję od walidacji danych użytkownika,
- wyjaśnić, co oznacza niespełniona asercja.

## 1. Co sprawdza asercja

Asercja to sprawdzenie założenia, które według programisty powinno być prawdziwe.

Najprostszy zapis można opisać tak:

```text
Sprawdź, czy ten warunek jest prawdziwy.
Jeżeli nie jest, pokaż problem.
```

Asercja nie służy do zwykłej rozmowy z użytkownikiem. Nie pytamy w niej użytkownika o dane. Asercja pomaga programiście sprawdzić, czy kod działa zgodnie z założeniem.

## 2. Warunek asercji

Asercja sprawdza warunek logiczny. Taki warunek ma wynik typu `bool`, czyli:

- `true` - warunek jest spełniony,
- `false` - warunek nie jest spełniony.

Przykład warunku:

```csharp
wynik == 5
```

Ten warunek oznacza:

```text
Czy zmienna wynik ma wartość 5?
```

Jeżeli odpowiedź brzmi `true`, założenie jest spełnione. Jeżeli odpowiedź brzmi `false`, trzeba sprawdzić program.

## 3. Przykład założenia

Załóżmy, że metoda `Dodaj(2, 3)` powinna zwrócić `5`.

```csharp
static int Dodaj(int a, int b)
{
    return a + b;
}
```

Możemy sprawdzić wynik metody:

```csharp
int wynik = Dodaj(2, 3);
```

Oczekujemy wartości `5`. Warunek sprawdzający to:

```csharp
wynik == 5
```

To jest dobry kandydat na asercję, ponieważ sprawdza wynik naszego kodu.

## 4. Co oznacza niespełniona asercja

Jeżeli poprawnie zaprojektowana asercja nie jest spełniona, oznacza to, że:

- program działa inaczej niż zakładaliśmy,
- testowane założenie jest nieprawidłowe,
- albo w kodzie występuje błąd.

Nie należy usuwać asercji tylko dlatego, że wykazała problem.

Jeżeli asercja pokazuje błąd, trzeba sprawdzić:

- czy założenie jest poprawne,
- czy testowane dane są poprawne,
- czy metoda działa prawidłowo.

## 5. Asercja a instrukcja if

Instrukcja `if` jest częścią normalnej logiki programu.

Przykład:

```csharp
if (wiek >= 18)
{
    Console.WriteLine("Osoba jest pełnoletnia.");
}
else
{
    Console.WriteLine("Osoba nie jest pełnoletnia.");
}
```

Ten kod obsługuje dwie możliwe sytuacje. Obie są normalne.

Asercja ma inny cel. Sprawdza założenie, które w danym miejscu programu powinno być prawdziwe.

```text
if
=> wybór działania programu

asercja
=> sprawdzenie założenia programisty
```

## 6. Asercja a walidacja danych użytkownika

Walidacja danych użytkownika sprawdza dane wpisane przez użytkownika.

Przykład:

```csharp
Console.WriteLine("Podaj wiek:");
string tekst = Console.ReadLine();

bool czyLiczba = int.TryParse(tekst, out int wiek);

if (czyLiczba)
{
    Console.WriteLine("Wiek został wczytany.");
}
else
{
    Console.WriteLine("To nie jest poprawna liczba.");
}
```

Walidacja jest potrzebna, ponieważ użytkownik może wpisać błędne dane.

Asercja nie zastępuje walidacji. Nie używamy asercji do informowania użytkownika, że źle wpisał dane.

## 7. Asercja a test jednostkowy

Asercja może być użyta w zwykłym programie podczas jego uruchamiania.

Test jednostkowy to osobny fragment kodu testowego, który automatycznie uruchamia wybraną metodę i sprawdza jej wynik.

W tym dziale kolejność będzie taka:

```text
Debug.Assert
=> zrozumienie idei asercji
=> sensowna asercja własnej metody
=> test jednostkowy
=> MSTest
=> kilka przypadków testowych
```

Najpierw zaczniemy od `Debug.Assert`, ponieważ działa w zwykłym projekcie konsolowym.

## Zapamiętaj

- Asercja sprawdza założenie programu.
- Warunek asercji powinien być prawdziwy.
- Wynik `true` oznacza, że sprawdzane założenie jest spełnione.
- Wynik `false` oznacza, że trzeba sprawdzić założenie albo kod.
- Asercja nie zastępuje instrukcji `if`.
- Asercja nie zastępuje walidacji danych użytkownika.

## Ćwiczenia

1. Wyjaśnij własnymi słowami, czym jest asercja.
2. Podaj przykład warunku, który może być sprawdzony przez asercję.
3. Wyjaśnij, czym różni się asercja od instrukcji `if`.
4. Wyjaśnij, dlaczego asercja nie służy do sprawdzania danych wpisanych przez użytkownika.
5. Napisz, co należy zrobić, gdy poprawnie zaprojektowana asercja nie jest spełniona.
