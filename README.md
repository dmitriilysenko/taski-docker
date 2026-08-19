# Taski - Менеджер задач
[![Main Taski workflow](https://github.com/dmitriilysenko/taski-docker/actions/workflows/main.yml/badge.svg)](https://github.com/dmitriilysenko/taski-docker/actions/workflows/main.yml)
## Описание
**Taski** — это простое веб-приложение для управления задачами, разработанное на **Django** и **React**. 
Проект позволяет создавать, редактировать, отмечать выполненные и удалять задачи. **Taski** создан для упрощения планирования и повышения продуктивности.
Помимо прочего реализована возможность разворачивания проекта при помощи **Docker Compose**.

**Доступен по адресу:** [https://taski-docker.hopto.org/](https://taski-docker.hopto.org/)

### Основные возможности
- Создание задач с заголовком и описанием
- Отметка о выполнении
- Редактирование и удаление задач
- Хранение данных в PostgreSQL

## Установка и запуск

### Требования
- Docker и Docker Compose
- Git
- Python 3.12+

### Локальный запуск (без Docker)
```bash
# Клонировать репозиторий
git clone https://github.com/dmitriilys/taski-docker.git
cd taski-docker

# Установить зависимости для бэкенда
cd backend
python -m venv venv

# Для UNIX-подобных систем 
source venv/bin/activate

# Для Windows
source venv/Script/activate  

pip install -r requirements.txt

# Выполнить тесты
python manage.py test

# Выполнить миграции и запустить сервер
python manage.py migrate
python manage.py runserver
```

### Запуск с Docker
```bash
# Запустить проект в контейнерах
docker compose -f docker-compose.production.yml up -d

# Остановить проект
docker compose -f docker-compose.production.yml down
```

### Примеры запросов к API

| Метод | Эндпоинт | Описание |
|-------|----------|----------|
| GET | `/api/tasks/` | Получить список всех задач |
| POST | `/api/tasks/` | Создать новую задачу |
| PATCH | `/api/tasks/{id}/` | Обновить задачу |
| DELETE | `/api/tasks/{id}/` | Удалить задачу |

**Пример создания задачи:**
```bash
curl -X POST https://taski-docker.hopto.org/api/tasks/ \
  -H "Content-Type: application/json" \
  -d '{"title": "Новая задача", "description": "Описание"}'
```

## Используемые технологии
- **Django** — веб-фреймворк для бэкенда
- **Django REST Framework** — создание API
- **React** — фронтенд-библиотека
- **PostgreSQL** — база данных
- **Docker** — контейнеризация
## Автор
**Лысенко Дмитрий**  
[GitHub](https://github.com/dmitriilys)