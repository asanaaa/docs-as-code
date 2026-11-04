# Диаграммы

## Диаграмма последовательности

```mermaid
sequenceDiagram
    actor User as Пользователь
    participant WebApp as Веб-сервис
    participant Assistant as ИИ-ассистент
    participant AI as ИИ-модель

    User->>WebApp: Открыть веб-сервис
    WebApp-->>User: Отобразить интерфейс

    Assistant->>WebApp: Запросить данные интерфейса
    WebApp-->>Assistant: Передать структуру страницы

    Assistant->>AI: Передать данные интерфейса для анализа
    AI-->>Assistant: Вернуть описание интерфейса

    User->>Assistant: Описать задачу
    Assistant->>AI: Передать задачу и данные интерфейса
    AI-->>Assistant: Вернуть последовательность действий

    Assistant-->>User: Показать первую подсказку
    User->>WebApp: Выполнить действие

    WebApp-->>Assistant: Передать обновлённое состояние
    Assistant->>AI: Запросить следующий шаг
    AI-->>Assistant: Вернуть следующую подсказку

    Assistant-->>User: Показать следующую подсказку
```

## Диаграмма классов

```mermaid
classDiagram
    class User {
        +int id
        +string name
        +string currentTask
        +describeTask()
        +receiveHint()
    }

    class WebService {
        +string url
        +string pageContent
        +getPageStructure()
        +updatePageState()
    }

    class AIAssistant {
        +int id
        +analyzeInterface()
        +processTask()
        +generateHint()
    }

    class AIModel {
        +string modelName
        +analyzePage()
        +generateInstructions()
    }

    class Hint {
        +int id
        +string text
        +int stepNumber
        +display()
    }

    User "1" --> "1" WebService : uses
    User "1" --> "1" AIAssistant : interacts
    AIAssistant "1" --> "1" WebService : analyzes
    AIAssistant "1" --> "1" AIModel : sends requests
    AIAssistant "1" --> "*" Hint : generates
    Hint "*" --> "1" User : receives
```