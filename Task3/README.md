# Task 3. Нефункциональные требования и стратегия доступности

| Артефакт | Файл |
|-|-|
| Экономика доступности: сколько стоит каждая девятка и где останавливаемся | [availability-strategy.md](availability-strategy.md) |
| Реестр НФТ (29 требований, включая критерии Cloud Native) | [nfr-registry.md](nfr-registry.md) |
| SLO-контракты (SLI / SLO / SLA, OpenSLO) | [slo/catalog.md](slo/catalog.md), [slo/payments.md](slo/payments.md), [slo/notifications.md](slo/notifications.md) |
| Quality Attribute Scenarios (7 сценариев) | [quality-attribute-scenarios.md](quality-attribute-scenarios.md) |
| FMEA (12 точек отказа, из них 8 — партнёры и внешняя среда) | [fmea.md](fmea.md) |
| ADR-002 «Стратегия кеширования» | [adr-002-caching-strategy.md](adr-002-caching-strategy.md) |
| Наблюдаемость | [observability.md](observability.md), схема: [observability.puml](observability.puml) → [observability.png](observability.png) |

Главный вывод: на запуске 99,9 % для пути «заказ и оплата» — единственная ступень, которая окупается при реальной стоимости минуты ($114 в Году 1) и помещается в лимит CFO. 99,95 % включается в Году 2 (GMV ≥ $37 млн), 99,99 % для оплаты — в Году 3–4 (GMV ≥ $142 млн).
