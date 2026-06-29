# break i continue

## Cel lekcji

Nauczysz się przerywać pętlę i pomijać jeden obieg pętli.

## Krótkie wyjaśnienie

`break` kończy pętlę. `continue` pomija dalszą część aktualnego obiegu i przechodzi do następnego.

## Przykłady kodu

```csharp
for (int i = 1; i <= 10; i++)
{
    if (i == 5)
    {
        break;
    }

    Console.WriteLine(i);
}
```

```csharp
for (int i = 1; i <= 5; i++)
{
    if (i == 3)
    {
        continue;
    }

    Console.WriteLine(i);
}
```

## Najważniejsze elementy

- `break` natychmiast kończy pętlę.
- `continue` nie kończy pętli, tylko pomija część kodu.
- Obu instrukcji należy używać ostrożnie.
- Najczęściej występują wewnątrz `if`.

## Typowe błędy

- Użycie `break`, gdy potrzebne jest `continue`.
- Użycie `continue` przed zmianą licznika w pętli `while`.
- Trudny do czytania kod z wieloma instrukcjami `break`.

## Ćwiczenia kontrolne

1. Przerwij pętlę po znalezieniu liczby `7`.
2. Wypisz liczby od `1` do `10` bez liczby `5`.
3. Sprawdź różnicę między `break` i `continue` na tym samym przykładzie.
