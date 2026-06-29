# Ćwiczenia — tablice, listy i przekazywanie danych

## Jak pracować z ćwiczeniami

- Najpierw przeczytaj dokładnie, jakich danych używa zadanie.
- Zdecyduj, czy potrzebujesz tablicy, listy czy metody.
- Pisz program małymi fragmentami.
- Po każdej części uruchom program.
- Sprawdzaj indeksy i zakresy.
- Nie używaj LINQ ani gotowych skrótów.

## Ćwiczenia: tablice dwuwymiarowe

1. Utwórz tablicę `int[,]` o rozmiarze `2x3` i wpisz do niej liczby.
2. Wypisz element z wiersza `0` i kolumny `1`.
3. Wypisz wszystkie elementy tablicy 2D za pomocą dwóch pętli `for`.
4. Wypisz tablicę 2D w formie tabeli.
5. Oblicz sumę wszystkich elementów tablicy 2D.
6. Oblicz sumę pierwszego wiersza.
7. Oblicz sumę wybranej kolumny.
8. Znajdź największy element w tablicy 2D.
9. Znajdź najmniejszy element w tablicy 2D.
10. Policz, ile elementów tablicy 2D jest parzystych.

## Ćwiczenia: tablice wielowymiarowe

1. Utwórz tablicę `int[,,]` o rozmiarze `2x2x2`.
2. Przypisz wartość do elementu `dane[0, 1, 1]`.
3. Wypisz rozmiary wszystkich trzech wymiarów za pomocą `GetLength`.
4. Przejdź po wszystkich elementach tablicy 3D trzema pętlami `for`.
5. Wyjaśnij, dlaczego tablice 3D są trudniejsze do czytania niż tablice 2D.

## Ćwiczenia: List<int>

1. Utwórz pustą listę `List<int>`.
2. Dodaj do listy pięć liczb metodą `Add`.
3. Wypisz liczbę elementów listy za pomocą `Count`.
4. Wypisz pierwszy i ostatni element listy.
5. Wypisz wszystkie elementy listy pętlą `for`.
6. Wypisz wszystkie elementy listy pętlą `foreach`.
7. Oblicz sumę elementów listy.
8. Policz, ile elementów listy jest większych od `10`.

## Ćwiczenia: List<string>

1. Utwórz pustą listę `List<string>` o nazwie `imiona`.
2. Dodaj do listy pięć imion.
3. Wypisz liczbę elementów listy.
4. Wypisz wszystkie imiona pętlą `foreach`.
5. Sprawdź, czy lista zawiera wybrane imię.
6. Usuń jedno imię metodą `Remove`.
7. Usuń pierwszy element listy metodą `RemoveAt`.
8. Po każdej operacji usuwania wypisz aktualną zawartość listy.

## Ćwiczenia: tablica czy lista

Dla każdego przypadku wskaż, czy lepsza będzie tablica, czy lista, i krótko uzasadnij:

1. Znamy dokładnie `5` ocen ucznia.
2. Użytkownik będzie dodawał dowolną liczbę wyników.
3. Chcemy przechować planszę gry `3x3`.
4. Chcemy przechowywać listę uczestników, która może się zmieniać.
5. Chcemy przechować tabelę temperatur: `7` dni i `4` pomiary dziennie.
6. Chcemy dodawać i usuwać zadania z prostej listy zadań.

## Ćwiczenia: przekazywanie przez wartość

1. Napisz metodę `PokazLiczbe(int liczba)`, która wypisuje przekazaną liczbę.
2. Napisz metodę `ZmienLiczbe(int liczba)`, która ustawia parametr na `100` i wypisuje go w metodzie.
3. Sprawdź, czy zmienna z `Main` zmieniła się po wywołaniu `ZmienLiczbe`.
4. Napisz metodę `int Zwieksz(int liczba)`, która zwraca liczbę większą o `1`.
5. Wywołaj `Zwieksz(x)` bez przypisania wyniku i sprawdź wartość `x`.
6. Wywołaj `x = Zwieksz(x)` i sprawdź wartość `x`.

## Ćwiczenia: ref

1. Napisz metodę `ZmienNaZero(ref int liczba)`, która ustawia przekazaną zmienną na `0`.
2. Napisz metodę `Podwoj(ref int liczba)`, która podwaja przekazaną zmienną.
3. Napisz metodę `Zamien(ref int a, ref int b)`, która zamienia wartości dwóch zmiennych.
4. Pokaż różnicę między metodą `Podwoj(int liczba)` a `Podwoj(ref int liczba)`.
5. Wyjaśnij, dlaczego przy `ref` słowo `ref` musi pojawić się i w definicji metody, i przy wywołaniu.

## Ćwiczenia: out

1. Napisz metodę `UstawLiczbe(out int liczba)`, która ustawia wartość `50`.
2. Napisz metodę `PobierzDane(out string imie, out int wiek)`, która ustawia przykładowe dane.
3. Napisz metodę `SprobujPodzielic(int a, int b, out double wynik)`, która zwraca `false` przy dzieleniu przez zero.
4. Popraw metodę z `out`, w której nie każda ścieżka przypisuje wartość do parametru.
5. Wyjaśnij różnicę między `return` a `out`.

## Zadania przekrojowe

1. Program „Analiza tabeli”

   - utwórz tablicę `int[,]` `3x3`,
   - wypisz ją jako tabelę,
   - oblicz sumę wszystkich elementów,
   - znajdź minimum i maksimum.

2. Program „Oceny ucznia”

   - utwórz `List<int>` ocen,
   - dodaj kilka ocen,
   - oblicz średnią bez LINQ,
   - policz oceny pozytywne,
   - sprawdź, czy lista zawiera ocenę `6`.

3. Program „Lista obecności”

   - utwórz `List<string>` imion,
   - dodaj kilka imion,
   - wypisz listę,
   - sprawdź obecność wybranego ucznia,
   - usuń jedno imię i wypisz listę ponownie.

4. Program „Zamiana liczb”

   - utwórz dwie zmienne `int`,
   - napisz metodę `Zamien(ref int a, ref int b)`,
   - pokaż wartości przed i po zamianie.

5. Program „Bezpieczne dzielenie”

   - napisz metodę `SprobujPodzielic` z parametrem `out`,
   - w `Main` sprawdź kilka przypadków,
   - wypisz wynik albo komunikat o błędzie.

6. Program „Tablica czy lista”

   - napisz krótki opis problemu,
   - wybierz tablicę albo listę,
   - uzasadnij wybór w komentarzu,
   - napisz prostą implementację.

## Kontrola samodzielna

- Czy wiem, czym różni się `int[]` od `int[,]`?
- Czy wiem, co oznaczają `GetLength(0)` i `GetLength(1)`?
- Czy umiem przejść po tablicy 2D dwiema pętlami?
- Czy wiem, kiedy użyć `List<int>`?
- Czy wiem, kiedy użyć `List<string>`?
- Czy pamiętam różnicę między `Length` i `Count`?
- Czy wiem, co oznacza przekazywanie przez wartość?
- Czy wiem, kiedy `ref` zmienia zmienną z `Main`?
- Czy wiem, czym `out` różni się od `ref`?
- Czy umiem zdecydować, kiedy wystarczy `return`?

## Podsumowanie

Tablice 2D służą do danych tabelarycznych, a tablice wielowymiarowe wymagają wielu indeksów.

`List<int>` i `List<string>` pozwalają przechowywać zmienną liczbę elementów.

Tablica ma `Length`, a lista ma `Count`.

Zwykły parametr typu `int` jest przekazywany przez wartość. `ref` pozwala zmienić istniejącą zmienną, a `out` pozwala zwrócić wartość przez parametr.

W prostych programach najpierw warto rozważyć zwykły `return`.
