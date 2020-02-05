# Bitad docker

## Opis struktury
    .
    ├── api                       
    │    ├── Dockerfile             # Obraz kontenera api
    │    └── ...                    # Miejsce na pliki ASP.NET Core
    ├── mysql                     
    │    └── ...                    # Plik konfiguracyjny mysql
    ├── nginx                     
    │    └── ...                    # Plik konfiguracyjny nginx
    ├── php                       
    │    └── ...                    # Plik konfiguracyjny php
    ├── src                       
    │    └── ...                    # Miejsce na pliki aplikacji Laravel
    ├── .gitignore
    ├── Dockerfile                  # Obraz kontenera aplikacji Laravel
    ├── README.md
    └── docker-compose.yml          # Plik opisujący strukturę kontenerów

## Wstęp

### Przed uruchomieniem

Upewnij się, że [docker](https://www.docker.com/) i [docker-compose](https://docs.docker.com/compose/) są zainstalowane:

```
docker --version
docker-compose --version
```

### Uruchomienie

Przejdź do pobranego reposytorium:
```
cd /bitad-docker 
```

Wykonaj komendę, która pobierze i zbuduje obraz kontenerów:
```
docker-compose build
```

Uruchom wszystkie kontenery (-d pozwala na działanie w tle):
```
docker-compose up -d
```
## Pomocne polecenia 

### Sprawdzenie statusu kontenerów

```
docker ps -a
```
-a pokaże wszystkie kontenery, również zatrzymane.

### Zatrzymanie pracy wszystkich kontenerów

```
docker-compose stop
```

### Zatrzymanie pracy i usunięcie wszystkich kontenerów

Polecenie zatrzymuje i usuwa kontenery:
```
docker-compose down
```
Kontenery utracą wszystkie zmiany w nich wykonane. Pliki zapisane w dołączonych woluminach nie zostaną usunięte.

### Wykonywanie polecenia wewnątrz kontenera

```
docker-compose exec nazwa-kontenera polecenie
```

Przykład:
```
docker-compose exec app php artisan migrate
```

Polecenie docker-compose exec działa tylko na włączonych kontenerach.

### Podłączenie się do pracującego kontenera

```
docker-compose exec nazwa-kontenera bash
```

Przykład:
```
docker-compose exec mysql bash
```

### Kopiowanie pliku do (lub z) kontenera

Kopiowanie do kontenera:
```
docker cp /copy/from nazwa-kontenera:/copy/to
```

Kopiowanie z kontenera:
```
docker cp nazwa-kontenera:/copy/from /copy/to
```

### Poboczne polecenia

```
docker run --rm -v $(pwd):/app composer install
php artisan config:clear
docker-compose exec app php artisan migrate
```


## Warte uwagi
* [The beauty of Docker for local Laravel development](https://dev.to/aschmelyun/the-beauty-of-docker-for-local-laravel-development-13c0?fbclid=IwAR2QfJg5qrXJfq4bBjBxltZUU1i1K6DyOIw3oFbRmAvVXXDd5u1_0E1fYQk) - Andrew Schmelyun
* [How To Set Up Laravel, Nginx, and MySQL with Docker Compose](https://www.digitalocean.com/community/tutorials/how-to-set-up-laravel-nginx-and-mysql-with-docker-compose) - Faizan Bashir
* [Running in Docker | ASP.NET Core 2.2 REST API Tutorial 14](https://www.youtube.com/watch?v=fAtfVu569CY) - Nick Chapsas
