# Pętla for

## Cel lekcji

Nauczysz się używać pętli `for`, gdy z góry znasz liczbę powtórzeń albo chcesz sterować pętlą za pomocą licznika.

## Krótkie przypomnienie pętli

Pętla `while` działa dopóki warunek ma wartość `true`.

Pętla `do while` wykonuje blok instrukcji co najmniej raz, a dopiero potem sprawdza warunek.

Pętla `for` jest szczególnie wygodna wtedy, gdy znamy liczbę powtórzeń. Często używa licznika, który zwiększa się lub zmniejsza po każdym obiegu pętli.

## Składnia pętli for

Ogólny schemat pętli `for` wygląda tak:

```csharp
for (inicjalizacja; warunek; zmiana)
{
    // instrukcje wykonywane w pętli
}
```

Nagłówek pętli `for` ma trzy części:

- inicjalizacja wykonuje się raz na początku,
- warunek jest sprawdzany przed każdym obiegiem pętli,
- zmiana licznika wykonuje się po wykonaniu bloku pętli.

Jeżeli warunek ma wartość `true`, blok pętli się wykonuje. Po wykonaniu bloku program zmienia licznik i ponownie sprawdza warunek.

Typowy zapis:

```csharp
for (int i = 1; i <= 5; i++)
{
    Console.WriteLine(i);
}
```

W tym zapisie:

- `int i = 1` oznacza start licznika,
- `i <= 5` oznacza warunek działania pętli,
- `i++` oznacza zwiększenie licznika o `1` po każdym obiegu.

## Pierwszy przykład: liczby od 1 do 5

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine(i);
        }
    }
}
```

Pętla zaczyna od `i = 1`. Działa dopóki `i <= 5`. Po każdym wykonaniu bloku zmienna `i` zwiększa się o `1`.

Program wypisze:

```csharp
1
2
3
4
5
```

## Przykład: liczby od 0 do 4

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

Ten zapis jest bardzo częsty w programowaniu.

Licznik zaczyna od `0`. Warunek `i < 5` daje wartości `0`, `1`, `2`, `3`, `4`.

Taki sposób przyda się później przy tablicach, gdzie indeksy zaczynają się od `0`. Na razie wystarczy zapamiętać sam schemat.

## Przykład: odliczanie w dół

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 5; i >= 1; i--)
        {
            Console.WriteLine(i);
        }
    }
}
```

W tym przykładzie:

- licznik zaczyna od `5`,
- pętla działa dopóki `i >= 1`,
- `i--` zmniejsza licznik o `1`,
- program wypisze `5`, `4`, `3`, `2`, `1`.

## Przykład: liczby parzyste

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int i = 2; i <= 10; i += 2)
        {
            Console.WriteLine(i);
        }
    }
}
```

Instrukcja `i += 2` zwiększa licznik o `2`. Dlatego program wypisze liczby `2`, `4`, `6`, `8`, `10`.

## Wyjaśnienie metodą Feynmana

Wyobraź sobie, że nauczyciel mówi:

Rozwiąż zadania od 1 do 10. Po każdym zadaniu przejdź do następnego numeru. Zatrzymaj się po zadaniu 10.

To jest właśnie pętla `for`:

- ustawiamy licznik,
- sprawdzamy, czy licznik nadal mieści się w zakresie,
- wykonujemy instrukcje,
- zwiększamy licznik.

```csharp
using System;

class Program
{
    static void Main()
    {
        for (int numerZadania = 1; numerZadania <= 10; numerZadania++)
        {
            Console.WriteLine($"Rozwiązuję zadanie numer {numerZadania}");
        }
    }
}
```

W tym przykładzie:

- `int numerZadania = 1` oznacza, od czego zaczynamy,
- `numerZadania <= 10` oznacza, że pętla działa dopóki warunek jest prawdziwy,
- `numerZadania++` oznacza przejście do następnego numeru po każdym obiegu.

Proste porównanie:

- `while`: najpierw sprawdzam, czy mam coś robić,
- `do while`: robię raz, potem pytam, czy powtórzyć,
- `for`: mam licznik i wykonuję zadanie określoną liczbę razy.

## Przykład: suma liczb od 1 do 10

```csharp
using System;

class Program
{
    static void Main()
    {
        int suma = 0;

        for (int i = 1; i <= 10; i++)
        {
            suma += i;
        }

        Console.WriteLine($"Suma liczb od 1 do 10 wynosi: {suma}");
    }
}
```

W tym programie:

- `suma` zaczyna od `0`,
- w każdym obiegu dodajemy aktualną wartość `i`,
- `suma += i` oznacza: dodaj `i` do zmiennej `suma`,
- `suma` jest przykładem akumulatora, czyli zmiennej zbierającej wynik.

## Przykład: wczytanie 5 liczb i obliczenie sumy

```csharp
using System;

class Program
{
    static void Main()
    {
        int suma = 0;

        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine($"Podaj liczbę {i}:");
            int liczba = int.Parse(Console.ReadLine());

            suma += liczba;
        }

        Console.WriteLine($"Suma podanych liczb: {suma}");
    }
}
```

Pętla wykona się dokładnie `5` razy. Za każdym razem użytkownik poda jedną liczbę.

Zmienna `i` służy jako numer kolejnego powtórzenia. Zmienna `suma` przechowuje narastający wynik.

## Przykład: średnia z kilku liczb

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczbaOcen = 3;
        double suma = 0;

        for (int i = 1; i <= liczbaOcen; i++)
        {
            Console.WriteLine($"Podaj ocenę {i}:");
            double ocena = double.Parse(Console.ReadLine());

            suma += ocena;
        }

        double srednia = suma / liczbaOcen;

        Console.WriteLine($"Średnia: {srednia:F2}");
    }
}
```

W tym przykładzie:

- `liczbaOcen` określa, ile razy pętla ma się wykonać,
- `suma` przechowuje sumę ocen,
- średnia to suma podzielona przez liczbę ocen,
- `{srednia:F2}` wypisuje wynik z dwoma miejscami po przecinku.

## Zgadnij, ile razy wykona się pętla

Przykład z odpowiedzią:

```csharp
for (int i = 1; i <= 3; i++)
{
    Console.WriteLine(i);
}
```

Odpowiedź: pętla wykona się 3 razy i wypisze `1`, `2`, `3`.

Spróbuj najpierw samodzielnie przewidzieć wyniki kolejnych przykładów.

```csharp
for (int i = 0; i < 4; i++)
{
    Console.WriteLine(i);
}
```

```csharp
for (int i = 5; i >= 1; i--)
{
    Console.WriteLine(i);
}
```

```csharp
for (int i = 2; i <= 10; i += 2)
{
    Console.WriteLine(i);
}
```

```csharp
for (int i = 10; i < 5; i++)
{
    Console.WriteLine(i);
}
```

Odpowiedzi:

- pierwszy przykład wykona się 4 razy i wypisze `0`, `1`, `2`, `3`,
- drugi przykład wykona się 5 razy i wypisze `5`, `4`, `3`, `2`, `1`,
- trzeci przykład wykona się 5 razy i wypisze `2`, `4`, `6`, `8`, `10`,
- czwarty przykład nie wykona się ani razu.

## Porównanie for i while

Pętlę `for` wybieramy zwykle wtedy, gdy:

- znamy liczbę powtórzeń,
- potrzebujemy licznika,
- chcemy przejść przez kolejne numery,
- później będziemy przechodzić po elementach tablicy.

Pętlę `while` wybieramy zwykle wtedy, gdy:

- nie wiemy z góry, ile razy pętla ma się wykonać,
- czekamy na spełnienie warunku,
- powtarzamy działanie do momentu zmiany sytuacji.

Przykłady:

- wypisz liczby od `1` do `10` - `for`,
- pytaj użytkownika, dopóki nie wpisze `0` - `while` albo `do while`.

## Typowe błędy

### Błąd 1: zły warunek końcowy

Przykład:

```csharp
for (int i = 1; i < 5; i++)
{
    Console.WriteLine(i);
}
```

Ta pętla wypisze `1`, `2`, `3`, `4`. Nie wypisze `5`.

Jeśli chcemy wypisać liczby od `1` do `5`, warunek powinien być `i <= 5`.

Poprawnie:

```csharp
for (int i = 1; i <= 5; i++)
{
    Console.WriteLine(i);
}
```

### Błąd 2: brak zmiany licznika w dobrą stronę

Niepoprawnie:

```csharp
for (int i = 1; i <= 5; i--)
{
    Console.WriteLine(i);
}
```

Zmienna `i` zmniejsza się zamiast zwiększać. Warunek `i <= 5` może pozostawać prawdziwy, więc może powstać pętla nieskończona.

### Błąd 3: średnik po for

Niepoprawnie:

```csharp
for (int i = 1; i <= 5; i++);
{
    Console.WriteLine("To nie jest poprawny zapis pętli.");
}
```

Średnik po nagłówku `for` kończy pustą instrukcję pętli. Blok poniżej nie działa wtedy tak, jak uczeń zwykle oczekuje.

W tym kursie nie stawiamy średnika po nagłówku `for`.

### Błąd 4: mylenie < i <=

Warunek `i < 5` oznacza wartości mniejsze niż `5`.

Warunek `i <= 5` oznacza wartości mniejsze lub równe `5`.

Ta różnica często decyduje o liczbie powtórzeń pętli.

### Błąd 5: za długa lub nieczytelna pętla

Pętla powinna mieć czytelny licznik. Ciało pętli powinno być poprawnie wcięte.

Jeśli w pętli dzieje się zbyt dużo rzeczy, kod staje się trudniejszy do czytania.

## Zapowiedź kolejnej lekcji

Pętla `for` porządkuje powtarzanie instrukcji z licznikiem. W kolejnych lekcjach uporządkujemy pojęcia licznika i akumulatora, a później omówimy `break` i `continue`.

Przy tablicach pojawi się też pętla `foreach`, ale na razie nie jest potrzebna.

## Zapamiętaj

- `for` jest wygodny, gdy znamy liczbę powtórzeń.
- Nagłówek `for` ma trzy części: inicjalizację, warunek i zmianę.
- Licznik często nazywa się `i`.
- `i++` zwiększa licznik o `1`.
- `i--` zmniejsza licznik o `1`.
- `i += 2` zwiększa licznik o `2`.
- Warunek decyduje, czy pętla wykona kolejny obieg.
- Trzeba uważać na różnicę między `<` i `<=`.
- Nie stawiamy średnika po nagłówku `for`.

## Ćwiczenia

1. Wypisz liczby od `1` do `10` za pomocą `for`.
2. Wypisz liczby od `10` do `1` za pomocą `for`.
3. Wypisz liczby parzyste od `2` do `20`.
4. Wypisz liczby nieparzyste od `1` do `19`.
5. Oblicz sumę liczb od `1` do `100`.
6. Wczytaj `5` liczb i oblicz ich sumę.
7. Wczytaj `4` oceny i oblicz średnią.
8. Sprawdź, ile razy wykona się podana pętla.
9. Popraw pętlę z błędnym warunkiem `<` zamiast `<=`.
10. Popraw pętlę, w której licznik zmienia się w złą stronę.
11. Napisz pętlę, która wypisze: `3`, `6`, `9`, `12`, `15`.
12. Napisz własny przykład pętli `for` z licznikiem.
