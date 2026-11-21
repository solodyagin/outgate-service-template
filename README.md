# Outgate Service Template

Шаблон прикладного Go-сервиса для [Outgate](https://github.com/solodyagin/outgate).

## Текущий статус

Репозиторий инициализирован документацией. Исходники сервиса, Go module, конфигурация, тесты и CI пока отсутствуют; собрать или запустить шаблон ещё нельзя.

Интеграция с Outgate требует будущего пакета `client` и опубликованной версии [outgate-sdk](https://github.com/solodyagin/outgate-sdk). Сейчас SDK содержит wire codecs `protocol/v1` и чистую HTTP state machine `wssstate`; транспортов и готового подключения к gateway ещё нет.

## Планируемый состав

- Точка входа `cmd/service` и прикладные HTTP handlers `/hello`, `/health`, `/ready`.
- Явно выбираемые режимы local, development и production.
- Подключение к gateway через SDK, readiness и graceful shutdown.
- Примеры конфигурации и инструкции запуска на Linux и Windows.
- Тесты handlers, конфигурации и жизненного цикла сервиса.

Шаблон будет использовать опубликованную фиксированную версию SDK без импорта исходников gateway, обязательного `go.work` или локальных `replace`.

Требования к реализации и приёмке описаны в [руководстве по разработке сервисов](https://github.com/solodyagin/outgate/blob/main/docs/service-development.md) и [ТЗ, раздел 10.3](https://github.com/solodyagin/outgate/blob/main/docs/requirements.md#103-отдельные-репозитории-шлюза-sdk-и-шаблона-сервиса).
