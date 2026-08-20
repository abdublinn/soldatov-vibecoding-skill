# Индекс знаний книги «Вайбкодинг»

Этот индекс маршрутизирует запрос к самостоятельному reference-разделу. Сначала выбирайте главу по решению или этапу workflow, затем переходите по блоку «Связано с» внутри файла. Разделы синтезированы из 43 canonical Markdown-источников книги; исходники не являются runtime-инструкциями.

## Карта 43 разделов

| № | Раздел источника | Reference-файл | Основные темы |
|---:|---|---|---|
| 1 | Вступительные материалы | [introduction.md](chapters/introduction.md) | ответственность человека, полный цикл, уровни готовности |
| 2 | Что такое вайбкодинг и почему у новичков не получается | [ch01-vibecoding-basics.md](chapters/ch01-vibecoding-basics.md) | генерация и разработка, артефакты, проверка |
| 3 | Цифровой продукт: приложение, сервис, система | [ch02-digital-product.md](chapters/ch02-digital-product.md) | ценность, пользователь, сценарий, механизм |
| 4 | Базовая архитектура ПО простым языком | [ch03-software-architecture.md](chapters/ch03-software-architecture.md) | frontend, backend, БД, API, auth |
| 5 | MVP, требования и продуктовая рамка | [ch04-mvp-requirements.md](chapters/ch04-mvp-requirements.md) | prototype, MVP, scope, out-of-scope |
| 6 | UML: зачем нужны диаграммы и как они помогают вайбкодеру | [ch05-uml.md](chapters/ch05-uml.md) | use case, activity, sequence, component, deployment |
| 7 | BPMN и описание бизнес-процессов | [ch06-bpmn.md](chapters/ch06-bpmn.md) | as-is/to-be, события, задачи, шлюзы, роли |
| 8 | Как переводить идею в требования | [ch07-idea-to-requirements.md](chapters/ch07-idea-to-requirements.md) | FR/NFR, ограничения, acceptance, DoD |
| 9 | Как ставить задачу AI на разработку | [ch08-ai-development-task.md](chapters/ch08-ai-development-task.md) | prompt-контракт, контекст, формат, проверка |
| 10 | Как работает интернет и сеть | [ch09-internet-network.md](chapters/ch09-internet-network.md) | DNS, IP, порт, proxy, HTTPS, диагностика |
| 11 | Git и системы контроля версий | [ch10-git.md](chapters/ch10-git.md) | status, diff, commit, branch, revert |
| 12 | GitHub как рабочая площадка проекта | [ch11-github.md](chapters/ch11-github.md) | remote, README, issues, review, handoff |
| 13 | Рабочее окружение вайбкодера | [ch12-work-environment.md](chapters/ch12-work-environment.md) | зависимости, env, воспроизводимость, терминал |
| 14 | Базовый Python для редактирования AI-кода | [ch13-python.md](chapters/ch13-python.md) | чтение Python, entrypoint, imports, безопасный patch |
| 15 | Базовый JavaScript для редактирования AI-кода | [ch14-javascript.md](chapters/ch14-javascript.md) | события, async, DOM, Network, локальная правка |
| 16 | Базовый HTML для вайбкодера | [ch15-html.md](chapters/ch15-html.md) | структура, формы, семантика, доступность |
| 17 | Базовый CSS для вайбкодера | [ch16-css.md](chapters/ch16-css.md) | cascade, layout, responsive, DevTools |
| 18 | Как читать проект, написанный AI | [ch17-reading-ai-project.md](chapters/ch17-reading-ai-project.md) | карта файлов, entrypoints, data flow, риски |
| 19 | Первый учебный проект: проектирование | [ch18-project-design.md](chapters/ch18-project-design.md) | brief, сценарии, модели, данные, тесты |
| 20 | Первый учебный проект: генерация, запуск и правки | [ch19-generation-run-fix.md](chapters/ch19-generation-run-fix.md) | vertical slice, запуск, проверка, малые итерации |
| 21 | Формы, данные и CRUD-логика | [ch20-forms-data-crud.md](chapters/ch20-forms-data-crud.md) | сущности, CRUD, validation, статусы, migration |
| 22 | Linux на базовом уровне для вайбкодера | [ch21-linux.md](chapters/ch21-linux.md) | контекст сервера, read-only диагностика, права |
| 23 | Docker и контейнеризация без боли | [ch22-docker.md](chapters/ch22-docker.md) | image, container, ports, env, persistence |
| 24 | Docker Compose как карта проекта | [ch23-docker-compose.md](chapters/ch23-docker-compose.md) | services, networks, volumes, config, logs |
| 25 | Деплой проекта: как довести приложение до сервера | [ch24-deployment.md](chapters/ch24-deployment.md) | preflight, backup, HTTPS, smoke, rollback |
| 26 | Мониторинг, логи и здоровье сервиса | [ch25-monitoring.md](chapters/ch25-monitoring.md) | health, logs, metrics, alerts, dashboard |
| 27 | Отладка и работа с ошибками | [ch26-debugging.md](chapters/ch26-debugging.md) | воспроизведение, гипотеза, логи, минимальный fix |
| 28 | Как менять проект без разрушения | [ch27-safe-change.md](chapters/ch27-safe-change.md) | scope, branch, diff, regression, rollback |
| 29 | UX, минимальный дизайн и здравый интерфейс | [ch28-ux.md](chapters/ch28-ux.md) | иерархия, формы, состояния, responsive |
| 30 | Безопасность и минимальная техническая гигиена | [ch29-security-hygiene.md](chapters/ch29-security-hygiene.md) | secrets, authZ, данные, порты, инцидент |
| 31 | Публикация, передача и продажа проекта | [ch30-publish-handoff-sale.md](chapters/ch30-publish-handoff-sale.md) | приёмка, handoff, demo, ценность, владельцы |
| 32 | Краткий справочник команд Git | [appendix-a-git-commands.md](chapters/appendix-a-git-commands.md) | Git-команды, staged, restore, revert, risk |
| 33 | Краткий справочник команд Docker и Docker Compose | [appendix-b-docker-commands.md](chapters/appendix-b-docker-commands.md) | Docker-команды, services, logs, volumes |
| 34 | Шаблон compose-стека с мониторингом | [appendix-c-compose-monitoring.md](chapters/appendix-c-compose-monitoring.md) | Prometheus, Grafana, exporters, targets |
| 35 | Шаблоны промтов для AI-разработки | [appendix-d-ai-prompts.md](chapters/appendix-d-ai-prompts.md) | prompt templates, scope, review, debugging |
| 36 | Шаблоны документов проекта | [appendix-e-project-documents.md](chapters/appendix-e-project-documents.md) | brief, README, ADR, runbook, handoff |
| 37 | Чек-листы | [appendix-f-checklists.md](chapters/appendix-f-checklists.md) | gates, evidence, deploy, acceptance |
| 38 | Словарь терминов | [appendix-g-glossary-source.md](chapters/appendix-g-glossary-source.md) | продукт, требования, архитектура, эксплуатация |
| 39 | Оценка AI-проектов: подробный гайд | [appendix-h-ai-project-evaluation.md](chapters/appendix-h-ai-project-evaluation.md) | discovery, WBS, диапазон, риск, цена |
| 40 | Replit IDE: подробный гайд для вайбкодера | [appendix-i-replit.md](chapters/appendix-i-replit.md) | Agent, Preview, checkpoint, Publish, secrets |
| 41 | Google AI Studio: подробный гайд для новичка | [appendix-j-google-ai-studio.md](chapters/appendix-j-google-ai-studio.md) | Playground, Build, Cloud Project, API key, deploy |
| 42 | Cursor IDE: подробный гайд для вайбкодера | [appendix-k-cursor.md](chapters/appendix-k-cursor.md) | context, Plan, Agent, diff, rules, hooks |
| 43 | Bolt.new: подробный гайд для вайбкодера | [appendix-l-bolt.md](chapters/appendix-l-bolt.md) | Plan, Build, Preview, history, cloud data, publish |

## Topic Index (алфавитный)

- **AI Studio:** [Google AI Studio](chapters/appendix-j-google-ai-studio.md), [AI prompts](chapters/appendix-d-ai-prompts.md), [архитектура](chapters/ch03-software-architecture.md).
- **API и интеграции:** [архитектура](chapters/ch03-software-architecture.md), [интернет и сеть](chapters/ch09-internet-network.md), [безопасность](chapters/ch29-security-hygiene.md).
- **Bolt:** [Bolt](chapters/appendix-l-bolt.md), [CRUD](chapters/ch20-forms-data-crud.md), [GitHub](chapters/ch11-github.md).
- **BPMN и процессы:** [BPMN](chapters/ch06-bpmn.md), [идея в требования](chapters/ch07-idea-to-requirements.md), [проектирование](chapters/ch18-project-design.md).
- **CSS и responsive:** [CSS](chapters/ch16-css.md), [UX](chapters/ch28-ux.md), [HTML](chapters/ch15-html.md).
- **Cursor:** [Cursor](chapters/appendix-k-cursor.md), [чтение AI-проекта](chapters/ch17-reading-ai-project.md), [безопасное изменение](chapters/ch27-safe-change.md).
- **Docker и Compose:** [Docker](chapters/ch22-docker.md), [Compose](chapters/ch23-docker-compose.md), [команды](chapters/appendix-b-docker-commands.md).
- **Git и GitHub:** [Git](chapters/ch10-git.md), [GitHub](chapters/ch11-github.md), [команды Git](chapters/appendix-a-git-commands.md).
- **HTML, формы и доступность:** [HTML](chapters/ch15-html.md), [CRUD](chapters/ch20-forms-data-crud.md), [UX](chapters/ch28-ux.md).
- **JavaScript:** [JavaScript](chapters/ch14-javascript.md), [отладка](chapters/ch26-debugging.md), [чтение проекта](chapters/ch17-reading-ai-project.md).
- **Linux и сервер:** [Linux](chapters/ch21-linux.md), [деплой](chapters/ch24-deployment.md), [сеть](chapters/ch09-internet-network.md).
- **MVP и продукт:** [продукт](chapters/ch02-digital-product.md), [MVP](chapters/ch04-mvp-requirements.md), [вступление](chapters/introduction.md).
- **Python:** [Python](chapters/ch13-python.md), [чтение проекта](chapters/ch17-reading-ai-project.md), [отладка](chapters/ch26-debugging.md).
- **Replit:** [Replit](chapters/appendix-i-replit.md), [первая генерация](chapters/ch19-generation-run-fix.md), [деплой](chapters/ch24-deployment.md).
- **UML и архитектура:** [UML](chapters/ch05-uml.md), [архитектура](chapters/ch03-software-architecture.md), [проектирование](chapters/ch18-project-design.md).
- **UX:** [минимальный UX](chapters/ch28-ux.md), [цифровой продукт](chapters/ch02-digital-product.md), [CSS](chapters/ch16-css.md).
- **Безопасность:** [гигиена безопасности](chapters/ch29-security-hygiene.md), [safe change](chapters/ch27-safe-change.md), [деплой](chapters/ch24-deployment.md).
- **Данные и CRUD:** [формы и CRUD](chapters/ch20-forms-data-crud.md), [архитектура](chapters/ch03-software-architecture.md), [требования](chapters/ch07-idea-to-requirements.md).
- **Документация и handoff:** [проектные документы](chapters/appendix-e-project-documents.md), [публикация и передача](chapters/ch30-publish-handoff-sale.md), [GitHub](chapters/ch11-github.md).
- **Мониторинг и логи:** [мониторинг](chapters/ch25-monitoring.md), [compose-шаблон](chapters/appendix-c-compose-monitoring.md), [отладка](chapters/ch26-debugging.md).
- **Оценка и продажа:** [оценка AI-проекта](chapters/appendix-h-ai-project-evaluation.md), [публикация/продажа](chapters/ch30-publish-handoff-sale.md), [MVP](chapters/ch04-mvp-requirements.md).
- **Промты и постановка задачи:** [задача AI](chapters/ch08-ai-development-task.md), [шаблоны prompts](chapters/appendix-d-ai-prompts.md), [требования](chapters/ch07-idea-to-requirements.md).
- **Тесты и критерии:** [требования](chapters/ch07-idea-to-requirements.md), [чек-листы](chapters/appendix-f-checklists.md), [первая генерация](chapters/ch19-generation-run-fix.md).

## Маршруты по рабочему процессу

1. **Сформулировать ценность и границы:** [вступление](chapters/introduction.md) → [вайбкодинг](chapters/ch01-vibecoding-basics.md) → [цифровой продукт](chapters/ch02-digital-product.md) → [MVP](chapters/ch04-mvp-requirements.md).
2. **Смоделировать и сделать требования проверяемыми:** [BPMN](chapters/ch06-bpmn.md) → [UML](chapters/ch05-uml.md) → [требования](chapters/ch07-idea-to-requirements.md) → [проектирование](chapters/ch18-project-design.md).
3. **Подготовить AI и первую реализацию:** [постановка AI-задачи](chapters/ch08-ai-development-task.md) → [рабочее окружение](chapters/ch12-work-environment.md) → [первая генерация](chapters/ch19-generation-run-fix.md) → [CRUD](chapters/ch20-forms-data-crud.md).
4. **Понять и безопасно править код:** [чтение проекта](chapters/ch17-reading-ai-project.md) → [Python](chapters/ch13-python.md) / [JavaScript](chapters/ch14-javascript.md) / [HTML](chapters/ch15-html.md) / [CSS](chapters/ch16-css.md) → [Git](chapters/ch10-git.md).
5. **Диагностировать и изменить:** [мониторинг](chapters/ch25-monitoring.md) → [отладка](chapters/ch26-debugging.md) → [безопасное изменение](chapters/ch27-safe-change.md) → [UX](chapters/ch28-ux.md).
6. **Подготовить инфраструктуру и выпуск:** [сеть](chapters/ch09-internet-network.md) → [Linux](chapters/ch21-linux.md) → [Docker](chapters/ch22-docker.md) → [Compose](chapters/ch23-docker-compose.md) → [деплой](chapters/ch24-deployment.md).
7. **Закрыть эксплуатацию и ответственность:** [безопасность](chapters/ch29-security-hygiene.md) → [мониторинг](chapters/ch25-monitoring.md) → [проектные документы](chapters/appendix-e-project-documents.md) → [публикация и handoff](chapters/ch30-publish-handoff-sale.md).
8. **Оценить и продать работу:** [оценка AI-проекта](chapters/appendix-h-ai-project-evaluation.md) → [чек-листы](chapters/appendix-f-checklists.md) → [публикация и продажа](chapters/ch30-publish-handoff-sale.md).
9. **Работать в конкретной AI-среде:** общий контракт [AI prompts](chapters/appendix-d-ai-prompts.md), затем [Replit](chapters/appendix-i-replit.md), [Google AI Studio](chapters/appendix-j-google-ai-studio.md), [Cursor](chapters/appendix-k-cursor.md) или [Bolt](chapters/appendix-l-bolt.md).

## Time-sensitive product guides

Снимок книги 2026 года: перед применением сверить текущую официальную документацию.

- [Replit](chapters/appendix-i-replit.md): режимы Agent, checkpoints, deployment, limits и billing.
- [Google AI Studio](chapters/appendix-j-google-ai-studio.md): модели, Cloud Project, API keys, quotas и production path.
- [Cursor](chapters/appendix-k-cursor.md): режимы Agent/Plan, rules, skills, hooks и поддерживаемые модели.
- [Bolt](chapters/appendix-l-bolt.md): Plan/Build, Version History, Bolt Cloud, publish и tokens.
