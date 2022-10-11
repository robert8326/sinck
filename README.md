## Запуск в среде разработки

1. Создать файл переменных окружения и поправить нужные значения в `.env`
    ```sh
    cp src/.env_example src/.env
    ```
1. Запустить docker compose
    ```sh
    docker-compose up -d --build
    ```
1. Применить миграции к БД:
    ```sh
    docker-compose exec app ./manage.py migrate

    ```
1. Перегенерировать статические ресурсы:
    ```sh
    docker-compose exec app ./manage.py collectstatic --noinput

    ```
Приложение будет доступно в браузере http://localhost:80/

Сменить порт можно в `.env` **HTTP_PORT**

### Для выполнения команд внутри docker можно использовать docker-compose exec
Например применить миграции:
```sh
docker-compose exec app ./manage.py migrate
```

### Доступ к административной панели
```
   username: admin
   password: adminpass_000
```