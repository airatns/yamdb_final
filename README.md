# YaMDb workflow status badge

![example workflow](https://github.com/airatns/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# YaMDb_final

В данном проекте реализовал задачу по настройке для приложения **YaMDb** *Continuous Integration* и *Continuous Deployment* с использованием **GitHub Actions**:

1. Автоматический запуск тестов (*flake8* и *pytest*)

2. Сборка и обновление докер-образа на *Docker Hub*

3. Автоматический деплой на сервер в Яндекс.Облако

4. Отправка уведомления в Telegram, что процесс деплоя успешно завершился

YaMDb - это проект, который собирает отзывы пользователей на произведения.

Бэкенд для проекта YaMDb реализован по ссылке:

>*https://github.com/airatns/api_yamdb*

Первоначальная сборка YaMDb в контейнерах Docker реализована по сслыке:

>*https://github.com/airatns/infra_sp2*

## **Стек технологий**

Python, Django, PostgreSQL, Docker, Gunicorn, Nginx, Ubuntu, Telegram

## **Регистрация нового пользователя**
Для регистрации сделайте POST-запрос с данными **email** и **username** на адрес:

>*http://127.0.0.1:8000/api/v1/auth/signup/*

Затем на ваш электронный почтовый ящик придёт **confirmation_code**.

## **Получение JWT-токена**
Для аутентификации сделайте POST-запрос с данными **username** и **confirmation_code** на адрес:

>*http://127.0.0.1:8000/api/v1/auth/token/*

Вам будет выдан **token** для запросов к API.

Срок действия токена **14 дней**.

### **Пример использования JWT-токена**

>*Bearer ey8Df...*

## **Подготовка на локале:**

Клонировать репозиторий и перейти в него в командной строке:

>*git clone git@github.com:airatns/yamdb_final.git*

Прописать параметры окружения в файле .env:

* SECRET_KEY=<SECRET_KEY>

* DEBUG=<True | False>

* DB_ENGINE=django.db.backends.postgresql

* DB_NAME=postgres

* POSTGRES_USER=postgres

* POSTGRES_PASSWORD=postgres

* DB_HOST=db

* DB_PORT=5432

## **Подготовка на сервере:**

Остановить службу nginx:

>*sudo systemctl stop nginx*

Установить **docker** и **docker-compose**

Скопировать файлы *docker-compose.yaml* и *nginx/default.conf* на сервер в 

>*home/<your_username>/docker-compose.yaml* \
>*home/<your_username>/nginx/default.conf*

## **Запуск:**

Выполнить в терминале на локале команды

>*git add .* \
>*git commit -m '<your_comment>'* \
>*git push*

Результатом автоматизации будет сообщение:

>*yamdb-app успешно выполнен!*

## **Создать суперпользователя:**

На сервере в домашней директории выполнить команду:

>*sudo docker compose exec web python manage.py createsuperuser*

## **Проверить, что приложение успешно разворачивается:**

>*http://158.160.8.173/admin/*

## **Техническая документация**

Полное описание можно найти по ссылке после запуска проекта - <a href="http://127.0.0.1:8000/redoc" target="_blank">Redoc</a>
