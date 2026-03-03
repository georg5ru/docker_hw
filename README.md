# Django Project

Современное веб-приложение на Django с использованием PostgreSQL, Redis и Celery.

## Описание

Проект представляет собой REST API бэкенд на Django REST Framework с:
- Аутентификацией через JWT токены
- Асинхронными задачами на Celery
- Планировщиком периодических задач Django Celery Beat
- Фильтрацией данных Django Filter
- Отправкой email уведомлений

## Быстрый старт

### Предварительные требования

- Docker (версия 20.10+)
- Docker Compose (версия 2.0+)

### Установка и запуск

**Клонируйте репозиторий**

git clone <repository-url>
cd <project-directory>

**Настройте переменные окружения**

Отредактируйте файл .env и укажите ваши значения:
- Данные для подключения к PostgreSQL
- Настройки Redis
- SMTP настройки для отправки email
- SECRET_KEY для Django

**Запустите проект**

docker-compose up --build

**Примените миграции (в новом терминале)**

docker-compose exec app python manage.py migrate
docker-compose exec app python manage.py createsuperuser

**Откройте приложение**

- Django Admin: http://localhost:8000/admin/

## Структура проекта

.
├── config/                 # Настройки Django проекта
│   ├── settings.py        # Основные настройки
│   ├── urls.py           # URL конфигурация
│   └── celery.py         # Celery конфигурация
├── users/                 # Приложение пользователей
├── materials/            # Приложение материалов
├── docker-compose.yml    # Docker Compose конфигурация
├── Dockerfile           # Docker образ приложения
├── .env.example         # Шаблон переменных окружения

## Технологии

- Backend: Django 4.x + Django REST Framework
- База данных: PostgreSQL 15
- Кэш и брокер: Redis 7
- Асинхронные задачи: Celery + Django Celery Beat
- Аутентификация: JWT (Simple JWT)
- Контейнеризация: Docker + Docker Compose

## API Документация

После запуска проекта документация API доступна по адресу:
- Swagger UI: http://localhost:8000/swagger/
- ReDoc: http://localhost:8000/redoc/
- Django Admin: http://localhost:8000/admin/

## Настройки

Основные настройки находятся в config/settings.py. Для изменения поведения приложения используйте переменные окружения в файле .env.

### Основные переменные окружения

| Переменная | Описание | Пример |
|------------|----------|--------|
| POSTGRES_DB | Имя базы данных | mydb |
| POSTGRES_USER | Пользователь БД | admin |
| POSTGRES_PASSWORD | Пароль БД | secret |
| POSTGRES_HOST | Хост БД | db |
| POSTGRES_PORT | Порт БД | 5432 |
| REDIS_HOST | Хост Redis | redis |
| REDIS_PORT | Порт Redis | 6379 |
| EMAIL_HOST | SMTP сервер | smtp.gmail.com |
| EMAIL_PORT | SMTP порт | 587 |
| EMAIL_HOST_USER | Email пользователя | user@gmail.com |
| EMAIL_HOST_PASSWORD | Пароль приложения | app_password |
| SECRET_KEY | Секретный ключ Django | your-secret-key |
| DEBUG | Режим отладки | True/False |

## Docker команды

**Запуск проекта:**
docker-compose up

**Просмотр логов:**
docker-compose logs -f
docker-compose logs -f app

**Остановка проекта:**
docker-compose down

**Перезапуск сервиса:**
docker-compose restart app

**Выполнение команд внутри контейнера:**
docker-compose exec app python manage.py shell
docker-compose exec app python manage.py migrate
docker-compose exec app python manage.py createsuperuser

**Сборка образа заново:**
docker-compose up --build

## Безопасность

Важно:
- Никогда не коммитьте файл .env в репозиторий
- В production используйте DEBUG=False
- Обязательно измените SECRET_KEY на уникальный
- Настройте ALLOWED_HOSTS для вашего домена

## Зависимости

Основные Python пакеты:
- Django
- djangorestframework
- djangorestframework-simplejwt
- django-filter
- django-celery-beat
- psycopg2-binary
- redis
- celery
- python-dotenv

## Вклад в проект

- Создайте ветку для вашей фичи
- Внесите изменения
- Протестируйте изменения
- Отправьте pull request

## Лицензия

MIT License