# Cloud_12

W ramach zadania stworzyłem środowisko LEMP złożone z czterech kontenerów:
- serwer Nginx (web server),
- serwer PHP-FPM (backend do obsługi PHP),
- baza danych MySQL,
- interfejs phpMyAdmin do obsługi bazy.

Całość została uruchomiona za pomocą pliku `docker-compose.yml`, który definiuje sieci, obrazy i zależności między kontenerami. Projekt umożliwia przeglądanie strony PHP przez przeglądarkę oraz dostęp do bazy danych i phpMyAdmin.

---

## Opis plików

- `docker-compose.yml` – główny plik konfiguracyjny Docker Compose, definiuje wszystkie cztery usługi, sieci oraz porty. Uwzględnia też automatyczne ładowanie bazy z pliku SQL.

- `config/nginx.conf` – konfiguracja Nginx. Ustawia katalog główny na `/usr/share/nginx/html`, obsługuje pliki `.php` przez usługę `php` (PHP-FPM).

- `src/index.php` – testowy plik PHP wyświetlający komunikat o działaniu stacka oraz wersję PHP.

- `db/init.sql` – plik SQL inicjalizujący bazę danych `exampledb` i dodający przykładową tabelę `users` z dwoma rekordami.

---

## Co zrobiłem

1. Skonfigurowałem cztery kontenery: Nginx, PHP, MySQL i phpMyAdmin.
2. Zorganizowałem projekt w logicznej strukturze katalogów (`src`, `config`, `db`).
3. Zdefiniowałem sieci `net_front` i `net_back` zgodnie z wymaganiami zadania.
4. Umożliwiłem dostęp do:
   - strony PHP przez port 4001,
   - phpMyAdmin przez port 6001.
5. Dodałem plik `init.sql`, który automatycznie tworzy bazę danych i testowe dane w tabeli `users`, po to aby sprawdzić działanie kontenerów.

---

## Działanie

Po uruchomieniu stacka:
- Strona `index.php` wyświetla się poprawnie przez przeglądarkę (http://localhost:4001).
- phpMyAdmin działa i umożliwia dostęp do bazy danych (http://localhost:6001).
- Baza `exampledb` zawiera tabelę `users` z dwoma wpisami: Anna Nowak i Jan Kowalski.

---

## Komendy których użyłem

- `docker-compose down -v` – zatrzymuje i usuwa wszystkie kontenery oraz wolumeny.
- `docker-compose up -d` – uruchamia wszystkie kontenery w tle.
- `docker-compose ps` – sprawdza status uruchomionych kontenerów.

## Działanie prezentują screeny

- Można je znaleźć w w main folderze projektowym, w podkatalogu `screenshots`.