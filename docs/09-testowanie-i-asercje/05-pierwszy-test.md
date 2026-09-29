# Pierwszy test MSTest

## Cel lekcji

Na tej lekcji napiszesz pierwszy test MSTest. Test sprawdzi wynik prostej metody `Dodaj`.

## Po lekcji potrafisz

- utworzyć klasę testową,
- oznaczyć klasę atrybutem `[TestClass]`,
- oznaczyć metodę atrybutem `[TestMethod]`,
- użyć `Assert.AreEqual`,
- użyć `Assert.IsTrue`,
- użyć `Assert.IsFalse`,
- zastosować prosty układ Arrange - Act - Assert.

## 1. Kod w projekcie właściwym

W projekcie konsolowym przygotuj klasę `Program` i metodę `Dodaj`.

```csharp
using System;

namespace AplikacjaKonsolowa
{
    public class Program
    {
        public static void Main()
        {
            int wynik = Dodaj(2, 2);
            Console.WriteLine(wynik);
        }

        public static int Dodaj(int a, int b)
        {
            return a + b;
        }

        public static bool CzyPelnoletni(int wiek)
        {
            return wiek >= 18;
        }
    }
}
```

Metody są `public static`, ponieważ projekt testowy ma je wywoływać bez tworzenia obiektu klasy `Program`.

## 2. Kod w projekcie testowym

W projekcie testowym dodaj test:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using AplikacjaKonsolowa;

namespace AplikacjaKonsolowa.Tests
{
    [TestClass]
    public class TestyProgramu
    {
        [TestMethod]
        public void Dodaj_DwaIDwa_ZwracaCztery()
        {
            int wynik = Program.Dodaj(2, 2);

            Assert.AreEqual(4, wynik);
        }
    }
}
```

Ten test:

- wywołuje metodę `Program.Dodaj(2, 2)`,
- zapisuje wynik w zmiennej,
- sprawdza, czy wynik jest równy `4`.

## 3. Znaczenie elementów testu

`[TestClass]` oznacza klasę zawierającą testy.

```csharp
[TestClass]
public class TestyProgramu
```

`[TestMethod]` oznacza metodę, którą MSTest ma uruchomić jako test.

```csharp
[TestMethod]
public void Dodaj_DwaIDwa_ZwracaCztery()
```

`Assert.AreEqual` sprawdza, czy dwie wartości są równe.

```csharp
Assert.AreEqual(4, wynik);
```

Pierwsza wartość to wartość oczekiwana. Druga wartość to wartość otrzymana.

## 4. Arrange - Act - Assert

Test można zapisać w układzie:

```text
Arrange
=> przygotowanie danych

Act
=> wykonanie testowanej operacji

Assert
=> sprawdzenie wyniku
```

Przykład:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using AplikacjaKonsolowa;

namespace AplikacjaKonsolowa.Tests
{
    [TestClass]
    public class TestyProgramu
    {
        [TestMethod]
        public void Dodaj_DwaIDwa_ZwracaCztery()
        {
            // Arrange
            int a = 2;
            int b = 2;

            // Act
            int wynik = Program.Dodaj(a, b);

            // Assert
            Assert.AreEqual(4, wynik);
        }
    }
}
```

Komentarze `Arrange`, `Act` i `Assert` pomagają w nauce. Jeżeli test jest bardzo krótki i czytelny, nie zawsze trzeba je dodawać.

## 5. Assert.IsTrue

`Assert.IsTrue` sprawdza, czy warunek jest prawdziwy.

```csharp
[TestMethod]
public void CzyPelnoletni_Wiek18_ZwracaTrue()
{
    bool wynik = Program.CzyPelnoletni(18);

    Assert.IsTrue(wynik);
}
```

Ten test sprawdza, czy osoba w wieku `18` lat jest uznana za pełnoletnią.

## 6. Assert.IsFalse

`Assert.IsFalse` sprawdza, czy warunek jest fałszywy.

```csharp
[TestMethod]
public void CzyPelnoletni_Wiek16_ZwracaFalse()
{
    bool wynik = Program.CzyPelnoletni(16);

    Assert.IsFalse(wynik);
}
```

Ten test sprawdza, czy osoba w wieku `16` lat nie jest uznana za pełnoletnią.

## 7. Uruchomienie testu

W Visual Studio 2022:

1. Otwórz `Test`.
2. Wybierz `Test Explorer`.
3. Znajdź test na liście.
4. Kliknij test prawym przyciskiem myszy i wybierz uruchomienie testu albo użyj przycisku uruchamiania w Test Explorer.
5. Możesz też uruchomić wszystkie testy z poziomu Test Explorer.

Test zakończony powodzeniem jest oznaczony jako zaliczony.

Test zakończony niepowodzeniem jest oznaczony jako niezaliczony. W szczegółach można zobaczyć informację o problemie, na przykład wartość oczekiwaną i otrzymaną.

## 8. Typowe błędy

- Brak referencji z projektu testowego do projektu właściwego.
- Brak `using AplikacjaKonsolowa;`.
- Klasa `Program` nie jest `public`.
- Testowana metoda nie jest `public`.
- Pomylenie wartości oczekiwanej i otrzymanej w `Assert.AreEqual`.
- Nazwa testu nie mówi, co jest sprawdzane.

## Zapamiętaj

- `[TestClass]` oznacza klasę z testami.
- `[TestMethod]` oznacza metodę testową.
- `Assert.AreEqual` porównuje wartość oczekiwaną z otrzymaną.
- `Assert.IsTrue` sprawdza warunek prawdziwy.
- `Assert.IsFalse` sprawdza warunek fałszywy.
- Układ Arrange - Act - Assert zwiększa czytelność testu.

## Ćwiczenia

1. Utwórz test metody `Dodaj`.
2. Utwórz test metody `CzyPelnoletni` dla wieku `18`.
3. Utwórz test metody `CzyPelnoletni` dla wieku `16`.
4. Zmień metodę `Dodaj`, aby zwracała błędny wynik, i sprawdź wynik testu.
5. Popraw metodę `Dodaj` i uruchom test ponownie.
