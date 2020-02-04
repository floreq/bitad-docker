## Struktura
    .
    ├── api                       # Pliki ASP.NET Core
    ├── mysql                     # Plik konfiguracyjny mysql
    ├── nginx                     # Plik konfiguracyjny nginx
    ├── php                       # Plik konfiguracyjny php
    ├── src                       # Pliki aplikacji Laravel
    ├── .gitignore
    ├── Dockerfile
    ├── README.md
    └── docker-compose.yml

## Polecenia 

```
docker run --rm -v $(pwd):/app composer install
php artisan config:clear
docker-compose exec app php artisan migrate
```

## Warte uwagi
* [The beauty of Docker for local Laravel development](https://dev.to/aschmelyun/the-beauty-of-docker-for-local-laravel-development-13c0?fbclid=IwAR2QfJg5qrXJfq4bBjBxltZUU1i1K6DyOIw3oFbRmAvVXXDd5u1_0E1fYQk) - Andrew Schmelyun
* [How To Set Up Laravel, Nginx, and MySQL with Docker Compose](https://www.digitalocean.com/community/tutorials/how-to-set-up-laravel-nginx-and-mysql-with-docker-compose) - Faizan Bashir
* [Running in Docker | ASP.NET Core 2.2 REST API Tutorial 14](https://www.youtube.com/watch?v=fAtfVu569CY) - Nick Chapsas
