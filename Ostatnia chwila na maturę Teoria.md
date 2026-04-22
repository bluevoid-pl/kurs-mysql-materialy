## Protokoły

Protokoły stron internetowych

- HTTP (Hypertext Transfer Protocol) służy do przesyłania dokumentów hipertekstowych, czyli stron [WWW](http://WWW).
- HTTPS to bezpieczna wersja HTTP, wykorzystująca szyfrowanie SSL/TLS, zapewnia poufność i integralność przesyłanych danych.

Protokoły przesyłu plików

- FTP (File Transfer Protocol) umożliwia przesyłanie plików między klientem a serwerem.
- FTPS to rozszerzona wersja FTP z szyfrowaniem.

Protokoły pocztowe

- POP3 (Post Office Protocol 3) służy do pobierania poczty elektronicznej ze zdalnego serwera na lokalny komputer.
- IMAP (Internet Message Access Protocol) pozwala na zarządzanie(odczyt i modyfikacje) pocztą bez pobierania jej na urządzenie.
- SMTP(Simple Mail Transfer Protocol) Protokół służący do ==wysyłania== poczty elektroniczne

**Protokoły** do administracji

- SSH (Secure Shell) - to protokół umożliwiający bezpieczne, zaszyfrowane zdalne połączenie z serwerem. Zwykle używany w terminalu.
- Telnet - pozwala na zdalne logowanie do komputera, ale bez szyfrowania, co czyni go mniej bezpiecznym.

Protokoły sieciowe i transportowe

- **TCP/IP** Podstawowy zestaw protokołów internetu, składający się z TCP (Transmission Control Protocol) zapewniającego niezawodną transmisję danych przez sieć. Działa on tak że wysyła pakiety i oczekuje na odpowiedź zwrotną z informacją czy pakiet doszedł do adresata, w przypadku zgubienia pakietu, wysyłany jest on ponownie.
- **UDP** Protokół umożliwiający szybką transmisję danych bez potwierdzeń odbioru, wykorzystywany tam, gdzie liczy się szybkość, np. w streamingu czy grach online
- **DNS** Protokół zamieniający nazwy domenowe na adresy IP. Przykładowo zmienia on domenę google.com na adres ipv4 142.250.203.206. Pozwala on ludziom na używanie napisów zamiast liczb w nawigacji internetu.
- **DHCP** Protokół automatycznej konfiguracji adresów IP w sieciach lokalnych, jest on zwykle używany przez lokalny router w celu przydzielenia komputerom adresów IP.
- **IP (Internet Protocol)**, jest on jednym z najbardziej podstawowych protokołów internetowych, odpowiada on za adresację i routing pakietów. Jest to protokół, którego zadaniem jest przekazywanie pakietów danych od nadawcy do odbiorcy poprzez sieć, wybierając odpowiednią trasę na podstawie adresów IP, niezależnie od tego, czy urządzenia znajdują się w tej samej, czy w różnych sieciach.

#### Szyfrowanie

TLDR

- **Szyfrowanie symetryczne** (np. AES): ten sam klucz do szyfrowania i deszyfrowania, szybkie, wymaga bezpiecznej wymiany klucza.
- **Szyfrowanie asymetryczne** (np. RSA): para kluczy (publiczny i prywatny), wolniejsze, ale bezpieczniejsze w kontekście wymiany kluczy, umożliwia także podpisy cyfrowe i uwierzytelnianie

**AES (Advanced Encryption Standard)** to jeden z najpopularniejszych algorytmów szyfrowania symetrycznego. W szyfrowaniu symetrycznym ten sam klucz służy zarówno do szyfrowania, jak i deszyfrowania danych. Oznacza to, że nadawca i odbiorca muszą posiadać identyczny, tajny klucz, który musi być przekazany w bezpieczny sposób. Szyfrowanie symetryczne jest bardzo szybkie i wydajne, dlatego często stosuje się je do ochrony dużych ilości danych

**Przykład działania:**  
Alicja i Bob ustalają wspólny tajny klucz. Alicja szyfruje wiadomość tym kluczem i wysyła ją do Boba, który używa tego samego klucza do odszyfrowania treści

**RSA (Rivest-Shamir-Adleman)** to jeden z najczęściej wykorzystywanych algorytmów szyfrowania asymetrycznego. W tej metodzie stosuje się parę kluczy: publiczny (do szyfrowania) i prywatny (do deszyfrowania). Klucz publiczny można udostępnić każdemu, natomiast klucz prywatny zna tylko właściciel. Dzięki temu możliwe jest bezpieczne przesyłanie danych bez konieczności wcześniejszego ustalania wspólnego sekretu

**Przykład działania:**  
Bob udostępnia swój klucz publiczny. Alicja szyfruje wiadomość kluczem publicznym Boba i wysyła ją. Tylko Bob, posiadający klucz prywatny, może odszyfrować tę wiadomość

## Kompresja danych i formaty plików

**Kompresja danych** to proces przekształcania, kodowania lub modyfikowania danych w taki sposób, aby zmniejszyć ich rozmiar bez utraty kluczowych informacji. Celem kompresji jest efektywniejsze wykorzystanie przestrzeni dyskowej oraz szybsza transmisja danych przez sieci.

Rodzaje kompresji

- **Kompresja bezstratna**  
    Pozwala na odzyskanie oryginalnych danych w 100% po dekompresji. Stosowana jest tam, gdzie ważna jest integralność danych, np. w dokumentach tekstowych, archiwach, programach czy niektórych formatach graficznych (PNG, ZIP, FLAC).  
    Przykładowy algorytm kompresji bezstratnej to **Huffman Coding** przypisuje on krótsze kody częściej występującym symbolom, co zmniejsza rozmiar pliku.
- **Kompresja stratna**  
    Osiąga większe zmniejszenie rozmiaru pliku kosztem utraty części informacji, często niezauważalnej dla użytkownika. Wykorzystywana głównie w multimediach (obrazy, dźwięk, wideo), gdzie pewna utrata jakości jest akceptowalna (JPEG, MP3, MP4)

## Zestawienie typów komunikacji sieciowej

|Typ komunikacji|Opis|Przykłady zastosowań|Zalety|Wady|
|---|---|---|---|---|
|**Client-Server**|Jeden lub więcej centralnych serwerów zarządza zasobami i usługami, a klienci zgłaszają żądania do serwera.|Strony WWW, e-mail, bankowość online|Centralne zarządzanie, wysoka skalowalność|Możliwy pojedynczy punkt awarii, koszty|
|**Peer-to-Peer**|Każdy komputer (peer) może być jednocześnie klientem i serwerem, wymieniając się zasobami bez centralnego serwera.|Udostępnianie plików (BitTorrent), Skype|Brak centralnego punktu awarii, łatwa rozbudowa|Trudniejsze zarządzanie, mniejsza stabilność przy dużej liczbie węzłów|
