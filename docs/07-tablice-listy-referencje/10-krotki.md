# Krotki - grupowanie i zwracanie wielu wartości

## Cel lekcji

Nauczysz się grupować kilka powiązanych wartości w jednej krotce. Poznasz krotki dwuelementowe i wieloelementowe, nauczysz się odczytywać ich elementy, wykonywać dekonstrukcję oraz używać krotek podczas wywoływania metod.

Po tej lekcji powinieneś umieć:

- utworzyć krotkę zawierającą dwie, trzy lub więcej wartości,
- zapisać w krotce wartości różnych typów,
- odczytać elementy za pomocą nazw oraz właściwości `Item1`, `Item2` i kolejnych,
- zmienić wartość elementu krotki,
- wykonać dekonstrukcję krotki,
- zwrócić kilka powiązanych wyników z metody,
- przekazać krotkę jako argument metody,
- wybrać między krotką, tablicą, listą, `ref`, `out` i klasą.

## 1. Czym jest krotka

Krotka jest jedną złożoną wartością, która grupuje kilka powiązanych wartości. Poszczególne elementy krotki mogą mieć różne typy.

Krotka nie jest ograniczona do dwóch elementów. Może zawierać dwie, trzy, cztery lub więcej wartości. Składnia krotki w C# wymaga jednak co najmniej dwóch elementów.

Przykładowa krotka może przechowywać jednocześnie imię typu `string` i wiek typu `int`.

```csharp
using System;

class Program
{
    static void Main()
    {
        (string imie, int wiek) uczen = ("Anna", 17);

        Console.WriteLine($"Imię: {uczen.imie}");
        Console.WriteLine($"Wiek: {uczen.wiek}");
    }
}
```

Zmienna `uczen` jest jedną krotką. Zawiera dwa nazwane elementy: `imie` i `wiek`.

## 2. Krotka bez nazw elementów

Elementy krotki nie muszą mieć własnych nazw.

```csharp
using System;

class Program
{
    static void Main()
    {
        (string, int) uczen = ("Anna", 17);

        Console.WriteLine($"Imię: {uczen.Item1}");
        Console.WriteLine($"Wiek: {uczen.Item2}");
    }
}
```

W krotce bez nazw:

- `Item1` oznacza pierwszy element,
- `Item2` oznacza drugi element,
- `Item3` oznacza trzeci element,
- kolejne elementy mają kolejne numery.

Nazwy takie jak `imie` i `wiek` są zwykle czytelniejsze niż `Item1` i `Item2`. W krótkim przykładzie łatwo zapamiętać kolejność elementów, ale w większym programie znaczące nazwy ograniczają ryzyko pomyłki.

## 3. Krotka utworzona za pomocą var

Typ krotki można zapisać jawnie albo pozwolić kompilatorowi ustalić go na podstawie podanych wartości.

```csharp
using System;

class Program
{
    static void Main()
    {
        (string imie, int wiek) pierwszyUczen = ("Anna", 17);
        var drugiUczen = (imie: "Piotr", wiek: 18);

        Console.WriteLine($"{pierwszyUczen.imie}, {pierwszyUczen.wiek}");
        Console.WriteLine($"{drugiUczen.imie}, {drugiUczen.wiek}");
    }
}
```

W pierwszym przypisaniu typ został zapisany dokładnie. W drugim użyto `var`, ale nazwy elementów podano po prawej stronie.

## 4. Krotki wieloelementowe

Krotka może zawierać więcej niż dwie wartości.

### Krotka trzyelementowa

```csharp
using System;

class Program
{
    static void Main()
    {
        (string nazwa, double cena, int liczbaSztuk) produkt =
            ("Klawiatura", 129.99, 8);

        Console.WriteLine($"Produkt: {produkt.nazwa}");
        Console.WriteLine($"Cena: {produkt.cena:F2} zł");
        Console.WriteLine($"Liczba sztuk: {produkt.liczbaSztuk}");
    }
}
```

Krotka `produkt` zawiera trzy elementy dwóch różnych typów: `string`, `double` i `int`.

### Krotka czteroelementowa

```csharp
using System;

class Program
{
    static void Main()
    {
        (string imie, string nazwisko, int wiek, double srednia) uczen =
            ("Anna", "Nowak", 17, 4.75);

        Console.WriteLine($"Imię: {uczen.imie}");
        Console.WriteLine($"Nazwisko: {uczen.nazwisko}");
        Console.WriteLine($"Wiek: {uczen.wiek}");
        Console.WriteLine($"Średnia: {uczen.srednia:F2}");
    }
}
```

Ta krotka grupuje cztery powiązane informacje o uczniu.

### Wieloelementowa krotka bez nazw

```csharp
using System;

class Program
{
    static void Main()
    {
        (string, double, int, bool) produkt = ("Monitor", 899.99, 5, true);

        Console.WriteLine($"Nazwa: {produkt.Item1}");
        Console.WriteLine($"Cena: {produkt.Item2:F2} zł");
        Console.WriteLine($"Liczba sztuk: {produkt.Item3}");
        Console.WriteLine($"Dostępny: {produkt.Item4}");
    }
}
```

Im więcej elementów ma krotka, tym ważniejsze stają się ich czytelne nazwy.

## 5. Zmiana wartości elementu krotki

Wartość elementu krotki można zmienić.

```csharp
using System;

class Program
{
    static void Main()
    {
        (string nazwa, double cena, int liczbaSztuk) produkt =
            ("Mysz", 79.99, 10);

        produkt.cena = 69.99;
        produkt.liczbaSztuk = 8;

        Console.WriteLine($"Produkt: {produkt.nazwa}");
        Console.WriteLine($"Nowa cena: {produkt.cena:F2} zł");
        Console.WriteLine($"Pozostało sztuk: {produkt.liczbaSztuk}");
    }
}
```

Typ elementu się nie zmienia. Do elementu `cena` nadal trzeba przypisać wartość zgodną z typem `double`.

## 6. Dekonstrukcja krotki

Dekonstrukcja rozdziela elementy krotki do osobnych zmiennych.

### Deklaracja nowych zmiennych

```csharp
using System;

class Program
{
    static void Main()
    {
        (string imie, int wiek) uczen = ("Anna", 17);

        (string imieUcznia, int wiekUcznia) = uczen;

        Console.WriteLine(imieUcznia);
        Console.WriteLine(wiekUcznia);
    }
}
```

Po lewej stronie powstają dwie nowe zmienne.

### Przypisanie do istniejących zmiennych

```csharp
using System;

class Program
{
    static void Main()
    {
        (string imie, int wiek) uczen = ("Anna", 17);

        string imieUcznia;
        int wiekUcznia;

        (imieUcznia, wiekUcznia) = uczen;

        Console.WriteLine(imieUcznia);
        Console.WriteLine(wiekUcznia);
    }
}
```

Zmienne zostały zadeklarowane przed dekonstrukcją, dlatego po lewej stronie wpisujemy tylko ich nazwy.

### Pominięcie elementu

Niepotrzebny element można pominąć za pomocą `_`.

```csharp
using System;

class Program
{
    static void Main()
    {
        (string imie, string nazwisko, int wiek) uczen =
            ("Anna", "Nowak", 17);

        (string imieUcznia, _, int wiekUcznia) = uczen;

        Console.WriteLine(imieUcznia);
        Console.WriteLine(wiekUcznia);
    }
}
```

Liczba pozycji po lewej stronie musi odpowiadać liczbie elementów krotki. `_` zajmuje pozycję pomijanego elementu, ale nie tworzy używanej zmiennej.

## 7. Metoda zwracająca krotkę dwuelementową

Metoda może zwrócić kilka powiązanych wyników jako jedną krotkę.

```csharp
using System;

class Program
{
    static (int minimum, int maksimum) ZnajdzMinMax(int[] liczby)
    {
        int minimum = liczby[0];
        int maksimum = liczby[0];

        foreach (int liczba in liczby)
        {
            if (liczba < minimum)
            {
                minimum = liczba;
            }

            if (liczba > maksimum)
            {
                maksimum = liczba;
            }
        }

        return (minimum, maksimum);
    }

    static void Main()
    {
        int[] liczby = { 7, 2, 9, 4, 1 };

        (int minimum, int maksimum) wynikJawny = ZnajdzMinMax(liczby);
        Console.WriteLine($"Minimum: {wynikJawny.minimum}");
        Console.WriteLine($"Maksimum: {wynikJawny.maksimum}");

        var wynikAutomatyczny = ZnajdzMinMax(liczby);
        Console.WriteLine($"Minimum: {wynikAutomatyczny.minimum}");
        Console.WriteLine($"Maksimum: {wynikAutomatyczny.maksimum}");

        (int najmniejsza, int najwieksza) = ZnajdzMinMax(liczby);
        Console.WriteLine($"Najmniejsza: {najmniejsza}");
        Console.WriteLine($"Największa: {najwieksza}");
    }
}
```

W przykładzie pokazano trzy sposoby wykorzystania wyniku:

- jawnie zadeklarowaną zmienną krotkową,
- zmienną utworzoną za pomocą `var`,
- bezpośrednią dekonstrukcję wyniku wywołania metody.

Metoda zakłada, że tablica zawiera co najmniej jeden element. Jest to konieczne, ponieważ początkowe minimum i maksimum są pobierane z `liczby[0]`.

## 8. Metoda zwracająca krotkę wieloelementową

Jedna metoda może zwrócić więcej niż dwa wyniki.

```csharp
using System;

class Program
{
    static (int minimum, int maksimum, double srednia, int liczbaElementow)
        ObliczStatystyki(int[] liczby)
    {
        int minimum = liczby[0];
        int maksimum = liczby[0];
        int suma = 0;

        foreach (int liczba in liczby)
        {
            if (liczba < minimum)
            {
                minimum = liczba;
            }

            if (liczba > maksimum)
            {
                maksimum = liczba;
            }

            suma += liczba;
        }

        double srednia = (double)suma / liczby.Length;

        return (minimum, maksimum, srednia, liczby.Length);
    }

    static void Main()
    {
        int[] liczby = { 7, 2, 9, 4, 1 };

        var statystyki = ObliczStatystyki(liczby);

        Console.WriteLine($"Minimum: {statystyki.minimum}");
        Console.WriteLine($"Maksimum: {statystyki.maksimum}");
        Console.WriteLine($"Średnia: {statystyki.srednia:F2}");
        Console.WriteLine($"Liczba elementów: {statystyki.liczbaElementow}");

        (int minimum, int maksimum, double srednia, int liczbaElementow) =
            ObliczStatystyki(liczby);

        Console.WriteLine($"Wyniki po dekonstrukcji: {minimum}, {maksimum}, {srednia:F2}, {liczbaElementow}");
    }
}
```

Metoda zwraca cztery powiązane wyniki. Nazwy elementów krotki informują, co oznacza każda wartość.

## 9. Krotka dwuelementowa jako argument metody

Krotkę można przekazać do metody jako jeden argument.

```csharp
using System;

class Program
{
    static void WyswietlUcznia((string imie, int wiek) uczen)
    {
        Console.WriteLine($"Imię: {uczen.imie}");
        Console.WriteLine($"Wiek: {uczen.wiek}");
    }

    static void Main()
    {
        (string imie, int wiek) pierwszyUczen = ("Anna", 17);

        WyswietlUcznia(pierwszyUczen);
        WyswietlUcznia(("Piotr", 18));
    }
}
```

Pierwsze wywołanie przekazuje wcześniej utworzoną krotkę. Drugie tworzy krotkę bezpośrednio w liście argumentów metody.

W obu przypadkach metoda otrzymuje jeden argument zawierający dwie wartości.

## 10. Krotka wieloelementowa jako argument metody

Parametrem metody może być również krotka zawierająca więcej elementów.

```csharp
using System;

class Program
{
    static void WyswietlProdukt(
        (string nazwa, double cena, int liczbaSztuk, bool dostepny) produkt)
    {
        Console.WriteLine($"Nazwa: {produkt.nazwa}");
        Console.WriteLine($"Cena: {produkt.cena:F2} zł");
        Console.WriteLine($"Liczba sztuk: {produkt.liczbaSztuk}");
        Console.WriteLine($"Dostępny: {produkt.dostepny}");
    }

    static void Main()
    {
        (string nazwa, double cena, int liczbaSztuk, bool dostepny) produkt =
            ("Monitor", 899.99, 5, true);

        WyswietlProdukt(produkt);
        WyswietlProdukt(("Klawiatura", 129.99, 8, true));
    }
}
```

Kolejność oraz typy elementów przekazywanej krotki muszą odpowiadać typom elementów parametru.

## 11. Krotka a ref i out

`ref` i `out` służą do przekazywania danych przez referencję. Metoda zwracająca krotkę zwraca natomiast jedną złożoną wartość zawierającą kilka wyników.

| Cecha | Krotka | `ref` | `out` |
|---|---|---|---|
| Zapis metody | Typ krotki przed nazwą metody | `ref` przy parametrze | `out` przy parametrze |
| Zapis wywołania | Zwykłe wywołanie i odbiór wyniku | `ref` przy argumencie | `out` przy argumencie |
| Liczba przekazywanych informacji | Dwie lub więcej w jednej wartości | Jedna na parametr | Jedna na parametr |
| Czytelność kilku wyników | Wysoka przy nazwanych elementach | Zależy od liczby parametrów | Zależy od liczby parametrów |
| Wcześniejsza wartość zmiennej | Nie jest wymagana | Jest wymagana | Nie jest wymagana |
| Nazwy zwracanych wartości | Tak | Nazwy parametrów | Nazwy parametrów |
| Typowe zastosowanie | Kilka powiązanych wyników własnej metody | Zmiana istniejącej zmiennej | Zwrócenie wyniku przez parametr |

Krotka nie jest zawsze lepsza od `out`.

- `TryParse()` standardowo korzysta z `out`, dlatego wywołujemy tę metodę zgodnie z jej istniejącym interfejsem.
- Krotka jest wygodna, gdy własna metoda ma zwrócić kilka powiązanych wyników.
- `ref` służy głównie do modyfikowania istniejącej zmiennej przekazanej do metody.
- Klasa lub rekord są lepsze, gdy dane tworzą trwały i rozbudowany model.

## 12. Krotka, tablica, lista czy klasa

| Cecha | Krotka | Tablica | Lista | Klasa |
|---|---|---|---|---|
| Różne typy danych | Tak | Nie | Nie | Tak |
| Zmienna liczba elementów | Nie | Nie | Tak | Zależy od projektu klasy |
| Dostęp do danych | Nazwy lub `Item1`, `Item2` | Indeksy | Indeksy | Nazwane pola lub właściwości |
| Znaczące nazwy elementów | Tak, jeśli je nadamy | Nie | Nie | Tak |
| Typowe zastosowanie | Kilka powiązanych wartości | Wiele danych jednego typu | Zmienna liczba danych jednego typu | Trwały model danych i zachowania |
| Zwracanie kilku wyników z metody | Bardzo wygodne | Możliwe dla jednego typu | Możliwe dla jednego typu | Dobre dla rozbudowanych wyników |

Krotka jest przydatna dla niewielkiej grupy powiązanych wartości. Bardzo duża krotka staje się trudna do czytania. W takim przypadku lepiej utworzyć klasę z nazwanymi polami lub właściwościami.

## 13. Starszy typ Tuple

W starszym kodzie można spotkać klasę `Tuple`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Tuple<string, int> uczen = Tuple.Create("Anna", 17);

        Console.WriteLine(uczen.Item1);
        Console.WriteLine(uczen.Item2);
    }
}
```

W nowym kodzie zwykle stosuje się współczesne krotki wartościowe:

```csharp
using System;

class Program
{
    static void Main()
    {
        (string imie, int wiek) uczen = ("Anna", 17);

        Console.WriteLine(uczen.imie);
        Console.WriteLine(uczen.wiek);
    }
}
```

Taki zapis jest krótszy i pozwala nadawać elementom czytelne nazwy.

## Typowe błędy

- Próba utworzenia krotki jednoelementowej. Składnia krotki wymaga co najmniej dwóch elementów.
- Niezgodność liczby pozycji podczas dekonstrukcji.
- Niezgodność typów elementów krotki.
- Pomylenie `Item1` z `Item2`.
- Używanie nienazwanych elementów w rozbudowanym kodzie.
- Próba użycia nazwy elementu, której nie zadeklarowano.
- Przekazanie elementów do metody w nieprawidłowej kolejności.
- Zastosowanie bardzo dużej krotki zamiast klasy.
- Oczekiwanie, że krotka automatycznie zastąpi `ref` lub `out` w metodach bibliotecznych.
- Założenie, że metoda zwracająca minimum i maksimum poradzi sobie z pustą tablicą bez dodatkowego sprawdzenia.

## Zapamiętaj

- Krotka grupuje kilka powiązanych wartości w jedną złożoną wartość.
- Krotka może zawierać dwie, trzy lub więcej wartości.
- Elementy jednej krotki mogą mieć różne typy.
- Składnia krotki w C# wymaga co najmniej dwóch elementów.
- Elementy mogą mieć nazwy albo być dostępne jako `Item1`, `Item2` i kolejne.
- Dekonstrukcja rozdziela elementy krotki do osobnych zmiennych.
- `_` pozwala pominąć niepotrzebny element podczas dekonstrukcji.
- Metoda może zwracać krotkę lub przyjmować krotkę jako argument.
- Krotka dobrze nadaje się do zwracania kilku powiązanych wyników z własnej metody.
- Dla trwałego i rozbudowanego modelu danych lepsza jest klasa lub rekord.

## Ćwiczenia

1. Utwórz krotkę bez nazw zawierającą nazwę miasta i liczbę mieszkańców. Odczytaj dane przez `Item1` i `Item2`.
2. Utwórz nazwaną krotkę przechowującą tytuł książki i liczbę stron. Wypisz oba elementy.
3. Utwórz za pomocą `var` krotkę zawierającą nazwę przedmiotu i ocenę.
4. Utwórz trzyelementową krotkę przechowującą nazwę produktu, cenę i liczbę sztuk.
5. Utwórz krotkę zawierającą imię, nazwisko, wiek i informację typu `bool`, czy uczeń jest pełnoletni.
6. Zmień cenę i liczbę sztuk w krotce opisującej produkt.
7. Wykonaj dekonstrukcję krotki zawierającej tytuł filmu, rok produkcji i ocenę.
8. Wykonaj dekonstrukcję krotki czteroelementowej i pomiń drugi element za pomocą `_`.
9. Napisz metodę zwracającą krotkę zawierającą sumę i iloczyn dwóch liczb.
10. Napisz metodę zwracającą najmniejszą i największą wartość z tablicy bez używania LINQ.
11. Napisz metodę zwracającą liczbę elementów dodatnich, ujemnych i równych zero w tablicy.
12. Napisz metodę przyjmującą krotkę `(string nazwa, double cena)` i wypisującą dane produktu.
13. Wywołaj metodę z poprzedniego ćwiczenia, tworząc krotkę bezpośrednio w liście argumentów.
14. Przepisz własną metodę zwracającą dwa wyniki przez parametry `out` tak, aby zwracała nazwaną krotkę.
15. Dla każdego przykładu wybierz krotkę, tablicę, listę albo klasę i uzasadnij wybór: współrzędne punktu, lista ocen, dane ucznia używane w całym systemie, minimum i maksimum zwracane przez metodę.

## Podsumowanie

Krotki pozwalają połączyć kilka powiązanych wartości, także różnych typów. Mogą mieć dwa, trzy lub więcej elementów.

Nazwane elementy zwiększają czytelność kodu. Dekonstrukcja pozwala rozdzielić krotkę do osobnych zmiennych, a `_` umożliwia pominięcie niepotrzebnego elementu.

Metoda może zwrócić kilka wyników jako krotkę. Krotkę można również przekazać do metody jako jeden argument. W przypadku większych i trwalszych modeli danych lepszym rozwiązaniem jest klasa lub rekord.
