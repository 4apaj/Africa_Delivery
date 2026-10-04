# Task 4. Регуляторные ограничения и стратегия данных

| Артефакт | Файл |
|-|-|
| Требования по странам: факт, допущение, открыто | [regulatory-requirements.md](regulatory-requirements.md) |
| Data Residency Map (шаблон 3) | [data-residency-map.md](data-residency-map.md) |
| Сравнение облачных регионов | [cloud-regions-comparison.md](cloud-regions-comparison.md) |
| ADR-003 «Стратегия размещения данных» с разделом об обратимости | [adr-003-data-residency.md](adr-003-data-residency.md) |
| C4 Container Diagram по регионам | [c4-container.puml](c4-container.puml) → [c4-container.png](c4-container.png) |
| Deployment Diagram | [deployment-diagram.puml](deployment-diagram.puml) → [deployment-diagram.png](deployment-diagram.png) |
| Высокая доступность и план переключения | [failover-plan.md](failover-plan.md) |

Как мы действуем без точных требований: проектируем под **самое строгое прочтение**. ПДн, платёжные данные, бэкапы, логи и ключи остаются в стране субъекта, в страновой ячейке у локального провайдера. Размещение каждого класса данных задано **политикой как код**. Заключение юриста (05.09–19.09) смягчает конфигурацию, а не переписывает систему. Шифрование — дополнительная мера, а не основание для вывоза.
