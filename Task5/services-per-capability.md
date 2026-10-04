# Сервисы по capability

«Продукт / сервис» - это модуль модульного монолита (ADR-001) или внешний продукт. Границы модулей заранее совпадают с будущими сервисами ([transition-architecture](transition-architecture.md)). Владельцы - потоки команды из [team-structure](team-structure.md): **App** (2 Flutter), **Core** (2 Go: коммерция и платежи), **Integrations** (1 Go: партнёры и каналы), **Platform** (1 SRE). Ответственные за решения - CTO и архитектор.

| Capability | Продукт / сервис | Владелец | Внешняя зависимость | Когда |
|-|-|-|-|-|
| 1.1 Идентификация и согласия | Модули `identity` (OTP, JWT) и `consent` (журнал согласий) | Core | SMS-агрегатор (OTP) | MVP |
| 1.2 Поиск и каталог | Модуль `catalog` (PostgreSQL FTS, deployment `catalog-read`) | Core | CDN | MVP |
| 1.3 Мобильное приложение | Flutter-приложение iOS и Android | App | App Store, Google Play, FCM/APNs | MVP |
| 1.3 USSD и SMS | Модуль `channels-ussd` | Integrations | Africa's Talking (кандидат), USSD-коды операторов | Месяц 3 (статус), месяц 12 (заказ) |
| 1.4 Уведомления | Модуль `notification` (outbox-воркеры, fallback каналов) | Integrations | WhatsApp BSP, SMS-агрегатор, FCM | MVP |
| 1.5 Маркетинг по согласию | Opt-in через `consent` + кампании в `notification` | Integrations | SMS-агрегатор (короткий номер) | MVP (opt-in), месяц 6 (кампании) |
| 1.6 Локализация | Ресурсы приложения и API, Weblate | App | Переводчики | MVP (EN, FR), месяц 6 (суахили), месяц 12 (хауса, йоруба) |
| 2.1-2.4 Товары, цены, флеш-распродажи, корзина, заказы, остатки | Модули `catalog`, `pricing`, `order`, `inventory` | Core | - | MVP |
| 3.1 Приём платежей | Модуль `payment` (оркестратор, ADR-004) | Core | M-Pesa Daraja, Flutterwave, Paystack | MVP |
| 3.2 Выплаты продавцам | Модуль `payout` (резерв на возвраты, B2C и Transfers) | Core | M-Pesa B2C, Flutterwave Transfers | MVP - выгрузка для массовой выплаты, месяц 3 - автоматизация |
| 3.3 Возвраты денег | Модуль `ledger` (кредит на баланс) | Core | PSP (возврат на карту) | MVP |
| 3.4 Сверка | Джоб `reconciliation` | Core | Отчёты PSP | MVP |
| 3.5 Антифрод | Правила в `payment` и `order` + скоринг PSP | Core | Скоринг Flutterwave и Paystack | MVP (правила), Год 1 (ML, Buy) |
| 4.1-4.2 Отправления и отслеживание | Модуль `delivery` (порт + адаптеры Sendbox, Sendy) | Integrations | Sendbox (NG), Sendy (KE) | MVP |
| 4.3 Адресация | Компонент выбора точки в приложении (Plus Codes + ориентир) | App | Карты: OSM-тайлы | MVP |
| 4.4 Пункты выдачи | Расширение `delivery` (пункт как тип адреса) | Integrations | Агентские точки логистов | Месяц 6 |
| 5.1 Онбординг и KYC продавца | Модуль `seller` + экраны бэк-офиса | Core | Год 1: KYC-провайдер (Smile ID - кандидат) | MVP (вручную), месяц 6 (WhatsApp-онбординг) |
| 5.2 Заказы продавца в WhatsApp | Модуль `channels-whatsapp` | Integrations | WhatsApp BSP | MVP (подтверждение заказа) |
| 5.3 Аналитика продавца | Модуль `seller-insights` по агрегатам | Core | - | Месяц 6-12 |
| 6.1 Резидентность и ПДн | Vault (токенизация), OPA / Kyverno, классификация полей | Platform | - | MVP |
| 6.2-6.4 Модерация, снятие, споры, верификация | Бэк-офис на Appsmith / Budibase поверх API модулей | Core | - | MVP |
| 6.5 Регуляторная отчётность | Генератор RoPA и audit return | Platform | - | Месяц 3 |
| 7.1 Дашборд руководства | Grafana по агрегатам, обновление раз в 1 мин | Platform | - | MVP |
| 7.2-7.3 Продуктовая аналитика, BI | PostHog и Metabase self-hosted в ячейке | Platform | - | Год 1 |
| 8.1-8.4 Платформа | Certified Kubernetes на ячейку, ArgoCD, CloudNativePG, MinIO, Valkey, OTel-стек | Platform | Локальные ЦОДы Лагоса и Найроби, AWS af-south-1 (глобальный слой) | MVP |
| Live-стрим (A2, обещание 7) | Диплинки на карточки + прогрев CDN перед эфиром | App | Внешняя стриминговая платформа | MVP |

## Assumptions

- Состав потоков (App / Core / Integrations / Platform) и ставки соответствуют [team-structure](team-structure.md) и модели TCO (вариант A).
- «Кандидаты» (Africa's Talking, Smile ID и другие) - не финальный выбор: закупка по процедуре A6, п. 2 (КП плюс названная альтернатива).
- Названия модулей - логические границы внутри одного бинарника монолита (ADR-001); выделение в отдельные сервисы происходит по триггерам из [transition-architecture](transition-architecture.md).
