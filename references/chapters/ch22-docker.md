# Docker и контейнеризация без боли

## Главная мысль

Docker делает окружение явным и повторяемым: Dockerfile — рецепт, image — собранная упаковка, container — запущенный экземпляр. Он помогает переносить проект, но не исправляет плохую архитектуру; особенно важно понимать port mapping, env, persistent data и logs.

## Модели и правила

- **Dockerfile** фиксирует base image, workdir, dependencies, copied files и startup command.
- **Image** неизменяемо собирается из контекста; ручная правка внутри container исчезает при пересоздании.
- `host_port:container_port` задаёт внешний вход; приложение внутри должно слушать подходящий address, обычно `0.0.0.0`.
- `.dockerignore` исключает `.env`, `.venv`, caches, local database и ненужный build context.
- Секреты передаются при запуске через env/secrets, не зашиваются в image.
- Данные внутри writable layer контейнера временны; постоянное состояние выносится в volume/external database.

## Практический метод

Сначала подтвердите запуск без Docker. Создайте минимальный Dockerfile с конкретной версией base image, `WORKDIR`, установкой dependencies из файла и реальной startup command. Соберите и запустите:

```sh
docker build -t support-app:latest .
docker run --detach --name support-app-check -p 8000:8000 --env-file .env support-app:latest
docker ps --filter "name=support-app-check"
docker logs --tail=100 support-app-check
docker stop support-app-check
docker rm support-app-check
```

Откройте приложение, пройдите главный сценарий, остановите container и объясните судьбу данных. При «container running, сайт не открыт» проверяйте logs, internal listen address, container port, mapping и env. Новую dependency добавляйте в project file, пересобирайте image и повторяйте smoke-test.

## Антипаттерны

- Добавить Docker ради «production-вида» до стабильного локального запуска.
- Использовать `latest` везде и не фиксировать base image/dependencies.
- Копировать `.env`, virtualenv, caches и локальную базу в image.
- Сохранять код/данные вручную внутри container.
- Открывать лишние ports или запускать приложение только на `127.0.0.1` внутри container.
- Диагностировать локальный bug полным rebuild всей инфраструктуры без логов.

## Критерии проверки

- Проект запускается без Docker, а Dockerfile отражает фактическую команду.
- Base image version, `WORKDIR`, dependency installation и startup command явны.
- `.dockerignore` исключает секреты и мусор; image не содержит реальные ключи.
- Port mapping понятен, приложение доступно на ожидаемом host URL.
- `docker logs` показывает startup и пользовательский запрос без критических ошибок.
- Судьба данных при stop/remove/recreate описана и проверена.
- Другой компьютер может собрать image и пройти тот же smoke-test.

## Связано с

- [Глава 12](ch12-work-environment.md) — зависимости и воспроизводимый запуск.
- [Глава 21](ch21-linux.md) — серверный контекст и команды.
- [Глава 23](ch23-docker-compose.md) — несколько сервисов и volumes.
- [Глава 24](ch24-deployment.md) — контейнерный rollout.
- [Приложение Б](appendix-b-docker-commands.md) — точный command reference.
