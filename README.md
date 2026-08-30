# Kittygram

[![Main Kittygram workflow](https://github.com/FanisNK/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/FanisNK/kittygram_final/actions/workflows/main.yml)

Kittygram — веб-приложение для публикации информации о домашних котах.

Пользователи могут создавать записи о своих питомцах, добавлять фотографии, указывать имя, возраст и достижения кота. Для работы с данными используется API на Django REST Framework, а пользовательский интерфейс реализован на React.

## Возможности

* регистрация и авторизация пользователей;
* добавление, редактирование и удаление информации о котах;
* загрузка фотографий котов;
* добавление достижений;
* просмотр записей других пользователей;
* работа с данными через REST API;
* административная панель Django;
* автоматическое тестирование проекта;
* сборка Docker-образов;
* автоматический деплой на сервер через GitHub Actions.

## Стек технологий

### Backend

* Python 3.10
* Django 5.1.1
* Django REST Framework 3.15.2
* Djoser 2.3.1
* PostgreSQL
* Gunicorn
* Pillow

### Frontend

* React 17
* React Router
* React Scripts
* Jest / React Testing Library

### DevOps

* Docker
* Docker Compose
* Nginx
* GitHub Actions
* Docker Hub

## Структура проекта

```text
kittygram_final/
├── backend/                  # Backend на Django
├── frontend/                 # Frontend на React
├── nginx/                    # Конфигурация Nginx
├── tests/                    # Автотесты проекта
├── .github/workflows/        # GitHub Actions
├── docker-compose.yml        # Docker Compose для локального запуска
├── docker-compose.production.yml
├── kittygram_workflow.yml    # Конфигурация workflow для проверки
├── tests.yml                 # Конфигурация автотестов
├── .env.example              # Пример переменных окружения
└── README.md
```

## Запуск проекта локально

### 1. Клонировать репозиторий

```bash
git clone https://github.com/FanisNK/kittygram_final.git
cd kittygram_final
```

### 2. Создать файл `.env`

Скопируйте пример файла:

```bash
cp .env.example .env
```

При необходимости измените значения переменных.

### 3. Запустить проект

Для запуска контейнеров используйте Docker Compose:

```bash
docker compose up -d
```

После запуска приложение будет доступно по адресу:

```text
http://localhost
```

### 4. Остановить проект

```bash
docker compose down
```

## Переменные окружения

Пример переменных находится в файле `.env.example`:

```env
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
```

Файл `.env` не следует добавлять в Git-репозиторий, так как он может содержать конфиденциальные данные.

## Запуск автотестов

Для локального запуска тестов можно создать виртуальное окружение:

```bash
python3 -m venv env
```

Активация виртуального окружения на Linux/macOS:

```bash
source env/bin/activate
```

Установка зависимостей:

```bash
python -m pip install --upgrade pip
pip install -r backend/requirements.txt
```

Запуск тестов из корня проекта:

```bash
pytest
```

## CI/CD

При каждом push в ветку `main` GitHub Actions запускает workflow.

Workflow выполняет следующие действия:

1. устанавливает зависимости backend;
2. запускает проверку Flake8;
3. запускает тесты Django;
4. устанавливает зависимости frontend;
5. запускает тесты frontend;
6. собирает Docker-образы backend, frontend и gateway;
7. отправляет образы в Docker Hub;
8. подключается к серверу по SSH;
9. обновляет контейнеры приложения;
10. выполняет миграции и собирает статику;
11. отправляет сообщение об успешном деплое в Telegram.

Статус workflow можно посмотреть по бейджу в начале этого README или во вкладке **Actions** репозитория.

## Автор

**Fanis Safiullin**

GitHub: https://github.com/FanisNK
