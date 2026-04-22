### Podstawy

#### Wczytywanie plików bez znanego rozmiaru, pojedyncze elementy
```cpp
#include <iostream>
#include <fstream>
#include <vector>

int main(){
  // Otwiera plik do odczytu (ifstream to skrócone `input file stream`)
  std::ifstream plik( "plik_z_zadaniem.txt" );
  // Sprawdzamy czy plik został poprawnie otwarty
  if( !plik.is_open() ){
    std::cout << "Blad pliku" <<std::endl;
    // Zwracamy wartość inną niż zero aby zasygnalizować błąd
    return -1;
  }
  // W nawiasach `<>` w std::vector musi być zawarty jeden argument który oznacza typ danych zawartych w tablicy dynamicznej
  std::vector<std::string> dane;
  // Pętla wykonuje się tak długo jak są dane do odczytania w pliku.
  // !!! Jeśli zapomnieliśmy wczytać dane w środku while będzie się on wykonywał w nieskończoność
  while( !plik.eof() ){
    std::string temp;
    // Wczytujemy dane operatorem `>>` bierze on dane z pliku o typie zmiennej temp do następnego znaku białego(spacji, tabulatora, nowej linii).
    // W przypadku gdy temp jest typu char zostanie wczytany pojedynczy znak, a znaki białe będą pomijane.
    plik >> temp;
    // Pomijamy puste linie.
    if( temp == "" ){
      continue;
    }
    // Dodajemy elementy na końcu vector-a dane.
    dane.push_back( temp );
  }
  // Zamykamy plik ręcznie.
  // Pominięcie tej metody może to powodować błędy, ale nie musi co jest ciężkie do debugowania.
  plik.close();

  // Przechodzimy po danych aby sprawdzić czy są poprawnie wczytane
  for( int i=0; i<dane.size(); i++ ){
    std::cout << dane[i] << std::endl;
  }
  return 0;
}
```
#### Wczytywanie plików bez znanego rozmiaru, pary
```cpp
#include <iostream>
#include <fstream>
#include <vector>
int main() {
    std::ifstream plik("plik_z_zadaniem.txt");
    if (!plik.is_open()) {
        std::cout << "Blad pliku" << std::endl;
        return -1;
    }
    // W nawiasach `<>` w std::vector musi być zawarty jeden argument który oznacza typ danych zawartych w tablicy dynamicznej
    std::vector<std::pair<std::string,int>> dane;
    while (!plik.eof()) {
        // Definiujemy zmienne o takim typie jak w pair
        std::string temp;
        int temp2;
        // Wczytujemy dane operatorem `>>` bierze on dane z pliku o typie zmiennej temp do następnego znaku białego(spacji, tabulatora, nowej linii).
        // W przypadku gdy temp jest typu char zostanie wczytany pojedynczy znak, a znaki białe będą pomijane.
        plik >> temp;
        plik >> temp2;
        // Pomijamy puste linie. Sprawdzamy tylko pierwszy element w linii, bo jeśli linia jest pusta reszta też będzie pusta.
        if (temp == "") {
            continue;
        }
        // Dodajemy elementy na końcu vector-a dane, podajemy je jako listę inicjalizacyjną(w nawiasach `{}`) lub używamy funkcji std::makepair.
        dane.push_back({ temp, temp2 });
        //dane.push_back(std::make_pair( temp, temp2 ));
    }
    plik.close();
    for (int i = 0; i < dane.size(); i++) {
        // Pamiętamy że pair zawiera w sobie elementy first i second.
        std::cout << dane[i].first << ' ' << dane[i].second << std::endl;
    }
    return 0;
}
```
#### Wczytywanie plików bez znanego rozmiaru, pary alternatywnie
```cpp

#include <iostream>
#include <fstream>
#include <vector>
int main() {
    std::ifstream plik("plik_z_zadaniem.txt");
    if (!plik.is_open()) {
        std::cout << "Blad pliku" << std::endl;
        return -1;
    }
    // W nawiasach `<>` w std::vector musi być zawarty jeden argument który oznacza typ danych zawartych w tablicy dynamicznej
    std::vector<std::pair<std::string,int>> dane;
    while (!plik.eof()) {
        // Definujemy parę pomocniczą
        std::pair<std::string, int> temp;
        plik >> temp.first;
        plik >> temp.second;
        // Pomijamy puste linie. Sprawdzamy tylko pierwszy element w lini, bo jesli linia jest pusta reszta też będzie pusta.
        if (temp.first == "") {
            continue;
        }
        // Dodajemy parę na końcu vector-a dane
        dane.push_back(temp);
    }
    plik.close();
    for (int i = 0; i < dane.size(); i++) {
        std::cout << dane[i].first << ' ' << dane[i].second << std::endl;
    }
    return 0;
}
```
#### Wczytywanie plików bez znanego rozmiaru, strukt-y

Strukt-y działają podobnie do par, ale jest utrudnione używanie std::sort z nimi. Ich największą zaletą jest możliwość nadania nazw zmiennym w środku obiektów, mogą one przechowywać dowolną ilość zmiennych, w tym tablic i innych strukt-ów i par.  
Przykład:
```cpp
struct Vector3 {
    double x;
    double y;
    double z;
}
```


```cpp
#include <iostream>
#include <fstream>
#include <vector>

struct DataPoint {
    int M;
    int a;
    int b;
    std::string nazwa;
};

int main() {
    std::ifstream plik("plik_z_zadaniem.txt");
    if (!plik.is_open()) {
        std::cout << "Blad pliku" << std::endl;
        return -1;
    }
    // W nawiasach `<>` podajemy nazwę struct-a `DataPoint`
    std::vector<DataPoint> dane;
    while (!plik.eof()) {
        // Definiujemy parę pomocniczą
        DataPoint temp;
        // Nadajemy pierwszemu elementowi wartość z poza zakresu aby wykluczyć puste linie później
        temp.M = INT_MIN;
        plik >> temp.M;
        plik >> temp.a;
        plik >> temp.b;
        plik >> temp.nazwa;
        // Pomijamy puste linie. Sprawdzamy tylko pierwszy element w linii, bo jeśli linia jest pusta reszta też będzie pusta.
        if (temp.M == INT_MIN) {
            continue;
        }
        // Dodajemy elementy na końcu vector-a dane
        dane.push_back(temp);
    }

    plik.close();
    for (int i = 0; i < dane.size(); i++) {
        std::cout << dane[i].M << ' ' << dane[i].a << ' ' << dane[i].b << ' ' << dane[i].nazwa << std::endl;
    }
    return 0;
}
```
#### Wczytywanie plików z znanym rozmiarem, tablica std::array 3 wymiarowa.
```cpp

#include <iostream>
#include <fstream>
#include <array>

int main()
{
    std::ifstream plik("plik_z_zadaniem.txt");
    if (!plik.is_open()) {
        std::cout << "Blad pliku" << std::endl;
        return -1;
    }
    // W nawiasach `<>` array podajemy typ przechowywanych danych oraz ilość elementów;
    // Ten array będzie przyjmować index-y w zakresach dane[0-29][0-19][0-9];
    // Kolejność odnoszenia się do danych jest taka jak zagnierzdżenia, więc kolejne ilości czytamy "od końca".
    std::array< std::array< std::array< int, 10 >, 20 >, 30 > dane;
    // W pliku mamy 30 plansz które są o wymiarach 20x10
    for (int i = 0; i < dane.size(); i++) {
        // W przypadku wczytywania elementów na osi liczbowej, może wystąpić potrzeba zamiany kolejności x i y.
        for (int y = 0; y < dane[0][0].size(); y++) {
            for (int x = 0; x < dane[0].size(); x++) {
                plik >> dane[i][x][y];
            }
        }
    }

    plik.close();
    for (int i = 0; i < dane.size();i++) {
        // W przypadku wypisywania elementów musimy zamienić x i y, ponieważ zawsze wypisujemy elementy wiersz po wierszu.
        for (int y = 0; y < dane[0][0].size(); y++) {
            for (int x = 0; x < dane[0].size(); x++) {
                plik >> dane[i][x][y];
            }
            std::cout << std::endl;
        }
        std::cout << std::endl;
    }
    return 0;
}
```
### Zliczanie elementów

#### Liczenie liczb w tablicy o małym zakresie (do około 100000)
```cpp

#include <iostream>
#include <vector>
#include <array>

int main() {
    // Dane do zadania
    std::vector<int> dane = { 1, 2, 3, 100, 2, 3, 4, 5, 6 };
    // Tablica zawiera w sobie ilości poszczególnych liczb, dlatego typem danych w tablicy jest int.
    // Jako drugi argument w nawiasach `<>` podajemy maksyamlną możliwą liczbę którą można będzie znaleźć w danych.
    // Dla danych w tablicy dane jest to 100, maksymalną możliwą wartością jest około 100000, jesli ją przekroczymy to musimy użyć innego podejścia.
    std::array<int, 100> ilosci;
    // !!! Bardzo ważne !!! Zapełniamy tablicę zerami.
    ilosci.fill(0);
    // Przechodzimy po wszystkich liczbach w danych
    for (int i = 0; i < dane.size(); i++) {
        // Wyciągamy pojedynczą liczbę z tablicy dane.
        char liczba = dane[i];
        // Dodajemy jeden w miejscu gdzie index tablicy ilosci jest równy naszej liczbie.
        ilosci[liczba]++;
    }
    // TUTAJ tablica zawiera ilości liczb w tablicy
    // Można je wyświetlić tą pętlą
    for (int liczba = 0; liczba < ilosci.size(); liczba++) {
        // ilość wyciągamy podając do tablicy ilosci numer indexu równy naszej liczbie.
        int ilosc = ilosci[liczba];
        std::cout << liczba << ' ' << ilosc << std::endl;
    }
    // Ta metoda najlepiej działa jesli jest mała różnica w poszegulnych liczbach w danych, w przypadku dużych różnic lepiej jest użyć map-a.
    return 0;
}
```
#### Liczenie liczb w tablicy o dużym zakresie
```cpp
#include <iostream>
#include <vector>
#include <map>
// Ta metoda najlepiej działa jesli dane są nieciągłe.
int main() {
    // Dane do zadania
    std::vector<int> dane = { 1, 2, 3, 10000000, 2, 3, 4, 5, 6 };
    // Pierwszy argument w nawiasach `<>` to typ klucza odpowiada on typowi zliczanych elementów
    // Jako drugi argument w nawiasach `<>` podajemy typ int jako że będziemy przechowywać ilości.
    std::map<int, int> ilosci;
    // Przechodzimy po wszystkich liczbach w danych
    for (int i = 0; i < dane.size(); i++) {
        // Wyciągamy pojedynczą liczbę z tablicy dane, będziemy używali jej jako klucz w map.
        int liczba = dane[i];
        // Jeśli w map wykonamy operację na kluczu jest on dodwawany z domyślną wartością jesli nie istnieje.
        // Dodajemy jeden w miejsce klucza.
        ilosci[liczba]++;
    }
    // TUTAJ map zawiera ilości liczb w tablicy
    // Można je wyświetlić tą pętlą
    // Map przechowuje nie ciągłe dane, aby wyciągnąć z niego wszystkie wartości używamy for z auto&.
    // `p` tutaj to para klucza i wartości.
    // !!! Ta pętla pomija puste wartości.
    for (auto& p: ilosci) {
        // Wyciągamy liczbę z pary `p`
        int liczba = p.first;
        // Wyciągamy ilość z pary `p`
        int ilosc = p.second;
        std::cout << liczba << ' ' << ilosc << std::endl;
    }
    std::cout << std::endl;
    // Jesli potrzebujemy wartości z 0 można je wyświetlić tą pętlą.
    // Zakres w przykładzie jest ograniczony aby nie czekać 5 min na wykonanie tej pentli.
    for (int liczba = 9999990;liczba <= 10000000;liczba++) {
        // Sprawdzamy czy wartość jest zawarta w map-ie.
        if (ilosci.count(liczba) > 0) {
            // Metoda `.at()` zwraca dane z mapa o podanym kluczu lub wywołuje wyjątek(aka błąd) jeśli element o kluczu nie istnieje.
            // Myciągamy ilość z map, użycie metody `.at()` na mapie jest tutaj opcionalne ponieważ sprawdziliśmy już czy element się znajduje w map-ie.
            int ilosc = ilosci.at(liczba);
            std::cout << liczba << ' ' << ilosc << std::endl;
        }
        // Jeśli wartość nie jest w mapie to wyświetlamy zero.
        else {
            std::cout << liczba << ' ' << 0 << std::endl;
        }
    }

    return 0;
}
```
#### Liczenie liter w słowie o stałej wielkości liter

Ten kod można znacznie skrócić i nie jest to blędem, tutaj jest przedstawiony przypadek z dokładnym omówieniem.
```cpp

#include <iostream>
#include <array>

int main() {
    // Dane do zadania
    std::string napis = "alamakota";
    // Tablica zawiera w sobie ilości poszczególnych liter, dlatego typem danych w tablicy jest int.
    // Zawieramy w niej ilości liter alfabetu Angielskiego których jest 26.
    std::array<int, 26> alfabet;
    // !!! Bardzo ważne !!! Zapełniamy tablicę zerami.
    alfabet.fill(0);
    // Przechodzimy po wszystkich literach w słowie.
    for (int i = 0; i < napis.size(); i++) {
        // wyciągamy pojedynczą literę z słowa
        char litera = napis[i];
        // liczymy numer litery w alfabecie korzystając z własności tabeli ASCII.
        // W przypadku dużych liter odejmujemy duże 'A'.
        // A w przypadku małych liter małe 'a'.
        int index = litera - 'a';
        // Dodajemy jeden w miejscu gdzie w alfabecie dana litera odpowiada indexowi tablicy.
        alfabet[index]++;
    }
    // TUTAJ tablica zawiera ilości liter w słowie
    // Można je wyświetlić tą pętlą
    for (int nr_w_alfabecie = 0; nr_w_alfabecie < alfabet.size(); nr_w_alfabecie++) {
        // Ilość wyciągamy podając do tablicy alfabet numer w alfabecie odpowiadający danej literce.
        int ilosc = alfabet[nr_w_alfabecie];
        // Literkę otrzymujemy poprzez dodanie odstępu w ASCII małego 'a' dla małych liter i dużego 'A' dla dużych liter zgodnie z własnościami tabeli ASCII.
        char litera = nr_w_alfabecie + 'a';
        std::cout << litera << ' ' << ilosc << std::endl;
    }
    return 0;
}
```
#### Liczenie znaków w zdaniu

Ten kod można znacznie skrócić i nie jest to blędem, tutaj jest przedstawiony przypadek z dokładnym omówieniem.
```cpp

#include <iostream>
#include <array>

// W tym zadaniu wyświetlamy wszystkie znaki ASCII extended, niekture z nich nie wyświetlają się w konsoli
// lub zajmują wiele linii, dodtkowo jest symbol dzwonka który powoduje zagranie dzwięku powiadomienie, jest to zamierzone.

int main() {
    // Dane do zadania
    std::string napis = "Ala ma kota?! A kot ma ale...";
    // Tablica zawiera w sobie ilości poszczególnych znaków, dlatego typem danych w tablicy jest int.
    // Zawieramy w niej ilości znaków, w ASCII jest to 128, w rozszeżonym ASCII jest to 256.
    std::array<int, 256> znaki;
    // !!! Bardzo ważne !!! Zapełniamy tablicę zerami.
    znaki.fill(0);
    // Przechodzimy po wszystkich znakach w zdaniu.
    for (int i = 0; i < napis.size(); i++) {
        // wyciągamy pojedynczy znakach z zdania
        char litera = napis[i];
        // przekształcamy kod ASCII extended z char( od -128 do 127 ) do int(od 0 do 256) aby ta wartość była poprawnym indexem w tablicy
        int index = litera +128;
        // Dodajemy jeden w miejscu gdzie dany znak odpowiada indexowi tablicy.
        znaki[index]++;
    }
    // TUTAJ tablica zawiera ilości liter w słowie
    // Można je wyświetlić tą pętlą
    for (int nr_w_ascii = 0; nr_w_ascii < znaki.size(); nr_w_ascii++) {
        // Ilość wyciągamy podając do tablicy znaki numer w ASCII odpowiadający danemu znakowi( przekształcenie w char mozna pominąć, patrz niżej ).
        int ilosc = znaki[nr_w_ascii];
        // Konwertujemy `nr_w_ascii` na char, przekształcenie można pominąć ponieważ char przechowuje zakres od -128 do 127,
        // zajedzie tu więc overflow i wszystkie wartości powyrzej 127 będą ujemne, aka 128 => -128, 129 => -127, 130 => -126 itd.
        // To samo można osiągnąć poprzez przypisanie `nr_w_ascii` do zmiennej typu char.
        std::cout <<  (char)nr_w_ascii << ' ' << ilosc << std::endl;
    }

    return 0;
}
```
#### Przykładowa konwersja z systemu liczbowego piątkowego na dziesiętny.
```cpp

int pent_to_dec(string a)
{
  int potega = 1;
  int wynik = 0;
  for (int i = a.size() - 1; i >= 0; i--)
  {
    int cyfra = a[i] - '0';
    wynik += cyfra * potega;
    potega *= 5;
  }
  return wynik;
}

string dec_to_pent(int a)
{
  if (a == 0){
    return "0";
  }

  string wynik;
  while (a > 0)
  {
    int cyfra = a % 5;
    a = a / 5;
    wynik.insert(0,1,(char)cyfra + '0');
  }
  return wynik;
}
```
#### Funkcja do rozkładania napisu z użyciem separatora
```cpp

std::vector<std::string> split(std::string str, std::string separator) {
    // Utwórz wektor do przechowywania wynikowych podciągów
    std::vector<std::string> result;

    // Jeśli separator jest pusty, zwróć cały napis jako jeden element
    if (separator.empty()) {
        result.push_back(str);
        return result;
    }

    // Pozycja początkowa do wyszukiwania
    size_t start = 0;

    // Znajdź pierwsze wystąpienie separatora w napisie
    size_t end = str.find(separator);

    // Pętla dopóki znajdowane są kolejne separatory
    while (end != -1) {
        // Wyodrębnij podciąg od 'start' do 'end' (bez 'end')
        result.push_back(str.substr(start, end - start));

        // Przesuń 'start' na znak po znalezionym separatorze
        start = end + separator.length();

        // Znajdź kolejne wystąpienie separatora, zaczynając od 'start'
        end = str.find(separator, start);
    }

    // Dodaj ostatni podciąg (po ostatnim separatorze)
    result.push_back(str.substr(start));

    // Zwróć wektor zawierający wszystkie podciągi
    return result;
}
```
#### Czy liczba jest pierwsza
```cpp

bool czy_pierwsza(int n) {
    if (n < 2) {
        return false;
    }
    for (int i = 2; i*i <= n; i++) {
        if (n % i == 0) {
            return false;
        }
    }
    return true;
}

// Sprawdzamy dla 2,4,11,22
```
#### NWD euklidesa
```cpp

int NWD(int a, int b) {
    while(a!=b) {
       if(a>b) {
           a-=b;
       } else {
           b-=a;
       }
    }
    return a;
}
```
#### NWD z definicji
```cpp
int NWD(int a, int b) {
    int i;
    // przypisujemy mniejszą z liczb do i, większa nigdy nie będzie NWD.
    if (b < a) {
        i = b;
    }
    else {
        i = a;
    }
    // Idąc w dół sprawdzamy czy liczba i jest dzielnikiem obu liczb, jeśli jest to mamy odpowiedź.
    while (i >= 2) {
        if (a % i == 0 && b % i == 0) {
            return i;
        }
        i--;
    }
    // Jeśli żadna liczba nie jest NWD to wynik to 1, bo jeden zawsze jest dzielnikiem.
    return 1;
}


// Testujemy dla 2,3  7,14  2,2  2,4
```