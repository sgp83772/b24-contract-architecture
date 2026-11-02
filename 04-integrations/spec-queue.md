# Спецификация: RabbitMQ (брокер сообщений)

**Версия:** 1.0
**Дата:** 2026-11-02

## 1. Назначение
Развязать Bitrix24 и 1С по времени: портал не ждёт, пока 1С обработает платёж, а кладёт событие в очередь. 1С забирает, когда готова.

## 2. Топология
| Элемент | Имя | Назначение |
|---|---|---|
| Exchange | `b24.direct` | тип direct, durable |
| Queue | `payment.events` | события по платежам |
| Queue | `payment.dlq` | недоставленные |
| Routing key | `payment.created` | создание платежа |
| Routing key | `payment.confirmed` | подтверждение из 1С |

## 3. Формат сообщения
```json
{
  "event_id": "uuid",
  "event_type": "payment.created",
  "timestamp": "2026-11-02T10:15:00Z",
  "payload": {
    "payment_id": 12345,
    "invoice_id": 678,
    "contract_id": 90,
    "amount": 150000.00,
    "currency": "RUB",
    "payment_date": "2026-11-02"
  },
  "idempotency_key": "payment:12345:2026-11-02T10:00:00Z"
}
