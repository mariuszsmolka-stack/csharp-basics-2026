# Licznik i akumulator

## Cel lekcji

Nauczysz się rozróżniać licznik i akumulator oraz używać ich w prostych zadaniach z pętlami.

## Krótkie wprowadzenie

W pętlach często potrzebujemy czegoś więcej niż samo powtarzanie instrukcji.

Czasem chcemy policzyć, ile razy coś się zdarzyło. Czasem chcemy zgromadzić wynik, na przykład sumę liczb.

Do takich zadań służą licznik i akumulator.

## Licznik

Licznik to zmienna, która zwykle zwiększa się o `1`, aby policzyć liczbę wystąpień, powtórzeń albo elementów spełniających warunek.

Przykład prostego licznika:

```csharp
using System;

class Program
{
    static void Main()
    {
        int licznik = 0;

        for (int i = 1; i <= 5; i++)
        {
            licznik++;
        }

        Console.WriteLine($"Liczba powtórzeń: {licznik}");
    }
}
```

W tym przykładzie:

- `licznik` zaczyna od `0`,
- `licznik++` zwiększa jego wartość o `1`,
- po pięciu powtórzeniach `licznik` ma wartość `5`.

## Akumulator

Akumulator to zmienna, która gromadzi wynik, najczęściej sumę. Do akumulatora dodajemy kolejne wartości.

Przykład akumulatora:

```csharp
using System;

class Program
{
    static void Main()
    {
        int suma = 0;

        for (int i = 1; i <= 5; i++)
        {
            suma += i;
        }

        Console.WriteLine($"Suma: {suma}");
    }
}
```

W tym przykładzie:

- `suma` zaczyna od `0`,
- `suma += i` oznacza dodanie aktualnej wartości `i` do sumy,
- po zakończeniu pętli zmienna `suma` przechowuje wynik.

## Licznik a akumulator: różnica

| Pojęcie | Do czego służy | Typowa operacja | Przykład |
| --- | --- | --- | --- |
| Licznik | liczy wystąpienia | `licznik++` | liczba liczb parzystych |
| Akumulator | gromadzi wynik | `suma += liczba` | suma podanych liczb |

Licznik najczęściej zwiększamy o `1`. Akumulator zwiększamy o wartość, którą chcemy dodać do wyniku.

Nazwa zmiennej powinna pokazywać jej rolę, na przykład `liczbaParzystych` albo `sumaPunktow`.

## Przykład: zliczanie liczb parzystych

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczbaParzystych = 0;

        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine($"Podaj liczbę {i}:");
            int liczba = int.Parse(Console.ReadLine());

            if (liczba % 2 == 0)
            {
                liczbaParzystych++;
            }
        }

        Console.WriteLine($"Liczb parzystych: {liczbaParzystych}");
    }
}
```

W tym programie:

- `liczbaParzystych` jest licznikiem,
- zwiększamy ją tylko wtedy, gdy liczba jest parzysta,
- warunek `liczba % 2 == 0` sprawdza parzystość.

## Przykład: suma podanych liczb

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

        Console.WriteLine($"Suma: {suma}");
    }
}
```

W tym programie:

- `suma` jest akumulatorem,
- każda podana liczba jest dodawana do sumy,
- po zakończeniu pętli mamy łączny wynik.

## Przykład: suma i średnia

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczbaOcen = 4;
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

- `suma` jest akumulatorem,
- `liczbaOcen` mówi, przez ile dzielimy sumę,
- średnia to suma podzielona przez liczbę wartości.

## Przykład: licznik i akumulator razem

```csharp
using System;

class Program
{
    static void Main()
    {
        int liczbaDodatnich = 0;
        int sumaDodatnich = 0;

        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine($"Podaj liczbę {i}:");
            int liczba = int.Parse(Console.ReadLine());

            if (liczba > 0)
            {
                liczbaDodatnich++;
                sumaDodatnich += liczba;
            }
        }

        Console.WriteLine($"Liczb dodatnich: {liczbaDodatnich}");
        Console.WriteLine($"Suma dodatnich: {sumaDodatnich}");
    }
}
```

W tym programie:

- `liczbaDodatnich` jest licznikiem,
- `sumaDodatnich` jest akumulatorem,
- obie zmienne są aktualizowane tylko dla liczb dodatnich.

## Wyjaśnienie metodą Feynmana

Wyobraź sobie, że sprawdzasz kartkówki.

Masz dwa pudełka:

- pierwsze pudełko służy do liczenia, ile prac już sprawdziłeś,
- drugie pudełko służy do zbierania punktów ze wszystkich prac.

Pierwsze pudełko to licznik. Po każdej pracy zwiększasz go o `1`.

Drugie pudełko to akumulator. Do niego dodajesz liczbę punktów z kolejnej pracy.

W programie:

- `licznik++` oznacza: policz jeszcze jeden element,
- `suma += punkty` oznacza: dodaj punkty do łącznej sumy.

## Typowe wartości początkowe

Licznik zwykle zaczyna od `0`.

Suma zwykle zaczyna od `0`.

Dla średniej najpierw liczymy sumę, a potem dzielimy ją przez liczbę elementów.

Jeśli liczymy tylko elementy spełniające warunek, zwiększamy licznik wewnątrz instrukcji `if`.

```csharp
int liczbaParzystych = 0;
int suma = 0;
```

## Typowe błędy

### Błąd 1: brak wartości początkowej

Licznik i akumulator trzeba poprawnie zainicjalizować. Najczęściej zaczynamy od `0`.

### Błąd 2: zwiększanie licznika w złym miejscu

Jeśli licznik liczb parzystych zwiększamy poza `if`, policzymy wszystkie liczby, a nie tylko parzyste.

Niepoprawnie:

```csharp
if (liczba % 2 == 0)
{
    Console.WriteLine("Parzysta");
}

liczbaParzystych++;
```

Poprawnie:

```csharp
if (liczba % 2 == 0)
{
    liczbaParzystych++;
}
```

### Błąd 3: mylenie licznika z akumulatorem

Licznik zwykle zwiększamy o `1`.

Akumulator zwiększamy o wartość, na przykład:

```csharp
suma += liczba;
```

### Błąd 4: dzielenie przez zły licznik przy średniej

Jeśli średnia dotyczy wszystkich liczb, dzielimy przez liczbę wszystkich liczb.

Jeśli średnia dotyczy tylko liczb dodatnich, dzielimy przez liczbę dodatnich.

Trzeba uważać, żeby licznik nie był równy `0`. Pełne zabezpieczanie takiej sytuacji omówimy później.

## Zgadnij, co będzie wynikiem

Przykład z odpowiedzią:

```csharp
int licznik = 0;

for (int i = 1; i <= 3; i++)
{
    licznik++;
}

Console.WriteLine(licznik);
```

Odpowiedź: program wypisze `3`.

Spróbuj najpierw samodzielnie przewidzieć wyniki kolejnych przykładów.

```csharp
int suma = 0;

for (int i = 1; i <= 4; i++)
{
    suma += i;
}

Console.WriteLine(suma);
```

```csharp
int liczbaParzystych = 0;

for (int i = 1; i <= 6; i++)
{
    if (i % 2 == 0)
    {
        liczbaParzystych++;
    }
}

Console.WriteLine(liczbaParzystych);
```

```csharp
int suma = 0;
int licznik = 0;

for (int i = 1; i <= 5; i++)
{
    if (i > 2)
    {
        suma += i;
        licznik++;
    }
}

Console.WriteLine(suma);
Console.WriteLine(licznik);
```

Odpowiedzi:

- pierwszy przykład wypisze `10`,
- drugi przykład wypisze `3`,
- trzeci przykład wypisze `12` i `3`.

## Zapowiedź kolejnej lekcji

Licznik i akumulator bardzo często pojawiają się w zadaniach egzaminacyjnych i prostych algorytmach. W kolejnej lekcji omówimy instrukcje `break` i `continue`, które pozwalają sterować przebiegiem pętli.

## Zapamiętaj

- Licznik służy do zliczania.
- Akumulator służy do gromadzenia wyniku.
- Licznik zwykle zwiększamy przez `licznik++`.
- Akumulator zwykle zwiększamy przez `suma += wartość`.
- Licznik i akumulator zwykle zaczynają od `0`.
- Miejsce aktualizacji licznika ma znaczenie.
- Średnia wymaga sumy i liczby elementów.

## Ćwiczenia

1. Wczytaj `5` liczb i policz, ile z nich jest parzystych.
2. Wczytaj `5` liczb i policz, ile z nich jest dodatnich.
3. Wczytaj `5` liczb i oblicz ich sumę.
4. Wczytaj `4` oceny i oblicz średnią.
5. Wczytaj `6` liczb i oblicz sumę tylko liczb dodatnich.
6. Wczytaj `6` liczb i policz liczby ujemne.
7. Wczytaj `5` liczb i policz liczby podzielne przez `3`.
8. Popraw program, w którym licznik jest zwiększany w złym miejscu.
9. Wskaż, która zmienna jest licznikiem, a która akumulatorem.
10. Napisz własny przykład z licznikiem i akumulatorem.
