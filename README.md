
# Yatube API

## Описание

**Yatube API** — это API-сервер для социальной сети **Yatube**, в которой пользователи могут:
- публиковать посты;
- вступать в сообщества (группы);
- комментировать посты;
- подписываться на авторов;
- получать доступ к записям через токен (JWT).

Проект реализован на базе **Django REST Framework**, с авторизацией через **JWT** (Djoser + SimpleJWT).

---

## Установка и запуск проекта

1. Клонируйте репозиторий:

```commandline
git clone https://github.com/AtikinIBAS/api_final_yatube.git
cd api_final_yatube
```

2. Создайте и активируйте виртуальное окружение:

```commandline
python -m venv venv
source venv/bin/activate        
venv\Scripts\activate           
```

3. Установите зависимости:

```commandline
pip install -r requirements.txt
```

4. Выполните миграции:

```commandline
python manage.py makemigrations
python manage.py migrate
```

5. Запустите сервер:

```commandline
python manage.py runserver
```

6. Документация доступна по адресу:

```
http://127.0.0.1:8000/redoc/
```

---

## 🔐 Аутентификация (JWT)

Для использования API необходимо авторизоваться.

1. Получить токен:

```commandline
POST /api/v1/auth/token/login/
```

**Тело запроса:**
```json
{
  "username": "ваш_логин",
  "password": "ваш_пароль"
}
```

2. Использовать токен:

В каждом запросе указывайте заголовок:

```
Authorization: Bearer <ваш токен>
```

---

## Примеры запросов к API

### Подписки

- **GET /api/v1/follow/** — получить список подписок текущего пользователя.
- **POST /api/v1/follow/** — подписаться на пользователя.

**Пример запроса:**

```html
POST /api/v1/follow/
Authorization: Bearer <токен>
Content-Type: application/json

{
  "following": "username"
}
```

---

### Посты

- **GET /api/v1/posts/** — список постов
- **POST /api/v1/posts/** — создать пост

```json
{
  "text": "Новый пост!",
  "group": 1
}
```

---

### Комментарии

- **GET /api/v1/posts/{post_id}/comments/** — список комментариев к посту
- **POST /api/v1/posts/{post_id}/comments/** — добавить комментарий

```json
{
  "text": "Мой комментарий"
}
```

---

## Возможности

- Полноценное REST API для соцсети
- JWT-авторизация
- Поддержка подписок на авторов
- Ограничения прав доступа:
  - Только автор может редактировать/удалять свой контент
  - Анонимы — только чтение
- Поиск подписок по имени пользователя

---

## 🛠Технологии

- Python 3.10+
- Django 4.2+
- Django REST Framework
- SimpleJWT
- Djoser
- SQLite (по умолчанию)

---

## Тестирование

В проекте есть автотесты. Запуск:

```commandline
pytest
```

---

## 📎 Автор

Проект выполнен студентом 3 курса группы ИБАС-с-о-22-1 **Фисенко Никитой**
