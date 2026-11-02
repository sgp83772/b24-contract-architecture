# Архитектура портала договоров на Bitrix24 (ООО «Альфа-Строй»)

Пет-проект: архитектурные артефакты для корпоративного портала на коробочном Bitrix24.

## Навигация
- [C4 L1 — контекст](01-context/c4-l1-context.drawio)
- [C4 L2 — контейнеры](02-containers/c4-l2-containers.drawio)
- [Объектная модель](03-data-model/er-model.drawio) · [типы сущностей](03-data-model/entities.md)
- [Схема интеграций](04-integrations/integration-landscape.drawio)
- Спецификации: [1С](04-integrations/spec-1c.md) · [телефония](04-integrations/spec-telephony.md) · [очередь](04-integrations/spec-queue.md)
- ADR: [001](05-adr/ADR-001-message-broker.md) · [002](05-adr/ADR-002-contract-entity.md) · [003](05-adr/ADR-003-versioning.md) · [004](05-adr/ADR-004-idempotency.md)
- [NFR](06-nfr/nfr.md)
- [One-pager](07-summary/architecture-summary.md)

## Ключевые решения
1. Договор — смарт-процесс, не сделка и не инфоблок.
2. Платежи в 1С — через RabbitMQ, не прямым REST.
3. Версии файлов — HL-блок + S3.
4. Идемпотентность — Redis-ключ с TTL 24ч.
