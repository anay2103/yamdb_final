## API_YAMDb
![YAMDb-app workflow](https://github.com/anay2103/yamdb_final/actions/workflows/main.yml/badge.svg)

Проект YAMDb собирает отзывы пользователей на произведения, список которых составляется и редактируется администратором. Произведения классифицируются по категориям (например, "книги", "фильмы", "музыка") и жанрам ("джаз", "рок", "классика"), но в базе данных проекта не хранятся.

Стек технологий: Django 3.0.5, Posgresql, Gunicorn, Nginx, Docker.

Проект доступен в Сети [здесь](http://62.84.116.179/api/v1/) 

Документация с описанием и параметрами всех конечных точек (API endpoints) проекта размещена [здесь](http://62.84.116.179/redoc/) 

### Установка и начало работы:
1. Установите Docker согласно [инструкции для вашей ОС](https://docs.docker.com/engine/install/). 
2. Склонируйте данный репозиторий: 
   ```
   git clone git@github.com:anay2103/yamdb_final.git
   ``` 
4. Создайте файл `.env` в корневой директории проекта и укажите в нем следующие переменные:
   * `DEBUG` - True/False для debug-режима
   * `ALLOWED_HOSTS`- список хостов/доменных имен, которые обслуживает Django-приложение;
   * `SECRET_KEY` - уникальный секретный ключ для установки Django;
   * `DB_ENGINE`- тип используемой БД. Значение по умолчанию: `django.db.backends.postgresql`
   * `DB_NAME` - название используемой БД;
   * `POSTGRES_USER` - имя пользователя для доступа к БД; 
   * `POSTGRES_PASSWORD`- пароль для доступа к БД;
   * `DB_HOST` - хост, используемый для доступа к БД;
   * `DB_PORT`- порт, используемый для доступа к БД.
5. Для работы с приложением используйте следующие команды в корневой директории проекта:
   * Запуск контейнеров: 
     ```
     docker-compose up
     ```
   * Создание миграций Django: 
     ```
     docker-compose exec web python manage.py makemigrations
     ```
   * Применение миграций Django:  
     ```
     docker-compose exec web python manage.py migrate
     ```
   * Создание суперюзера Django: 
     ```
     docker-compose exec web python manage.py createsuperuser
     ```
   * Сборка статических файлов проекта: 
     ```
     docker-compose exec web python manage.py collectstatic --no-input
     ``` 
   * Сохрание данных из БД в файл: 
     ```
     docker-compose exec web python manage.py dumpdata > fixtures.json
     ```
   * Запуск pytest в контейнере: 
     ```
     docker exec -it yamdb_final_web_1 bash
     pytest
     ```
   * Остановка контейнеров: 
     ```
     docker-compose down
     ```
### Об авторе:
[Яна](https://github.com/anay2103)

