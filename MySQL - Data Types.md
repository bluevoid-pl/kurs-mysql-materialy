
#### TLDR

|Typ|Min (signed)|Min - (unsigned)|Max - (unsigned)|Bajty|
|---|---|---|---|---|
|**INT**|-2147483648 ( -2^31 )|0|4294967295 ( 2^32 )|4|
|BOOLEAN|||0, FALSE|1, TRUE|

|Typ|Domyślnie ustawienia|Precyzja|Bajty|Alias|
|---|---|---|---|---|
|**FLOAT(P)**|P=24|P = 24 or 53(double)|4|-|
|**DOUBLE(P)**|P=53|P = 24(float) or 53|8|**REAL**|

|Typ|ilość wszystkich cyfr (M)|Ilość cyfr po przecinku (D)|Alias|
|---|---|---|---|
|**DECIMAL(M,D)**|M = [1-38]|0|**NUMERIC**|

|Typ|Format|Min|Max|
|---|---|---|---|
|**DATE**|YYYY-MM-DD|1000-01-01|9999-12-31|
|**DATETIME**|YYYY-MM-DD HH:MM:SS|1000-01-01 00:00:00|9999-12-31 23:59:59|
|**TIMESTAMP**|YYYYMMDDHHMMSS|1970-01-01 00:00:01 (0)|2038-01-19 03:14:07 (2^32)|

|Typ|ilość liter (M)|uzupełnienie spacjami|
|---|---|---|
|**VARCHAR(M)**|M = [1-65535]|NIE|
|**TEXT**|Max: 65535|NIE|



#### Numeryczne - Całkowite (Integer)

|Typ|Min (signed)|Max (signed)|Min - (unsigned)|Max - (unsigned)|Bajty|
|---|---|---|---|---|---|
|**INT**|-2147483648 <br>( -2^31 )|+2147483647 <br>( 2^31 - 1 )|0|4294967295 <br>( 2^32 )|4|
|**TINYINT**|-128 <br>( -2^7 )|+127 <br>( 2^7 - 1 )|0|255 <br>( 2^8 )|1|
|**SMALLINT**|-32768 <br>( -2^15 )|+32767 <br>( 2^15 - 1 )|0|65535 <br>( 2^16 )|2|
|**MEDIUMINT**|-8388608 <br>( -2^23 )|+8388607 <br>( 2^23 -1 )|0|16777215 <br>( 2^24 )|3|
|**BIGINT**|-9223372036854775808 <br>( -2^63 )|+9223372036854775807 <br>( 2^63 -1 )|0|9223372036854775807 <br>( 2^64 )|8|

#### Numeryczne - Zmiennoprzecinkowe (floating-point)

|Typ|Domyślnie ustawienia|Precyzja|Bajty|Alias|
|---|---|---|---|---|
|**FLOAT(P)**|P=24|P = 24 or 53|4|-|
|**DOUBLE(P)**|P=53|P = 24 or 53|8|**REAL**|

#### Numeryczne - Stałoprzecinkowa ( fixed-point )

|Typ|ilość wszystkich cyfr (M)|Ilość cyfr po przecinku (D)|Alias|
|---|---|---|---|
|**DECIMAL(M,D)**|M = [1-38]|0|**NUMERIC**|



#### Data i czas

|---|---|---|---|
|**DATE**|YYYY-MM-DD|1000-01-01|9999-12-31|
|Typ|Format|Min|Max|
|**DATETIME**|YYYY-MM-DD HH:MM:SS|1000-01-01 00:00:00|9999-12-31 23:59:59|
|**TIMESTAMP**|YYYYMMDDHHMMSS|1970-01-01 00:00:01 (0)|2038-01-19 03:14:07 (2^32)|
|**TIME**|HH:MM:SS|00:00:00|23:59:59|

#### Napisy (String)

|Typ|ilość liter (M)|uzupełnienie spacjami|
|---|---|---|
|**CHAR(M)**|M = [1-255]|TAK|
|**VARCHAR(M)**|M = [1-65535]|NIE|
|**TINYTEXT**|Max: 255|NIE|
|**TEXT**|Max: 65535|NIE|
|**MEDIUMTEXT**OB**|Max: 16777215|NIE|
|**LONGTEXT**|Max:4294967295|NIE|



#### Boolean

|Typ|Wartości|Alias|
|---|---|---|
|BOOLEAN|TRUE, FALSE|BOOL|

Wartości w boolean nie uwzględniają wielkości liter.  
Wartość 0 jest interpretowana jako False, a 1 jako True.



#### Dodatkowe typy danych

- JSON
- ENUM
- SET
- BIT
- BLOB



#### Ograniczenia - Constraints

- NOT NULL - Wymusza aby wartość nie była NULL
- UNIQUE - Wymusza aby wartkość była unikalna
- PRIMARY KEY - Klucz główny, unikalnie identyfikuje rekord w tabeli
- FOREIGN KEY - Klucz obcy, identyfikuje rekord tabeli
- CHECK - Wymusza aby dodawane dane spełniały podany warunek
- DEFAULT - Ustawia wartość domyślną dla danych
- AUTO_INCREMENT - Automatycznie przydziela nowym rekordom _wartość poprzedniego_+1
