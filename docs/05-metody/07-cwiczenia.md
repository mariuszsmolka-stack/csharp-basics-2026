# Ćwiczenia — metody

## Jak pracować z ćwiczeniami

Przy każdym ćwiczeniu pracuj spokojnie i krok po kroku:

* najpierw napisz nagłówek metody,
* potem ciało metody,
* potem wywołaj metodę w `Main`,
* sprawdź wynik dla kilku danych,
* nie pisz całego programu tylko w `Main`.

Celem tych ćwiczeń jest utrwalenie metod `void`, parametrów, `return` oraz metod pracujących na tablicach.

## Ćwiczenia podstawowe — metody void

1. Napisz metodę `PokazPowitanie()`, która wypisuje krótkie powitanie.
2. Napisz metodę `PokazSeparator()`, która wypisuje linię złożoną z myślników.
3. Napisz metodę `PokazMenu()`, która wypisuje trzy opcje menu.
4. Napisz metodę `PokazAutora()`, która wypisuje imię autora programu.
5. Napisz program, w którym metody `PokazSeparator()` i `PokazMenu()` są wywołane kilka razy.

## Ćwiczenia z parametrami

1. Napisz metodę `PokazImie(string imie)`, która wypisuje imię.
2. Napisz metodę `PokazWiek(int wiek)`, która wypisuje wiek.
3. Napisz metodę `PokazUcznia(string imie, int wiek)`, która wypisuje dane ucznia.
4. Napisz metodę `PokazOcene(string przedmiot, int ocena)`, która wypisuje nazwę przedmiotu i ocenę.
5. Napisz metodę `PokazZakres(int od, int do_)`, która wypisuje informację o zakresie liczb. Jeżeli nie chcesz używać nazwy `do_`, możesz użyć nazw `poczatek` i `koniec`.
6. Wywołaj jedną metodę z parametrami kilka razy z różnymi argumentami.

## Ćwiczenia z return

`bool` to typ logiczny, który przyjmuje wartość `true` albo `false`.

1. Napisz metodę `int Dodaj(int a, int b)`, która zwraca sumę.
2. Napisz metodę `int Odejmij(int a, int b)`, która zwraca różnicę.
3. Napisz metodę `int Pomnoz(int a, int b)`, która zwraca iloczyn.
4. Napisz metodę `double Podziel(int a, int b)`, która zwraca wynik dzielenia jako `double`. Na tym etapie załóż, że `b` nie jest równe `0`.
5. Napisz metodę `int Kwadrat(int x)`, która zwraca kwadrat liczby.
6. Napisz metodę `double ObliczSrednia(int a, int b)`, która zwraca średnią dwóch liczb.
7. Napisz metodę `string PrzygotujPowitanie(string imie)`, która zwraca tekst powitania.
8. Napisz metodę `bool CzyPelnoletni(int wiek)`, która zwraca `true`, jeśli wiek jest większy lub równy `18`, w przeciwnym razie `false`.

## Ćwiczenia z tablicami

1. Napisz metodę `void WypiszTablice(int[] liczby)`, która wypisuje wszystkie elementy tablicy.
2. Napisz metodę `int ObliczSume(int[] liczby)`, która zwraca sumę elementów.
3. Napisz metodę `double ObliczSrednia(int[] liczby)`, która zwraca średnią elementów.
4. Napisz metodę `int ZnajdzMinimum(int[] liczby)`, która zwraca najmniejszy element.
5. Napisz metodę `int ZnajdzMaksimum(int[] liczby)`, która zwraca największy element.
6. Napisz metodę `int PoliczParzyste(int[] liczby)`, która zwraca liczbę elementów parzystych.
7. Napisz metodę `int PoliczWiekszeOd(int[] liczby, int prog)`, która zwraca liczbę elementów większych od podanego progu.
8. Napisz metodę `bool CzyZawiera(int[] liczby, int szukana)`, która zwraca `true`, jeśli tablica zawiera szukaną liczbę.

## Zadania przekrojowe

1. Program „Analiza liczb”

   * utwórz tablicę liczb,
   * wypisz tablicę metodą,
   * oblicz sumę metodą,
   * oblicz średnią metodą,
   * znajdź minimum i maksimum metodami.

2. Program „Prosty kalkulator”

   * utwórz metody `Dodaj`, `Odejmij`, `Pomnoz`, `Podziel`,
   * w `Main` wywołaj każdą metodę dla przykładowych danych,
   * wypisz wyniki.

3. Program „Oceny ucznia”

   * utwórz tablicę ocen,
   * napisz metodę `ObliczSrednia`,
   * napisz metodę `ZnajdzNajlepszaOcene`,
   * napisz metodę `PoliczOcenyPozytywne`.

4. Program „Komunikaty”

   * napisz metodę `PrzygotujPowitanie`,
   * napisz metodę `PrzygotujPozegnanie`,
   * napisz metodę `PokazSeparator`,
   * użyj ich w `Main`.

5. Program „Liczby parzyste”

   * utwórz tablicę liczb,
   * napisz metodę `CzyParzysta`,
   * napisz metodę `PoliczParzyste`,
   * wypisz wynik.

## Kontrola samodzielna

* Czy wiem, kiedy użyć `void`?
* Czy wiem, kiedy użyć `return`?
* Czy umiem odróżnić parametr od argumentu?
* Czy umiem zapisać wynik metody w zmiennej?
* Czy umiem przekazać tablicę do metody?
* Czy `Main` jest czytelny, czy zawiera zbyt dużo szczegółów?

## Podsumowanie

Metody porządkują program i pomagają dzielić go na mniejsze fragmenty.

Parametry pozwalają przekazywać dane do metody, a `return` pozwala zwrócić wynik. Tablice również można przekazywać do metod, na przykład jako parametr `int[] liczby`.

Dobry program powinien mieć czytelny `Main` i sensownie nazwane metody.
