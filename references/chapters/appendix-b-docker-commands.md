# Краткий справочник команд Docker и Docker Compose

## Главная мысль

Команды контейнерного контура следует выбирать по объекту и последствию: image — шаблон, container — запущенный экземпляр, service — роль в Compose, volume — постоянные данные, network — связь. Безопасная работа начинается с обзора `ps`, конфигурации и логов, затем меняет только нужный слой. Особенно важно отличать перезапуск/пересборку от удаления: очистка контейнера обычно обратима, удаление volume может уничтожить единственную копию данных.

## Модели и правила

- `docker build` создаёт image; `docker run` создаёт container; `docker compose up` приводит набор services к описанному состоянию.
- `docker ps`/`docker compose ps` показывают процессы, но не подтверждают пользовательскую функцию. Дополняй logs, health и smoke-тестом.
- `docker logs` относится к container, `docker compose logs <service>` — к роли в проекте. Имена service бери из `compose.yaml`, не угадывай по имени контейнера.
- `restart` не применяет новый image или часть конфигурации; после изменения сборки нужен `up -d --build` для нужного service.
- Bind mount связывает путь хоста, named volume управляется Docker. До операций с данными выясни тип, точное имя и способ backup/restore.
- `down` останавливает и удаляет compose containers/networks; `down -v` дополнительно удаляет volumes. Флаг `-v` не является обычной очисткой.

## Практический метод

Диагностический минимум:

```bash
docker compose config
docker compose ps
docker compose logs app --tail=100
docker stats --no-stream
```

Сборка и проверка одного образа:

```bash
docker build -t support-app:latest .
docker run --detach --name support-app-check -p 8000:8000 --env-file .env support-app:latest
docker ps --filter "name=support-app-check"
docker logs --tail=100 support-app-check
docker stop support-app-check
docker rm support-app-check
```

Управление проектом:

```bash
docker compose up -d --build
docker compose ps
docker compose logs -f app
docker compose restart app
docker compose down
```

Перед обновлением БД найди volumes (`docker volume ls`, `docker inspect <container>`), сделай прикладной backup и проверь путь восстановления. После запуска проверь `curl` к health и ключевой сценарий. Для уборки сначала перечисли объекты и установи, кто ими владеет; не применяй prune к незнакомому хосту.

## Антипаттерны

- Лечить любую ошибку пересборкой всех сервисов без чтения первого сбоя в логах.
- Путать host port и container port или открывать БД на все интерфейсы.
- Использовать `latest` как единственный идентификатор production-версии без digest/tag/commit.
- Встраивать `.env` и секреты в image либо передавать их в Dockerfile.
- Запускать `docker compose down -v`, `docker system prune -a` или `docker volume prune` без точного списка и backup.
- Редактировать файлы внутри работающего container как постоянное исправление: при пересоздании правка исчезнет.
- Считать container healthy только потому, что процесс не завершился.

## Критерии проверки

- Понятно, к какому Docker/Compose проекту и service относится каждая команда.
- `docker compose config` успешно разрешает переменные и показывает ожидаемые ports, volumes, networks.
- Образы имеют идентифицируемые версии, containers созданы из ожидаемых images.
- Логи и health-check подтверждают работу, ключевой сценарий проходит извне.
- Постоянные данные находятся в известном volume/mount и переживают безопасное пересоздание container.
- Ненужные порты не опубликованы, секреты не встроены в image или репозиторий.
- Для удаления/обновления есть backup и понятный rollback; destructive-команды не применялись по умолчанию.

## Связано с

- [Docker](ch22-docker.md) и [Docker Compose](ch23-docker-compose.md) — модель контейнеров и сервисов.
- [Развёртывание](ch24-deployment.md) — production-порядок и внешний smoke.
- [Отладка](ch26-debugging.md) — чтение состояния до перезапуска.
- [Шаблон мониторинга](appendix-c-compose-monitoring.md) — отдельный наблюдаемый стек.
