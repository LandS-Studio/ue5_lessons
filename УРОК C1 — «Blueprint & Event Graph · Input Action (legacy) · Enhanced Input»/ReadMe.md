## Урок «Blueprint & Event Graph · Input Action (legacy) · Enhanced Input»

### Короткий опис
> Повний маршрут від першої ноди до інтеграції сучасної системи вводу в UE5.

| Блок | Що вивчаємо | Практика |
| :- | :- | :- |
| **Blueprint Fundamentals** | Класи, компоненти, viewport | Огляд Blueprint редактора |
| **Event Graph** | Потік виконання, послідовність | Логіка руху даних по Blueprint нодам |
| **Input Action (legacy)** | Axis & Action Mappings, `InputAxis`, `InputAction` | Налаштовуємо спрацювання клавіші та виводимо дані через Print String |
| **Enhanced Input** | `Input Action` asset, `Input Mapping Context`, модифікатори & тригери | Робимо переключення між різними Input Mapping Context |

---

### Q&A

| Питання | Відповідь |
| --- | --- |
| **Чому ноди `InputAxis` не спрацьовують?** | Переконайтеся, що в Project Settings → Input створені Axis Mappings і назви збігаються з нодою. |
| **Enhanced Input не бачить моїх дій у грі. Чому?** | Додайте `Input Mapping Context` у `PlayerController` (або `Pawn`) через `Enhanced Input Local Player Subsystem → Add Mapping Context`. |
| **Яку систему вибрати: legacy чи Enhanced?** | Legacy підтримується для сумісності, але Epic рекомендує **Enhanced Input** для нових проєктів – гнучкі тригери, контекстні мапи, підтримка SteamDeck/консолей «із коробки». |
| **Що таке модифікатор у Enhanced Input?** | Це функція обробки значення вводу (наприклад Scale, Dead Zone) **до** застосування його в грі. |
| **Чи можна міксувати обидві системи?** | Так, але краще мігрувати повністю – інакше важче дебажити конфлікти мапінгів. |

---

### Лайфхаки та рекомендації
 
- **Context-Sensitive ON/OFF:** вимикайте “Context Sensitive” у пошуку нод, коли шукаєте Input-події в сторонніх BP-класах.  
- **Instant Debug:** у Enhanced Input поставте `Log` триггер напряму у `Input Action` asset – бачите, спрацьовує чи ні без PrintString у графі.  
- **Single Responsibility:** тримайте виклики Input тільки у *PlayerController* або *Pawn*, а логіку — у компонентах / інших BP.  
- **Default Value Preview:** назначте значення змінних у Class Defaults, щоб при спавні BP мав коректні параметри (Velocity, Jump Height).  
- **Геймпад & KB/M:** у Enhanced Input робіть *окремі* `Mapping Context` для контролера та клавіатури – тоді UI легко перемикає пресети.

> Починайте з чистого Event Graph, додавайте Input-події послідовно й одразу переходьте на Enhanced Input — так витратите менше часу на рефактор.
