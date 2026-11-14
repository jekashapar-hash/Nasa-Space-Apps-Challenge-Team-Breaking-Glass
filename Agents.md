# Правила разработки в монорепозитории (зона Backend)

Этот репозиторий разделен на две независимые директории:

- `back_end/` — Python / Django (твоя единственная рабочая зона).

- `front_end/` — фронтенд (работает другой разработчик).

## 1. Жесткие границы

- НИКОГДА не создавай, не изменяй и не удаляй файлы внутри папки `front_end/`.

- Весь код бэкенда, виртуальное окружение (`.venv`), `pyproject.toml` и [`manage.py`](http://manage.py) должны находиться строго внутри `back_end/`.

## 2. Работа с uv и Django

- Перед выполнением любых команд Python/Django переходи в директорию `back_end` (`cd back_end`) или запускай команды с флагом директории: `uv --directory back_end run <команда>`.

- Для установки зависимостей используй: `uv --directory back_end add <пакет>` (или `uv add <пакет>` находясь внутри `back_end/`).

- НИКОГДА не используй `pip`, `poetry` или ручную активацию `venv`.

- Примеры запуска команд из корня репозитория:

  - Создание проекта Django: `uv --directory back_end run django-admin startproject config .`

  - Создание приложения: `uv --directory back_end run python [manage.py](http://manage.py) startapp <app_name>`

  - Проверка и миграции: `uv --directory back_end run python [manage.py](http://manage.py) check` и `uv --directory back_end run python [manage.py](http://manage.py) migrate`

## 3. Стандарты кода

- Выноси секреты в `back_end/.env` (не коммитить) и создавай `back_end/.env.example`.

- Разделяй бизнес-логику ([`services.py`](http://services.py)) и представления ([`views.py`](http://views.py)).