#### Podstawy

Pojedyncze cudzysłowy (`' '`) służą głównie do obejmowania wartości tekstowych.

Podwójne cudzysłowy (`" "`) są podobne, ale rzadziej używane.

Odwrotne apostrofy (`` ` ` ``) służą do obejmowania identyfikatorów, takich jak nazwy tabel lub kolumn.
```SQL
-- komentarz jedno liniowy
SELECT * FROM `przyklad`; -- komentarz jedno liniowy

/*
komentarz wieloliniowy
*/

SELECT * FROM `przyklad`; /*
komentarz wieloliniowy
*/ SELECT * FROM `przyklad`;
```
<br>

#### CREATE TABLE

Tworzy tabelę z podanymi kolumnami
```sql
CREATE TABLE nazwa_tabeli(
   kolumna1 typ_danych,
   kolumna2 typ_danych,
   ...
   kolumnaN typ_danych,
   PRIMARY KEY( kolumna? )
);
```
<br>
Przykład:
```SQL
CREATE TABLE uczen(
    uczen_id INT NOT NULL AUTO_INCREMENT,
    imie VARCHAR(40) NOT NULL,
    nazwisko VARCHAR(60) NOT NULL,
    data_urodzenia DATE,
    srednia_ocen DECIMAL(10,2),
    adres TEXT,
    PRIMARY KEY (uczen_id)
);
```
<br>

#### DROP TABLE

Usuwa tabelę z bazy danych
```SQL
DROP TABLE nazwa_tabeli;
```
<br>
Przykład:
```SQL
DROP TABLE uczen;
```
<br>

#### ALTER TABLE

Pozwala na modyfikację kolumn w tabeli.
```SQL
-- Dodaje nową kolumnę
ALTER TABLE nazwa_tabeli ADD kolumna typ_danych;

-- Usuwa kolumnę z tabeli
ALTER TABLE nazwa_tabeli DROP COLUMN kolumna;

-- Modyfikuje kolumnę w tabeli
ALTER TABLE nazwa_tabeli MODIFY COLUMN kolumna typ_danych;
```
<br>
Przykład:
```SQL
-- Dodaje kolumnę obecnosci do tabeli uczen
ALTER TABLE uczen ADD obecnosci INT NOT NULL DEFAULT 0;

-- Usuwa kolumnę obecnosci z tabeli uczen
ALTER TABLE uczen DROP COLUMN obecnosci;

-- Zmienia typ kolumny srednia_ocen w tabeli uczen z DECIMAL(10,2) na FLOAT
ALTER TABLE uczen MODIFY COLUMN srednia_ocen FLOAT;
```
<br>
#### Zadanie

Utwórz 3 tabele w bazie danych:

Uczen

| Nazwa    | typ          |
| -------- | ------------ |
| IdUcznia | INT          |
| Imie     | VARCHAR(80)  |
| Nazwisko | VARCHAR(120) |
| Wiek     | INT          |
| IdKlasy  | INT          |

Klasa


|Nazwa|typ|
|---|---|
|IdKlasy|varchar(12)|
|ProfilKlasy|TEXT|

Ewidencja

| Nazwa       | typ      |
| ----------- | -------- |
| IdEwidencji | INT      |
| IdUcznia    | INT      |
| Wejscie     | DATETIME |
| Wyjscie     | DATETIME |

#### [TLDR - Typy Danych](https://bluevoid.pl/mysql-typy-danych/)

|Typ|Min (signed)|Min - (unsigned)|Max - (unsigned)|Bajty|
|---|---|---|---|---|
|**INT**|-2147483648 ( -2^31 )|0|4294967295 ( 2^32 )|4|
|BOOLEAN|||0, FALSE|1, TRUE|


| Typ           | Domyślnie ustawienia | Precyzja             | Bajty | Alias    |
| ------------- | -------------------- | -------------------- | ----- | -------- |
| **FLOAT(P)**  | P=24                 | P = 24 or 53(double) | 4     | -        |
| **DOUBLE(P)** | P=53                 | P = 24(float) or 53  | 8     | **REAL** |

|Typ|ilość wszystkich cyfr (M)|Ilość cyfr po przecinku (D)|Alias|
|---|---|---|---|
|****DECIMAL(M,D)****|M = [1-38]|0|**NUMERIC**|

| Typ           | Format              | Min                     | Max                        |
| ------------- | ------------------- | ----------------------- | -------------------------- |
| **DATE**      | YYYY-MM-DD          | 1000-01-01              | 9999-12-31                 |
| **DATETIME**  | YYYY-MM-DD HH:MM:SS | 1000-01-01 00:00:00     | 9999-12-31 23:59:59        |
| **TIMESTAMP** | YYYYMMDDHHMMSS      | 1970-01-01 00:00:01 (0) | 2038-01-19 03:14:07 (2^32) |

|Typ|ilość liter (M)|uzupełnienie spacjami|
|---|---|---|
|**VARCHAR(M)**|M = [1-65535]|NIE|
|**TEXT**|Max: 65535|NIE|

#### [TLDR - Constraints](https://bluevoid.pl/mysql-constraints/)

- `NOT NULL` - Wymusza aby wartość nie była `NULL`
- `UNIQUE` - Wymusza aby wartkość była unikalna
- `PRIMARY KEY` - Klucz główny, unikalnie identyfikuje rekord w tabeli
- `FOREIGN KEY` - Klucz obcy, identyfikuje rekord w tabeli
- `DEFAULT` - Ustawia wartość domyślną dla danych
- `AUTO_INCREMENT` - Automatycznie przydziela nowym rekordom _wartość poprzedniego_ +1
- `CHECK` - Wymusza aby dodawane dane spełniały podany warunek

#### Zadanie

Dodaj constraint NOT NULL do wszystkich Id z użyciem ALTER TABLE.

- Uczen - dodaj NOT NULL do IdUcznia
- Ewidencja - dodaj NOT NULL do IdEwidencja
- Klasa - dodaj NOT NULL IdKlasy

Dodaj PRIMARY KEY do tabel z użyciem _ALTER TABLE_.

- Uczen - PRIMARY KEY
- Ewidencja - PRIMARY KEY
- Klasa - PRIMARY KEY

Dodaj relacje do tabel z użyciem _ALTER TABLE_.

- Uczen - IdKlasy -> Klasy( IdKlasy )
- Ewidencja - IdUcznia -> Uczen( IdUcznia )

Ustaw constraint na tabeli Uczen kolumnie wiek na DEFAULT 18

#### ALTER TABLE - RENAME

Modyfikuje kolumnę w tabeli.
```SQL
ALTER TABLE nazwa_tabeli RENAME COLUMN stara_nazwa_kolumny TO nowa_nazwa_kolumny;
```
<br>
