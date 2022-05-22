# OOPL4
Obiekty w języku Java

## Zadanie 1
Utwórz dwie klasy:

* Person
* PersonalData


Uzupełnij klasy następującym kodem:
* Person

```java
package pl.edu.ur.polab4.zad1;

public class Person {

    /* ------
     * Fields
     * ------ */
    public String name;      //
    public String surname;  // Pola klasy osoba
    public int age;         //

    /* --------------------------
     * Constructors - 3 overloads
     * -------------------------- */
    // Konstruktor pierwszy
    public Person(String name, String surname, int age) {
        this.name = name;
        this.surname = surname;
        this.age = age;
    }

    // Konstruktor drugi
    public Person(String name, String surname) {
        this.name = name;
        this.surname = surname;
    }

    // Konstruktor trzeci
    public Person() {
    }

    /* -------
     * Methods
     * ------- */
    //Metoda pokazująca dane osoby
    public void showData() {
        System.out.println("Person");
        System.out.println("name: " + this.name);
        System.out.println("surname: " + this.surname);
        System.out.println("age: " + this.age);
    }
} //end class
```

* DaneOsobowe

```java
package pl.edu.ur.oopl4.zad1;

public class PersonalData {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        Person person1 = new Person("Jan", "Kowalski", 15);
        person1.showData();

        System.out.println("---------------------");
        Person person2 = new Person("Adam", "Nowak");
        person2.showData();

        System.out.println("---------------------");
        person2.name = "Stefan";
        person2.age = 70;
        person2.showData();

        System.out.println("---------------------");
        Person person3 = new Person();
        person3.name = "Anna";
        person3.surname = "Wiśniewska";
        person3.age = 45;
        person3.showData();
    }
}
```

Jakie wyniki zostaną wyświetlone na konsoli?

### Ważne (przeczytać !!!):

* Konstruktory służą do tworzenia obiektów. W języku Java konstruktor posiada następujące cechy: jego nazwa jest identyczna z nazwą klasy, w której się znajduje; może posiadać parametry, którymi najczęściej ustawia wartości pól w klasie; w odróżnieniu od metod nie zwraca żadnej wartości. Jeśli programista nie zdefiniuje, żadnego konstruktora wewnątrz klasy, kompilator utworzy w trakcie kompilacji konstruktor domniemany dla tej klasy. Będzie on ekwiwalentem konstruktora pustego, z tą różnicą, że nie będzie on obecny w kodzie programu. Java tworzy konstruktory domyślne tylko w przypadku braku jakiegokolwiek konstruktora w kodzie klasy. 

* Konstruktory i metody w języku Java podlegają mechanizmowi przeciążenia (ang. overload). Oznacza to, że mogą występować w różnych wersjach (pod różnymi postaciami). Metody przeciążane cechują się tą samą nazwą. Różnić się natomiast mogą ilością argumentów, typem argumentów, typem zwracanym i wnętrzem metody (kodem programu wewnątrz metody). Podobnie jest z konstruktorami, przy czym te z definicji mają tę samą nazwę i dodatkowo w przeciwieństwie do metod nie zwracają wartości. Jeśli zatem konstruktory nie zwracają wartości, nie można ich przeciążać po zwracanym typie. Solidarnie do nich również i metody nie mogą być przeciążane po zwracanym typie, co jednak nie oznacza, że wszystkie one muszą mieć ten sam typ zwracany. Konkludując, można stwierdzić, że wariantywność przeciążanych metod objawia się poprzez różnice w ilości i typie argumentów przyjmowanych przez metodę czy konstruktor. Mechanizm przeciążania należy do zjawisk polimorfizmu w językach programowania.

## Zadanie 2
Na podstawie zadania utwórz klasę `Student` (możesz [nawet byłoby to wskazane] w tym celu użyć dziedziczenia po klasie `Person`), która posiada następujące pola: `name`, `surname`, `indexNumber`, `speciality`, `yearOfStudy`. Dla pól dobierz odpowiedni typ danych. Utwórz cztery przeciążenia konstruktorów dla tej klasy:

* `name`, `surname`, `indexNumber`, `speciality`, `yearOfStudy`
* `name`, `surname`, `indexNumber`, `speciality`
* `name`, `surname`, `indexNumber`
* `name`, `surname`

Utwórz metodę wyświetlającą dane o studencie. Utwórz cztery obiekty klasy `Student`, każdy korzystający z innego przeciążenia konstruktora podczas tworzenia obiektu. Dla każdego obiektu uruchom metodę wyświetlającą dane.
Przesłoń metodę `toString()` dla klasy `Student`.

## Zadanie 2.1
Utwórz w klasie `Student` z zadania 2 konstruktor przyjmujący obiekt klasy `Scanner` (`Student(Scanner in)`) w celu utworzenia obiektu klasy `Student` z polami zainicjalizowanymi poprzez dane wprowadzone przez użytkownika z konsoli.

## Zadanie 3
W nowym pakiecie (np. `pl.edu.ur.polab4.zad3`) utwórz klasy opisujące następujące figury geometryczne: `Circle`, ` Square`,  `Rectangle`, `Cube`, `Cuboid`, `Sphere`, `Cone`. Dla każdej klasy dobierz odpowiednie pola. Utwórz także metody obliczające pola figur (`area`), obwody (`perimeter`) (dla figur płaskich), oraz objętości (`size`) (dla figur przestrzennych). W tym celu zaimplementuj w klasach metody klas abstrakcyjnych `Figure2D` oraz `Figure3D`. Dla każdej klasy utwórz metodę wyświetlającą dane dotyczące figury tj. nazwa, parametry, wartość pola i obwodu lub objętości. Utwórz obiekty tych figur i pokaż wyniki obliczeń przy użyciu funkcji wyświetlającej dane.

*Utwórz kalkulator dla figur geometrycznych tj. odpowiednie menu pozwalające na: wybór figury geometrycznej oraz wprowadzanie parametrów dla tej figury z konsoli. Następnie wyświetl wyniki przy użyciu metody wyświetlającej dane. 

### Uwaga!
Pamiętać należy o tym, że w Javie np. (4/3) = 1 a (4.0/3) = 1.3333 - dzieje się tak, ponieważ przy podziale 4 (int) i 3 (int) "ogonek" zostaje ucięty a nie zaokrąglony co w sposób znaczny może wpłynąć na wynik końcowy (w tym przypadku to ~30%!).
Należy pamiętać o tym aby poprawnie dokondać takiego podziału oraz poprawnie zaokrąglić (`Math.round(double a)`) wynik w przypadku kiedy metoda ma zwracać `int`.

## Zadanie 4
W nowym pakiecie (np. `pl.edu.ur.polab4.zad4`) utwórz klasę `StudentGroup` zawierającą 100 elementową tablicę klasy `Student` (użyj klasy `Student` z zadania 2). Zaimplementuj w tym celu metodę `init()` z interfejsu `StudentGroupInterface` tak aby tworzyła obiekt dla każdego elementu tablicy i ustawiała domyślne wartości tj. dla typu liczbowego: `0`, dla typu łańcuchowego: łańcuch pusty `""`.

Zaimplementuj metody z interfejsu `StudentGroupInterface` umożliwiające:

*	wprowadzanie/edycję danych studenta pod wybrany index tablicy (`setStudentDataAtIndex(int index)`)
*	usunięcie danych studenta (tj. nadpisanie elementów tablicy wartościami domyślnymi) (`setDefaultDataAtIndex(int index)`)
*	pobranie (jako `String`)/wyświetlenie obiektu o danym indeksie (`getStudentDataAtIndex(int index)` + `showStudentDataAtIndex(int index)`)
*	pobranie (jako `String`)/wyświetlenie wszystkich obiektów (`getDataOfAllStudents()` + `showDataOfAllStudents()`)
*	pobranie (jako `String`)/wyświetlenie zakresu obiektów w podanym zakresie (`getStudentsFromRange(int start, int end)`, `showStudentsFromRange(int start, int end)`)
 

##### W oparciu o opracowanie dr inż. Wojciecha Kozła
