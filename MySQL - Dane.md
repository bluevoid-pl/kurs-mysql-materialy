#### INSERT INTO

Dodaje rekord do tabeli

INSERT INTO nazwa_tabeli (kolumna1, kolumna2, kolumna3, ...)
  VALUES (wartosc1, wartosc2, wartosc3, ...);

Przykład:
```SQL
/*
CREATE TABLE uczen(
    uczen_id INT NOT NULL AUTO_INCREMENT,
    imie VARCHAR(40) NOT NULL,
    nazwisko VARCHAR(60) NOT NULL,
    data_urodzenia DATE,
    srednia_ocen DECIMAL(10,2),
    adres TEXT,
    PRIMARY KEY (uczen_id)
);
*/

INSERT INTO uczen ( imie, nazwisko, data_urodzenia, adres )
  VALUES ( 'Mateusz', 'Kifner', '2000-01-01', Null );

INSERT INTO uczen
  VALUES ( 1,'Mateusz', 'Kifner', '2000-01-01', Null, Null );

INSERT INTO uczen VALUES
  ( 3, 'Mateusz', 'Kifner', '2000-01-01', Null, Null ),
  ( 4, 'Jan', 'Kowalski', '2000-01-01', 4.2, 'ul. Kameliowa 123/45' );
```
<br>
#### SELECT

Polecenie to służy do pobierania danych z bazy danych.
```SQL
-- Pobierz wszystkie dane z tabeli
SELECT * FROM nazwa_tabeli;

-- Pobierz dane z kolumn kolumna1, kolumna2, kolumna3, ... z tabeli
SELECT kolumna1, kolumna2, kolumna3, ... FROM nazwa_tabeli;
```
<br>
Przykład:
```SQL
-- Pobierz wszystkie dane z tabeli przyklad
SELECT * FROM `przyklad`;

-- Pobierz dane z kolumn imie, nazwisko, adres z tabeli przyklad
SELECT imie, nazwisko, adres FROM przyklad;
```
<br>

#### SELECT - DISTINCT

Klauzula jest używana do usuwania duplikujących się wyników w zapytaniach. Pozwala na zwrócenie tylko unikalnych wartości w kolumnie lub zestawie kolumn.
```SQL
-- Pobierz wszystkie dane z tabeli
SELECT DISTINCT * FROM nazwa_tabeli;

-- Pobierz dane z kolumn kolumna1, kolumna2, kolumna3, ... z tabeli
SELECT DISTINCT kolumna1, kolumna2, kolumna3, ... FROM nazwa_tabeli;
```
<br>

Przykład:
```SQL
-- Pobierz wszystkie dane z tabeli przyklad
SELECT DISTINCT * FROM `przyklad`;

-- Pobierz dane z kolumn imie, nazwisko, adres z tabeli przyklad
SELECT DISTINCT imie, nazwisko, adres FROM przyklad;
```
<br>

#### SELECT - WHERE

Klauzula która służy do filtrowania danych na podstawie określonych warunków. Umożliwia pobieranie tylko tych rekordów, które spełniają podane kryteria.
```SQL
-- Pobierz wszystkie dane z tabeli, które spełniają warunek
SELECT * FROM nazwa_tabeli WHERE warunek;

-- Pobierz dane z kolumn kolumna1, kolumna2, kolumna3, ... z tabeli, które spełniają warunek
SELECT kolumna1, kolumna2, kolumna3, ...
  FROM nazwa_tabeli
  WHERE warunek;
```
<br>
Przykład:
```SQL
-- Pobierz wszystkie dane z tabeli uczen, które spełniają warunek srednia_ocen > 3
SELECT *
  FROM `uczen`
  WHERE srednia_ocen > 3;

-- Pobierz dane z kolumn imie, nazwisko, adres z tabeli przyklad, które spełniają warunek srednia_ocen > 3
SELECT imie, nazwisko, adres
  FROM uczen
  WHERE srednia_ocen > 3;
```
<br>

#### SELECT - WHERE - BETWEEN

Klauzula **`BETWEEN`** służy do wyszukiwania wartości w określonym zakresie (np. liczbowym, datowym). Zawiera wartości **początkową i końcową** (włącznie).
```SQL
SELECT kolumna1, kolumna2, ...
FROM nazwa_tabeli
WHERE kolumna BETWEEN value1 AND value2;
```
<br>
Przykład:
```
<br>
SELECT *
  FROM `uczen`
  WHERE srednia_ocen BETWEEN 2 AND 3;
```
<br>

#### SELECT - WHERE - IN

Klauzula **`IN`** służy do sprawdzania, czy wartość należy do określonego zbioru wartości. Działa jak **wiele operatorów `OR`**, ale jest czytelniejsza i bardziej wydajna.
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IN (value1, value2, ...);
```
<br>
Przykład:
```SQL
SELECT *
  FROM `uczen`
  WHERE srednia_ocen IN (2,4);

SELECT * FROM `uczen`
  WHERE IdUcznia IN (SELECT IdUcznia FROM ewidencja);
```
<br>

#### SELECT - WHERE - LIKE

Operator **`LIKE`** w MySQL służy do wyszukiwania danych w kolumnach tekstowych na podstawie wzorca. Jest często używany z symbolem wieloznacznym (`%` lub `_`) do dopasowywania częściowego.

- % zastępuje zero lub więcej znaków
- _ zastępuje dokładnie jeden znak
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna LIKE 'wzorzec'; 
```
<br>
Przykład:
```SQL
SELECT * FROM `uczen`
  WHERE imie LIKE 'J%';

SELECT * FROM `uczen`
  WHERE imie LIKE 'J__';

SELECT * FROM uczen
  WHERE nazwisko NOT LIKE '%ski';
```
<br>

#### SELECT - WHERE - NULL, NOT NULL

**`NULL`** w SQL oznacza brak wartości lub brak danych w kolumnie. Jest to specjalna wartość, która wskazuje, że brak jest konkretnej wartości (np. dla daty urodzenia osoby, której data nie została wprowadzona).
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IS NULL;

SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IS NOT NULL;
```
<br>
Przykład:
```SQL
SELECT * FROM `uczen`
  WHERE data_urodzenia IS NULL;

SELECT * FROM `uczen`
  WHERE data_urodzenia IS NOT NULL;
```
<br>
#### INSERT INTO

Dodaje rekord do tabeli

INSERT INTO nazwa_tabeli (kolumna1, kolumna2, kolumna3, ...)
  VALUES (wartosc1, wartosc2, wartosc3, ...);

Przykład:
```SQL
/*
CREATE TABLE uczen(
    uczen_id INT NOT NULL AUTO_INCREMENT,
    imie VARCHAR(40) NOT NULL,
    nazwisko VARCHAR(60) NOT NULL,
    data_urodzenia DATE,
    srednia_ocen DECIMAL(10,2),
    adres TEXT,
    PRIMARY KEY (uczen_id)
);
*/

INSERT INTO uczen ( imie, nazwisko, data_urodzenia, adres )
  VALUES ( 'Mateusz', 'Kifner', '2000-01-01', Null );

INSERT INTO uczen
  VALUES ( 1,'Mateusz', 'Kifner', '2000-01-01', Null, Null );

INSERT INTO uczen VALUES
  ( 3, 'Mateusz', 'Kifner', '2000-01-01', Null, Null ),
  ( 4, 'Jan', 'Kowalski', '2000-01-01', 4.2, 'ul. Kameliowa 123/45' );
```
<br>
#### SELECT

Polecenie to służy do pobierania danych z bazy danych.
```SQL
-- Pobierz wszystkie dane z tabeli
SELECT * FROM nazwa_tabeli;

-- Pobierz dane z kolumn kolumna1, kolumna2, kolumna3, ... z tabeli
SELECT kolumna1, kolumna2, kolumna3, ... FROM nazwa_tabeli;
```
<br>
Przykład:
```SQL
-- Pobierz wszystkie dane z tabeli przyklad
SELECT * FROM `przyklad`;

-- Pobierz dane z kolumn imie, nazwisko, adres z tabeli przyklad
SELECT imie, nazwisko, adres FROM przyklad;
```
<br>

#### SELECT - DISTINCT

Klauzula jest używana do usuwania duplikujących się wyników w zapytaniach. Pozwala na zwrócenie tylko unikalnych wartości w kolumnie lub zestawie kolumn.
```SQL
-- Pobierz wszystkie dane z tabeli
SELECT DISTINCT * FROM nazwa_tabeli;

-- Pobierz dane z kolumn kolumna1, kolumna2, kolumna3, ... z tabeli
SELECT DISTINCT kolumna1, kolumna2, kolumna3, ... FROM nazwa_tabeli;
```
<br>
Przykład:
```SQL
-- Pobierz wszystkie dane z tabeli przyklad
SELECT DISTINCT * FROM `przyklad`;

-- Pobierz dane z kolumn imie, nazwisko, adres z tabeli przyklad
SELECT DISTINCT imie, nazwisko, adres FROM przyklad;
```
<br>

#### SELECT - WHERE

Klauzula która służy do filtrowania danych na podstawie określonych warunków. Umożliwia pobieranie tylko tych rekordów, które spełniają podane kryteria.
```SQL
-- Pobierz wszystkie dane z tabeli, które spełniają warunek
SELECT * FROM nazwa_tabeli WHERE warunek;

-- Pobierz dane z kolumn kolumna1, kolumna2, kolumna3, ... z tabeli, które spełniają warunek
SELECT kolumna1, kolumna2, kolumna3, ...
  FROM nazwa_tabeli
  WHERE warunek;
```
<br>
Przykład:
```SQL
-- Pobierz wszystkie dane z tabeli uczen, które spełniają warunek srednia_ocen > 3
SELECT *
  FROM `uczen`
  WHERE srednia_ocen > 3;

-- Pobierz dane z kolumn imie, nazwisko, adres z tabeli przyklad, które spełniają warunek srednia_ocen > 3
SELECT imie, nazwisko, adres
  FROM uczen
  WHERE srednia_ocen > 3;
```
<br>


#### SELECT - WHERE - BETWEEN

Klauzula **`BETWEEN`** służy do wyszukiwania wartości w określonym zakresie (np. liczbowym, datowym). Zawiera wartości **początkową i końcową** (włącznie).
```SQL
SELECT kolumna1, kolumna2, ...
FROM nazwa_tabeli
WHERE kolumna BETWEEN value1 AND value2;
```
<br>
Przykład:
```SQL
SELECT *
  FROM `uczen`
  WHERE srednia_ocen BETWEEN 2 AND 3;
```
<br>

#### SELECT - WHERE - IN

Klauzula **`IN`** służy do sprawdzania, czy wartość należy do określonego zbioru wartości. Działa jak **wiele operatorów `OR`**, ale jest czytelniejsza i bardziej wydajna.
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IN (value1, value2, ...);
```
<br>
Przykład:
```SQL
SELECT *
  FROM `uczen`
  WHERE srednia_ocen IN (2,4);

SELECT * FROM `uczen`
  WHERE IdUcznia IN (SELECT IdUcznia FROM ewidencja);
```
<br>

#### SELECT - WHERE - LIKE

Operator **`LIKE`** w MySQL służy do wyszukiwania danych w kolumnach tekstowych na podstawie wzorca. Jest często używany z symbolem wieloznacznym (`%` lub `_`) do dopasowywania częściowego.

- % zastępuje zero lub więcej znaków
- _ zastępuje dokładnie jeden znak
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna LIKE 'wzorzec'; 
```
<br>
Przykład:
```SQL
SELECT * FROM `uczen`
  WHERE imie LIKE 'J%';

SELECT * FROM `uczen`
  WHERE imie LIKE 'J__';

SELECT * FROM uczen
  WHERE nazwisko NOT LIKE '%ski';
```
<br>
#### SELECT - WHERE - NULL, NOT NULL

**`NULL`** w SQL oznacza brak wartości lub brak danych w kolumnie. Jest to specjalna wartość, która wskazuje, że brak jest konkretnej wartości (np. dla daty urodzenia osoby, której data nie została wprowadzona).
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IS NULL;

SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IS NOT NULL;
```
<br>
Przykład:
```SQL
SELECT * FROM `uczen`
  WHERE data_urodzenia IS NULL;

SELECT * FROM `uczen`
  WHERE data_urodzenia IS NOT NULL;
```
<br>

#### SELECT - WHERE - NULL, NOT NULL

**`NULL`** w SQL oznacza brak wartości lub brak danych w kolumnie. Jest to specjalna wartość, która wskazuje, że brak jest konkretnej wartości (np. dla daty urodzenia osoby, której data nie została wprowadzona).
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IS NULL;

SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IS NOT NULL;
```
<br>
Przykład:
```SQL
SELECT * FROM `uczen`
  WHERE data_urodzenia IS NULL;

SELECT * FROM `uczen`
  WHERE data_urodzenia IS NOT NULL;
```
<br>
#### Operatory

#### Matematyczne

|Operator|Opis|
|---|---|
|=|równość|
|!=|nierówność|
|>|większe|
|<|mniejsze|
|>=|większe równe|
|<=|mniejsze równe|

#### Logiczne

|Operator|Opis|
|---|---|
|AND|i (oba warunki muszą być spełnione)|
|OR|lub (przynajmniej jeden warunek musi być spełniony)|
|NOT|nie (negacja warunku)|


#### UPDATE

Polecenie to służy do modyfikowania istniejących rekordów w tabeli bazy danych. Pozwala na zmianę wartości w jednej lub kilku kolumnach, a warunek **WHERE** określa, które wiersze mają zostać zaktualizowane. **W przypadku pominięcia klauzuli WHERE zmodyfikowane zostaną wszystkie rekordy.**
```SQL
UPDATE nazwa_tabeli
SET kolumna1 = wartosc1, kolumna2 = wartosc2, ...
WHERE warunek;
```
<br>
Przykład:
```SQL
UPDATE uczen SET imie = 'Jan', nazwisko = 'Kowalski' WHERE id = 1;

UPDATE uczen
  SET srednia_ocen = srednia_ocen + 1
  WHERE imie = 'Jan';
```
<br>

#### DELETE

Polecenie to służy do usuwania rekordów z tabeli bazy danych. Możesz usunąć wybrane wiersze przy użyciu klauzuli **WHERE**. **W przypadku pominięcia klauzuli WHERE usunięte zostaną wszystkie rekordy.**
```SQL
DELETE FROM table_name WHERE condition; 
```
<br>
Przykład:
```SQL
DELETE FROM uczen WHERE id = 1;

DELETE FROM uczen WHERE imie = 'Jan';
```
<br>


#### Zadanie

- Dodaj 3 rekordy do tabeli ``uczen``
- Usuń przedostatni rekord z użyciem `id`


#### SELECT - `LIMIT`

Klauzula ta służy do ograniczenia liczby rekordów które zostaną zwrócone.
```SQL
-- ogranicz liczbę rekordów
SELECT kolumna1, kolumna2, kolumna3, ...
  FROM nazwa_tabeli
  WHERE warunek
  LIMIT liczba_rekordow;

-- ogranicz liczbę rekordów oraz pomiń pewną ilość pierwszych
SELECT kolumna1, kolumna2, kolumna3, ...
  FROM nazwa_tabeli
  WHERE warunek
  LIMIT liczba_rekordow OFFSET ilosc_rekordow_do_pominiencia; 
```
<br>
Przykład:
```SQL
-- Pobierz pierwsze 10 rekordów z tabeli uczen,
-- które spełniają warunek srednia_ocen > 3
SELECT *
  FROM `uczen`
  WHERE srednia_ocen > 3
  LIMIT 10;

-- Pobierz 10 rekordów z tabeli uczen zaczynając od 11, które spełniają warunek srednia_ocen > 3
SELECT imie, nazwisko, adres
  FROM uczen
  WHERE srednia_ocen > 3;
  LIMIT 10 OFFSET 10;
```
<br>

#### SELECT - table aliasy

**Alias** w SQL to tymczasowa nazwa nadana tabeli lub kolumnie w celu ułatwienia odczytu i skrócenia zapytań. Alias nie zmienia struktury bazy danych – działa tylko podczas wykonywania zapytania.
```SQL
-- Alias kolumny
SELECT kolumna AS alias FROM tabela;

-- Alias tabeli
SELECT alias1.kolumna1, alias2.kolumna2
  FROM tabela1 AS alias1, tabela2 AS alias2;
```
<br>
Przykład:
```SQL
SELECT imie AS 'Imię' FROM uczen;

SELECT u.imie, u.nazwisko, k.profil_klasy
  FROM uczen as u, klasa as k;
```
<br>


#### SELECT - ORDER BY

Klauzula służy do sortowania wyników zapytania w porządku rosnącym (domyślnie) lub malejącym. Można go używać zarówno do sortowania po jednej, jak i po wielu kolumnach.
```SQL
SELECT kolumna1, kolumna2, ...
FROM nazwa_tabeli
ORDER BY kolumna1, kolumna2, ... ;

SELECT kolumna1, kolumna2, ...
FROM nazwa_tabeli
ORDER BY kolumna1, kolumna2, ... DESC;
```
<br>
Przykład:
```SQL
SELECT *
  FROM `uczen`
  ORDER BY imie;

SELECT *
  FROM `uczen`
  ORDER BY nazwisko ASC;

SELECT imie, nazwisko, adres
  FROM uczen
  ORDER BY imie, nazwisko DESC;
```
<br>

#### Funkcje

#### Agregujące

|Operator|Opis|
|---|---|
|**`COUNT()`**|Liczy liczbę wierszy w zbiorze danych.|
|**`SUM()`**|Oblicza sumę wartości w kolumnie numerycznej.|
|**`AVG()`**|Oblicza średnią wartość w kolumnie numerycznej.|
|**`MIN()`**|Zwraca najmniejszą wartość w kolumnie.|
|**`MAX()`**|Zwraca największą wartość w kolumnie.|
|**`GROUP_CONCAT()`**|Łączy wartości z wielu wierszy w jedną, tworząc ciąg znaków.|

#### Logiczne

|Operator|Opis|
|---|---|
|**`ASCII(znak)`**|Zwraca kod ASCII pierwszego znaku w ciągu znaków.|
|**`CHAR(kod)`**|Zamienia kod ASCII na odpowiadający mu znak.|
|`**LENGTH(tekst)**`|Zwraca długość ciągu znaków.|
|**`CONCAT(napis1, …)`**|Łączy dwa lub więcej ciągów znaków w jeden.|
|**``UPPER(`**tekst**`)``**|zamienia wszystkie litery w ciągu znaków na wielkie litery|
|**``LOWER(`**tekst**`)``**|zamienia wszystkie litery w ciągu znaków na małe litery.|
|TRIM(`**tekst**`)||
|**`NOW()`**|zwraca bieżącą datę i godzinę.|
|**SUBSTRING(tekst, poczatek, dlugosc)**|zwraca część ciągu znaków, zaczynając od określonej pozycji.|
|**ROUND(liczba, miejsca_po_przecinku);**|zaokrągla liczbę do określonej liczby miejsc po przecinku.|
|SIN(kat)|oblicza sinus kąta w radianach.|


#### SELECT - `GROUP BY`

Klauzula jest używana do grupowania wyników na podstawie wartości jednej lub kilku kolumn. Jest szczególnie przydatne w połączeniu z funkcjami agregującymi, takimi jak `COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()`, które operują na grupach danych.
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  GROUP BY kolumna1, kolumna2, ...;

SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  GROUP BY kolumna1, kolumna2, ...
  ORDER BY kolumna1, kolumna2, ...;
```
<br>
Przykład:
```SQL
SELECT Count(*), sreadnia_ocen
  FROM `uczen`
  GROUP BY srednia_ocen
  ORDER BY imie;
```
<br>
#### SELECT - INNER JOIN

**`INNER JOIN`** to typ łączenia tabel, który zwraca tylko te rekordy, które mają pasujące dane w obu tabelach na podstawie określonego warunku.
```SQL
SELECT kolumna1, kolumna2, ...
FROM tabela1
INNER JOIN tabela2
ON tabela1.kolumna1 = tabela2.kolumna1; 
```
<br>
Przykład:
```SQL
SELECT u.imie, u.nazwisko, e.profil_klasy
FROM uczen AS u
JOIN ewidencja AS e ON u.uczen_id = e.uczen_id;
```
<br>
#### SELECT - LEFT JOIN

Zwróci wszystkie rekordy z tabeli po lewej (np. `uczen`), nawet jeśli nie ma pasujących rekordów w tabeli po prawej (np. `ewidencja`).
```SQL
SELECT kolumna1, kolumna2, ...
FROM tabela1
LEFT JOIN tabela2
ON tabela1.kolumna1 = tabela2.kolumna2; 
```
<br>
Przykład:
```SQL
SELECT u.imie, u.nazwisko, e.profil_klasy
FROM uczen AS u
LEFT JOIN ewidencja AS e ON u.uczen_id = e.uczen_id;
```
<br>
#### SELECT - RIGHT JOIN

Zwróci wszystkie rekordy z tabeli po prawej (np. `ewidencja`), nawet jeśli nie ma pasujących rekordów w tabeli po lewej (np. `uczen`).
```SQL
SELECT kolumna1, kolumna2, ...
FROM tabela1
RIGHT JOIN tabela2
ON tabela1.kolumna1 = tabela2.kolumna2; 
```
<br>
Przykład:
```SQL
SELECT u.imie, u.nazwisko, e.profil_klasy
FROM uczen AS u
RIGHT JOIN ewidencja AS e ON u.uczen_id = e.uczen_id;
```
<br>


#### SELECT - `CROSS JOIN`

Klauzula ta **`CROSS JOIN`** to typ łączenia tabel, który zwraca iloczyn kartezjański obu tabel, czyli wszystkie możliwe kombinacje rekordów z obu tabel, bez względu na warunki dopasowania. do ograniczenia liczby rekordów które zostaną zwrócone.
```SQL
SELECT kolumna1, kolumna2, ...
FROM tabela1
CROSS JOIN tabela2; 
```
<br>
Przykład:
```SQL
SELECT u.imie, u.nazwisko, e.profil_klasy
FROM uczen AS u
RIGHT JOIN ewidencja AS e;
```
<br>

#### SELECT - `FULL OUTER JOIN` ----

**`FULL OUTER JOIN`** to typ łączenia tabel, który zwraca wszystkie rekordy z obu tabel, łącząc je na podstawie warunku, a dla rekordów, które nie mają pasujących danych w drugiej tabeli, wstawia wartości **NULL**.
```SQL
SELECT * FROM t1
LEFT JOIN t2 ON t1.id = t2.id
UNION ALL
SELECT * FROM t1
RIGHT JOIN t2 ON t1.id = t2.id
WHERE t1.id IS NULL
```
<br>
Przykład:
```SQL
```
<br>

#### SELECT - **Podzapytani**a

**Podzapytania** to zapytania, które są osadzone w innym zapytaniu, a ich wyniki mogą być używane w klauzulach **`SELECT`**, **`WHERE`**, **`FROM`** lub **`HAVING`**. Podzapytania umożliwiają bardziej złożone operacje i analizy na danych, umożliwiając wplecenie wyników zapytania w inne zapytanie.
```SQL
SELECT * FROM tabela1, (SELECT kolumna1 FROM tabela2) as kolumna;

SELECT * FROM tabela1 WHERE kolumna1 in (SELECT kolumna1 FROM tabela2);
```
<br>
Przykład:
```SQL
SELECT imie,
       (SELECT AVG(ocena) FROM ewidencja WHERE id_uczen = uczen.id_uczen) AS srednia_ocena
FROM uczen;

SELECT imie, nazwisko
FROM uczen
WHERE id_uczen IN
   (SELECT id_uczen
    FROM ewidencja
    GROUP BY id_uczen
    HAVING AVG(ocena) > 4.0);
```
<br>



#### SELECT - WHERE - NULL, NOT NULL

**`NULL`** w SQL oznacza brak wartości lub brak danych w kolumnie. Jest to specjalna wartość, która wskazuje, że brak jest konkretnej wartości (np. dla daty urodzenia osoby, której data nie została wprowadzona).
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IS NULL;

SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  WHERE kolumna IS NOT NULL;
```
<br>
Przykład:
```SQL
SELECT * FROM `uczen`
  WHERE data_urodzenia IS NULL;

SELECT * FROM `uczen`
  WHERE data_urodzenia IS NOT NULL;

```
<br>

#### Operatory

#### Matematyczne

|Operator|Opis|
|---|---|
|=|równość|
|!=|nierówność|
|>|większe|
|<|mniejsze|
|>=|większe równe|
|<=|mniejsze równe|

#### Logiczne

|Operator|Opis|
|---|---|
|AND|i (oba warunki muszą być spełnione)|
|OR|lub (przynajmniej jeden warunek musi być spełniony)|
|NOT|nie (negacja warunku)|


#### UPDATE

Polecenie to służy do modyfikowania istniejących rekordów w tabeli bazy danych. Pozwala na zmianę wartości w jednej lub kilku kolumnach, a warunek **WHERE** określa, które wiersze mają zostać zaktualizowane. **W przypadku pominięcia klauzuli WHERE zmodyfikowane zostaną wszystkie rekordy.**
```SQL
UPDATE nazwa_tabeli
SET kolumna1 = wartosc1, kolumna2 = wartosc2, ...
WHERE warunek;
```
<br>
Przykład:
```SQL
UPDATE uczen SET imie = 'Jan', nazwisko = 'Kowalski' WHERE id = 1;

UPDATE uczen
  SET srednia_ocen = srednia_ocen + 1
  WHERE imie = 'Jan';
```
<br>

#### DELETE

Polecenie to służy do usuwania rekordów z tabeli bazy danych. Możesz usunąć wybrane wiersze przy użyciu klauzuli **WHERE**. **W przypadku pominięcia klauzuli WHERE usunięte zostaną wszystkie rekordy.**
```SQL
DELETE FROM table_name WHERE condition; 
```
<br>
Przykład:
```SQL
DELETE FROM uczen WHERE id = 1;

DELETE FROM uczen WHERE imie = 'Jan';
```
<br>

#### Zadanie

- Dodaj 3 rekordy do tabeli ``uczen``
- Usuń przedostatni rekord z użyciem `id`



#### SELECT - `LIMIT`

Klauzula ta służy do ograniczenia liczby rekordów które zostaną zwrócone.
```SQL
-- ogranicz liczbę rekordów
SELECT kolumna1, kolumna2, kolumna3, ...
  FROM nazwa_tabeli
  WHERE warunek
  LIMIT liczba_rekordow;

-- ogranicz liczbę rekordów oraz pomiń pewną ilość pierwszych
SELECT kolumna1, kolumna2, kolumna3, ...
  FROM nazwa_tabeli
  WHERE warunek
  LIMIT liczba_rekordow OFFSET ilosc_rekordow_do_pominiencia; 
```
<br>
Przykład:
```SQL
-- Pobierz pierwsze 10 rekordów z tabeli uczen,
-- które spełniają warunek srednia_ocen > 3
SELECT *
  FROM `uczen`
  WHERE srednia_ocen > 3
  LIMIT 10;

-- Pobierz 10 rekordów z tabeli uczen zaczynając od 11, które spełniają warunek srednia_ocen > 3
SELECT imie, nazwisko, adres
  FROM uczen
  WHERE srednia_ocen > 3;
  LIMIT 10 OFFSET 10;
```
<br>


#### SELECT - table aliasy

**Alias** w SQL to tymczasowa nazwa nadana tabeli lub kolumnie w celu ułatwienia odczytu i skrócenia zapytań. Alias nie zmienia struktury bazy danych – działa tylko podczas wykonywania zapytania.
```SQL
-- Alias kolumny
SELECT kolumna AS alias FROM tabela;

-- Alias tabeli
SELECT alias1.kolumna1, alias2.kolumna2
  FROM tabela1 AS alias1, tabela2 AS alias2;
```
<br>
Przykład:
```SQL
SELECT imie AS 'Imię' FROM uczen;

SELECT u.imie, u.nazwisko, k.profil_klasy
  FROM uczen as u, klasa as k;
```
<br>

#### SELECT - ORDER BY

Klauzula służy do sortowania wyników zapytania w porządku rosnącym (domyślnie) lub malejącym. Można go używać zarówno do sortowania po jednej, jak i po wielu kolumnach.
```SQL
SELECT kolumna1, kolumna2, ...
FROM nazwa_tabeli
ORDER BY kolumna1, kolumna2, ... ;

SELECT kolumna1, kolumna2, ...
FROM nazwa_tabeli
ORDER BY kolumna1, kolumna2, ... DESC;
```
<br>
Przykład:
```SQL
SELECT *
  FROM `uczen`
  ORDER BY imie;

SELECT *
  FROM `uczen`
  ORDER BY nazwisko ASC;

SELECT imie, nazwisko, adres
  FROM uczen
  ORDER BY imie, nazwisko DESC;
```
<br>


#### Funkcje

#### Agregujące

|Operator|Opis|
|---|---|
|**`COUNT()`**|Liczy liczbę wierszy w zbiorze danych.|
|**`SUM()`**|Oblicza sumę wartości w kolumnie numerycznej.|
|**`AVG()`**|Oblicza średnią wartość w kolumnie numerycznej.|
|**`MIN()`**|Zwraca najmniejszą wartość w kolumnie.|
|**`MAX()`**|Zwraca największą wartość w kolumnie.|
|**`GROUP_CONCAT()`**|Łączy wartości z wielu wierszy w jedną, tworząc ciąg znaków.|

#### Logiczne

|Operator|Opis|
|---|---|
|**`ASCII(znak)`**|Zwraca kod ASCII pierwszego znaku w ciągu znaków.|
|**`CHAR(kod)`**|Zamienia kod ASCII na odpowiadający mu znak.|
|`**LENGTH(tekst)**`|Zwraca długość ciągu znaków.|
|**`CONCAT(napis1, …)`**|Łączy dwa lub więcej ciągów znaków w jeden.|
|**``UPPER(`**tekst**`)``**|zamienia wszystkie litery w ciągu znaków na wielkie litery|
|**``LOWER(`**tekst**`)``**|zamienia wszystkie litery w ciągu znaków na małe litery.|
|TRIM(`**tekst**`)||
|**`NOW()`**|zwraca bieżącą datę i godzinę.|
|**SUBSTRING(tekst, poczatek, dlugosc)**|zwraca część ciągu znaków, zaczynając od określonej pozycji.|
|**ROUND(liczba, miejsca_po_przecinku);**|zaokrągla liczbę do określonej liczby miejsc po przecinku.|
|SIN(kat)|oblicza sinus kąta w radianach.|

#### SELECT - `GROUP BY`

Klauzula jest używana do grupowania wyników na podstawie wartości jednej lub kilku kolumn. Jest szczególnie przydatne w połączeniu z funkcjami agregującymi, takimi jak `COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()`, które operują na grupach danych.
```SQL
SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  GROUP BY kolumna1, kolumna2, ...;

SELECT kolumna1, kolumna2, ...
  FROM nazwa_tabeli
  GROUP BY kolumna1, kolumna2, ...
  ORDER BY kolumna1, kolumna2, ...;
```
<br>
Przykład:
```SQL
SELECT Count(*), sreadnia_ocen
  FROM `uczen`
  GROUP BY srednia_ocen
  ORDER BY imie;
```
<br>

#### SELECT - INNER JOIN

**`INNER JOIN`** to typ łączenia tabel, który zwraca tylko te rekordy, które mają pasujące dane w obu tabelach na podstawie określonego warunku.
```SQL
SELECT kolumna1, kolumna2, ...
FROM tabela1
INNER JOIN tabela2
ON tabela1.kolumna1 = tabela2.kolumna1; 
```
<br>
Przykład:
```SQL
SELECT u.imie, u.nazwisko, e.profil_klasy
FROM uczen AS u
JOIN ewidencja AS e ON u.uczen_id = e.uczen_id;
```
<br>
#### SELECT - LEFT JOIN

Zwróci wszystkie rekordy z tabeli po lewej (np. `uczen`), nawet jeśli nie ma pasujących rekordów w tabeli po prawej (np. `ewidencja`).
```SQL
SELECT kolumna1, kolumna2, ...
FROM tabela1
LEFT JOIN tabela2
ON tabela1.kolumna1 = tabela2.kolumna2; 
```
<br>
Przykład:
```SQL
SELECT u.imie, u.nazwisko, e.profil_klasy
FROM uczen AS u
LEFT JOIN ewidencja AS e ON u.uczen_id = e.uczen_id;
```
<br>

#### SELECT - RIGHT JOIN

Zwróci wszystkie rekordy z tabeli po prawej (np. `ewidencja`), nawet jeśli nie ma pasujących rekordów w tabeli po lewej (np. `uczen`).
```SQL
SELECT kolumna1, kolumna2, ...
FROM tabela1
RIGHT JOIN tabela2
ON tabela1.kolumna1 = tabela2.kolumna2; 
```
<br>
Przykład:
```SQL
SELECT u.imie, u.nazwisko, e.profil_klasy
FROM uczen AS u
RIGHT JOIN ewidencja AS e ON u.uczen_id = e.uczen_id;
```
<br>
#### SELECT - `CROSS JOIN`

Klauzula ta **`CROSS JOIN`** to typ łączenia tabel, który zwraca iloczyn kartezjański obu tabel, czyli wszystkie możliwe kombinacje rekordów z obu tabel, bez względu na warunki dopasowania. do ograniczenia liczby rekordów które zostaną zwrócone.
```SQL
SELECT kolumna1, kolumna2, ...
FROM tabela1
CROSS JOIN tabela2; 
```
<br>
Przykład:
```SQL
SELECT u.imie, u.nazwisko, e.profil_klasy
FROM uczen AS u
RIGHT JOIN ewidencja AS e;
```
<br>
#### SELECT - `FULL OUTER JOIN` ----

**`FULL OUTER JOIN`** to typ łączenia tabel, który zwraca wszystkie rekordy z obu tabel, łącząc je na podstawie warunku, a dla rekordów, które nie mają pasujących danych w drugiej tabeli, wstawia wartości **NULL**.
```SQL
SELECT * FROM t1
LEFT JOIN t2 ON t1.id = t2.id
UNION ALL
SELECT * FROM t1
RIGHT JOIN t2 ON t1.id = t2.id
WHERE t1.id IS NULL
```
<br>
Przykład:
```SQL
```
<br>

#### SELECT - **Podzapytani**a

**Podzapytania** to zapytania, które są osadzone w innym zapytaniu, a ich wyniki mogą być używane w klauzulach **`SELECT`**, **`WHERE`**, **`FROM`** lub **`HAVING`**. Podzapytania umożliwiają bardziej złożone operacje i analizy na danych, umożliwiając wplecenie wyników zapytania w inne zapytanie.
```SQL
SELECT * FROM tabela1, (SELECT kolumna1 FROM tabela2) as kolumna;

SELECT * FROM tabela1 WHERE kolumna1 in (SELECT kolumna1 FROM tabela2);
```
<br>
Przykład:
```SQL
SELECT imie,
       (SELECT AVG(ocena) FROM ewidencja WHERE id_uczen = uczen.id_uczen) AS srednia_ocena
FROM uczen;

SELECT imie, nazwisko
FROM uczen
WHERE id_uczen IN
   (SELECT id_uczen
    FROM ewidencja
    GROUP BY id_uczen
    HAVING AVG(ocena) > 4.0);
    ```
