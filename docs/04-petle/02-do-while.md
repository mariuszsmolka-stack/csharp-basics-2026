# do while

## Cel lekcji

Nauczysz się używać pętli `do while`.

## Krótkie wyjaśnienie

Pętla `do while` najpierw wykonuje instrukcje, a dopiero potem sprawdza warunek. Dlatego wykona się co najmniej raz.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int wybor;

        do
        {
            Console.WriteLine("1. Start");
            Console.WriteLine("0. Koniec");
            Console.Write("Wybór: ");
            wybor = int.Parse(Console.ReadLine());
        }
        while (wybor != 0);
    }
}
```

## Najważniejsze elementy

- `do` rozpoczyna blok pętli.
- `while` z warunkiem jest na końcu.
- Po warunku w `do while` stawiamy średnik.
- Pętla jest dobra do prostego menu konsolowego.

## Typowe błędy

- Brak średnika po `while (warunek)`.
- Warunek zapisany odwrotnie niż potrzeba.
- Brak wcześniejszego utworzenia zmiennej używanej w warunku.

## Ćwiczenia kontrolne

1. Napisz pętlę, która pyta o hasło aż do wpisania poprawnego tekstu.
2. Napisz proste menu z opcją `0. Koniec`.
3. Sprawdź, czy pętla wykona się raz, gdy warunek od razu jest fałszywy.
