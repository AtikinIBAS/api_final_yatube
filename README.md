# Yatube API

## Описание

Yatube API — это backend для социальной сети, в которой пользователи могут публиковать посты, комментировать, и подписываться на других пользователей. Авторизация реализована через JWT.

## Установка

```bash
git clone https://github.com/AtikinIBAS/api_final_yatube.git
cd yatube_api_final
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
