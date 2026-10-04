# Task 5. MVP Roadmap и Build / Buy / Partner

| Артефакт | Файл |
|-|-|
| Capability Map (L1/L2 + Build / Buy / Partner с расчётом) | [capability-map.md](capability-map.md) |
| Value Stream | [value-stream.puml](value-stream.puml) → [value-stream.png](value-stream.png) |
| Сервисы по capability | [services-per-capability.md](services-per-capability.md) |
| Roadmap: месяц 1, 2 (MVP), 6, 12 и разбор 29 функций | [roadmap.md](roadmap.md), [roadmap.mmd](roadmap.mmd) → [roadmap.png](roadmap.png) |
| ADR-004 «Выбор платёжного провайдера» | [adr-004-payment-provider.md](adr-004-payment-provider.md) |
| Transition Architecture | [transition-architecture.md](transition-architecture.md), [transition-architecture.puml](transition-architecture.puml) → [png](transition-architecture.png) |
| Реестр рисков | [risk-register.md](risk-register.md) |
| Оргструктура, удалёнка или офис, дежурства 24/7 | [team-structure.md](team-structure.md) |

## Готовы ли мы к встрече в Найроби?

**Да — если на встрече будут приняты четыре решения. Без них план не выполним, и мы честно говорим, где он ломается.**

| Что готово | Чем подтверждается |
|-|-|
| План запуска 15.10 в $4 750/мес силами 6 контракторов | 44,5 из 48 человеко-недель, запас 7 %, лестница сокращений ([roadmap](roadmap.md)) |
| Из 29 функций PM: 3 в MVP полностью, 7 частично, 15 перенесены, 4 отклонены | Критерии K1–K4: успех по A1, обещания A2, законность A3, ёмкость и бюджет A6 |
| Позиция CTO разобрана по цифрам | Своя логистика: 104 пн против 48 пн до запуска, окупается с Года 2 (≈ 1,16 млн отправлений в год) — отложена с триггером. Прямое подключение к M-Pesa принято: −2 п.п. комиссии, ~$90k в год. Свой эквайринг отклонён: лицензия |
| Издержки на платежи ≤ 2,5 % GMV | 1,46 % взвешенно, ≤ 1,67 % в каждой стране ([ADR-004](adr-004-payment-provider.md)) |
| Путь к 5 странам без переписывания | Шаблон ячейки, порты и адаптеры, политика резидентности как код ([transition-architecture](transition-architecture.md)) |

| Решение, без которого план ломается | Кто | Срок | Если нет |
|-|-|-|-|
| SLO 99,9 % на запуске вместо «не падает никогда» | К. Орлов | 18.08 | Бюджет ×1,3 и +3 SRE ([Task3](../Task3/availability-strategy.md)), иначе запуск 15.10 срывается |
| Закупка площадок, аварийный лимит, операторы бэк-офиса | А. Вебер | 21.08 | Площадки не готовы к 22.09 (R-04) — сдвиг запуска |
| Письмо A5 — целевое состояние с триггерами, а не стартовая архитектура | Р. Менон | 18.08 | Раскол в руководстве (R-10), scope ×2 |
| Scope 15.10 по критериям K1–K4, и купленная база не используется | М. Лефевр, С. Алмейда | 18.08 | Перегруз команды (R-02), санкции регулятора (C-08) |
