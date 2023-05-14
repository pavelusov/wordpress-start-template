# Шаблон Wordpress


## Start setup
1. `docker-compose up -d db` - запускаем сервис с базой данных
2. `docker exec -i db sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD" wordpress' < ./db_dump/wordpress.sql` - востанавливаем базу данных
3. `docker-compose up -d` - запускаем остальные сервисы

## Before  stopping docker containers
1. `docker exec db sh -c 'exec mysqldump wordpress -uroot -p"$MYSQL_ROOT_PASSWORD"' > ./db_dump/wordpress.sql`
2. `git add .; git commit -m "The DB was changed. Some changes"; git push origin main`

## Creating database dump
`docker exec db sh -c 'exec mysqldump wordpress -uroot -p"$MYSQL_ROOT_PASSWORD"' > ./db_dump/wordpress.sql`

## Restoring data from dump files
`docker exec -i db sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD" wordpress' < ./db_dump/wordpress.sql`

### Админ панель
`http://127.0.0.1/wp-login.php`

Администратор
- логин - admin
- пароль - synergy_admin

Пользователь
- логин - synergy_user
- пароль - synergy_root_2023

### Веб-морда
Главная - `http://127.0.0.1`

Авторизация - `http://127.0.0.1/wp-login.php`
