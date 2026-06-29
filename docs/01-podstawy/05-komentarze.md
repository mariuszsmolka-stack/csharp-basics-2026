# Komentarze

## Cel lekcji

Nauczysz się dodawać komentarze do kodu.

## Krótkie wyjaśnienie

Komentarz to tekst w kodzie, który jest ignorowany przez program. Komentarze pomagają wyjaśnić, co robi fragment programu.

## Przykład kodu

```csharp
using System;

class Program
{
    static void Main()
    {
        // To jest komentarz jednowierszowy.
        int a = 5;
        int b = 8;

        /*
         To jest komentarz
         wielowierszowy.
        */
        Console.WriteLine(a + b);
    }
}
```

## Najważniejsze elementy

- `//` rozpoczyna komentarz jednowierszowy.
- `/* ... */` oznacza komentarz wielowierszowy.
- Komentarze nie powinny zastępować czytelnych nazw zmiennych.
- Dobry komentarz wyjaśnia trudniejszy fragment kodu.

## Typowe błędy

- Komentowanie każdej prostej instrukcji.
- Brak zakończenia komentarza wielowierszowego.
- Wpisywanie ważnego kodu w komentarzu i zastanawianie się, dlaczego się nie wykonuje.

## Ćwiczenia kontrolne

1. Dodaj komentarz nad zmienną `suma`.
2. Zakomentuj jedną instrukcję `Console.WriteLine()` i uruchom program.
3. Napisz komentarz, który wyjaśnia obliczenie pola prostokąta.
