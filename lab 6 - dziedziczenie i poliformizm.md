
# OOPL7
Dziedziczenie i polimorfizm


## Zadanie -2
#### [Dziedziczenie](http://naukajavy.pl/kurs-jezyka-java/91-dziedziczenie)

Dziedziczenie jest jednym z podstawowych mechanizmów programowania obiektowego. Mechanizm ten umożliwia definiowanie nowych klas na bazie istniejących.

Słowo dziedziczenie kojarzy się nam z życia codziennego z przejmowaniem przez jedną osobę majątku po drugiej osobie. Analogia w języku Java nie jest bardzo daleka. Dziedziczenie oznacza tu przejmowanie przez jedną klasę metod i zmiennych z innej klasy.

Dziedziczenie jest w języku Java mechanizmem wszechobecnym i niezwykle potężnym. Prawie każda klasa – a mówiąc precyzyjniej każda klasa z wyjątkiem klasy `java.lang.Object` – dziedziczy z jakiejś innej klasy, każda bowiem klasa dziedziczy w sposób niejawny ze wspomnianej klasy Object.

Co dziedziczymy z klasy Object? Kilka metod, a wśród nich metodę `equals(…)`, która służy do sprawdzania równości obiektów. Cóż z tego? Ano chociażby to, że możemy każdy obiekt dowolnego typu porównać z każdym innym każdego dowolnego typu za pomocą dokładnie tej samej metody. Kolejną metodą którą dziedziczymy z klasy Object jest metoda `toString()`. Metoda ta zwraca tekstową reprezentację obiektu. Ta sama metoda zwraca tekstową reprezentację każdego obiektu, niezależnie od jego typu.

Zobaczmy teraz na przykładzie, w jaki sposób deklarujemy dziedziczenie i w jaki sposób metody zdefiniowane w nadklasie są dziedziczone przez podklasę. Zdefiniujmy wpierw klasę `Product`, która mogłaby opisywać aktykuły które sprzedajemy w implementowanym przez nas sklepie internetowym. Klasa ta ma jedną metodę, która zwraca cenę towaru i metodę do przypisania tej ceny tuż po utworzeniu obiektu. 

Kod poniżej:

```java
class Product {

    private double price;

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }
}
```

Książka jest produktem i tak jak każdy produkt ma swoją cenę. Skoro książka jest produktem, to ma też wszelkie cechy produktu, zatem klasa która opisuje obiekt książki powinna dziedziczyć z klasy która opisuje produkt, tj. z klasy `Product`. 
Przykładowa implementacja klasy modelującej produkty typu książka poniżej:

```java
class Book extends Product {

    private int pagesNum;

    public Book(double price, int pagesNum) {
        this.setPrice(price);

        this.pagesNum = pagesNum;
    }

    public int getPagesNum() {
        return pagesNum;
    }
}
```

Zwróćmy uwagę na słówko kluczowe `extends` w deklaracji klasy. To właśnie w ten sposób oznaczamy, że klasa `Book` dziedziczy z klasy `Product`. 

Zauważmy, że implementując konstruktor w klasie `Book` posłużyliśmy się odziedziczoną metodą `setPrice(...)` aby zapisać cenę książki. Co więcej, klasa `Book` dziedziczy nie tylko metody zdefiniowane w klasie `Product`, tj. metody `setPrice(...)` i `getPrice()`, ale także metody odziedziczone przez nią z klasy `Object`. Klasa `Product` nie dziedziczy jawnie z żadnej klasy, a więc - zgodnie z tym co sobie już powiedzieliśmy - dziedziczy niejawnie z klasy `Object`. Dziedziczenie działa przechodnio, tak więc metody odziedziczone przez klasę `Product` przechodzą dalej, do dziedziczącej z niej klasy `Book`.

## Zadanie -1
#### [Przesłanianie metod](http://naukajavy.pl/kurs-jezyka-java/92-przeslanianie-metod)

Przesłonięcie metody to implementacja na nowo metody, którą odziedziczyliśmy z klasy nadrzędnej. Mechanizm ten daje nam możliwość dostosowania implementacji metod do specyfiki podklasy.

Jak wiemy każda klasa dziedziczy z klasy Object metodę `toString()`. Metoda ta ma za zadanie zwrócić tekstowy opis obiektu. Standardowa implementacja metody zwraca jako opis obiektu nazwę klasy oraz nic nie mówiący kod będący wynikiem funkcji skrótu. Jednym słowem – opis ten jest słaby i należałoby go zmienić. Zmienić ten opis możemy naturalnie poprzez przesłonięcie w naszej klasie metody `toString()`. W klasie Book opisującej książkę metoda ta mogłaby mieć następującą implementację:

```java
class Book extends Product {

    private int pagesNum;
    private String title;
    private String isbn;

    public Book(double price, int pagesNum) {
        this.setPrice(price);

        this.pagesNum = pagesNum;
    }

    public String toString() {
        return "Książka '" + getTitle() + "', ISBN: " + getIsbn();
    }

    public String getIsbn() {
        return isbn;
    }

    public void setIsbn(String isbn) {
        this.isbn = isbn;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }
    
    public int getPagesNum() {
        return pagesNum;
    }
}
```

## Zadanie 0
#### [Polimorfizm](http://naukajavy.pl/kurs-jezyka-java/93-polimorfizm)

Korzyści jakie możemy osiągnąć z tytułu dziedziczenia byłyby bardzo ograniczone, gdyby nie polimorfizm. Polimorfizm oznacza możliwość traktowania obiektów różnych podtypów pewnego wspólnego typu w taki sam sposób. Za chwilkę przekonamy się, co to oznacza i jak bardzo potrafi ułatwić programowanie. 

Skoro książka jest produktem – w języku Java oznacza to, że klasa `Book` dziedziczy z klasy `Product` – to przecież możemy potraktować książkę jak produkt. Skoro możemy książkę potraktować jak produkt, to możemy obiekt reprezentujący konkretną książkę, a więc obiekt typu Book, przypisać do referencji typu Product. 

Możemy więc napisać:

`Product myProd = new Book(39.90, 210);`

Oczywiście w naszym sklepie będziemy sprzedawali też inne artykuły, nie tylko książki. Będziemy więc mieli także klasy takie jak `MusicCD`, `GameCD` i `AppCD` opisujące kolejno płyty CD czy DVD z muzyką, grami i aplikacjami. Wszystkie one będą dziedziczyły z klasy `Product` i wszystkie one mogą być przetwarzane w systemie tak jak produkty. 

Możemy więc napisać:

`Product myProd = new MusicCD(19.90, "The Beatles", "A Hard Day's Night");`

a nstępnie:

`myProd.getPrice();`

Następnie należy zaimplementować w naszej aplikacji sklepu internetowego koszyk, który przechowuje wybrane przez klienta artykuły i który potrafi odpowiedzieć na pytanie – jaka jest łączna wartość zamówienia. Aby policzyć wartość zamówienia trzeba zsumować ceny poszczególnych produktów, niezależnie od tego, jakiego typu są te produkty. Wygodnie jest móc traktować wszystkie obiekty reprezentujące produkty takie jak książki, płyty muzyczne, gry i wszelakie inne w ten sam sposób. Możemy wówczas przejrzeć kolekcję produktów z koszyka i dla każdego z nich wywołać metodę `getPrice()`. Suma wyników będzie wartością zamówienia.

Łącząc ze sobą mechanizm polimorfizmu i przesłaniania metod możemy osiągnąć jeszcze ciekawsze rezultaty. Przykładowo, możemy zdefiniować produkt `BonusPackage`, tj. produkt, który jest zbiorem dowolnych innych produktów oferowanych w pakiecie po promocyjnej cenie. Moglibyśmy wówczas w klasie `BonusPackage` przesłonić implementację metody `getPrice()` tak, aby metoda ta sumowała ceny wszystkich produktów z pakietu i na końcu odejmowała od tej sumy np. 10%.

Zauważmy, że wprowadzenie produktu `BonusPackage` nie pociąga za sobą w skutkach konieczności zmiany klasy opisującej koszyk i funkcjonalności liczenia wartości zamówienia. Tak jak do tej pory sumujemy wyniki wywołania metody `getPrice()` dla każdego obiektu. Z punktu widzenia tego algorytmu jest nie istotne, że niektóre z tych obiektów, te które są typu `BonusPackage` mają zmienioną implementację metody `getPrice()`.

## Zadanie 1

Zaimplementuj klasę `Person`. Klasa ta powinna umożliwiać przechowywanie takich wartości jak:
`name`, `surname`, `dateOfBirth`, `sex` oraz cechować się zachowaniami w postaci
zaimplementowanej metody zwracającej informację o osobie (`showInfo()`). 

### Uwaga
Data powinna być zwracana w metodzie showInfo w formacie `yyyy-MM-dd`!

Następnie zdefiniuj klasy dziedziczące po klasie `Person`:

1. `Student` – klasa powinna zawierać następujące składowe:

* pola
  - `indexNumber` (`int`) 
  - `typeOfStudies` (`String`)
  - `fieldOfStudy` (`String`)
  - `yearOfStudy` (`int`)
  
* metody 
  - zwracającą informację o studencie (należy przesłonić metodę odziedziczoną po klasie `Person`).
  
2. `Lecturer` – klasę tę należy zaprojektować samodzielnie (poprzez analogię do klasy `Student`) wykazując się pomysłowością i inwencją twórczą. 

## Zadanie 2

Zaimplementuj klasę `Point2D`, która przechowuje informacje opisujące punkt na płaszczyźnie dwuwymiarowej (współrzędne `x` oraz `y`). 

Klasa `Point2D` powinna:

* Posiadać dwa konstruktory -  bezparametrowy ustawiający pola na wartość 0, oraz przyjmujący dwa argumenty i ustawiający pola obiektu zgodnie z podanymi parametrami
* Posiadać metodę `randomPoint()` losującą współrzędne punktu na płaszczyźnie. Współrzędne mają być losowane w zakresie od -10 do 10
* Posiadać przesłoniętą metodę `toString()` tak aby wyświetlała informacje o współrzędnych punktu w płaszczyźnie

Zaimplementuj klasę `Point3D` stanowiącą rozszerzenie klasy `Point2D`.

Klasa `Point3D` powinna:

* Posiadać wszystkie cechy klasy `Point2D` a ponadto zostać rozszeżona o dodatkowe pole opisujące trzeci wymiar `z` (konstruktor zparametryzowany powinien posiadać obsługę dodatkowego pola)
* Posiadać przesłoniętą metode `RandomPoint` z klasy `Point2D` tak aby losowała również trzeci wymiar
* Przesłoniętą metodę `toString()` tak aby wyświetlała informacje o współrzędnych punktu w przestrzeni

W klasie `Main` utwórz obiekty obu klas i przetestuj działanie. Następnie utwórz dwie tablice 100-elementowe, jedna dla klasy `Point2D` o nazwie `array2D`, a druga dla klasy `Point3D` o nazwie `array3D`. W obydwu tablicach wylosuj dla wszystkich elementów punkty przy użyciu utworzonych wcześniej metod. Sprawdź czy w tablicy `array3D` i `array2D` istnieją elementy mające wspólne składowe (x,y) tj. istnieją punkty `point2D(x1,y1)` i `point3D(x2,y2,z2)`, takie że x1=x2 i y1=y2. Jeśli takie pary istnieją wypisz je na ekranie (wykorzystaj metodę `toString()`. 

###### W oparciu o opracowanie dr inż. Wojciecha Kozła

###### Źródła

* http://naukajavy.pl/kurs-jezyka-java/91-dziedziczenie
* http://naukajavy.pl/kurs-jezyka-java/92-przeslanianie-metod
* http://naukajavy.pl/kurs-jezyka-java/93-polimorfizm
