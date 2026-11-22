# Outgate Service Template

Шаблон прикладного Go-сервиса для [Outgate](https://github.com/solodyagin/outgate).

## Текущий статус

Репозиторий инициализирован документацией. Исходники сервиса, Go module, конфигурация, тесты и CI пока отсутствуют; собрать или запустить шаблон ещё нельзя.

Готовая интеграция шаблона требует будущего пакета `client` и SDK release с фиксированной версией [outgate-sdk](https://github.com/solodyagin/outgate-sdk). SDK уже содержит wire codecs, модели lifecycle, HTTP signatures, QUIC bootstrap/control и потоковый HTTP/3, а также service-side `quicsession` driver для readiness/status, minor-1 drain/unregister и actual cleanup. Прикладной Client/dial, автоматический reconnect и WebSocket/Hijacker ещё не реализованы; самостоятельный готовый boilerplate пока отсутствует.

## Планируемый состав

- Точка входа `cmd/service` и прикладные HTTP handlers `/hello`, `/health`, `/ready`.
- Явно выбираемые режимы local, development и production.
- Подключение к gateway через SDK, readiness и graceful shutdown.
- Примеры конфигурации и инструкции запуска на Linux и Windows.
- Тесты handlers, конфигурации и жизненного цикла сервиса.

Шаблон будет использовать опубликованную фиксированную версию SDK и не будет импортировать исходники gateway. Локальные `replace` не потребуются; файл `go.work` для сборки не требуется.

Требования к реализации и приёмке описаны в [руководстве по разработке сервисов](https://github.com/solodyagin/outgate/blob/main/docs/service-development.md) и [ТЗ, раздел 10.3](https://github.com/solodyagin/outgate/blob/main/docs/requirements.md#103-отдельные-репозитории-шлюза-sdk-и-шаблона-сервиса).
