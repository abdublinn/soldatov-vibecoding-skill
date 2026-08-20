# Шаблон compose-стека с мониторингом

## Главная мысль

Шаблон мониторинга — отправная архитектура, а не готовый production-рецепт. Его ценность в явном разделении ролей: Prometheus опрашивает targets и хранит временные ряды, Grafana читает их и строит панели, node exporter показывает хост, cAdvisor — контейнеры. Перед применением нужно сверить версии образов, сетевую модель, порты, retention, ресурсы и защиту доступа. Сначала докажи прохождение данных от exporter до dashboard, затем наращивай панели и alerts.

## Модели и правила

- Поток: **exporter/app metrics → Prometheus scrape → time series → Grafana datasource → dashboard/alert**. Ошибку ищи по этой цепочке.
- Monitoring лучше держать в отдельном Compose-контуре или явно отделённых services/network, чтобы обновление приложения не удаляло его данные.
- Постоянные volumes нужны Prometheus/Grafana, если история и настройки должны пережить пересоздание. Для них задаются retention и контроль диска.
- Порты интерфейсов не должны быть публичными по умолчанию. Привязка `127.0.0.1:<host>:<container>` оставляет доступ локальному proxy/SSH tunnel.
- `depends_on` задаёт порядок создания, но не гарантирует готовность datasource/target; readiness подтверждается health и страницей targets.
- Конкретные теги образов лучше плавающего `latest`; обновление выполняется отдельно и проверяется на совместимость конфигурации/данных.

## Практический метод

1. Зафиксируй цели: какие пользовательские и системные сигналы нужны, срок хранения, кто видит панели, куда приходят alerts.
2. В Compose опиши Prometheus, Grafana, node exporter и cAdvisor; выдели сеть и named volumes. Привязывай UI к localhost либо закрытому proxy.
3. В `prometheus.yml` добавь targets по DNS-имени service и внутреннему порту, не по случайному container IP. Для приложения используй стабильный `/metrics`.
4. Перед запуском проверь разрешённую конфигурацию и статус:

```bash
docker compose config
docker compose up -d
docker compose ps
docker compose logs prometheus --tail=100
docker compose logs grafana --tail=100
```

5. Открой Prometheus Targets через защищённый доступ: все ожидаемые endpoints должны быть `UP`. Затем добавь Prometheus datasource в Grafana и выполни простой запрос.
6. Создай минимальную панель: availability, request errors/latency, CPU, RAM, disk, restarts. Проверь данные искусственной безопасной нагрузкой.
7. Ограничь ресурсы/retention, смени начальные пароли, настрой backup конфигурации и volumes, протестируй alert и задокументируй обновление/rollback.

## Антипаттерны

- Копировать Compose из книги напрямую в production без проверки текущих images и документации.
- Публиковать Grafana, Prometheus, cAdvisor и exporters на `0.0.0.0` без аутентификации и firewall.
- Использовать container IP в targets: он меняется при пересоздании.
- Считать наличие панели доказательством сбора корректных метрик, не проверив Targets и запрос.
- Хранить пароль администратора Grafana в Compose-файле репозитория.
- Не ограничивать retention и обнаружить заполненный диск уже после отказа приложения.
- Удалять monitoring volumes при обычном `down` или переносе без backup.

## Критерии проверки

- `docker compose config` проходит, версии images зафиксированы и сверены с текущей документацией.
- Все services запущены без цикла restart; логи не показывают ошибок конфигурации/прав.
- Prometheus Targets отображает ожидаемые endpoints как `UP`; Grafana datasource отвечает успешно.
- Панель показывает актуальные значения и реагирует на безопасное тестовое событие.
- UI/metrics endpoints не доступны публично без предусмотренной защиты; начальные credentials заменены.
- Retention, ресурсы, volumes, backup и disk alert определены.
- Runbook содержит команды проверки, владельца, способ обновления и отката мониторинга.

## Связано с

- [Мониторинг](ch25-monitoring.md) — выбор сигналов и alerts.
- [Docker Compose](ch23-docker-compose.md) — сети, services и volumes.
- [Развёртывание](ch24-deployment.md) — защищённая публикация и rollback.
- [Безопасность](ch29-security-hygiene.md) — доступ к панелям, секреты и минимальная поверхность.
