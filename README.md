# Деплой

1. `docker compose up`
2. Зайти в контейнер с php-fpm и в корне проекта

```
composer install
```

3. Зайти в контейнер с frontend и в корне

```
npm install
npm run build
```

4. Готово.
   Адрес фронтенда - http://localhost
   Адрес бэкэнда - http://localhost/api/ или http://localhost/_.php (где _ название php файла)
