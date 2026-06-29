# Suma i średnia elementów tablicy

## Cel lekcji

Nauczysz się obliczać sumę elementów tablicy oraz średnią na podstawie sumy i liczby elementów.

## Krótkie przypomnienie

Tablica przechowuje wiele wartości.

Pętla `for` pozwala przejść po wszystkich elementach tablicy.

Akumulator pozwala gromadzić wynik.

Do sumowania elementów tablicy używamy zwykle zmiennej `suma`.

## Suma elementów tablicy

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = { 4, 7, 2, 9 };

        int suma = 0;

        for (int i = 0; i < liczby.Length; i++)
        {
            suma += liczby[i];
        }

        Console.WriteLine($"Suma: {suma}");
    }
}
```

W tym przykładzie:

- `suma` zaczyna od `0`,
- pętla przechodzi po indeksach `0`, `1`, `2`, `3`,
- `liczby[i]` oznacza aktualny element tablicy,
- `suma += liczby[i]` dodaje aktualny element do sumy,
- po zakończeniu pętli `suma` zawiera sumę wszystkich elementów.

## Przebieg działania krok po kroku

Dla tablicy:

```csharp
int[] liczby = { 4, 7, 2, 9 };
```

akumulator zmienia się tak:

| i | liczby[i] | suma po dodaniu |
| --- | --- | --- |
| `0` | `4` | `4` |
| `1` | `7` | `11` |
| `2` | `2` | `13` |
| `3` | `9` | `22` |

Tabela pokazuje, jak akumulator zmienia się w kolejnych obiegach pętli.

Ostateczna suma wynosi `22`.

## Średnia elementów tablicy

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] oceny = { 5, 4, 3, 5 };

        int suma = 0;

        for (int i = 0; i < oceny.Length; i++)
        {
            suma += oceny[i];
        }

        double srednia = (double)suma / oceny.Length;

        Console.WriteLine($"Suma ocen: {suma}");
        Console.WriteLine($"Średnia ocen: {srednia:F2}");
    }
}
```

Średnia to suma podzielona przez liczbę elementów.

Liczbę elementów pobieramy z `oceny.Length`.

Użycie `(double)suma` wymusza dzielenie rzeczywiste. Bez tego moglibyśmy otrzymać dzielenie całkowite.

Zapis `{srednia:F2}` wypisuje wynik z dwoma miejscami po przecinku.

## Dlaczego używamy Length

Nie wpisujemy na sztywno liczby elementów, jeśli można użyć `tablica.Length`.

Dzięki temu kod łatwiej poprawić, gdy zmieni się rozmiar tablicy.

Jeśli tablica ma `4` elementy, `Length` wynosi `4`. Jeśli później dodamy elementy, pętla nadal może działać poprawnie.

Lepszy zapis:

```csharp
for (int i = 0; i < oceny.Length; i++)
{
    suma += oceny[i];
}
```

Słabszy zapis:

```csharp
for (int i = 0; i < 4; i++)
{
    suma += oceny[i];
}
```

Liczba `4` działa tylko dla konkretnej tablicy. `Length` jest bezpieczniejsze i bardziej uniwersalne.

## Wczytywanie liczb do tablicy i obliczanie średniej

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] liczby = new int[5];

        for (int i = 0; i < liczby.Length; i++)
        {
            Console.WriteLine($"Podaj liczbę numer {i + 1}:");
            liczby[i] = int.Parse(Console.ReadLine());
        }

        int suma = 0;

        for (int i = 0; i < liczby.Length; i++)
        {
            suma += liczby[i];
        }

        double srednia = (double)suma / liczby.Length;

        Console.WriteLine($"Suma: {suma}");
        Console.WriteLine($"Średnia: {srednia:F2}");
    }
}
```

Pierwsza pętla wczytuje dane do tablicy.

Druga pętla oblicza sumę.

Średnia powstaje po zakończeniu sumowania.

`i + 1` służy tylko do czytelnej numeracji dla użytkownika.

## Suma i średnia liczb rzeczywistych

```csharp
using System;

class Program
{
    static void Main()
    {
        double[] temperatury = { 21.5, 22.0, 19.8, 20.7 };

        double suma = 0;

        for (int i = 0; i < temperatury.Length; i++)
        {
            suma += temperatury[i];
        }

        double srednia = suma / temperatury.Length;

        Console.WriteLine($"Średnia temperatura: {srednia:F2}");
    }
}
```

Dla tablicy `double[]` zmienna `suma` też powinna być typu `double`.

Nie trzeba tu rzutować sumy na `double`, bo `suma` już jest typu `double`.

## Wyjaśnienie metodą Feynmana

Wyobraź sobie, że masz kilka kartek z punktami uczniów: `4`, `7`, `2`, `9`.

Chcesz policzyć sumę.

Bierzesz pustą kartkę z napisem `suma = 0`.

Potem przechodzisz po kolei po każdej kartce:

- dodajesz `4`,
- potem dodajesz `7`,
- potem dodajesz `2`,
- potem dodajesz `9`.

Na końcu na kartce masz wynik `22`.

W programie ta kartka to zmienna `suma`.

Przechodzenie po kartkach to pętla `for`.

Aktualna kartka to `liczby[i]`.

Średnia to następny krok: bierzesz sumę i dzielisz przez liczbę kartek.

## Typowe błędy

### Błąd 1: brak wyzerowania sumy przed pętlą

`suma` powinna zwykle zaczynać od `0`.

Jeśli `suma` ma wcześniejszą wartość, wynik będzie błędny.

Poprawnie:

```csharp
int suma = 0;
```

### Błąd 2: dzielenie całkowite przy średniej

Niepoprawnie:

```csharp
int suma = 17;
int liczbaElementow = 4;

double srednia = suma / liczbaElementow;
```

`suma` i `liczbaElementow` są typu `int`. Wynik dzielenia może zostać policzony jako liczba całkowita, a część po przecinku zostanie utracona.

Poprawnie:

```csharp
double srednia = (double)suma / liczbaElementow;
```

### Błąd 3: użycie złej liczby elementów

Zamiast wpisywać ręcznie liczbę elementów, lepiej użyć `tablica.Length`.

Wtedy kod jest mniej podatny na błędy.

### Błąd 4: obliczanie średniej w złym miejscu

Sumę liczymy w pętli.

Średnią najczęściej obliczamy po zakończeniu pętli, gdy mamy już pełną sumę.

### Błąd 5: pomylenie indeksu z wartością

`i` to indeks.

`liczby[i]` to wartość elementu.

Do sumy dodajemy `liczby[i]`, a nie samo `i`, jeśli chcemy sumować elementy tablicy.

## Zgadnij, jaki będzie wynik

Przykład z odpowiedzią:

```csharp
int[] liczby = { 2, 4, 6 };
int suma = 0;

for (int i = 0; i < liczby.Length; i++)
{
    suma += liczby[i];
}

Console.WriteLine(suma);
```

Odpowiedź: program wypisze `12`.

Spróbuj najpierw samodzielnie przewidzieć wyniki kolejnych przykładów.

```csharp
int[] liczby = { 1, 3, 5, 7 };
int suma = 0;

for (int i = 0; i < liczby.Length; i++)
{
    suma += liczby[i];
}

Console.WriteLine(suma);
```

```csharp
int[] punkty = { 10, 20, 30 };
int suma = 0;

for (int i = 0; i < punkty.Length; i++)
{
    suma += punkty[i];
}

double srednia = (double)suma / punkty.Length;

Console.WriteLine(srednia);
```

```csharp
double[] temperatury = { 20.5, 21.5 };
double suma = 0;

for (int i = 0; i < temperatury.Length; i++)
{
    suma += temperatury[i];
}

Console.WriteLine(suma);
```

Odpowiedzi:

- pierwszy przykład wypisze `16`,
- drugi przykład wypisze `20`,
- trzeci przykład wypisze `42`.

## Zapowiedź kolejnej lekcji

Suma i średnia to jedne z najczęstszych operacji na tablicach.

W kolejnej lekcji użyjemy pętli do znalezienia najmniejszego i największego elementu tablicy.

## Zapamiętaj

- Suma elementów tablicy wymaga akumulatora.
- Akumulator zwykle zaczyna od `0`.
- W pętli dodajemy do sumy `tablica[i]`.
- `Length` oznacza liczbę elementów.
- Średnia to suma podzielona przez liczbę elementów.
- Przy średniej z liczb całkowitych warto wymusić dzielenie rzeczywiste przez `(double)`.
- `{wynik:F2}` pozwala wypisać wynik z dwoma miejscami po przecinku.

## Ćwiczenia

1. Utwórz tablicę pięciu liczb i oblicz ich sumę.
2. Utwórz tablicę pięciu liczb i oblicz ich średnią.
3. Wczytaj `5` liczb do tablicy i oblicz ich sumę.
4. Wczytaj `5` liczb do tablicy i oblicz średnią.
5. Utwórz tablicę ocen typu `int[]` i oblicz średnią ocen.
6. Utwórz tablicę temperatur typu `double[]` i oblicz średnią temperaturę.
7. Popraw program, który dzieli dwie liczby `int` i traci część po przecinku.
8. Popraw program, który dodaje do sumy `i` zamiast `tablica[i]`.
9. Sprawdź, co się stanie, gdy zmienisz liczbę elementów tablicy, ale używasz `Length`.
10. Napisz własny przykład sumowania elementów tablicy.
