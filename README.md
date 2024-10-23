# Taski-docker

## Описание
Taski - приложение для планирования задач. Задачи можно добавлять, изменять, удалять и переводить из группы "незавершённые" в "завершённые". Деплой на удаленный сервер. Есть фронтенд (SPA-приложение на React)
и бэкенд (Django-приложение). Деплой на удаленный сервер.

## Технологический стек
[![Python](https://img.shields.io/badge/-Python-464646?style=flat&logo=Python&logoColor=56C0C0&color=cd5c5c)](https://www.python.org/)
[![Django](https://img.shields.io/badge/-Django-464646?style=flat&logo=Django&logoColor=56C0C0&color=0095b6)](https://www.djangoproject.com/)
[![Django REST Framework](https://img.shields.io/badge/-Django%20REST%20Framework-464646?style=flat&logo=Django%20REST%20Framework&logoColor=56C0C0&color=cd5c5c)](https://www.django-rest-framework.org/)
[![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-464646?style=flat&logo=PostgreSQL&logoColor=56C0C0&color=0095b6)](https://www.postgresql.org/)
[![Nginx](https://img.shields.io/badge/-NGINX-464646?style=flat&logo=NGINX&logoColor=56C0C0&color=cd5c5c)](https://nginx.org/ru/)
[![gunicorn](https://img.shields.io/badge/-gunicorn-464646?style=flat&logo=gunicorn&logoColor=56C0C0&color=0095b6)](https://gunicorn.org/)
[![Docker](https://img.shields.io/badge/-Docker-464646?style=flat&logo=Docker&logoColor=56C0C0&color=cd5c5c)](https://www.docker.com/)
[![Docker-compose](https://img.shields.io/badge/-Docker%20compose-464646?style=flat&logo=Docker&logoColor=56C0C0&color=0095b6)](https://www.docker.com/)
[![Docker Hub](https://img.shields.io/badge/-Docker%20Hub-464646?style=flat&logo=Docker&logoColor=56C0C0&color=cd5c5c)](https://www.docker.com/products/docker-hub)
[![GitHub%20Actions](https://img.shields.io/badge/-GitHub%20Actions-464646?style=flat&logo=GitHub%20actions&logoColor=56C0C0&color=0095b6)](https://github.com/features/actions)

## Развернуть проект через Docker

Установите Docker, используя инструкции с официального сайта:
- для [Windows и MacOS](https://www.docker.com/products/docker-desktop)
- для [Linux](https://docs.docker.com/engine/install/ubuntu/). Отдельно потребуется установть [Docker Compose](https://docs.docker.com/compose/install/)

- Клонируйте репозиторий с проектом на свой компьютер:
```bash
git clone https://github.com/Creee9/Taski.git
```

- Установить и активировать виртуальное окружение:
```bash
python -m venv venv
source venv/Scripts/activate
# or
# source venv/bin/activate
```

- Переименуйте файл ".env.example" в ".env" в корне проекта

- Выполните команду сборки docker-compose:
```bash
docker-compose up -d --build
```
- Выполните миграции:
```bash
docker-compose exec backend python manage.py migrate
```
- Создайте суперпользователя:
```bash
docker-compose exec backend python manage.py createsuperuser
```
- Соберите файлы статики:
```bash
docker-compose exec backend python manage.py collectstatic
```
- Скопируйте файлы статики в /backend_static/static/ backend-контейнера :
```bash
docker compose exec backend cp -r /app/collected_static/. /backend_static/static/
# При выполнении команды на Windows может возникнуть ошибка "The system cannot find the file specified"
# В таком случае выполните команду "cp -r /app/collected_static/. /backend_static/static/"
# через терменал backend-контейнера в десктоп-приложении Docker
```

## Основные адреса: 
| Адрес                 | Описание |
|:----------------------|:---------|
| 127.0.0.1:9000            | Главная страница |
| 127.0.0.1:9000/admin/     | Для входа в панель администратора |
| 127.0.0.1:9000/api/       | API |


## Автор (бэкенд и деплой): 
_Молодцова Светлана_  
**telegram** _@smolodtsova_
