# Docker Compose как карта проекта

## Главная мысль

Compose описывает маленькую систему сервисов в одном YAML: кто запускается, из какого image/build, с какими env, ports, networks и volumes. Это одновременно исполняемая инструкция и handoff-карта; хороший файл должен позволять понять судьбу данных и связи без набора запомненных `docker run`.

## Модели и правила

- **Service** — участник стека (`app`, `db`, `proxy`), доступный другим по имени в compose-network.
- `build` собирает локальный код; `image` использует готовую упаковку.
- `ports` публикует container port на host; внутренние сервисы не обязаны публиковаться наружу.
- `env_file`/environment передают configuration; secrets не должны находиться в YAML.
- **Named volume** сохраняет данные вне жизненного цикла контейнера; `down -v` удаляет volumes и может уничтожить базу.
- `depends_on` задаёт порядок старта, но не всегда готовность database; health/retry остаются отдельной задачей.

## Практический метод

Составьте карту `service → build/image → internal port → published port → env → volume → dependency`. Для `app + db` приложение использует hostname `db`, не `localhost`; у базы есть named volume, наружу публикуется только нужный app/proxy port. Запустите и наблюдайте:

```sh
docker compose up -d --build
docker compose ps
docker compose logs app --tail=100
docker compose logs db --tail=100
```

Создайте запись, перезапустите только `app`, затем весь стек без `-v` и проверьте сохранение. Перед `docker compose down -v` подтвердите точный project, содержимое volume и наличие backup; AI должен явно предупреждать об удалении. В handoff укажите команды first run, logs, update, stop и recovery.

## Антипаттерны

- Один огромный compose для local, production, tests и экспериментов с закомментированными сервисами.
- Использовать `localhost` для связи `app → db`.
- Защивать passwords/API keys в YAML или публиковать database/monitoring ports без причины.
- Полагать, что `depends_on` гарантирует готовую к запросам базу.
- Выполнять `down -v` как универсальное лечение.
- Считать `docker compose ps` с `Up` достаточной проверкой бизнес-сценария.

## Критерии проверки

- Сервисы имеют понятные имена и единственную объяснимую роль.
- Связи используют service names; опубликованы только необходимые ports.
- `.env.example` полон, реальные secrets отсутствуют в compose/Git.
- У постоянной базы объявлен volume и проверена сохранность после restart/recreate.
- `ps` и logs показывают здоровый запуск; app умеет дождаться/повторить связь с db.
- Главный сценарий проходит после `up -d --build` на чистой машине.
- Остановка, update, logs и риск `down -v` документированы для получателя.

## Связано с

- [Глава 03](ch03-software-architecture.md) — component map.
- [Глава 22](ch22-docker.md) — image/container fundamentals.
- [Глава 24](ch24-deployment.md) — production compose и proxy.
- [Глава 25](ch25-monitoring.md) — monitoring services.
- [Приложение В](appendix-c-compose-monitoring.md) — шаблон наблюдаемого стека.
