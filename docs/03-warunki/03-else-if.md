# Instrukcja else if - wiele warunków

## Cel lekcji

Nauczysz się używać `else if`, aby sprawdzać kolejne warunki, gdy wcześniejsze warunki nie zostały spełnione.

Po tej lekcji powinieneś umieć:

- zapisać łańcuch `if / else if / else`,
- wyjaśnić, w jakiej kolejności sprawdzane są warunki,
- wskazać pierwszy pasujący blok,
- dobrać kolejność warunków przy progach liczbowych,
- odróżnić kilka osobnych `if` od jednego łańcucha wyboru.

## 1. Krótkie przypomnienie

`if` sprawdza jeden warunek.

`if else` wybiera jedną z dwóch możliwości.

`else if` pozwala sprawdzić kolejne warunki, gdy wcześniejsze warunki były fałszywe.

## 2. Składnia else if

Schemat:

```csharp
if (warunek1)
{
    // instrukcje, gdy warunek1 jest true
}
else if (warunek2)
{
    // instrukcje, gdy warunek1 jest false, a warunek2 jest true
}
else
{
    // instrukcje, gdy żaden wcześniejszy warunek nie był true
}
```

Najważniejsze zasady:

- warunki są sprawdzane od góry do dołu,
- wykonuje się pierwszy blok, którego warunek jest `true`,
- pozostałe bloki są pomijane,
- `else` na końcu jest opcjonalne, ale często przydatne.

## 3. Liczba dodatnia, ujemna albo zero

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę:");
        int liczba = int.Parse(Console.ReadLine());

        if (liczba > 0)
        {
            Console.WriteLine("Liczba jest dodatnia.");
        }
        else if (liczba < 0)
        {
            Console.WriteLine("Liczba jest ujemna.");
        }
        else
        {
            Console.WriteLine("Liczba jest równa zero.");
        }
    }
}
```

Jeśli `liczba > 0`, wykonuje się pierwszy blok.

Jeśli nie, sprawdzany jest kolejny warunek.

Jeśli liczba nie jest ani dodatnia, ani ujemna, zostaje `0`, więc wykonuje się blok `else`.

## 4. Próg punktów

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj liczbę punktów:");
        int punkty = int.Parse(Console.ReadLine());

        if (punkty >= 90)
        {
            Console.WriteLine("Wynik bardzo dobry.");
        }
        else if (punkty >= 75)
        {
            Console.WriteLine("Wynik dobry.");
        }
        else if (punkty >= 50)
        {
            Console.WriteLine("Wynik wystarczający.");
        }
        else
        {
            Console.WriteLine("Wynik niewystarczający.");
        }
    }
}
```

Kolejność warunków ma znaczenie.

Najpierw sprawdzamy najwyższy próg. Gdy `punkty` wynoszą `92`, wykona się tylko pierwszy pasujący blok.

Program nie sprawdza dalej pozostałych `else if` po znalezieniu pasującego warunku.

## 5. Temperatura

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj temperaturę:");
        double temperatura = double.Parse(Console.ReadLine());

        if (temperatura < 0)
        {
            Console.WriteLine("Mróz.");
        }
        else if (temperatura < 15)
        {
            Console.WriteLine("Chłodno.");
        }
        else if (temperatura < 25)
        {
            Console.WriteLine("Ciepło.");
        }
        else
        {
            Console.WriteLine("Gorąco.");
        }
    }
}
```

Warunki są sprawdzane po kolei.

Przy temperaturze `10` pierwszy warunek jest `false`, drugi warunek jest `true`, więc program wypisze `Chłodno.`.

Po wykonaniu drugiego bloku reszta łańcucha jest pomijana.

## 6. Prosty przykład z zakresem i operatorem &&

Operator `&&` oznacza „i”. Oba warunki muszą być `true`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Podaj ocenę:");
        int ocena = int.Parse(Console.ReadLine());

        if (ocena >= 1 && ocena <= 6)
        {
            Console.WriteLine("Ocena mieści się w szkolnym zakresie.");
        }
        else
        {
            Console.WriteLine("Ocena poza zakresem.");
        }
    }
}
```

Ten przykład tylko przypomina operator logiczny. Pełne użycie operatorów logicznych można rozwijać później.

## 7. Proste menu tekstowe

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Wybierz opcję:");
        Console.WriteLine("1 - Start");
        Console.WriteLine("2 - Pomoc");
        Console.WriteLine("3 - Wyjście");

        int opcja = int.Parse(Console.ReadLine());

        if (opcja == 1)
        {
            Console.WriteLine("Wybrano start.");
        }
        else if (opcja == 2)
        {
            Console.WriteLine("Wybrano pomoc.");
        }
        else if (opcja == 3)
        {
            Console.WriteLine("Wybrano wyjście.");
        }
        else
        {
            Console.WriteLine("Nieznana opcja.");
        }
    }
}
```

Do takich wyborów często dobrze pasuje instrukcja `switch`, którą poznamy w kolejnej lekcji.

## 8. Zgadnij, który blok się wykona

Przykład z odpowiedzią:

```csharp
using System;

class Program
{
    static void Main()
    {
        int punkty = 80;

        if (punkty >= 90)
        {
            Console.WriteLine("A");
        }
        else if (punkty >= 75)
        {
            Console.WriteLine("B");
        }
        else if (punkty >= 50)
        {
            Console.WriteLine("C");
        }
        else
        {
            Console.WriteLine("D");
        }
    }
}
```

Odpowiedź: program wypisze `B`, ponieważ `punkty >= 75` jest pierwszym spełnionym warunkiem.

Spróbuj przewidzieć wyniki kolejnych przykładów:

```csharp
using System;

class Program
{
    static void Main()
    {
        int x = 0;

        if (x > 0)
        {
            Console.WriteLine("Dodatnia");
        }
        else if (x < 0)
        {
            Console.WriteLine("Ujemna");
        }
        else
        {
            Console.WriteLine("Zero");
        }

        int temperatura = 20;

        if (temperatura < 0)
        {
            Console.WriteLine("Mróz");
        }
        else if (temperatura < 15)
        {
            Console.WriteLine("Chłodno");
        }
        else if (temperatura < 25)
        {
            Console.WriteLine("Ciepło");
        }
        else
        {
            Console.WriteLine("Gorąco");
        }

        int opcja = 4;

        if (opcja == 1)
        {
            Console.WriteLine("Start");
        }
        else if (opcja == 2)
        {
            Console.WriteLine("Pomoc");
        }
        else if (opcja == 3)
        {
            Console.WriteLine("Wyjście");
        }
        else
        {
            Console.WriteLine("Nieznana opcja");
        }
    }
}
```

Odpowiedzi:

- pierwszy przykład wypisze `Zero`,
- drugi przykład wypisze `Ciepło`,
- trzeci przykład wypisze `Nieznana opcja`.

## 9. Typowe błędy

### Błąd 1 - zła kolejność progów

Niepoprawnie:

```csharp
if (punkty >= 50)
{
    Console.WriteLine("Wynik wystarczający.");
}
else if (punkty >= 75)
{
    Console.WriteLine("Wynik dobry.");
}
else if (punkty >= 90)
{
    Console.WriteLine("Wynik bardzo dobry.");
}
```

Dla punktów `95` pierwszy warunek `punkty >= 50` jest już `true`.

Kolejne warunki nie zostaną sprawdzone.

Dlatego przy progach od góry trzeba zaczynać od najwyższego progu.

Poprawnie:

```csharp
if (punkty >= 90)
{
    Console.WriteLine("Wynik bardzo dobry.");
}
else if (punkty >= 75)
{
    Console.WriteLine("Wynik dobry.");
}
else if (punkty >= 50)
{
    Console.WriteLine("Wynik wystarczający.");
}
else
{
    Console.WriteLine("Wynik niewystarczający.");
}
```

### Błąd 2 - kilka osobnych if zamiast else if

Kilka osobnych `if` oznacza kilka niezależnych sprawdzeń.

```csharp
if (punkty >= 90)
{
    Console.WriteLine("Bardzo dobry.");
}

if (punkty >= 75)
{
    Console.WriteLine("Dobry.");
}

if (punkty >= 50)
{
    Console.WriteLine("Wystarczający.");
}
```

Przy punktach `95` mogą wypisać się wszystkie trzy komunikaty.

Jeśli chcemy wybrać jedną kategorię, stosujemy `if / else if / else`.

### Błąd 3 - else w złym miejscu

`else` odnosi się do najbliższego pasującego `if` albo `else if`.

Dla czytelności zawsze używamy nawiasów klamrowych.

## 10. Zapowiedź kolejnej lekcji

Instrukcja `else if` dobrze nadaje się do wielu warunków.

Gdy sprawdzamy jedną zmienną na kilka konkretnych wartości, wygodna może być instrukcja `switch`, którą poznamy w kolejnej lekcji.

## Zapamiętaj

- `else if` pozwala sprawdzić kolejny warunek.
- Warunki są sprawdzane od góry do dołu.
- Wykonuje się pierwszy pasujący blok.
- Po wykonaniu jednego bloku reszta łańcucha jest pomijana.
- Kolejność warunków ma znaczenie.
- `else` na końcu obsługuje przypadek, gdy żaden warunek nie był `true`.
- Kilka osobnych `if` to nie to samo co `if / else if / else`.

## Ćwiczenia

1. Wczytaj liczbę i wypisz, czy jest dodatnia, ujemna, czy równa zero.
2. Wczytaj liczbę punktów i wypisz kategorię wyniku: bardzo dobry, dobry, wystarczający, niewystarczający.
3. Wczytaj temperaturę i wypisz komunikat: mróz, chłodno, ciepło, gorąco.
4. Wczytaj numer dnia tygodnia od `1` do `7` i wypisz nazwę dnia, używając `if / else if / else`.
5. Wczytaj numer opcji menu i wypisz odpowiedni komunikat.
6. Popraw błędną kolejność progów punktowych.
7. Zamień kilka osobnych `if` na jeden łańcuch `if / else if / else`.
8. Dla podanych wartości przewidź, który blok programu się wykona.
9. Dodaj końcowe `else` obsługujące niepoprawną wartość.
10. Napisz własny przykład wyboru jednej z co najmniej trzech możliwości.
