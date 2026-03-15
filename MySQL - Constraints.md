#### TLDR

- NOT NULL - Wymusza aby wartość nie była NULL
- UNIQUE - Wymusza aby wartkość była unikalna
- PRIMARY KEY - Klucz główny, unikalnie identyfikuje rekord w tabeli
- FOREIGN KEY - Klucz obcy, identyfikuje rekord w tabeli
- DEFAULT - Ustawia wartość domyślną dla danych
- AUTO_INCREMENT - Automatycznie przydziela nowym rekordom _wartość poprzedniego_+1
- CHECK - Wymusza aby dodawane dane spełniały podany warunek



#### NOT NULL

Wymusza aby wartość nie była NULL

Przykład:
```SQL
CREATE TABLE przyklad(
    id INT NOT NULL,
    wiek INT
);

ALTER TABLE przyklad MODIFY COLUMN wiek INT NOT NULL;
```
<br>


#### UNIQUE

Wymusza aby wartkość była unikalna, nie jest wymagane jeśli używasz PRIMARY KEY na kolumnie.

Przykład:
```SQL
CREATE TABLE przyklad(
    id INT UNIQUE,
    numer_bagazu INT
);

ALTER TABLE przyklad MODIFY COLUMN numer_bagazu INT UNIQUE;
```
<br>


#### PRIMARY KEY

Klucz główny, unikalnie identyfikuje rekord w tabeli. Kolumny użyte w PRIMARY KEY muszą mieć nadane ograniczenie NOT NULL.

Przykład:
```SQL
CREATE TABLE przyklad(
    id INT NOT NULL,
    numer_bagazu INT,
    PRIMARY KEY (id)
);

CREATE TABLE przyklad2(
    id INT NOT NULL,
    nick VARCHAR(40) NOT NULL,
    numer_bagazu INT,
    CONSTRAINT PK_id_nick PRIMARY KEY (ID,nick)
);

-- Dodaj klucz główny
ALTER TABLE przyklad ADD PRIMARY KEY (id);

-- Dodaj klucz główny z nazwą
ALTER TABLE przyklad ADD CONSTRAINT PK_id_nick PRIMARY KEY (id,nick);

-- Usuń klucz główny
ALTER TABLE przyklad DROP PRIMARY KEY;
```
<br>


#### FOREIGN KEY

Klucz obcy, identyfikuje rekord w tabeli.

Przykład:
```SQL
CREATE TABLE temp(
    id int NOT NULL,
    PRIMARY KEY (id)
);

CREATE TABLE przyklad(
    id INT UNIQUE,
    numer_bagazu INT,
    id_temp INT,
    id_temp2 INT,
    PRIMARY KEY (id),
    FOREIGN KEY (id_temp) REFERENCES temp(id),
    CONSTRAINT FK_temp2 FOREIGN KEY (id_temp2) REFERENCES temp(id),
);

-- Dodaj klucz obcy odwołujący się do tabeli temp
ALTER TABLE przyklad ADD FOREIGN KEY (id_temp) REFERENCES temp(id);

-- Dodaj klucz obcy z nazwą
ALTER TABLE przyklad ADD CONSTRAINT FK_temp2 FOREIGN KEY (id_temp2) REFERENCES temp(id);
```
<br>


#### DEFAULT

Ustala wartość domyślną dla danych, która zostanie użyta, jeśli kolumna zostanie pominięta podczas wprowadzania danych.

Przykład:
```SQL
CREATE TABLE przyklad(
    id INT NOT NULL,
    profil_klasy varchar(255) DEFAULT 'Mat-Inf',
    data_utworzenia date DEFAULT CURRENT_DATE(),
    wiek INT,
);

-- Zmień typ danych aby miał wartość domyślną
ALTER TABLE przyklad MODIFY COLUMN wiek INT DEFAULT 18;

-- Dodaj wartość domyślna bezpośrednio
ALTER TABLE przyklad ALTER wiek SET DEFAULT 18;

-- Zmień typ danych aby usunąć wartość domyślną
ALTER TABLE przyklad MODIFY COLUMN wiek INT;

-- Usuń wartość domyślna bezpośrednio
ALTER TABLE przyklad ALTER wiek DROP DEFAULT; 
```
<br>


#### AUTO_INCREMENT

Automatycznie zwiększa nowe rekordy o 1, jeśli nie podano danych przy wstawianiu.

Przykład:
```SQL
CREATE TABLE przyklad(
    id INT AUTO_INCREMENT,
    numer_bagazu INT
);

ALTER TABLE przyklad MODIFY COLUMN numer_bagazu INT AUTO_INCREMENT;
```
<br>
Pierwszą wartością domyślnie jest 1, aby to zmienić można użyć:

```SQL
ALTER TABLE przyklad AUTO_INCREMENT=100;
```
<br>


#### CHECK

Wymusza aby dodawane dane spełniały podany warunek

Przykład:
```SQL
CREATE TABLE przyklad(
    id INT UNIQUE,
    wiek INT,
    jest_studentem BOOLEAN,
    CHECK (wiek>=18)
);

-- Dodaj warunek
ALTER TABLE przyklad ADD CHECK (wiek>=18);

-- Dodaj warunek z nazwą
ALTER TABLE przyklad ADD CONSTRAINT CHK_wiek_profil CHECK (wiek>=18 AND jest_studentem=TRUE);

-- Usuń warunek z nazwą
ALTER TABLE przyklad DROP CHECK CHK_wiek_profil; 
```
<br>
