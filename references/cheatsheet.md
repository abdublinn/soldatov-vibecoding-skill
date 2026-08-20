# One-screen operating guide

## Stage selector
Идея не ясна → brief. Границы расплывчаты → MVP. Поведение не проверяемо → requirements. Решение не связано с частями системы → architecture. Перед правкой нет scope и rollback → implementation packet. Есть код без факта работы → run/test. Есть локальный результат без целевой среды → deploy/observe. Меняется владелец → handoff.

## Next artifact
Выбери ровно один: brief, MVP-рамка, карта требований, схема архитектуры, implementation packet, карта проекта, воспроизводимый test-result, deploy-plan или handoff packet.

## Exit gate
Цель, границы, критерий приёмки и способ проверки известны; для изменения — объяснимый минимальный diff и откат; для релиза — целевая среда, внешний smoke и наблюдение; для передачи — новый владелец может запустить, проверить и откатить.

## Red flags
AI угадывает пользователя, стек или доступы; MVP растёт; код появился раньше артефакта; локальный экран объявлен готовым продуктом; несколько гипотез или широких правок смешаны; секреты попали в чат, код или логи; нет backup/rollback; handoff состоит из одной ссылки.

## Minimal command checklist
Выбирай только команды, соответствующие контуру: `git status --short`; `git diff`; `docker compose ps`; `docker compose logs app --tail=100`; `curl -f http://127.0.0.1:8000/health`. Сначала наблюдай, затем меняй; опасные команды запускай только с понятными последствиями и возвратом.

## Handoff checklist
Передай назначение и версию; ссылки на brief/requirements/README; фактические setup/run/test-команды; безопасный маршрут доступов и секретов; данные, backup/restore, deploy/rollback; monitoring/runbook; ограничения и backlog; владельца следующего действия и подтверждение самостоятельной проверки.
