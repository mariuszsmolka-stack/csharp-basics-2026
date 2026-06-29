# Pierwszy program w C#

## Cel lekcji

Poznasz najprostszy program konsolowy w C# i zobaczysz, gdzie wpisuje się instrukcje programu.

## Krótkie wyjaśnienie

Program konsolowy działa w oknie konsoli. Na początku kursu będziemy pisać krótkie programy, które wypisują dane, pobierają dane od użytkownika i wykonują proste obliczenia.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Witaj w C#!");
    }
}
```

## Najważniejsze elementy

- `using System;` pozwala używać klasy `Console`.
- `class Program` oznacza klasę programu.
- `static void Main()` to miejsce startu programu.
- `Console.WriteLine()` wypisuje tekst w konsoli.
- Średnik `;` kończy instrukcję.

## Typowe błędy

- Brak średnika na końcu instrukcji.
- Brak nawiasu `)` lub klamry `}`.
- Wpisanie `console` małą literą zamiast `Console`.
- Uruchamianie innego projektu niż ten, w którym piszesz kod.

## Ćwiczenia kontrolne

1. Zmień tekst na swoje imię.
2. Dopisz drugą instrukcję `Console.WriteLine()`.
3. Sprawdź, co się stanie po usunięciu średnika.
