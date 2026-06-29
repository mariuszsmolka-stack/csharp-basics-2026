# Licznik i akumulator

## Cel lekcji

Nauczysz się zliczać zdarzenia i sumować wartości w pętli.

## Krótkie wyjaśnienie

Licznik służy do zliczania, ile razy coś się wydarzyło. Akumulator służy do gromadzenia wyniku, na przykład sumy liczb.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        int suma = 0;
        int licznikParzystych = 0;

        for (int i = 1; i <= 5; i++)
        {
            suma += i;

            if (i % 2 == 0)
            {
                licznikParzystych++;
            }
        }

        Console.WriteLine($"Suma: {suma}");
        Console.WriteLine($"Liczb parzystych: {licznikParzystych}");
    }
}
```

## Najważniejsze elementy

- `suma += i` oznacza `suma = suma + i`.
- `licznikParzystych++` zwiększa licznik o `1`.
- `-=`, `+=`, `*=` skracają zapis działań na tej samej zmiennej.
- Akumulator zwykle ustawiamy na początku na `0`.

## Typowe błędy

- Brak wartości początkowej akumulatora.
- Zerowanie sumy wewnątrz pętli.
- Zwiększanie licznika w złym miejscu.

## Ćwiczenia kontrolne

1. Oblicz sumę liczb od `1` do `10`.
2. Zlicz liczby większe od `5`.
3. Pomnóż kolejne liczby, używając operatora `*=`.
