# Task 2. Architecture Vision и выбор архитектурного стиля

| Артефакт | Файл |
|-|-|
| Сравнение вариантов | [options-comparison.md](options-comparison.md) |
| Модель TCO на 5 лет: листы на каждый вариант, «Сравнение», «Цена ошибки» | [tco-model.xlsx](tco-model.xlsx) |
| ADR-001 «Выбор архитектурного стиля» | [adr-001-architecture-style.md](adr-001-architecture-style.md) |
| C4 Context Diagram | [c4-context.puml](c4-context.puml) -> [c4-context.png](c4-context.png) |
| Use Case Diagram (MVP) | [use-cases.puml](use-cases.puml) -> [use-cases.png](use-cases.png) |
| Architecture Vision | [architecture-vision.md](architecture-vision.md) |
| Слайд и транскрипт для Найроби | [nairobi-slide.pptx](nairobi-slide.pptx) ([pdf](nairobi-slide.pdf)), [nairobi-script.md](nairobi-script.md) |

Диаграммы рендерятся так: `docker run --rm -v "$PWD":/data -w /data plantuml/plantuml -tpng -charset UTF-8 c4-context.puml use-cases.puml`.
