8) Staircase (Schody)

Przeczytać swoje zadanie
1. Prawidłowo ustawić dane wejściowe i wyjściowe
2. Napisać pseudokod algorytmu
Dopelnić program z algorytmem w języku C/C++. Zapisac w swojim repozitorium jako `Egzamin/zadanie.c`
3. Wskazać zlozonosć czasowa
4. Udowodnić czy wskazany algorytm poprawny. Jeżeli tak, cesciowo czy całkowicie poprawny

1. dane wejściowe: n - ilość schodów
dane wyjściowe: odpieczętowane "schody" z przekazaną dla funkcji ilością;

2. wejście: ilość schodek - n
  Dopóki i <= n: drukuj "\n"; i++
    Dopóki k > 0 (k = n - i) : drukuj " "; k--
    Dopóki j <= i: drukuj "#"; j++

3. T= O(i*(k+j)) lub inaczej T = O(n^2)
    
4. Algorytm poprawny ponieważ:
    -> dla dowolnej dozwolonej "n" algorytm zakonczy sie i na wyjściu będzie poprawny wynik.
    -> w dowolnym kroku algorytmu możemy zatrzymać sie i sprawdzić i warunki algorytmu będą spełnione.


