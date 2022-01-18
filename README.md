# yamdb_final
![example workflow](https://github.com/arthurchahalyan/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

Проект поможет развернуть мини-приложение с предпоготовленными моделями данных и базовым функционалом API.

<br>

## Демо развернутого проекта
http://51.250.27.122/admin/<br>
Почта: admin@admin<br>
Пароль: admin

<br>

## Запуск приложения | Docker

1. Создать файл infra/.env и наполнить дефолтными данными:

```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

2. Создать образы и запустить контейнеры

```
# Выполнить команду из корневой директории проекта
docker-compose -f infra/docker-compose.yaml up -d --build
```

3. Выполнить миграции и собрать статику

```
docker-compose -f infra/docker-compose.yaml exec web python manage.py migrate 
docker-compose -f infra/docker-compose.yaml exec web python manage.py collectstatic --no-input
```
<br>

## Наполнение базы тестовыми данными

```
docker-compose -f infra/docker-compose.yaml exec web python manage.py loaddata fixtures.json
```
Будут загружены тестовые данные из api_yamdb/fixtures.json, также будет создан суперпользователь.
Данные тестового суперпользователя:

> Почта: admin@admin.ru

> Логин: admin

> Пароль: admin
<br>

## Автор

Артур Чахалян
