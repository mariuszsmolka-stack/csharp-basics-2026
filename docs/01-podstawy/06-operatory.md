# Operatory

## Cel lekcji

Poznasz podstawowe operatory arytmetyczne, porównania i logiczne.

## Krótkie wyjaśnienie

Operator wykonuje działanie na wartościach. W C# używamy operatorów do obliczeń, porównań i budowania warunków.

## Przykłady kodu

```csharp
int a = 10;
int b = 3;

Console.WriteLine(a + b);
Console.WriteLine(a - b);
Console.WriteLine(a * b);
Console.WriteLine(a / b);
Console.WriteLine(a % b);
```

```csharp
int wiek = 18;
bool maLegitymacje = true;

Console.WriteLine(wiek >= 18);
Console.WriteLine(wiek >= 18 && maLegitymacje);
Console.WriteLine(wiek < 18 || maLegitymacje);
Console.WriteLine(!maLegitymacje);
```

## Najważniejsze elementy

- `+`, `-`, `*`, `/`, `%` służą do obliczeń.
- `%` daje resztę z dzielenia.
- `==`, `!=`, `<`, `>`, `<=`, `>=` służą do porównań.
- `&&` oznacza logiczne „i”.
- `||` oznacza logiczne „lub”.
- `!` oznacza zaprzeczenie.

## Typowe błędy

- Użycie `=` zamiast `==` przy porównaniu.
- Dzielenie liczb całkowitych i oczekiwanie wyniku z przecinkiem.
- Mylenie `&&` z `||`.
- Pomijanie nawiasów w trudniejszych warunkach.

## Ćwiczenia kontrolne

1. Oblicz resztę z dzielenia `17` przez `5`.
2. Sprawdź, czy liczba `x` jest większa od `10`.
3. Sprawdź, czy wiek jest co najmniej `18` i użytkownik ma zgodę.
