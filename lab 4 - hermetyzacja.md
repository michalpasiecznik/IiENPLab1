# OOPL5
Hermetyzacja

## Zadanie 0
Przeczytać przed przystąpieniem do rozwiązywania zadań z konspektu:
Przypomnienie informacji o hermetyzacji: 

* http://edu.pjwstk.edu.pl/wyklady/poj/scb/

## Zadanie 1
Dla wszystkich zadań z poprzedniego konspektu [Lab4](https://github.com/UR-OOP/OOPL4) dodać hermetyzację.

## Zadanie 2
Zaprojektuj i utwórz klasę, która opisuje pozycję książkową (`Book`) w księgarni. Książki cechują się następującymi właściwościami: `title`, `author`, `pages`, `year`, `price`. Zastosuj enkapsulację pól w klasie, przy czym uwzględnij, że tylko `price` książki może się zmieniać w czasie, a pozostałe atrybuty są niezmienne (tylko do odczytu). Utwórz przykładowe obiekty i pokaż w jaki sposób można dostać się do pól obiektu poprzez metody `get`, `set`.

## Zadanie 3
Zaprojektuj klasę symulującą działanie struktury stosu `Stack`. Należy zastosować dziedziczenie z dostarczonej klasy abstrakcyjnej `AbstractStack` oraz zaimplementować metody z tej klasy. W ramach klasy powinny występować następujące prywatne pola: `n-elementowa tablica liczb całkowitych reprezentująca stos`,zmieną przechowującą aktualny rozmiar stosu(liczbę elementów wstawionych do tablicy) jako liczba całkowita, wskaźnik stosu `index` jako liczba całkowita. `index` wskazuje element ze szczytu stosu. 

* Zaimplementuj metody: umieszczającą element na szczycie stosu `push(int i)` oraz  ściągającą wartość ze szczytu stosu `pop()`. 

* Zaimplementuj metodę `isEmpty()` zwracającą informację (`boolean`) o tym, czy stos jest pusty.

* Zadbaj o to aby w razie przepełnienia stosu nie można było umieścić wartości na stosie (w takim przypadku metoda powinna rzucać wyjątek `StackOverflowError` z pakietu `java.lang`), a w razie stosu pustego nie można było ściągnąć danej ze stosu (w takim przypadku metoda powinna rzucać wyjątek `EmptyStackException` z pakietu `java.util`). Zauważ, że instrukcje `push(int i)` i `pop()` zachowują się jak `get()` i `set(int i)`. 

* Utwórz konstruktor, którego argumentem jest rozmiar stosu. W ciele konstruktora dokonaj inicjalizacji n-elementowej tablicy reprezentującej stos. Pamiętaj, że instrukcja `push(int i)` i `pop()` zmieniają odpowiednio wskaźnik stosu.

![https://www.tutorialspoint.com/data_structures_algorithms/stack_algorithm.htm](https://www.tutorialspoint.com/data_structures_algorithms/images/stack_representation.jpg)

###### https://www.tutorialspoint.com/data_structures_algorithms/stack_algorithm.htm

## Zadanie 4
Zdefiniuj klasę opisującą datę `MyDate`, klasa powinna zanjdować się w pakiecie `pl.edu.ur.oopl5.date`:

* Zastanów się nad wyborem wewnętrznej reprezentacji dat. 
* Zdefiniuj metody pozwalające na odczytywanie bieżącej daty i przestawianie jej o jeden tydzień w przód i w tył. 
* Zadbaj o dobranie odpowiednich modyfikatorów dostępu do składowych. 


## Zadanie 5
Zdefiniuj klasę `Employee` (podobnie do klasy [Person](https://github.com/UR-OOP/OOPL4#zadanie-1) z wykładu, dodając jeszcze tekstową informację o zajmowanym przez pracownika stanowisku `position`).

* Zaimplementuj w klasie `Employee` metody z klasy `AbstractPerson` oraz interfejsu `EmployeeInterface`.
* Przeciąż konstruktor z klasy `AbstractPerson`, tak aby odpowidał klasie `Employee` z dodatkowym polem `Position`.

Następnie zdefiniuj klasę `Company`, która by przechowywała w tablicy spis wszystkich pracowników (możesz założyć, że liczba pracowników nie przekracza 100). 

* Zaimplementuj metody dodawania nowych pracowników `addEmployee(Employee e)` do firmy oraz zwracania `getEmploees()` i wypisywania `printEmployees()` aktualnego spisu pracowników z klasy `AbstractCompany`. 
* Zastanów się, jak przy ostatnim zadaniu rozdzielić odpowiedzialności pomiędzy obie klasy.

## Zadanie 6
Zdefiniuj klasę `Number`, która przechowuje w polu liczbę całkowitą. Zdefiniuj operacje wypisywania liczby, nadawania jej wartości (w postaci parametru konstruktora będącego napisem oraz metody `set`) oraz mnożenia `multiply(int i)` przez liczbę typu `int`. Zdefiniuj metodę `factorial()`, która policzy silnię zadanej jako parametr (konstruktora/metody `set`) liczby. 

* metoda `multiply(int i)` ZWRACA wynik działania bez przypisania go do pola w klasie `Number`.
* metoda `factorial()` ZWRACA wynik działania bez przypisania go do pola w klasie `Number`.
* metoda `setNumber(String number)` przypisuje wartość łańcucha znakowego do pola w klasie `Number` w postaci liczby.

##### W oparciu o opracowanie dr inż. Wojciech Kozła
