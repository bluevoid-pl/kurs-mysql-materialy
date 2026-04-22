### Podstawy
#### Wczytywanie plików bez znanego rozmiaru, pojedyncze elementy

```py
# Tworzymy listę dynamiczną
dane = []

# Otwieramy plik do odczytu w trybie tekstowym
with open("plik_z_zadaniem.txt") as plik:
	# Pętla wykonuje się tak długo jak są dane do odczytania w pliku.
	for linia in plik:            
		# Usuwamy białe znaki z początku i końca linii
		temp = linia.strip()
		# Pomijamy puste linie
		if temp == "":                
			continue
			
		# Dodajemy element na końcu listy            
		dane.append(temp)
		
	# Plik automatycznie zamyka się po wyjściu z bloku with
	# Nie nalerzy wykonywać plik.close()


# Przechodzimy po danych aby sprawdzić czy są poprawnie wczytane
for wiersz in dane:
	print(wiersz)

```

#### Wczytywanie plików bez znanego rozmiaru, pary

Przykład dla pary string, int:

```py
dane = []

# Otwieramy plik do odczytu w trybie tekstowym
with open("plik_z_zadaniem.txt") as plik:        
	# Pętla wykonuje się tak długo jak są dane do odczytania w pliku.
	for linia in plik:            
		# Usuwamy białe znaki z początku i końca linii
		temp = linia.strip()
		# Pomijamy puste linie
		if temp == "":                
			continue

		a,b = temp.split(" ")
		# Dodajemy dane jako tuple, pamiętając że `b` jest int-em i trzeba go przekonwertować. 
		dane.append((a,int(b)))
		
for wiersz in dane:
	print(wiersz) # to jest touple

```
#### Wczytywanie plików bez znanego rozmiaru, sŁowniki

Przykład:
```py

dane = []

with open("plik_z_zadaniem.txt") as plik:
  for linia in plik:
    temp = linia.strip()
    if temp == "":  # pomijamy puste linie
      continue
    
    parts = temp.split()
    if len(parts) >= 4:
      M, a, b, *nazwa_parts = parts
      slownik = {
        'M': int(M),
        'a': int(a),
        'b': int(b),
        'nazwa': ' '.join(nazwa_parts)
      }
      dane.append(slownik)
      
for punkt in dane:
    print(f"{punkt['M']} {punkt['a']} {punkt['b']} {punkt['nazwa']}")
```

#### Wczytywanie plików z znanym rozmiarem, tablica std::array 3 wymiarowa.

TODO
#### Liczenie liczb w tablicy o małym zakresie (do około 100000)

# Dane do zadania
dane = [1, 2, 3, 100, 2, 3, 4, 5, 6]

# Używamy listy o stałym rozmiarze (maksymalna wartość + 1)
MAKS_LICZBA = 100
ilosci = [0] * (MAKS_LICZBA + 1)

# Przechodzimy po wszystkich liczbach w danych
for liczba in dane:
    ilosci[liczba] += 1

# Wyświetlamy wyniki
for liczba in range(len(ilosci)):
    if ilosci[liczba] > 0:  # Pokazujemy tylko liczby które wystąpiły
        print(f"{liczba} {ilosci[liczba]}")
        
print(liczba)
