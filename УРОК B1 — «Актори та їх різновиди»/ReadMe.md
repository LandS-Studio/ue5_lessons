## 📄 Урок B-1 — «Актори та їх різновиди»  
*(StaticMesh, SkeletalMesh, Light, Camera, Trigger, Volume, Custom Blueprint)*  

### 1. Короткий опис
На цьому уроці ми розглянули, що таке **Actor** в Unreal Engine 5 і чим відрізняються
найуживаніші типи — від звичайного статичного меша до спеціалізованих світильників
та камер. Головна ідея: Actor — це контейнер із Transform, а **функції** приходять через
компоненти.

| Що зробили | Що навчилися |
|------------|--------------|
| Порівняли StaticMeshActor і SkeletalMeshActor | Статичні ≠ анімовані: другі мають Skeleton & Animation Mode |
| Додали PointLightActor | Налаштували інтенсивність, колір, радіус |
| Використали CameraActor | Зберегли ракурс закладками Ctrl + 1…9 |
| Дослідили Trigger Box | Увімкнули Generate Overlap Events |
| Показали PostProcessVolume | Локальна тон-корекція без коду |
| Через World Outliner відфільтрували Lights | Швидко шукаємо об’єкти за типом |

---

### 2. Q&A

| Питання | Відповідь |
|---------|-----------|
| **Чому StaticMeshActor не відтворює анімацію?** | У нього немає скелетних кісток. Використовуйте **SkeletalMeshActor** або Character. |
| **Мій Trigger Box не спрацьовує при зіткненні.** | Переконайтесь, що **Generate Overlap Events** увімкнено в Details і у вас не вимкнений Collision канал Pawn/WorldDynamic. |
| **Чи можна перетворити StaticMeshActor на SkeletalMeshActor?** | Ні, клас актора не змінюється. Створіть новий SkeletalMeshActor і скопіюйте Transform. |
| **Як прибрати прев’ю у CameraActor?** | Вкладка **Details → Camera Options → Draw Frustum** → вимкнути Preview Frustum. |
| **PostProcessVolume діє на всю сцену, а не тільки всередині.** | Зніміть прапорець **Infinite Extent (Unbound)** у Details. |

---

### 3. Лайфхаки / Рекомендації

- **Швидка заміна Mesh.** Ctrl + Drag будь-який Static Mesh із ContentBrowser прямо на StaticMeshActor у Viewport — мить і модель підмінено без втрати матеріалів.
- **Камера як зйомний девайс.** Поєднайте CameraActor із **CineCameraComponent** — отримуєте depth-of-field, f-stop і ISO як у реальній оптиці.
- **Trigger Box у 10× разів легший за Box Collision.** Для зони події використовуйте саме Trigger Actors — вони не беруть участі у фізиці.
- **Post-process LUT за 30 с.** У PostProcessVolume → вкладка Color Grading → забийте 256×16 PNG-LUT, згенерований у Photoshop — миттєва стилізація сцени.
- **Групування в Outliner.** Виділіть кілька Actor → Ctrl + G -> отримуєте пустий «Folder Actor» для колективного переміщення/масштабування.

---
