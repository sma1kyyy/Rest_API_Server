# REST API Server

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0E9F6E?logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white)

Учебный проект по микросервисной архитектуре: REST API на Python/FastAPI, контейнеризация и балансировка запросов через Nginx.

## Возможности

- CRUD-маршруты для ресурсов `contact` и `group`;
- валидация моделей через Pydantic;
- запуск приложения в Docker;
- несколько экземпляров API-сервиса;
- маршрутизация запросов через Nginx;
- Docker Compose для воспроизводимого локального запуска.

## Архитектура

```text
HTTP client
    │
    ▼
Nginx load balancer
    ├── API replica 1
    ├── API replica 2
    └── API replica 3
```

Маршруты `/api/v1/contact` распределяются между экземплярами API, а `/api/v1/group` направляются в отдельный upstream согласно конфигурации Nginx.

## Стек

- Python 3.12
- FastAPI, Uvicorn, Pydantic
- Docker и Docker Compose
- Nginx
- REST API, HTTP, JSON

## Запуск

Требуется Docker Desktop или Docker Engine с Compose.

```bash
docker compose up --build
```

После запуска API доступен через Nginx:

```bash
curl http://localhost/api/v1/contact/
```

Документация FastAPI:

- `http://localhost/docs`
- `http://localhost/redoc`

## Структура

```text
.
├── app/                 # модели и общие компоненты
├── cmd/                 # точка входа и API-роутеры
├── nginx/               # Dockerfile и конфигурация балансировщика
├── templates/           # простая web-страница проекта
├── compose.yaml
├── Dockerfile
└── requirements.txt
```

## Что демонстрирует проект

Проект показывает базовые практики backend-разработки и эксплуатации сервисов: разделение ответственности, API-контракты, контейнеризацию, горизонтальное масштабирование и reverse proxy.

Автор: [Кирилл Куликов](https://github.com/sma1kyyy)
