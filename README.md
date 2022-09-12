
# Проект "API для Yatube"

## Описание

YaTube API представляет собой проект социальной сети в которой реализованы следующие возможности, публиковать записи, комментировать записи, а так же подписываться или отписываться от авторов.

## Стек

Python 3.7, Django 2.2, Django REST Framework, Simple-JWT + Joser, SQLite3

## API для сервиса Yatube позволяет:

    Создавать, редактировать и удалять собственные записи
    Создавать группы
    Оставлять комментарии под постами других авторов
    Получать и обновлять JWT-токены.

Позволяет делать запросы к моделям проекта: Посты, Группы, Комментарии, Подписчики.

Поддерживает методы GET, POST, PUT, PATCH, DELETE

Предоставляет данные в формате JSON

Ознакомиться с полным функционалом и примерами можно по адресу http://127.0.0.1:8000/redoc (Доступно после запуска проекта )

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```bash
git clone git@github.com:KAbashin/api_final_yatube.git cd API_yatube
```
Cоздать и активировать виртуальное окружение:
```bash
python3 -m venv venv source env/bin/activate (Mac OS, Linux) или source venv/Scripts/activate (Win10)
```
Установить зависимости из файла requirements.txt:
```bash
pip install -r requirements.txt
```
Перейти в каталог с manage.py
```bash
cd yatube_api
```
Выполнить миграции:
```bash
python3 manage.py migrate
```
Запустить проект:
```bash
python3 manage.py runserver
```
## Примеры работы с API

API Yatube возвращает ответы в формате JSON.

GET-запрос на получение списка публикаций или публикации по id:

http://127.0.0.1:8000/api/v1/posts/

http://127.0.0.1:8000/api/v1/posts/{id}/

Ответ:
```json
 { "id": 1, 
 "text": "Новый пост", 
 "author": "admin", 
 "group": null, 
 "image": null, 
 "pub_date": 
 "2022-06-06T11:00:39.364506Z", 
 "comments": [] }
```
GET-запрос на получение списка всех публикаций с указанием параметров limit и offset:

limit - какое число объектов вернётся

offset - с какого по счёту объекта начнется отсчёт

http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=2

API возвращает список с пагинацией:

Ответ: 
```json
{ "count": 4, 
"next": null, 
"previous": 
"http://127.0.0.1:8000/api/v1/posts/?limit=2", 
"results": [ 
{ "id": 3, "text": "И еще один новый пост", "author": "admin", "group": null, "image": null, "pub_date": "2022-01-05T08:44:55.037434Z", "comments": [] }, 
{ "id": 4, "text": "Новый пост №4", "author": "admin", "group": null, "image": null, "pub_date": "2022-01-05T08:45:19.129408Z", "comments": [] } 
] }
```
POST-запрос на создание новой публикации:

Поле text является обязательным

http://127.0.0.1:8000/api/v1/posts/

Зарос: 
```json
{ "text": "Новый пост №4" }
```

Ответ:
```json
 { "id": 4, 
 "text": "Новый пост №4", 
 "author": "admin", 
 "group": null, "image": null, 
 "pub_date": "2022-06-07T08:45:19.129408Z", 
 "comments": [] 
 }
```
POST-запрос на добавление комментария к публикации:

http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/

Запрос: 
```json
{ "text": "Тестовый комментарий к посту" }
```
Ответ: 
```json
{ "id": 1, "author": "admin", "post": 3, "created": "2022-06-07T09:17:45.575284Z", "text": "Тестовый комментарий к посту" }
```
Получение JWT-токена

http://127.0.0.1:8000/api/v1/jwt/create/

Запрос: 
```json
{

"username": "admin2",
"password": "password123"

}
```

Ответ: 
```json
{ "refresh": "string", "access": "string" }
```
## Разработчик проекта


Автор: Abashin Konstantin 
E-mail: kabashin@mail.ru

