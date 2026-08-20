# Bolt.new: подробный гайд для вайбкодера

Снимок книги 2026 года: перед применением сверить текущую официальную документацию.

## Главная мысль

Bolt ускоряет создание full-stack прототипа в браузере: AI формирует план и файлы, Preview показывает приложение, cloud-возможности могут дать БД, auth, functions и публикацию. Без дисциплины это приводит к длинной генерации, расходу tokens, скрытым изменениям схемы и ложной уверенности из-за работающего preview. Управляй Bolt короткими этапами: план, маленький target, просмотр Code/Diff, Version History, сценарная проверка, GitHub и отдельная production-приёмка. Возможности Bolt Cloud и тарифные ограничения требуют текущей сверки.

## Модели и правила

- Plan обсуждает архитектуру и scope; Build изменяет проект. Переключение в изменение должно быть сознательным после проверки плана.
- Preview — исполняемый интерфейс, Code View — фактические файлы. Ошибка может находиться в UI, backend/function, БД, auth, integration или конфигурации.
- Version History помогает вернуть код/состояние проекта, но не следует считать её гарантированным rollback внешней или cloud database. Для данных нужен отдельный backup/migration plan.
- Bolt Cloud может объединять database, authentication, server functions, file storage, analytics и payment-интеграции. У каждого ресурса есть owner, region/limits, secrets и production-настройки.
- Focus/target/lock files ограничивают изменение; точные названия controls могут меняться, но принцип неизменен: запрещай несвязанные зоны и проси список файлов.
- Tokens/usage — ограниченный ресурс. Цена длинного хаотичного диалога выше, чем короткого brief, отдельного плана и узкой итерации.

## Практический метод

1. Подготовь brief: пользователь, основной сценарий, MVP/out-of-scope, данные/роли, acceptance и допустимые cloud-зависимости.
2. В Plan попроси архитектуру, entities/statuses, routes/functions, этапы, риски и вопросы. Выбери первый vertical slice без платежей и лишних интеграций.
3. До Build создай точку Version History/синхронизации. Задай target, разрешённые файлы и запрет на смену стека/схемы без подтверждения.
4. После итерации просмотри Code View и изменения: зависимости, client/server границы, authZ, секреты, migration и обработку ошибок. Затем проверь Preview во всех состояниях.
5. Для cloud БД/auth/functions создай тестовые роли/данные, проверь доступ к чужому объекту, перезапуск и migration. Перед опасным изменением экспортируй/резервируй данные.
6. Подключи GitHub как независимую историю. Проверь README, `.env.example`, чистый clone/build и владельцев repository/cloud/billing.
7. Перед Publish проверь public/private режим, домен/HTTPS, production secrets, limits/cost, health/logs, внешний smoke и rollback кода плюс данных.

## Антипаттерны

- Одним сообщением просить marketplace/SaaS со всеми ролями, оплатой и админкой.
- Продолжать Build после неверного плана, надеясь исправить следующими prompts.
- Считать Preview доказательством backend-авторизации и постоянства данных.
- Полагаться на Version History как на backup БД или транзакционный rollback migration.
- Разрешать AI менять unlocked проект целиком ради локальной UI-правки.
- Вставлять payment/API secrets в prompt или client code.
- Публиковать проект с неверным privacy-режимом либо оставлять cloud/billing на аккаунте исполнителя.

## Критерии проверки

- Plan согласован, MVP и первый vertical slice ограничены, неизвестные вынесены в вопросы.
- Build затронул только ожидаемые файлы; Version History/Git дают точку возврата кода.
- Preview проходит happy/empty/error/mobile, а Code View подтверждает корректный поток данных.
- AuthN/authZ проверены негативными сценариями; secrets находятся server-side.
- Для cloud data известны schema, migration, persistence, backup и отдельный rollback.
- GitHub clone/build воспроизводим; owners ресурсов, домена и billing переданы.
- Published URL, privacy, HTTPS, logs, limits и внешний сценарий проверены по текущей документации.

## Связано с

- [MVP](ch04-mvp-requirements.md) и [проектирование](ch18-project-design.md) — scope до Build.
- [Формы и CRUD](ch20-forms-data-crud.md) — данные, статусы и authZ.
- [GitHub](ch11-github.md) и [безопасные изменения](ch27-safe-change.md) — история и узкий diff.
- [Развёртывание](ch24-deployment.md), [безопасность](ch29-security-hygiene.md) — production-проверка.
