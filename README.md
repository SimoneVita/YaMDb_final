# YaMDb(API)
_________________________________________________
## Описание
База произведений с обзорами, оценками и комментариями, которая находится в контейнере.

### YaMDB - возможности:

- Просмотреть список доступных произведений
- Оставлять обзоры, ставить оценки.
- Обсуждать обзоры в комментариях
- Посмотреть рейтинг произведения, либо поделиться своим опытом.
- Обладает удобным API-интерфейсом
 
_____________________________________________________

## Техническое описание

### Примененные технологии
 > Python 3.7.9
 > Django 3.2.16
 > djangorestframework 3.12.4
 > djangorestframework-simplejwt 4.7.2
 > PyJWT 2.1.0
 > Gunicorn 20.0.4
 > Postgres 13.0
 > Nginx 1.21.3

### Как запустить проект:
!!!Запустить на локальной машине Docker!!!


Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/SimoneVita/infra_sp2.git
```

```
cd infra_sp2/infra
```

Создать файл .env:
```
touch .env
```
Открыть в редакторе файл .env:
```
nano .env
```
Погрузить в файл .env следующие значения:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres # установите свой пароль для подключения к базе
DB_HOST=db
DB_PORT=5432
SECRET_KEY='...' # секретный ключ, нужно установить свой
```
Закрыть файл .env с сохранием:
```
^X
```
Чтобы оставить имя без изменения нажмите enter (return для MacOS), далее
выходим в корневую директорию:
```
cd ..
```
Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv
```

```
source venv/bin/activate
```
Переход в директорию infra и запуск:
```
cd infra
```
```
docker-compose up
```
Необходимо открыть новый терминал и ввести по порядку следующие команды:
```
docker-compose exec web python manage.py makemigrations
```
```
docker-compose exec web python manage.py migrate
```

```
docker-compose exec web python manage.py collectstatic --no-input
```
Создайте суперюзера:
```
docker-compose exec web python manage.py createsuperuser
```
Наполнить базу данных тестовыми данными (работает только при пустой базе данных):
```
docker-compose exec web python manage.py basefill
```

Документация к APi доступна по адресу: 
```
http://localhost/redoc/
```
Образ на Dockerhub:
```
simonevita / api_yamdb
```
## Примеры запросов
### Регистрация пользователя
>Тип запроса 
```POST```
>Endpoint 
```api/v1/auth/signup/```

Запрос:
```
{
  "email": "user@example.com",
  "username": "string"
}
```
Ответ:
```
{
  "email": "string",
  "username": "string"
}
```
______________________________________
### Авторы
Даниил Алексеенко(https://github.com/cra1ger51),
Андрей Иванишин(https://github.com/AIvanishin),
Виталий Симоненко(https://github.com/SimoneVita)

### Лицензия
BSD 3-Clause License
