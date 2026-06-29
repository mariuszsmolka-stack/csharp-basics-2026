# Pętla do while

## Cel lekcji

Nauczysz się używać pętli `do while` i rozpoznawać sytuacje, w których kod powinien wykonać się co najmniej raz.

## Przypomnienie pętli while

Pętla `while` sprawdza warunek przed pierwszym wykonaniem instrukcji.

Jeżeli warunek od razu jest fałszywy, instrukcje w pętli nie wykonają się ani razu.

Czasami chcemy, aby program najpierw coś zrobił, a dopiero potem zapytał, czy ma powtórzyć działanie. Do takich sytuacji pasuje pętla `do while`.

## Składnia pętli do while

```csharp
do
{
    // instrukcje wykonywane co najmniej raz
}
while (warunek);
```

W pętli `do while` najpierw wykonuje się blok instrukcji zapisany po `do`. Dopiero potem program sprawdza warunek w nawiasie przy `while`.

Jeżeli warunek ma wartość `true`, pętla wykona się ponownie. Jeżeli warunek ma wartość `false`, pętla zakończy działanie.

Ważne: po warunku w pętli `do while` stawiamy średnik:

```csharp
while (warunek);
```

To różni się od zwykłej pętli `while`, w której po warunku nie stawiamy średnika.

## Przykład: liczby od 1 do 5

```csharp
using System;

class Program
{
    static void Main()
    {
        int licznik = 1;

        do
        {
            Console.WriteLine(licznik);
            licznik++;
        }
        while (licznik <= 5);
    }
}
```

W tym przykładzie:

- zmienna `licznik` zaczyna od wartości `1`,
- program wypisuje wartość zmiennej `licznik`,
- instrukcja `licznik++` zwiększa licznik o `1`,
- pętla powtarza się tak długo, jak `licznik <= 5`.

Program wypisze:

```csharp
1
2
3
4
5
```

## Warunek fałszywy od początku

Pętla `do while` wykona się przynajmniej raz, nawet wtedy, gdy warunek jest fałszywy już na początku.

```csharp
using System;

class Program
{
    static void Main()
    {
        int licznik = 10;

        do
        {
            Console.WriteLine(licznik);
            licznik++;
        }
        while (licznik <= 5);

        Console.WriteLine("Koniec programu.");
    }
}
```

Warunek `licznik <= 5` jest fałszywy, bo `licznik` ma wartość `10`. Mimo to program najpierw wykona blok po `do`, czyli wypisze `10`. Dopiero potem sprawdzi warunek i zakończy pętlę.

## while a do while

Najważniejsza różnica:

- `while` sprawdza warunek przed wykonaniem bloku,
- `while` może nie wykonać się ani razu,
- `do while` wykonuje blok przed sprawdzeniem warunku,
- `do while` wykonuje się co najmniej raz.

Porównaj dwa fragmenty:

```csharp
using System;

class Program
{
    static void Main()
    {
        int x = 10;

        while (x < 5)
        {
            Console.WriteLine("while");
        }

        do
        {
            Console.WriteLine("do while");
        }
        while (x < 5);
    }
}
```

Napis `"while"` nie zostanie wypisany, ponieważ warunek `x < 5` jest fałszywy już przed wejściem do pętli.

Napis `"do while"` zostanie wypisany jeden raz, ponieważ pętla `do while` najpierw wykonuje blok, a dopiero potem sprawdza warunek.

## Wyjaśnienie metodą Feynmana

Wyobraź sobie nauczyciela, który mówi:

Najpierw rozwiąż jedno zadanie. Potem zapytam, czy chcesz rozwiązać kolejne.

Tak działa `do while`: najpierw wykonuje działanie, potem pyta o dalsze powtarzanie.

Zwykłe `while` działa inaczej: najpierw pyta, czy można zacząć, a dopiero potem wykonuje działanie.

```csharp
using System;

class Program
{
    static void Main()
    {
        string czyPowtorzyc;

        do
        {
            Console.WriteLine("Wykonuję zadanie.");
            Console.WriteLine("Czy powtórzyć? tak/nie");
            czyPowtorzyc = Console.ReadLine();
        }
        while (czyPowtorzyc == "tak");
    }
}
```

Ten program wykona zadanie co najmniej raz. Jeżeli użytkownik wpisze `tak`, program powtórzy działanie.

## Proste menu konsolowe

Pętla `do while` często pasuje do menu, ponieważ menu powinno pokazać się użytkownikowi przynajmniej raz.

```csharp
using System;

class Program
{
    static void Main()
    {
        int opcja;

        do
        {
            Console.WriteLine("Menu:");
            Console.WriteLine("1 - Start");
            Console.WriteLine("2 - Pomoc");
            Console.WriteLine("0 - Wyjście");
            Console.WriteLine("Wybierz opcję:");

            opcja = int.Parse(Console.ReadLine());

            if (opcja == 1)
            {
                Console.WriteLine("Wybrano start.");
            }
            else if (opcja == 2)
            {
                Console.WriteLine("Wybrano pomoc.");
            }
            else if (opcja == 0)
            {
                Console.WriteLine("Koniec programu.");
            }
            else
            {
                Console.WriteLine("Nieznana opcja.");
            }
        }
        while (opcja != 0);
    }
}
```

W tym programie menu pokazuje się co najmniej raz. Pętla powtarza się tak długo, jak użytkownik nie wybierze opcji `0`.

## Powtarzanie prostego obliczenia

Pętla `do while` może służyć do powtarzania prostych działań.

```csharp
using System;

class Program
{
    static void Main()
    {
        string decyzja;

        do
        {
            Console.WriteLine("Podaj pierwszą liczbę:");
            int pierwszaLiczba = int.Parse(Console.ReadLine());

            Console.WriteLine("Podaj drugą liczbę:");
            int drugaLiczba = int.Parse(Console.ReadLine());

            int suma = pierwszaLiczba + drugaLiczba;

            Console.WriteLine("Suma: " + suma);
            Console.WriteLine("Czy chcesz wykonać obliczenie ponownie? tak/nie");
            decyzja = Console.ReadLine();
        }
        while (decyzja == "tak");
    }
}
```

Porównanie `decyzja == "tak"` jest dokładne. Na tym etapie kursu przyjmujemy, że użytkownik wpisuje dokładnie `tak`. Tekst `"Tak"` nie jest tym samym co `"tak"`.

## Ile razy wykona się pętla?

Przykład z odpowiedzią:

```csharp
using System;

class Program
{
    static void Main()
    {
        int i = 1;

        do
        {
            Console.WriteLine(i);
            i++;
        }
        while (i <= 3);
    }
}
```

Ta pętla wykona się 3 razy i wypisze:

```csharp
1
2
3
```

Spróbuj najpierw samodzielnie przewidzieć wyniki kolejnych przykładów.

```csharp
int a = 10;

do
{
    Console.WriteLine(a);
    a++;
}
while (a < 5);
```

```csharp
int b = 3;

do
{
    Console.WriteLine(b);
    b--;
}
while (b > 0);
```

```csharp
int c = 0;

do
{
    Console.WriteLine(c);
    c++;
}
while (c < 4);
```

Odpowiedzi:

- pierwszy przykład wykona się 1 raz i wypisze `10`,
- drugi przykład wykona się 3 razy i wypisze `3`, `2`, `1`,
- trzeci przykład wykona się 4 razy i wypisze `0`, `1`, `2`, `3`.

## Typowe błędy

### Brak zmiany zmiennej sterującej

Gorszy przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        int licznik = 1;

        do
        {
            Console.WriteLine(licznik);
        }
        while (licznik <= 5);
    }
}
```

Wartość zmiennej `licznik` się nie zmienia, więc warunek cały czas pozostaje prawdziwy. Taka pętla może działać bez końca.

Lepszy przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        int licznik = 1;

        do
        {
            Console.WriteLine(licznik);
            licznik++;
        }
        while (licznik <= 5);
    }
}
```

### Brak średnika po while

Gorszy przykład:

```csharp
do
{
    Console.WriteLine("Test");
}
while (true)
```

Poprawny przykład:

```csharp
do
{
    Console.WriteLine("Test");
}
while (true);
```

W pętli `do while` średnik po warunku jest wymagany.

### Mylenie while i do while

Pętla `while` może nie wykonać się ani razu. Pętla `do while` wykona się co najmniej raz.

Dlatego `do while` jest wygodna na przykład przy menu lub pytaniu użytkownika, czy chce powtórzyć działanie.

### Zmienna zadeklarowana w złym miejscu

Jeżeli zmienna jest używana w warunku po bloku `do`, trzeba zadeklarować ją przed pętlą.

Poprawny przykład:

```csharp
using System;

class Program
{
    static void Main()
    {
        int opcja;

        do
        {
            Console.WriteLine("Wybierz opcję:");
            opcja = int.Parse(Console.ReadLine());
        }
        while (opcja != 0);
    }
}
```

Zmienna `opcja` jest dostępna zarówno wewnątrz bloku `do`, jak i w warunku po `while`.

## Kiedy używać do while?

Pętla `do while` jest przydatna wtedy, gdy blok kodu musi wykonać się co najmniej raz.

Przykłady:

- pokazanie menu,
- zapytanie użytkownika o decyzję,
- powtórzenie prostego obliczenia,
- wykonanie pierwszej próby przed sprawdzeniem warunku.

W następnej lekcji poznasz pętlę `for`, która dobrze pasuje do sytuacji, gdy z góry znamy liczbę powtórzeń.

## Zapamiętaj

- `do while` wykonuje blok instrukcji co najmniej raz.
- Warunek jest sprawdzany po wykonaniu bloku.
- Po warunku w `do while` trzeba postawić średnik.
- Trzeba zmieniać zmienną sterującą, aby uniknąć pętli nieskończonej.
- `do while` dobrze pasuje do menu i powtarzania działania na życzenie użytkownika.
- `while` i `do while` różnią się momentem sprawdzania warunku.

## Ćwiczenia

1. Wypisz liczby od `1` do `5` za pomocą pętli `do while`.
2. Wypisz liczby od `5` do `1` za pomocą pętli `do while`.
3. Sprawdź, co się stanie, gdy warunek w `do while` będzie fałszywy od początku.
4. Napisz proste menu z opcjami `1`, `2` i `0`.
5. Napisz program, który pyta użytkownika, czy powtórzyć działanie.
6. Wczytuj liczby i sumuj je, dopóki użytkownik nie wpisze `0`.
7. Popraw program, w którym brakuje średnika po `while`.
8. Popraw program, w którym pętla działa bez końca.
9. Porównaj działanie `while` i `do while` dla tego samego fałszywego warunku.
10. Wymyśl własny przykład, w którym kod powinien wykonać się co najmniej raz.
