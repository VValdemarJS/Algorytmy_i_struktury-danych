# Projekt do przedmiotu "Algorytmy i struktury danych"

### Pracę wykonał [Valdemar Kudžma](https://github.com/VValdemarJS)

### Data 2023-02-17

- [Algorytm sita Eratostenesa](#algorytm-sita-eratostenesa)
- [Algorytm naiwny wyszukiwania wzorca w łańcuchu tekstowym](#algorytm-naiwny-wyszukiwania-wzorca-w-łańcuchu-tekstowym)
- [Algorytm wyznaczania liczby elementów na liście jednokierunkowej](#algorytm-wyznaczania-liczby-elementów-na-liście-jednokierunkowej)

## Algorytm sita Eratostenesa

### Opis
SieveOfEratosthenes jest algorytmem do wyznaczania liczb pierwszych w zadanym zakresie. Algorytm opiera się na idei "sitowania", czyli usuwania wszystkich wielokrotności danej liczby, poczynając od najmniejszej, aż do momentu, gdy nie będzie już żadnych wielokrotności.

### Przykład
Jeśli chcemy wyznaczyć liczby pierwsze w zakresie od `2` do `20`, najpierw zakładamy, że wszystkie liczby są pierwsze. Następnie usuwamy wszystkie wielokrotności liczby `2` `(tj. 4, 6, 8, 10, 12, 14, 16, 18, 20)` i oznaczamy je jako niepierwsze. Następnie bierzemy następną nieusuniętą liczbę (`3`) i usuwamy wszystkie jej wielokrotności (tj. `9`, `15`), a resztę oznaczamy jako pierwsze. Proces ten kontynuujemy, aż do momentu, gdy nie będzie już żadnych wielokrotności do usunięcia. W tym przypadku, po zakończeniu procesu, pozostaną liczby pierwsze: `2, 3, 5, 7, 11, 13, 17, 19`.

Wejście: zakres liczb, do którego chcemy wyznaczyć liczby pierwsze (od `2` do `n`).

Dane wyjściowe: Lista liczb pierwszych w zadanym zakresie.

![przyklad](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Sieve_of_Eratosthenes_animation.gif/360px-Sieve_of_Eratosthenes_animation.gif)

### Pseudokod
```
WEJŚCIE: liczba całkowita n
WYJŚCIE: wszystkie liczby pierwsze do n

1. Stwórz tablicę boolowską "pierwsze" o rozmiarze n + 1 i ustaw wszystkie wartości na true.
2. Dla p = 2 do sqrt(n):
    a. Jeśli pierwsze[p] jest true:
        i. Dla i = p * p do n, zwiększając o p:
            1. Ustaw pierwsze[i] na false.
3. Dla p = 2 do n:
    a. Jeśli pierwsze[p] jest true:
        i. Wypisz p.
```
### Złożoność czasowa

Złożoność czasowa dla tego algorytmu to `O(n log log n)`.

Można ją obliczyć, biorąc pod uwagę, że główna pętla jest wykonywana od `2` do `√n` razy, a każde wywołanie wewnętrznej pętli jest wykonywane `log n` razy.

W rezultacie złożoność czasowa można obliczyć jako:

`O(n log log n) = O(√n * log n)`

**Kroki obliczania złożoności czasowej:**

1. Zidentyfikuj główną pętlę, która jest wykonywana od `2` do `√n` razy.

2. Zidentyfikuj wewnętrzną pętlę, która jest wykonywana `log n` razy.

3. Oblicz złożoność czasową, biorąc pod uwagę, że główna pętla jest wykonywana od `2` do `√n` razy, a każde wywołanie wewnętrznej pętli jest wykonywane `log n` razy.

4. Uzupełnij wynik, uwzględniając wszystkie współczynniki.

### Udowodnienie, że jest końcowy

Algorytm sita Eratostenesa jest oparty na wnioskach matematycznych dotyczących liczb pierwszych. W oparciu o te wnioski, algorytm przechodzi przez zakres liczb od `2` do `n` i oznacza jako `false` te, które są wielokrotnościami innych liczb. W ten sposób, na końcu algorytmu, pozostają tylko liczby pierwsze, które są oznaczone jako `true`.

Możemy potwierdzić poprawność tego algorytmu poprzez przetestowanie każdej liczby w zakresie od `2` do `n` i upewnienie się, że wszystkie wielokrotności są oznaczone jako `false`, a pozostałe liczby są oznaczone jako `true`.

W ten sposób możemy udowodnić, że algorytm Algorytm sita Eratostenesa jest poprawny i skutecznie wyznacza liczby pierwsze w zakresie od `2` do `n`.

### Przykład zastosowania

Sito Eratosthenesa jest używane do wyznaczania wszystkich liczb pierwszych w określonym zakresie. Oto jeden z przykładów jego zastosowania:

Problem: Znajdź wszystkie liczby pierwsze w zakresie od `2` do `n = 30`.

Rozwiązanie:

Stwórz tablicę boolowską o długości `n + 1` i oznacz wszystkie elementy jako `true` (prawdziwe).
Przejdź przez każdy element tablicy i jeśli jest on oznaczony jako `true`, oznacz jego wielokrotności jako `false` (fałszywe).
Wszystkie elementy, które pozostały oznaczone jako `true`, są liczbami pierwszymi.
Wynik: Liczby pierwsze w zakresie od `2` do `30` to: `2, 3, 5, 7, 11, 13, 17, 19, 23, 29`.

### Program

[Sito Eratostenesa](https://github.com/VValdemarJS/Algorytmy_i_struktury-danych/blob/main/Projekt/Przyk%C5%82ady%20kodu/eratosthenes.h)


## Algorytm naiwny wyszukiwania wzorca w łańcuchu tekstowym

### Opis
Naiwny algorytm do wyszukiwania wzorców w łańcuchu tekstowym to prosty sposób na znalezienie wystąpień wzoru w tekście. Algorytm działa poprzez iterowanie przez każdy możliwy początek wzoru w tekście i porównywanie każdego znaku wzoru i tekstu. Jeśli wszystkie znaki są takie same, wzorzec jest uważany za znaleziony.

### Przykład
Jeśli mamy łańcuch tekstowy `abcabc` i szukamy wzoru `abc`, algorytm zaczyna od pierwszego znaku tekstu i porównuje każdy znak z odpowiadającym znakiem wzoru. Jeśli wszystkie znaki pasują, algorytm uważa wzorzec za znaleziony i wyświetla indeks, na którym zaczyna się wzorzec. Proces powtarza się dla każdego możliwego początku wzoru w tekście. W tym przypadku, algorytm znajdzie wzorzec pod indeksami `0` i `3`.

**Wejście:** Wzorzec `pat` i tekst `txt`, w którym chcemy wyszukać wzorzec.

**Dane wyjściowe:** Indeksy, na których wzorzec został znaleziony w tekście.

### Pseudokod

```
Algorytm naivePattern(pat, txt)
    m ← długość(pat)
    n ← długość(txt)
    Dla i ← 0 do n - m
        j ← 0
        Dopóki j < m i txt[i + j] = pat[j]
            j ← j + 1
        Jeśli j = m
            Wypisz "Wzorzec znaleziony pod indeksem:", i
```

### Złożoność czasowa

Złożoność czasowa tego algorytmu to `O(n^2)`, gdzie `n` jest długością łańcucha tekstowego.

Wyjaśnienie: Dla każdego `i` od `0` do `n-m`, algorytm wykonuje pętlę `for j` od `0` do `m`. Wewnętrzna pętla `for j` jest wykonywana `m` razy dla każdego `i`, a zewnętrzna pętla jest wykonywana `n-m` razy. Łącznie jest wykonywanych `(n-m) * m` iteracji, co daje `n^2`. Z tego powodu złożoność czasowa tego algorytmu jest określona jako `O(n^2)`.

### Udowodnienie, że jest końcowy

Algorytm działa poprzez porównywanie każdego podciągu o długości wzorca w tekście i sprawdzanie, czy jest on taki sam jak wzorzec. Jeśli jest, to oznacza, że wzorzec został znaleziony w tekście. Algorytm działa poprawnie, ponieważ przegląda wszystkie podciągi o długości wzorca i zwraca indeks, gdy zostanie znaleziony wzorzec.

### Przykład zastosowania

Algorytm może być używany do wyszukiwania szukanego ciągu znaków w dłuższym tekście, np. wyszukiwanie wystąpień słów kluczowych w tekście dokumentu, wyszukiwanie numerów telefonów lub adresów e-mail w tekście, itp.

## Program
[Algorytm naiwny wyszukiwania wzorca w łańcuchu tekstowym](https://github.com/VValdemarJS/Algorytmy_i_struktury-danych/blob/main/Projekt/Przyk%C5%82ady%20kodu/naiveSearch.h)

## Algorytm wyznaczania liczby elementów na liście jednokierunkowej

### Opis
Funkcja size jest implementacją prostego algorytmu do obliczania liczby elementów w liście jednokierunkowej. Algorytm działa poprzez iterowanie przez każdy element listy od głowy do ogona, zliczanie elementów i zwracanie wyniku.

### Przykład
Jeśli mamy listę składającą się z `5` elementów, funkcja `size` zwróci wartość `5`. Funkcja przechodzi przez każdy element listy, zwiększając licznik o `1`, aż do osiągnięcia ostatniego elementu. W tym momencie funkcja zwróci wartość licznika jako wynik.

**Wejście:** Wskaźnik head na głowę listy jednokierunkowej.

**Dane wyjściowe:** Liczba elementów w liście jednokierunkowej.

[![](https://mermaid.ink/img/pako:eNp10DFug0AQBdCrjKa2i7QUiWTjVJYb2028FBOYhM3CgHYXIQwchHOkSxtyr2yI5Crppnj6-n96TKuMMcJXS3UOp1jJ0ZP1sF7fw-5ydp5aTWUHrTP09SHagBDkTFmiZLeoTb-9dsAFlywe3th5OJz3-4dRyWYBw4nMANvLU2sp_ckqdHp9nicwtjKf721ygwfNAzwGqOfJuOsfFiq4SxYc_1dOyPl5quXWKeTHv01xhSXbknQWFvdKABT6PCCFUTgzskahkjE4anx17CTFyNuGV9jUGXmONYVHlRi9UOF4_AYNDnH8?type=png)](https://mermaid.live/edit#pako:eNp10DFug0AQBdCrjKa2i7QUiWTjVJYb2028FBOYhM3CgHYXIQwchHOkSxtyr2yI5Crppnj6-n96TKuMMcJXS3UOp1jJ0ZP1sF7fw-5ydp5aTWUHrTP09SHagBDkTFmiZLeoTb-9dsAFlywe3th5OJz3-4dRyWYBw4nMANvLU2sp_ckqdHp9nicwtjKf721ygwfNAzwGqOfJuOsfFiq4SxYc_1dOyPl5quXWKeTHv01xhSXbknQWFvdKABT6PCCFUTgzskahkjE4anx17CTFyNuGV9jUGXmONYVHlRi9UOF4_AYNDnH8)

### Pseudokod
```
FUNKCJA size(wskaźnik head na struct Node):
    JEŚLI head RÓWNA SIĘ NULL, ZWRÓĆ 0
    DEKLARUJ licznik i RÓWNAJĄCY SIĘ 0
    DEKLARUJ wskaźnik current RÓWNAJĄCY SIĘ head
    DOPÓKI current NIE RÓWNA SIĘ NULL, WYKONUJ:
        ZWIĘKSZ licznik o 1
        PRZYPISZ do current wartość current->next
    KONIEC DOPÓKI
    ZWRÓĆ licznik
KONIEC FUNKCJI
```
### Złożoność czasowa

Czas skomplikowania tej funkcji to `O(n)`, gdzie `n` to liczba elementów w liście.

W pętli `while` wykonujemy dokładnie tyle iteracji, ile jest elementów w liście, dlatego czas skomplikowania tej funkcji jest proporcjonalny do `n`. W związku z tym możemy określić jego złożoność jako `O(n)`.

### Przykład zastosowania

Algorytm ten może być używany w wielu różnych sytuacjach związanych z listami jednokierunkowymi. Na przykład:

1. W systemie plików do przechowywania i manipulowania informacjami o plikach i katalogach.
2. W aplikacjach sieciowych do przechowywania i analizowania informacji o połączeniach sieciowych.
3. W grach komputerowych do przechowywania i manipulowania informacjami o elementach gry, takich jak obiekty, postaci i plansze.
4. W każdym z tych przypadków lista jednokierunkowa jest używana do przechowywania informacji o pojedynczym elemencie, a funkcja `size` jest używana do zliczania ilości elementów w liście.

## Program

[Algorytm wyznaczania liczby elementów na liście jednokierunkowej](https://github.com/VValdemarJS/Algorytmy_i_struktury-danych/blob/main/Projekt/Przyk%C5%82ady%20kodu/singlyLinkedList.h)

## Źródła
- [Wikipedia - Sito Eratostenesa](https://pl.wikipedia.org/wiki/Sito_Eratostenesa)
- [Geeksforgeeks - Naive algorithm for Pattern Searching](https://www.geeksforgeeks.org/naive-algorithm-for-pattern-searching/)
- [Geeksforgeeks - Finding length of a singly linked list](https://www.geeksforgeeks.org/find-length-of-a-linked-list-iterative-and-recursive/)
- [Dodatkowe materiały do wykonania projektów](https://wirtaw.github.io/algorytmy_i_struktury/materialy/index.html)
